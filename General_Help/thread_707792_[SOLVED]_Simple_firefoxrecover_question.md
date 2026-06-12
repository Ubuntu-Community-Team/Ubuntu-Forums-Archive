---
title: "[SOLVED] Simple firefox/recover question"
date: 2008-02-25
forum: General Help
---

### Post by uberlube on 2008-02-25
Hi guys, I am using PartedMagic to save some important files on my sda2 before I perform a clean install as I was unable to log into Linux today. I was going over all the stuff that I wanted to save when it hit me, what about my firefox bookmarks. Its a real pain in the *** to have to find them all over again and I figured that they have got to be saved somewhere in either root or /home, but so far cant find them. Any suggestions?

---

### Post by lluisanunez on 2008-02-25
/home/your_user/.mozilla/firefox/default/bookmarks.html

---

### Post by aysiu on 2008-02-25
They should be in /home/uberlube/**.mozilla**/*profilename*/bookmarks.html

*profilename* is some gobbledygook. Mine is 6z7u82ub.default, for example.

The bolded folder (.mozilla) is a hidden folder. If you press Control-H, you should see it.

---

### Post by uberlube on 2008-02-25
Thank you kindly!:biggrin:

---

### Post by warbird on 2008-02-25
or just do a "locate bookmarks.html" (if your db is up to date. else do "updatedb && locate bookmarks.html)

---

### Post by aysiu on 2008-02-25
> **warbird said:**
> or just do a "locate bookmarks.html" (if your db is up to date. else do "updatedb && locate bookmarks.html)
Wouldn't that need to have a *sudo* in there? ```
sudo updatedb && locate bookmarks.html
```

---

### Post by warbird on 2008-02-25
ah yes, I just wrote the locate part first, and then added the updatedb part just in case, and forgot about that since "locate" doesnt need sudo

---

