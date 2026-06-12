---
title: "Two Xorg processes (details inside)"
date: 2007-06-05
forum: General Help
---

### Post by shae on 2007-06-05
For some reason my laptop shows that there are two xorg processes running at the same time.  Is this normal?  On my other computers with feisty, they have only one running.  I attached xorg's log and conf files.  I have the following hardware:

Acer 5102
Turion x2 1.6
2gb of ram
Radeon Xpress 1100

I have the following customizations made:
I am running a custom compiled kernel, version 2.21.0 + viper2 patches.
I am running updated drivers from AMD/ATI's site, compiled against my current kernel.
I am running madwifi 9.3.1 compiled against my current kernel.

I doubt it is tied to the kernel because it was occurring before I used the custom one or used updated drivers.  I am not experiencing any problems that I can notice, but I am just curious.  Thank you for your help.

---

### Post by shae on 2007-06-07
Bump

Could this be tied to having a dual core processor?

---

### Post by borahshadow on 2007-06-07
I have a dual coer processor and one process so no 
Do you have multiple users that could cause it mabey
IDK i'm just stabbing in the dark

---

### Post by shae on 2007-06-14
Nope, single user.  But when I ended up reinstalling for an unrelated matter, I am back down to one.

---

### Post by jmoorse on 2007-09-27
**EDIT: An install of Version 8.40 from ATI's site fixed the issue**

Same issue, some digging shows it appears to be the fglrx v8.39.4-1 driver:

[http://www.debianhelp.org/node/10057](http://www.debianhelp.org/node/10057)

Apparently the message here is to use the open source alternative, or dumb down to vesa.

Cheers

---

