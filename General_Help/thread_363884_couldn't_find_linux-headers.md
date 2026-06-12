---
title: "couldn't find linux-headers"
date: 2007-02-17
forum: General Help
---

### Post by jmvidalvia on 2007-02-17
I am trying to compile an ATI driver, but get a linux-headers mistake.
I If use module-assistant get this message:
**Couldn't find linux-headers-2.6.15-28-386** (I'm translating form spanish)
My uname -vr:
2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007

¿any idea about how to solve this?
Thanks!

---

### Post by solar george on 2007-02-17
Try 
```
sudo apt-get install linux-headers-generic
```

---

### Post by jmvidalvia on 2007-02-17
Not found!
I have all ordinary repositories: restricted and multiverse
Thanks, any how...
When I start wit kernel 2.6.15-27-386, I see in synaptic that linux-headers 2.6.15-27-386 are instaled.
When I boot with 2.6.15-28-386, linux-headers simply are not there...
:(

---

### Post by solar george on 2007-02-17
Update you kernel.

In synaptic press the reload button then click mark all upgrades ( if it asks you select smart upgrade) then press apply.

If you are on edgy your kernel should be 2.6.17.

Hope this helps

---

### Post by jmvidalvia on 2007-02-17
Thank you!
I downloaded linux-headers from [http://packages.ubuntulinux.org](http://packages.ubuntulinux.org)
I am installing them now.
My question is: I am running dapper, so...
Should I update my kernel?
My system seems to be updated with my present kernel 2.6.15-28
Thanks again!

---

### Post by solar george on 2007-02-17
If you are using dapper stick with your current kernel.

Change your version in your profile - it says that you are using edgy.

---

### Post by jmvidalvia on 2007-02-17
Thank you.
Sorry for the missunderstanding.
In fact, I use kubuntu-dapper, and ubuntu-edgy and xubuntu-edgy (my prefered), so can not update my profile with so much information.
Best regards,

---

