---
title: "Update Manager Problem"
date: 2007-07-20
forum: General Help
---

### Post by Di@blo on 2007-07-20
On my laptop, update manager would build the dependency tree and everything, but as soon as that little progress box dissapeared, I would get this message, and then update manager would close, but it's not that big of a deal because I did a clean re-installation on it:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

On my desktop, I can see the updates but when I hit install, I get the same message. I hit "close", and it rebuilds the dependency tree, and basically starts over. 

I'm currently running Feisty Fawn 7.04

No, I did not install any piece of software that would cause this/tinker around.  The wierd thing is that I never did anything on my laptop that I did on my desktop, if I caused it myself.

---

### Post by Seisen on 2007-07-20
Put ```
sudo dpkg --configure -a 
``` in the termnal.

---

### Post by Di@blo on 2007-07-20
> **Seisen said:**
> Put ```
sudo dpkg --configure -a 
``` in the termnal.

Thank you so much. I think this should be stickied.

I think it has to do with downloaded software packages that are never installed. I remember that on my laptop, there was a problem with the Nvu installation, and on my desktop, I had stopped my VMware Server Installation.

---

### Post by Seisen on 2007-07-20
That has come up on the forum so many times its not even funny.

---

