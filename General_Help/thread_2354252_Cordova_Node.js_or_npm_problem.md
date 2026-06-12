---
title: "Cordova Node.js or npm problem"
date: 2017-03-01
forum: General Help
---

### Post by stepheny on 2017-03-01
I have been told by Google to upgrade my Apps to a more recent version of Cordova than 3.1.5. The latest version is 6.1.0. I have tried several later versions on my Ubuntu 16.04 laptop but cannot get any of them to work though I have always used earlier versions of Cordova on this same laptop. The problem seems to be with Node.js. When I get to run "cordova build" I get the following errors.

```
$ cordova build
Error: Cannot find module 'internal/fs'
    at Function.Module._resolveFilename (module.js:470:15)
    at Function.Module._load (module.js:418:25)
    at Module.require (module.js:498:17)
    at require (internal/module.js:20:19)
    at evalmachine.<anonymous>:18:20
    at Object.<anonymous> (/usr/share/cordova-cli/node_modules/cordova-lib/node_modules/glob/node_modules/graceful-fs/fs.js:11:1)
    at Module._compile (module.js:571:32)
    at Object.Module._extensions..js (module.js:580:10)
    at Module.load (module.js:488:32)
    at tryModuleLoad (module.js:447:12)
```
I have tried various versions of Cordova and am presently running cordova-cli version 4.3.1-ubuntu12 from the Ubuntu repositories installed via Synaptic.

I have spent hours on Google reading other peoples solutions for this problem which usually involves changing the versions of node.js and npm, see this example of a thread on the topic. [https://github.com/nodejs/node/issues/9377](https://github.com/nodejs/node/issues/9377) But none of them have worked for me,

I am presently using node v7.6.0 and npm v4.1.2 though I have tried many other combinations.

I would really appreciate any advice on fixing this issue in order to put my free apps back on Google play and to be able to continue to develop Apps using javaScript

---

### Post by stepheny on 2017-03-02
I have solved the problem described by removing cordova-cli and installing Cordova via npm like this: 

   ```
 sudo npm install -g cordova
```

---

