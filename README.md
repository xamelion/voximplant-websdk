This SDK works with [VoxImplant](https://voximplant.com) cloud platform for real-time communication app development. Browser-compatible, won't work on server. The SDK uses WebRTC in WebRTC-enabled browsers (Chrome, Firefox, Opera, etc).

<a href="https://voximplant.com/docs/references/websdk/">Documentation</a>.

<a href="https://voximplant.com/docs/references/websdk/using-voximplant-web-sdk">Quickstart</a>.

<a href="https://voximplant.com/blog/howto">Platform's HowTo's</a>.

## Installation

```bash
npm install voximplant-websdk --save
# OR
yarn add voximplant-websdk
```
CDN version
```html
<script type="text/javascript" src="//cdn.voximplant.com/edge/voximplant.min.js"></script>​
```


Importing:

```js
import * as VoxImplant from 'voximplant-websdk';
```

## First steps
Below you can see two simple client scripts with full initialization of the WebSDK

### Create call
```js
import * as VoxImplant from 'voximplant-websdk';

const customerName = 'foo',
      appName = 'bar',
      userName = 'baz',
      password = 'securepass';

const sdk = VoxImplant.getInstance();
sdk.init()
    .then(ev=>sdk.connect(false))
    .then(ev=>sdk.login(`${customerName}@${appName}.${userName}.voximplant.com`, password))
    .then(ev=>{
      // Now we ready for your first audio only call
      sdk.call({number:'anotherCustomer',video:{sendVideo:false,receiveVideo:false}});
    })
```

### Answer for incoming call

```js
import * as VoxImplant from 'voximplant-websdk';

const customerName = 'foo',
      appName = 'bar',
      userName = 'baz',
      password = 'securepass';

const sdk = VoxImplant.getInstance();
sdk.init()
    .then(ev=>sdk.connect(false))
    .then(ev=>sdk.login(`${customerName}@${appName}.${userName}.voximplant.com`, password))
    .then(ev=>{
      // Now we ready for processing incoming calls
      sdk.on(VoxImplant.Events.IncomingCall,ev=>{
        ev.call.answer('',{},{sendVideo:false,receiveVideo:false});
      })
    })
```
