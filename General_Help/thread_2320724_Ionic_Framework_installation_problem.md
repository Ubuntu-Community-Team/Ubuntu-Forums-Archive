---
title: "Ionic Framework installation problem"
date: 2016-04-16
forum: General Help
---

### Post by meetdilip on 2016-04-16
I use Ubuntu 14.04. I followed a few guides available online to install Ionic in Ubuntu 14.04 LTS. I could go as far as using the command 

```
  ionic start myApp1 blank

 


```  but it throws an error everytime. I checked with nodejs team. They  seem to believe it has something to do with setting up framework. The  following is the error I get
  ```
`$ ionic start myApp1 blank
module.js:341
    throw err;
    ^

Error: Cannot find module 'archiver'
    at Function.Module._resolveFilename (module.js:339:15)
    at Function.Module._load (module.js:290:25)
    at Module.require (module.js:367:17)
    at require (internal/module.js:16:19)
    at Object.<anonymous> (/usr/local/lib/node_modules/ionic/node_modules/ionic-app-lib/lib/utils.js:3:16)
    at Module._compile (module.js:413:34)
    at Object.Module._extensions..js (module.js:422:10)
    at Module.load (module.js:357:32)
    at Function.Module._load (module.js:314:12)
    at Module.require (module.js:367:17)
```  

I even tried

```
sudo apt-get install archiver
```

Plese help me fix it

---

