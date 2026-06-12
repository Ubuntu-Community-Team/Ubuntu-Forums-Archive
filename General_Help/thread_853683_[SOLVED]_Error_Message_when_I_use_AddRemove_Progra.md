---
title: "[SOLVED] Error Message when I use Add/Remove Programs"
date: 2008-07-08
forum: General Help
---

### Post by VexVishnu on 2008-07-08
Whenever I try to remove programs with Add/Remove Programs I get this error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to put dpkg --configure -a but it tells me I need to be a superuser.

I don't know if this has anything to do with it, but at the same time I developed this problem my Firefox's close, maximize, and minimize buttons (along with the entire top bar) disappeared, and while I'm online my screen continuously blinks black.

HALP PLEASE!!!

---

### Post by iaculallad on 2008-07-08
Open your terminal and use the command below:

```
sudo dpkg --configure -a
```

After the process is finished, try using/accessing Add/Remove Programs.

---

### Post by VexVishnu on 2008-07-08
Ok, I'll try that out.

---

### Post by VexVishnu on 2008-07-08
Mwahahaha! Thank you SOOOO MUCH!!!

---

### Post by iaculallad on 2008-07-08
> **VexVishnu said:**
> Mwahahaha! Thank you SOOOO MUCH!!!

You're welcome. Remember to use **sudo** when using terminal commands that uses "root" authentications.

Also, **gksudo** when using graphical applications that needed "root" authentication to perform tasks.

Goodluck.

---

