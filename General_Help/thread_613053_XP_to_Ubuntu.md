---
title: "XP to Ubuntu"
date: 2007-11-14
forum: General Help
---

### Post by melisandre on 2007-11-14
Hi... I'm making the transition for XP to Unbuntu... However, I'd like to keep my files. I created an EXT2 partition on a harddrive (shared with the non-primary NTFS for XP), and when I boot Ubuntu I get Error 21. I can't even access Windows now, and am left using a Live Session CD from in the installation. Any tips on how I can fix the problem and/or move my files over to a completely Ubuntu installation?

Thanks,
Melisandre

---

### Post by zaphod777 on 2007-11-14
install the nfs support for ubuntu 7.10 has it by default and you should be able to access the ntfs partition. I recomend backing up your data to an external USB drive starting a freash install and restoring your data.

---

### Post by melisandre on 2007-11-14
Hi Zaphod (cute!)
Erm... I'm rather new to Ubuntu (other than using it at a public computer lab regularly)... cold you explain? I installed 7.10, but what is nfs support?

---

### Post by zaphod777 on 2007-11-14
I meant NTFS that is the file system that Windows XP uses. Linux normaly can read it but not write to it it. 

check the artical below

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by melisandre on 2007-11-14
Oh great! Thanks... But what about the Error 21? I can't even boot Ubuntu in the first place!

---

### Post by meierfra on 2007-11-14
Boot from the LiveCD , open a terminal via "Application->Accessories->Terminal
type
```
sudo fdisk -l
```
( "l" is a lower case L)

copy the output and post it here.

---

### Post by Ub1476 on 2007-11-14
[Super Grub]("http://supergrub.forjamari.linex.org/") should fix it:)

BTW, I'm quite sure Ubuntu 7.10 have both read and write support for ntfs.

---

### Post by melisandre on 2007-11-14
I just put it into the other thread, meierfra :)

---

### Post by melisandre on 2007-11-14
sudo fdisk -l gives me:
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 * 6 4454 35736592+ 7 HPFS/NTFS
/dev/sda3 4455 4862 3277260 db CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fa2ddae

Device Boot Start End Blocks Id System
/dev/sdb1 1 11808 94847728+ 7 HPFS/NTFS
/dev/sdb2 11809 19395 60942577+ 83 Linux

I have two hard drives.

Upon putting "/media/boot/grub/menu.lst" in Terminal I get
bash: /media/boot/grub/menu.lst: No such file or directory

---

### Post by meierfra on 2007-11-14
According to your fdisk your windows partition is still there. So I'm quite sure that all your files are still intact.  I recommend to follow Ub1476 suggestion to use Supergrub. Some more information on supergrub:

[Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

If Supergrub does not solve your problem, come  back here.

---

### Post by confused57 on 2007-11-14
> **melisandre said:**
> Hi... I'm making the transition for XP to Unbuntu... However, I'd like to keep my files. I created an EXT2 partition on a harddrive (shared with the non-primary NTFS for XP), and when I boot Ubuntu I get Error 21. I can't even access Windows now, and am left using a Live Session CD from in the installation. Any tips on how I can fix the problem and/or move my files over to a completely Ubuntu installation?

Thanks,
Melisandre
You might try entering your bios setup and make sure the sdb hard drive controller is set to "auto"...

---

### Post by melisandre on 2007-11-14
Alright, I made a Super Grub Disc CD thing... When I boot it gives me a million options... What do I do with it?

Also, confused57, what is sdb?

---

### Post by confused57 on 2007-11-14
> **melisandre said:**
> Alright, I made a Super Grub Disc CD thing... When I boot it gives me a million options... What do I do with it?

Also, confused57, what is sdb?
Your output of "fdisk -l" showed your secondary drive as /dev/sdb, which I assume might be your slave drive...go into your bios setup and check the primary IDE controller and the hard drives I think are listed as hd0 and hd1...check that the hd1 shows "Auto".

I had a grub error 21 when I added a 2nd hard drive to my Dell Dimension 4550:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

See the link meierfra gave for instructions on using SGD.

---

### Post by melisandre on 2007-11-14
> **confused57 said:**
> Your output of "fdisk -l" showed your secondary drive as /dev/sdb, which I assume might be your slave drive...go into your bios setup and check the primary IDE controller and the hard drives I think are listed as hd0 and hd1...check that the hd1 shows "Auto".

I had a grub error 21 when I added a 2nd hard drive to my Dell Dimension 4550:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

See the link meierfra gave for instructions on using SGD.

just tried it - it's on AUTO already.

---

### Post by confused57 on 2007-11-14
Here's a description & possible solutions for grub error 21:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

I think there is an option in the Super Grub Disk menu to "Fix Boot of Windows", this should at least get you booting into Windows.

You might also try using the Ubuntu live cd to mount your Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
there are instructions in the link for accessing your /boot/grub/menu.lst after mounting your root partition with the live cd.

---

### Post by Tyke91 on 2007-11-14
putting a windows install disk into your machine, running it's recovery terminal, and running the command
```
CHKDSK
```will fix your windows install

I don't know why your ubuntu isn't booting though :(

try supergrub after windows is fixed?

PS: why do windows commands all have to be upper case? I feel like I'm shouting at my computer...

---

### Post by melisandre on 2007-11-26
I got rid of windows (thank god) and the installation went perfectly! Thanks so much for all your help!

---

