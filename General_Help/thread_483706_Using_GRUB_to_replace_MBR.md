---
title: "Using GRUB to replace MBR"
date: 2007-06-25
forum: General Help
---

### Post by YumZ on 2007-06-25
Kubuntu has caused nothing but problems on this machine which is very strange since I used K/Ubuntu for a year or so on another machine without incident.  I currently have a Windows XP/Kubuntu 7.04 dual boot but I'd like to just go back to Windows on this machine.  I don't have a Windows CD so I can't replace the MBR that way.  Could I use the Kubuntu Live CD to install GRUB after removing Kubuntu and still boot into Windows that way?

---

### Post by r0ck80y on 2007-06-25
If you remove kubuntu, the grub files will be lost. Your mbr will still search for grub files however. So upon rebooting you'll get some grub errors instead of the menu. You need to have a windows CD to fix the mbr in order to load windows.
Or you can try this (i have never tried it, so i cant tell for sure if it'll work):
Divide the linux partition into two parts: a small (say 100mb) part and a large part. **Install** linux again and place /boot in the small partition whereas make the large partition as the mount point for /. Your grub menu will be restored. Ensure you have the windows boot-up entry in /boot/grub/menu.lst file. See if you are able to load into windows with this grub menu. Then delete the larger partition but keep the smaller 100mb /boot partition intact.

This process wont harm your windows partition in any way, and since you dont need linux, you can safely try this method. Good luck and lemme know if this works :)

---

### Post by YumZ on 2007-06-25
Ok I installed /boot onto a 100 MB partition and root onto a ~7 GB partition.  I rebooted and Windows was found by GRUB.  I am now going to remove the ~7 GB partition and see if I can still boot into Windows.

EDIT:
Ok, it worked.  However, the Ubuntu GRUB entry is still there and when I select it, it attempts to boot Ubuntu and it obviously can't since there is no root.  Can I use the Live CD to edit the GRUB menu list and just remove the Ubuntu entries?

---

### Post by YumZ on 2007-06-25
bump

---

### Post by confused57 on 2007-06-25
> **YumZ said:**
> Ok I installed /boot onto a 100 MB partition and root onto a ~7 GB partition.  I rebooted and Windows was found by GRUB.  I am now going to remove the ~7 GB partition and see if I can still boot into Windows.

EDIT:
Ok, it worked.  However, the Ubuntu GRUB entry is still there and when I select it, it attempts to boot Ubuntu and it obviously can't since there is no root.  Can I use the Live CD to edit the GRUB menu list and just remove the Ubuntu entries?
You can replace Window's IPL to the mbr, using the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

MbrFix.exe can be used to restore Window's mbr, as well as a Win98SE OEM boot floppy(if you have a floppy drive):
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The GAG bootloader can be used to boot Windows:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

If you still want to use Grub, you can mount your /boot partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then you comment the Ubuntu entries

---

### Post by YumZ on 2007-06-25
The Windows 98 Floppy Disk Method looks interesting.  I will try this when I have the time.

---

