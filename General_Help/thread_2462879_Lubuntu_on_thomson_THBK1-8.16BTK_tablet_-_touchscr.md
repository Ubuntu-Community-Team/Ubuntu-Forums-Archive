---
title: "Lubuntu on thomson THBK1-8.16BTK tablet - touchscreen support"
date: 2021-05-29
forum: General Help
---

### Post by eniac314 on 2021-05-29
Hi folks,

I have successfully installed lubuntu 20.04 on the tablet but some hardware does not seem to be recognized. Most notably the touch screen does not work. The tablet comes with a dockable keyboard (working fine) but no mouse.
Is there anything I could install that would allow me to use the touch capabilities?

---

### Post by dddman on 2021-05-29
According to this spec sheet
 [https://icecat.biz/us/p/thomson/thbk1-8.16btk/tablets-3663792000558-thbk1-8.16btk-30289846.html](https://icecat.biz/us/p/thomson/thbk1-8.16btk/tablets-3663792000558-thbk1-8.16btk-30289846.html)
 you have just 1G of ram.
 

 I have a Dell tablet, the touch screen and mouse worked out of the box with Ubuntu.   But...
 Even if you get the touch and mouse working, Ubuntu will not run well on one gig of ram.

I do not know what to suggest

edit
Didn't register this is Lubuntu, still don't know about one gig.

Did find this
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

[https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen)

---

### Post by eniac314 on 2021-05-31
I know 1G of ram is not much nowadays, this tablet was sold with windows 8 and it put itself in an unrecoverable state while trying to restore to factory settings after a failed windows update. I tried reinstalling windows via an offcial iso but the install fails, probably due to ram being insufficient. I think the manufacturer probably had an master tailored for this config but I can't find it online. I could try something even more lightweight than Lubuntu but I fear the hardware would be even less supported. 

Do you know of a good distribution for this kind of hardware?

I tried the tips in your ubuntu/touchscreen link, but checking for touchscreen connectivity by probing the usb or serial interfaves returns nothing, maybe because it's a tablet with a dockable keyboard and not a laptop with a touchscreen.

---

### Post by guiverc on 2021-05-31
I tested releases into the *disco* (19.04) cycle with 1GB of ram, but the only devices that came with 1GB where generally x86/i386 (32-bit) devices so it made no sense on *amd64* or 64-bit.

I have no clues for you, however you weren't specific as to your release; did you try the GA kernel (Lubuntu 20.04 or 20.04.1 media) or the HWE kernel (ie. 20.04.2 media).  If one doesn't work for you, I'd try the other.  You can install both on a system (so if it's already installed, you can install the other).

The reason I mention this is *drivers* are actually kernel modules, and with luck, it maybe the other kernel stack may contain kernel modules (*drivers*) that work better than whichever you tested.  This is a long shot, but its easy to try.

For more details (if wanted) see
- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

---

### Post by eniac314 on 2021-05-31
I have a 64bit CPU (atom Z3735G 1.33ghz). 
I think I am using the HWE kernel (5.8.0-53). I have the 5.8.0-41 kernel available as well, I tried both, no luck.

---

### Post by guiverc on 2021-05-31
The GA kernel is 5.4; the HWE kernel currently is 5.8 yes (will bump to 5.11 next with 20.04.3) but it's the 5.4 or GA (general) kernel I was suggesting you try.

(*the -41, or -53 is just the patch level on the 5.8 kernel*)

---

### Post by eniac314 on 2021-05-31
I see. I installed and tried the 5.4 kernel but got the same results.

---

