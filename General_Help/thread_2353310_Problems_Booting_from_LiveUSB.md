---
title: "Problems Booting from LiveUSB"
date: 2017-02-20
forum: General Help
---

### Post by joshkt on 2017-02-20
So I have been using a live usb for a while. Every time that I have tried booting before I get in without any problems. Now whenever I try to boot it takes me to a line of code that ends with end kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)
[ATTACH=CONFIG]273814[/ATTACH]
I have been looking at different methods of trying to fix this, but they all point to doing something while in Ubuntu. The problem is I can't even get in... So how do i fix this if I can't access the tools to do so?

Any help is appreciated! Thanks

---

### Post by SchnappiJedi on 2017-02-20
Would download a new live boot image. If there is still a problem the issue is with your host machine.

---

### Post by RobGoss on 2017-02-20
Try accessing the **Grub **menu and choose a earlier kernel. Press the **Shift key** while booting your machine you will see the grub menu, at that point you can choose a **kernel **that was working before all this happened

---

### Post by yancek on 2017-02-21
If you are booting a 'Live USB', it is a read-only filesystem and if you are able to boot it after making some change (to an earlier kernel if there is one?), you will need to do it every time you try to boot it.  If that isn't what you are doing, post more details.  Might be a failing usb drive.

---

### Post by oldfred on 2017-02-21
Need to know brand, model system and video card/chip.
Is this a system you have booted before?

Many systems need boot parameter or two to work correctly.
Often nomodeset is required for video issues, but many other boot parameters are often required depending on system configuration.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by RobGoss on 2017-02-21
+1 Oldfred

Please see the link I posted it shows you how to use nomodeset

---

