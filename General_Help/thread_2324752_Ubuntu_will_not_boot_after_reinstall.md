---
title: "Ubuntu will not boot after reinstall"
date: 2016-05-16
forum: General Help
---

### Post by sarge3 on 2016-05-16
Dual boot machine with Windows wont boot up on Ubuntu after recent reinstall. No video signal. Windows working fine. 

I tried the boot repair disk (USB) twice, last time said successfully reinstalled, but still a blank screen. [http://paste.ubuntu.com/16454513/](http://paste.ubuntu.com/16454513/)

Any suggestions please?

---

### Post by blaze24-matrix on 2016-05-16
Could be a problem with your video driver. Try install/re-install it.

---

### Post by grahammechanical on 2016-05-16
Can we clarify a few things?

You get a Grub boot menu? You get options for both Ubuntu & Windows? The Windows option loads Windows correctly? The Ubuntu option does not load Ubuntu? It loads up to certain point and gets no further and all you see is a black screen with the No Signal message?

It may well be a conflict with a proprietary video driver. Re-installing the Grub boot loader will not solve this as the problem occurs after Grub has started the Linux loading process.

At the Grub menu select Advance options for Ubuntu and at the sub-menu select a recovery mode kernel to load. At the recovery menu select Resume. If that loads to a working desktop environment go to System Settings>Software & Updates>Additional Drivers tab and try a different video driver. You need to be connected to the internet and to allow time for the utility to find appropriate drivers from the repositories.

If recovery mode>resume does not get you to a desktop environment or you have problems activating a different video driver, then we will most certainly need the hardware specifications of that machine and in particular the specification of the video adapter.

By the way, the OS is 15.10.

Regards

---

### Post by oldfred on 2016-05-16
Script shows you have AMD:

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] [1002:68f9]
Subsystem: ASUSTeK Computer Inc. Device [1043:3000]
Kernel driver in use: radeon
```

[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes)
> 
[LIST]
[*]AMD's **fglrx** driver does not work with the current kernel ([1493888]("https://bugs.launchpad.net/bugs/1493888")).  It is warmly recommended to uninstall the fglrx driver before upgrading  to Ubuntu 15.10. The open source "radeon" driver can be used as a  temporary replacement until a fix is available. 

[/LIST]


You may need nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sarge3 on 2016-05-16
Many thanks all. Change to nomodeset nailed it. Back up again.

---

