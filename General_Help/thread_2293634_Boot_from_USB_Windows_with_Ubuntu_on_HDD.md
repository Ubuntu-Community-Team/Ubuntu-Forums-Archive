---
title: "Boot from USB Windows with Ubuntu on HDD"
date: 2015-09-06
forum: General Help
---

### Post by chemist931 on 2015-09-06
I have an internal SSHD with only Ubuntu installed on it, and I have Windows 10 (ugh) installed on an HDD in an external docking station connected to my laptop by USB.  I can boot to the SSHD fine, but I can't boot to Windows.  I have all my boot settings done logically, and whenever I try to boot to Windows I got to quick settings and choose "Boot from USB".
What settings should I choose to make this work?
For reference the HDD is a Toshiba, the dock is made by Orico, and my laptop is a Dell 3542.

---

### Post by yancek on 2015-09-06
I think your problem might be the usb connection.  You cannot install windows to a usb drive.  If you try, you will see this message:

> windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports

windows systems are designed specifically to run on only one computer per the license and they don't want people to have a 'portable' system which is why I expect it does not support installation to usb/IEEE 1394 and so I would not expect it to boot from either.  So what happens when you try to boot windows?  Any messages?  If you google "boot windows 10 from usb" mostly what you get is how to create and boot the installation media for windows.  I saw a few sites on how to install to a usb, seemed very convoluted and have no idea if they work.  Not really needed here as you already have it on the drive.  Didn't find anything on booting windows from usb. 

You might try some windows forums or a general google.  Noting Ubuntu/Linux can do to help with this.

---

### Post by chemist931 on 2015-09-06
In the boot menu there are several different boot options I haven't seen with Ubuntu previously.  I just asked on this forum because I thought maybe Ubuntu was messing with Windows.

---

### Post by yancek on 2015-09-06
> In the boot menu there are several different boot options I haven't seen  with Ubuntu previously.  I just asked on this forum because I thought  maybe Ubuntu was messing with Windows. 		

The Grub bootloader on Ubuntu chainloads windows and does not actually boot any windows directly.  It basically points to the IPL, the location on the partition containing windows boot files and from there it is up to windows to boot.  What new options do you see?  Using Ubuntu, you can cause all kinds of damage to a windows partition but that would need user intervention and nothing in a default install will do it.   Do you have windows and Ubuntu both installed MBR or UEFI?  I think the problem is trying to boot windows connected to usb but don't know as I don't use windows.  Good luck with it.

---

