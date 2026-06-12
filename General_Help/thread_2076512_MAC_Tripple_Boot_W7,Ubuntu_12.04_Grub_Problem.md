---
title: "MAC Tripple Boot W7,Ubuntu 12.04 Grub Problem"
date: 2012-10-26
forum: General Help
---

### Post by dakaku on 2012-10-26
Problem: Windows won't start.

Background:
Installed Windows 7 by Bootcamp.
Installed rEFIt
Created two partitions for Ubuntu+Swap
Installed Ubuntu, with GRUB to partition sda2

Ubuntu works fine.

At the rEFIt screen i have 3 options: MacOS / Linux / Windows
Linux: does nothing
Windows: boots Grub with the options to boot Ubuntu/Ubuntu Recovery/.../Windows 7 (Loader)

If I hit Windows 7 a screen pops up that File: BOOT/BCD is missing.
If I start up Ubuntu and mount the Bootcamp partition I can see the file is there.

What I tried so far:
update-grub
> dak@dak-Macmini:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
Found Windows 7 (loader) on /dev/sda5
done
Windowsrecovery from the Windows 7 CD:
chckdsk
bootrec.exe /fixmbr: works
bootrec.exe /fixboot: says there are no Windows partitions


Partitiontable:
> dev/sda1: EFI (210MB FAT)
dev/sda2: HFS+(32GB) - mac os x
dev/sda3: Ext4(14GB) - ubuntu
dev/sda4: Linux Swap(4,3GB) - ubuntu swap
dev/sda5: NTFS (78GB) - windowsSo it seems that the partition doesn't get mounted when I select Windows from grub ?

Could I just set "some" arguments manually from Grub to get Windows started.
> setparams 'Windows...'
insmod part-gpt
insmod ntfs
set root = '(hd0,gpt5)'
search --nofloppy --fs-uuid --set=root 1234...Edit: 
Just remebered that I changed the MBR before to get AHCI in Windows 7 working on this Mac Mini:

This is a Mac Mini 1.1 with updated firmware to 2.1 and added ahci by this tutorial:
[http://www.ocztechnologyforum.com/forum/showthread.php?87950-Enabling-AHCI-for-Windows-on-MBP-2011-now-possible](http://www.ocztechnologyforum.com/forum/showthread.php?87950-Enabling-AHCI-for-Windows-on-MBP-2011-now-possible)

---

### Post by dino99 on 2012-10-26
Seems like confused: gpt/mbr/uefi  :confused: :confused:

need to know if its a bios or an uefi machine
need to know how the bios is set: bios or uefi
need to know if you have installed grub into mbr or gpt

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi)

---

### Post by dakaku on 2012-10-26
> need to know if its a bios or an uefi machineHmm no idea, its a Mac without BIOS and i installed rEFIt so i guess, uefi

> need to know how the bios is set: bios or uefisee above, uefi ?

> need to know if you have installed grub into mbr or gptI did it like described here:
[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

(your link)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
/dev/sda3 I chose there


As said before: Grub works to start Ubuntu, so I kind of dont wont to reinstall Grub, as suggested in your link.

---

### Post by dakaku on 2012-10-26
Maybe this helps (from boot-repair):
[http://paste.ubuntu.com/1306904/](http://paste.ubuntu.com/1306904/)

Didnt went through the program further, tho.
Just for to get the info.

Edit: 
I cannot seem to get /dev/sda1 mounted so i created a new one.
(vFat msdos etc. wont work, seems it is corrupt)
Will try to reinstall ubuntu (one with efi support) and grub on that new efi partition.

---

### Post by YannBuntu on 2012-10-26
Hello
> **dakaku said:**
> Maybe this helps (from boot-repair):
[http://paste.ubuntu.com/1306904/](http://paste.ubuntu.com/1306904/)

- your BIOS is currently set to boot the HDD in Legacy mode.
- your EFI partition (=ESP) seems damaged. If i were you i would try to fix it via TestDisk.

---

