---
title: "Ubuntu won't run after install via wubi"
date: 2008-04-25
forum: General Help
---

### Post by isemmel on 2008-04-25
Install seemed to go alright although I don't think it accessed the network during configuration.

A text screen flashed up for about 5 milliseconds with some message about 'network bus' or something.

After reboot and selecting 'Ubuntu' it comes up with 'Disk Error' and goes back to the boot menu.

AMD 64 running Vista Business 32 bit.

I installed on to the F: drive (ie not C: or E:) and selected 30Gb space.

---

### Post by tinybit on 2008-04-25
> **isemmel said:**
> it comes up with 'Disk Error' and ...
I installed on to the F: drive (ie not C: or E:) and ...

I suppose the F: is a logical partition which exceeds the BIOS capability.

You may use C: or D: or E: instead of F: and try again.

---

### Post by isemmel on 2008-04-25
No, F: id a disk drive

---

### Post by tinybit on 2008-04-25
> **isemmel said:**
> No, F: id a disk drive

BIOS could also have bugs while accessing hard drives other than the first one.

GRLDR or WUBILDR should be placed in C:, which should be the same drive as the one containing NTLDR or BOOTMGR. And so should be other important boot files such as vmlinuz and initrd.gz.

---

### Post by isemmel on 2008-04-25
So how do you do that ?

The only option was where do you want to put Ubuntu and I don't want to use C:

---

### Post by tinybit on 2008-04-25
> **isemmel said:**
> So how do you do that ?

The only option was where do you want to put Ubuntu and I don't want to use C:

Sorry. I mean the developer should place these crucial boot files on C:. All other files may be placed elsewhere, e.g., in your F: drive. After Linux gains control, your F: drive can be recognized easily.

---

### Post by ago on 2008-04-25
[https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by isemmel on 2008-04-26
I uninstalled Ubuntu from mt 2nd Sata drive (F:) and then tried to install it on my first Sata Drive (E:), but then when it comes to do the first reboot, Ubuntu option does not appear on the boot menu.

I've followed the links about changing hd1 to hd0 etc, but as I don't know what I'm doing and don't want to trash windows, I'm not game to try it. (Anyway, when I tried one suggestion about hitting 'c' and typing in find /boot/grub/stage1 it came up with Error 15 File Not Found !!

That's it for me. I've got on OK without linux for the past 20 years or so so I won't miss it.

Might give version 9 a try when it comes out.

---

### Post by ago on 2008-04-26
> **isemmel said:**
> I uninstalled Ubuntu from mt 2nd Sata drive (F:) and then tried to install it on my first Sata Drive (E:), but then when it comes to do the first reboot, Ubuntu option does not appear on the boot menu.
Can you uninstall and install again on E:?
Also provide the wubi log which is in your user temp folder (%temp%).

> hitting 'c' and typing in find /boot/grub/stage1 it came up with Error 15 File Not Found !!
This is normal as we use grub4dos and not grub. 

There will be a fix app soon for common problems that emerged after final.

---

### Post by isemmel on 2008-04-26
Attached

You might like to change your forum parameters to
(a) Allow .log file type
(b) Increase the file size allowed for them

---

