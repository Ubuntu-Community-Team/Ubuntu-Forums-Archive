---
title: "Live CD Trouble"
date: 2007-01-09
forum: General Help
---

### Post by brochill18 on 2007-01-09
Hello all,

I have tried everything simple in order to make the Live CD for Ubuntu 6.10 work on my desktop, along with 6.06, and I have failed so far.  My problem is as follows.  I can boot the operating system, but as soon as everything is loaded, my computer freezes.  At the exact same spot every time, which is about 5-20 seconds after the OS boots.  I figure it may have been shoddy RAM but that's not it, because I used my one good stick of RAM and had the same problem.  I have been told to try passing ACPI at the start but I'm not even sure how to do that.  My system specs are as follows if they help, if its a hardware problem.  Thanks in advance for any help, I really want Linux working because I'm tired of Windows!  :confused: 

nForce 3 Chaintech motherboard
AMD64 3200+ 2.2GHz, socket 754
1GB Corsair value RAM
40GB IDE hard drive
Sony CD drive

---

### Post by bigken on 2007-01-09
its probablys your video drivers what is your video card ?

---

### Post by bigken on 2007-01-09
have you tried the alternate cd ?

---

### Post by brochill18 on 2007-01-09
My video card is a GeForce 5900XT, sorry that I forgot that.  I figured it would be covered by Ubuntu but maybe that's the problem.  As for the alternate CD, will that let me run it as a Live CD or is it strictly for installation?

---

### Post by meng on 2007-01-09
> **brochill18 said:**
> My video card is a GeForce 5900XT, sorry that I forgot that.  I figured it would be covered by Ubuntu but maybe that's the problem.  As for the alternate CD, will that let me run it as a Live CD or is it strictly for installation?
It's an installation-only affair. There are other live CDs for other distros...

---

### Post by brochill18 on 2007-01-09
I have tried the other distros, same problem, it freezes upon startup.  Maybe it really is the video card...:confused:](*,)  Are there any other possibilities for the freezing?

---

### Post by meng on 2007-01-09
Regarding boot options:
There should be an option to specify boot options, and the list of boot options can be brought up with one of the F-keys. Look at options like
noacpi, noapic, nolapic, safe graphics.

---

### Post by brochill18 on 2007-01-09
I tried the noacpi at the boot options, I tried safe graphics, still freezing.  AHH! :(

---

### Post by bigken on 2007-01-09
unplug everything ie printers usb devices ect :-k

---

