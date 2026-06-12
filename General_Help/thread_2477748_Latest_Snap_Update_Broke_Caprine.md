---
title: "Latest Snap Update Broke Caprine"
date: 2022-08-05
forum: General Help
---

### Post by Mark76 on 2022-08-05
> caprine
A JavaScript error occurred in the main process
Uncaught Exception:
Error: Cannot find module 'electron-util/main'
Require stack:
- /snap/caprine/49/resources/app.asar/dist-js/index.js
- 
    at Module._resolveFilename (internal/modules/cjs/loader.js:961:15)
    at Function.o._resolveFilename (electron/js2c/browser_init.js:257:921)
    at Module._load (internal/modules/cjs/loader.js:844:27)
    at Function.Module._load (electron/js2c/asar.js:779:28)
    at Module.require (internal/modules/cjs/loader.js:1023:19)
    at require (internal/modules/cjs/helpers.js:77:18)
    at Object.<anonymous> (/snap/caprine/49/resources/app.asar/dist-js/index.js:12:16)
    at Module._compile (internal/modules/cjs/loader.js:1145:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1166:10)
    at Module.load (internal/modules/cjs/loader.js:981:32)



Solutions?

---

### Post by deadflowr on 2022-08-05
Looking at *snap info caprine* it seems it was updated today.
Try reverting it 
```
snap revert caprine
```

Unfortunately, snap info shows no contact information to report issues.
(Only lists the publisher, and only by name, no email)

Reverting it keeps the reverted version as the one in use until the next time an update comes.
(or at least that has been my experience)

Also, this answer should help explain the generals of if you need to revert to a specific version: 
[https://askubuntu.com/a/1225257]("https://askubuntu.com/a/1225257")
though not specific to caprine, the basics are there.

---

### Post by Mark76 on 2022-08-05
Uh oh, I don't have a previous version to revert to :(

---

### Post by Mark76 on 2022-08-05
It's also available as a deb from [https://github.com/sindresorhus/caprine/releases/download/v2.16.0/caprine_2.16.0_amd64.deb](https://github.com/sindresorhus/caprine/releases/download/v2.16.0/caprine_2.16.0_amd64.deb) 

I installed that and now I get 

> caprine
Segmentation fault (core dumped)


---

### Post by deadflowr on 2022-08-05
Any reason you went with the older version instead of a newer release like 2.55.6?
The broken snap version shows for 2.55.7, so maybe the last one that worked was 2.55.6.
[https://github.com/sindresorhus/caprine/releases/tag/v2.55.6]("https://github.com/sindresorhus/caprine/releases/tag/v2.55.6")

---

### Post by Mark76 on 2022-08-05
I didn't look at the version number

---

### Post by Mark76 on 2022-08-05
2.55.6 works

---

