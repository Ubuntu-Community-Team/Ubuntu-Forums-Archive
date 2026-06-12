---
title: "Reinstall NodeJS and npm"
date: 2016-03-26
forum: General Help
---

### Post by meetdilip on 2016-03-26
I installed NodeJS and npm in 14.04 in the hope of setting up Ionic  Framework. But there seems to be something wrong and I was told to  reinstall NodeJS and npm. Can someone please give me the commands to do  the same ?

I used the following commands to install it

```

sudo apt-get install curl 

curl --silent --location [deb.nodesource.com/setup_5.x]("https://deb.nodesource.com/setup_5.x") | sudo bash - 

sudo apt-get install nodejs
```

---

### Post by cariboo on 2016-03-27
Might this have something to do with your problem?

[http://arstechnica.com/information-technology/2016/03/rage-quit-coder-unpublished-17-lines-of-javascript-and-broke-the-internet/](http://arstechnica.com/information-technology/2016/03/rage-quit-coder-unpublished-17-lines-of-javascript-and-broke-the-internet/)

---

### Post by meetdilip on 2016-03-27
Don't know. This is what I get when I try to start an Ionic Project

```
$ ionic start myApp1 blank
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


I tried to reach npm via GitHub raising an issue as seen in link below. I couldn't find a solution though

[https://github.com/npm/npm/issues/12073#issuecomment-201622045](https://github.com/npm/npm/issues/12073#issuecomment-201622045)

---

