---
title: "Cannot suspend the PC on Ubuntu 7.10"
date: 2007-11-03
forum: General Help
---

### Post by PmDematagoda on 2007-11-03
I seem to be having a problem suspending Ubuntu 7.10, the OS does suspend properly, but when I want to resume using the OS it just will not come back, I've tried pressing different buttons on the keyboard, pressing the Power button, but nothing:(. Does anyone know how to solve this problem?

---

### Post by trippinnik on 2007-11-03
Doesn't seem to be any fixes I can find.  If you're using the ATI fglrx driver I guess the newest one is supposed to work.  My PC uses the open source driver so the only fix I've been able to get to work is to switch to vesa, unfortunately that means that video is basically unwatchable.  Did it work for you in feisty?  You could go back and also file a bug report.

---

### Post by PmDematagoda on 2007-11-03
I do know about the ATi driver bug, but as I use an Nvidia card this doesn't apply to me.

---

### Post by #Reistlehr- on 2007-11-03
Don't hold your breathe. There are a million possible fixes, and half the time, what helps a few people, only makes it worse for others.

All i can suggest is play around with the settings in 

/etc/default/acpi-support

---

### Post by PmDematagoda on 2007-11-03
I have options, but messing acpi-support is not one of them. While my signature suggests experimenting, I do need at least one OS to work and in my case it is my Ubuntu 7.10 X64. But thanks for your suggestion anyway:).

---

### Post by shanepardue on 2007-11-03
I experience the same problem..Unfortunately there are just soo many threads and I don't even know where to begin on getting the issue resolved.

---

### Post by strabes on 2007-11-03
> **shanepardue said:**
> I experience the same problem..Unfortunately there are just soo many threads and I don't even know where to begin on getting the issue resolved.

The best thing you could do is send a letter to the manufacturers of each of your pieces of hardware asking them to provide specs of their hardware to the community or even better, linux drivers. It is my impression that a big reason why suspend & hibernate has so much trouble in linux is the fact that a lot of drivers have been reverse engineered.

---

