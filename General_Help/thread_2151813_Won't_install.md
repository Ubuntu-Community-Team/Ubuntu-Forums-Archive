---
title: "Won't install"
date: 2013-06-05
forum: General Help
---

### Post by jrosado on 2013-06-05
[SIZE=2]Xubuntu is humming along fine on my laptop.

But when I try to install it on my desktop (Dell Inspiron 531 - [/SIZE][SIZE=2]2.10 gigahertz AMD Athlon 64 X2 Dual Core[/SIZE][SIZE=2], 4 GB RAM)
I get this across the top of my monitor:

[/SIZE][COLOR=#000080][     0.9248331 Kernel panic - not syncing: VFS: Unable to mount root on unkn
own-block(Ø.Ø)[/COLOR]

Both the latest versions, the 386 and the 64bit, show the same problem.

How can I get it installed?

---

### Post by Cvxcvgg on 2013-06-05
Do you have any other Operating Systems on your desktop? How are your partitions formatted? I know that Ubuntu can not recognize NTFS partitions under some circumstances, and NTFS is a common format in Windows, so you may need to tweak your partition table a little.

---

### Post by searchfgold6789 on 2013-06-05
> **jrosado said:**
> [SIZE=2]Xubuntu is humming along fine on my laptop.

But when I try to install it on my desktop (Dell Inspiron 531 - [/SIZE][SIZE=2]2.10 gigahertz AMD Athlon 64 X2 Dual Core[/SIZE][SIZE=2], 4 GB RAM)
I get this across the top of my monitor:

[/SIZE][COLOR=#000080][     0.9248331 Kernel panic - not syncing: VFS: Unable to mount root on unkn
own-block(Ø.Ø)[/COLOR]

Both the latest versions, the 386 and the 64bit, show the same problem.

How can I get it installed?

Have you already installed the OS, or are you just trying to boot from a live DVD or USB? What happened before you see this error?

---

### Post by jrosado on 2013-06-06
> **searchfgold6789 said:**
> Have you already installed the OS, or are you just trying to boot from a live DVD or USB? What happened before you see this error?

This machine used to have Windows7 OEM.  The hard drive failed and I put in a new, empty  HDD.  No OS installed.  I'm trying to install Xubuntu from a DVD made from the downloaded iso file.  (This installation disk is OK, it's been used before.)

---

### Post by cincinnatus13 on 2013-06-06
Have you tried pre-formatting the partitions with gparted before attempting the install?

---

### Post by jrosado on 2013-06-06
> **cincinnatus13 said:**
> Have you tried pre-formatting the partitions with gparted before attempting the install?

No.  Can you please direct me to the instructions to do that?   Thanks.

---

### Post by cincinnatus13 on 2013-06-07
^If you're using the liveCD/USB just go into it and before installing, reformat with Gparted (it should be on the liveUSB, it is on the other Ubuntu distros anyway.)
If not, download the gparted ISO and make it bootable and use it on there.

It's a GUI program so you can just look at your partitions and reformat it to ext4 or whatever you prefer. Not sure if this will solve your issue but it'll at least help you make sure the HDD isn't the issue.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you have other OS's you want to keep, make sure you know what you are doing first. If not, ask here.
Also, I recommend separating your root (/) and home (/home) partitions for easier OS upgrading.

---

### Post by jrosado on 2013-06-08
Interesting - when I tried to open gparted on this machine, it did not open and I got the same message (along with much other data)  that I got from the install failure:  [COLOR=#0000cd]Kernel panic - not syncing: VFS: Unable to mount root on unknown-block[/COLOR]

I now think there's a problem with the CPU or chip set in this machine.  Fixing that is above my pay grade, so I may have a new boat anchor.

Thanks to everyone for trying to help.

---

