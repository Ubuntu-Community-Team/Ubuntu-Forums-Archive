---
title: "Where firefox saved cache in ubuntu  ?"
date: 2024-08-24
forum: General Help
---

### Post by nilovsergey on 2024-08-24
Where  firefox have cache subfolder in kubuntu 22  ?
Giogling I found a ref to 
```
    ~/.mozilla/firefox/*.default/Cache

```subdirectory, but looks like this is not valid now...
Also clear all cache inside of firefox  ?
The reason is that with firefox having a lot of  cache it slows my OS...

---

### Post by currentshaft on 2024-08-24
I doubt the Firefox "cache" is slowing down your OS.

What actual problem are you having and what evidence actually points to Firefox?

---

### Post by deadflowr on 2024-08-24
Ubuntu's default Firefox is a snap package, so the cache folder is in snap/firefox/common/.cache/mozilla/proflie-name-here.default.

But you can also clear it from within Firefox by going to Settings > Privacy and Security and scroll down to Cookies and Site Data.

---

### Post by ajgreeny on 2024-08-24
And should you still be using a .deb version of FF or running it from the extracted .tar.bz2 direct from Mozilla you will find the FF cache in **~/.cache/mozilla/firefox**

---

