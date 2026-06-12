---
title: "Messed up GPT"
date: 2014-01-16
forum: General Help
---

### Post by wazooman on 2014-01-16
I was trying to dual boot Ubuntu and Windows on my ASUS laptop and when trying to install Ubuntu it would not recognize Windows. I looked online and after reading I thought that the problem might have been with the GPT and so I reset it using gdisk and the zap function. However, now I cannot access my hard drive at all and when I restart it goes straight to the BIOS. Is it possible to fix this? Thanks in advance.


Edit: I checked GParted and it looks like this [IMG]http://i.imgur.com/F6fbv2t.png[/IMG]
does this mean everything on my hard drive is gone?

---

### Post by oldfred on 2014-01-16
Did you convert from gpt to MBR?
If you were booting pre-installed Windows 8 then you have to have gpt partitions.
If converted to MBR you may be able to convert back. I suppose you did not back up partition table? or have any documentation, screen shots or lists showing partitions.

If converted to MBR you can use gdisk to convert to gpt.

Or you can try testdisk but be sure to be in gpt mode, is system really is gpt.
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by wazooman on 2014-01-16
Thanks for your response. I think I backed up the MBR but that may have gotten erased. How do I run testdisk after extracting the tar.bz2 file?



I checked whether I have MBR or GPT and it shows this:
```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3C51FFF0-89C4-4E2D-8327-FA6EE4EA0FE3
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 976773101 sectors (465.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name


```

---

### Post by oldfred on 2014-01-16
I do not think that gdisk output shows anything. You in effect erased drive or removed all partitions (tecnically data should still be there). Since gdisk creates gpt drives it is just asking you if you want to create a new partition. 

Easier just to use testdisk from repository. Using terminal:

sudo apt-get install testdisk

One of its first questions is which type you want to recover UEFI/gpt or Intel/MBR/msdos. And you need to answer correctly if you want any chance to find old partitions.
Was this a Windows 8 system? If so then it was gpt. 
If Windows 7 probably BIOS/MBR, but a few newer systems were UEFI with gpt.

If UEFI partitions may have looked like this:
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by wazooman on 2014-01-16
You are right it was a gpt, and I was able to use testdisk to recover my data. However I still cannot boot into windows or a recovery usb. Thank you for all of your help.

---

### Post by oldfred on 2014-01-16
Boot-Repair cannot do much to repair Windows, but post link. To fix Windows you usually need the Windows repair flash drive.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by wazooman on 2014-01-16
Everything is now working as it was before I tried to install Ubuntu. Thanks again for the help. I think I'll stick to running Ubuntu on a VM until I better understand Linux.

---

### Post by oldfred on 2014-01-17
IF/When you think about dual boot again see all the links in the link in my signature.

Some other Asus that installed Ubuntu.
  ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

