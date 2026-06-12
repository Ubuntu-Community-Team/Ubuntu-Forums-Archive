---
title: "[SOLVED] Error after &amp;quot;TwinView&amp;quot;"
date: 2007-10-23
forum: General Help
---

### Post by Amazona aestiva on 2007-10-23
Hi, I've got a GeForce 7300GS, and after I enabled the S-video out with TwinView option, GridWars says this:

> nandor@nandor-desktop:~$ gridwars
Unable to calculate tex size
nandor@nandor-desktop:~$ 

I've tried with disabled the S-video, but got same error:(

What should I do?

---

### Post by Amazona aestiva on 2007-10-24
I've reconfigure the xorg -> it works again!:)

---

### Post by chm0d on 2007-12-25
Can you post what you did to fix this in your xorg?  I am running twinview as well and I am getting the same error.  TIA

Rich

---

### Post by Amazona aestiva on 2007-12-26
I'm not sure, but try this:
```
sudo dpkg-reconfigure xserver-xorg
```

Let me know if doesn't work.

---

