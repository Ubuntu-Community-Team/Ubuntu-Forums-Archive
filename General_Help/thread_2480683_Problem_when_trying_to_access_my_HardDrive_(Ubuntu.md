---
title: "Problem when trying to access my HardDrive (Ubuntu 22.04.1 LTS)"
date: 2022-11-06
forum: General Help
---

### Post by eliasmys1 on 2022-11-06
Hi!

I recently encountered the following error when trying to access my files on my HardDrive from my Ubuntu 22.04.1 LTS PC.

 
(*Image with error shown in attachment below.*)


 Previously, I tried to access a backup through Rescuezilla. I don't know if such thing is connected to my problem. I have to note that I was able to access the HardDrive from another PC, so it's checked that it's not  problem of the HardDrive. Any help would be appreciated!

 
Thanks!

---

### Post by ajgreeny on 2022-11-06
Is this an internal or external hard drive and do you know what filesystem it has on it?

For more detailed information about this drive, which may help us more, attach the drive if it's external, then please run command ```
sudo fdisk -l
``` and report back here the output you see.  That's a lower case L at the end of command not number 1.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by eliasmys1 on 2022-11-07
It is an external HardDrive.
The output of ```
sudo fdisk -l
``` is:

```

Disk /dev/loop0: 32.57 MiB, 34148352 bytes, 66696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 10.68 MiB, 11202560 bytes, 21880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 64.38 MiB, 67506176 bytes, 131848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 104.02 MiB, 109076480 bytes, 213040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 114.99 MiB, 120573952 bytes, 235496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 8.96 MiB, 9396224 bytes, 18352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 55.58 MiB, 58281984 bytes, 113832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: KBG30ZMS256G NVMe TOSHIBA 256GB         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2B471F7B-C4DB-4EFA-8251-F2AB2FFAC17F

Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1    2048   1050623   1048576   512M EFI System
/dev/nvme0n1p2 1050624   4550655   3500032   1.7G Linux filesystem
/dev/nvme0n1p3 4550656 500117503 495566848 236.3G Linux filesystem


Disk /dev/mapper/nvme0n1p3_crypt: 236.29 GiB, 253713448960 bytes, 495534080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-root: 234.37 GiB, 251649851392 bytes, 491503616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vgubuntu-swap_1: 1.91 GiB, 2046820352 bytes, 3997696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 55.56 MiB, 58261504 bytes, 113792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 72.79 MiB, 76324864 bytes, 149072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 63.2 MiB, 66265088 bytes, 129424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 5.61 MiB, 5885952 bytes, 11496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 166.87 MiB, 174977024 bytes, 341752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 122.69 MiB, 128651264 bytes, 251272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 61.96 MiB, 64970752 bytes, 126896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 238.47 MiB, 250052608 bytes, 488384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 203.67 MiB, 213565440 bytes, 417120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 521.44 MiB, 546766848 bytes, 1067904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 164.76 MiB, 172761088 bytes, 337424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 219 MiB, 229638144 bytes, 448512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 400.8 MiB, 420265984 bytes, 820832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 414.34 MiB, 434470912 bytes, 848576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 140 KiB, 143360 bytes, 280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 328.98 MiB, 344965120 bytes, 673760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 330.33 MiB, 346374144 bytes, 676512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 67.28 MiB, 70549504 bytes, 137792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 68.7 MiB, 72032256 bytes, 140688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 122.79 MiB, 128753664 bytes, 251472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 246.13 MiB, 258084864 bytes, 504072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 176 MiB, 184545280 bytes, 360440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 92.08 MiB, 96550912 bytes, 188576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 47.99 MiB, 50319360 bytes, 98280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 141.46 MiB, 148328448 bytes, 289704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 46.96 MiB, 49242112 bytes, 96176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop36: 284 KiB, 290816 bytes, 568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop37: 88.12 MiB, 92397568 bytes, 180464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop38: 45.93 MiB, 48156672 bytes, 94056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop39: 70.63 MiB, 74063872 bytes, 144656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop41: 9.45 MiB, 9912320 bytes, 19360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop40: 724 KiB, 741376 bytes, 1448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop42: 320.44 MiB, 336003072 bytes, 656256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 3.64 TiB, 4000752599040 bytes, 7813969920 sectors
Disk model: My Passport 25E1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B2D22EEA-63C3-4243-9214-B051D4FF64A6

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 7813967871 7813965824  3.6T Microsoft basic data

```.

Sadly, I don't know the filesystem it has on it. I'm not that advanced... :(

---

### Post by tea for one on 2022-11-07
> **eliasmys1 said:**
> It is an external HardDrive.
```

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 7813967871 7813965824  3.6T [COLOR="#0000FF"]Microsoft basic data[/COLOR]

```
Sadly, I don't know the filesystem it has on it. I'm not that advanced
Windows file system on the partition sdb1.

Ubuntu cannot repair Windows file systems so you will need access to a Windows PC.
Then use Windows tools/utilities to scan, check and hopefully repair the file system.

The error in post 1 may be due to the disk being unsafely removed.

---

### Post by eliasmys1 on 2022-11-07
I understand. I will have access on a Windows PC in the coming weekend. I will check it and send you the results. I tried, though, using an application named "EaseUS CleanGenius", where I ran a check and repair on the readability of the files on the drive. I ran it on an net cafe, because I have an Ubuntu PC. I'm going to check if this works and inform you.

---

### Post by oldfred on 2022-11-07
Windows fast startup sets hibernation flag.
The NTFS drive will not write into hibernated NTFS partition, to prevent damage to data. And then standard/default mount does not work.
NTFS can be force mounted read only  from Linux if required.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

You should only use NTFS if dual booting with Windows.
NTFS repairs can only be done from Windows. You may need chkdsk or defrag which cannot be run from Linux.
Always best to use Windows tools for Windows and Linux tools for Linux.

---

### Post by eliasmys1 on 2022-11-07
Thank you!

---

### Post by TheFu on 2022-11-07
> **eliasmys1 said:**
> I understand. I will have access on a Windows PC in the coming weekend. I will check it and send you the results. I tried, though, using an application named "EaseUS CleanGenius", where I ran a check and repair on the readability of the files on the drive. I ran it on an net cafe, because I have an Ubuntu PC. I'm going to check if this works and inform you.

You know, that if you have Ubuntu, really you should be using native Linux file systems like ext4, not NTFS.  All sorts of things become easier.
But if you need to physically disconnect the HDD and physically connect it (sata/usb) to a Windows system, then NTFS is probably the best solution, even with the problems it causes when connected to Ubuntu.   I have 1 NTFS partition on a HDD that connects to specialized hardware that only supports FAT32 or NTFS file system.  About every 2 months, NTFS becomes corrupted and needs to be reformatted  (which blanks all data too) so I can continue using it.  I think the corruption problem is caused by the specific hardware device, not NTFS or Linux.  But for any Linux only storage, I use ext4 or f2fs (for flash storage) as my preferred file systems.  In Linux, there are about 10 popular file system, each good at some specific things. Lacking any real requirements, go with ext4 for HDDs and SSDs, but f2fs for flash (microSD, SD, USB-flash) storage.  There are reasons to use BTRFS or ZFS too, but I suspect those wouldn't be a good idea for you.

BTW, your SSD is using drive encryption and LVM2.  If you have issues with that, post the output from 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
sudo pvs
sudo vgs
sudo lvs
```
to get help.  The first command is very useful at seeing an overview for how storage is laid out in a system.  The last 3 commands are all for LVM2 summary information.  None are harmful.

---

### Post by eliasmys1 on 2022-11-10
Sadly, I tried chkdsk *:/f and nothing changed. It says there are no problems to the disk.

---

### Post by ActionParsnip on 2022-11-10
Be sure to use the safe remove feature in the Windows OS before dethatching it. This will sync all caches. May help when you connect it to the system when running Ubuntu

---

### Post by eliasmys1 on 2022-11-10
No, it doesn't work... :(

---

### Post by TheFu on 2022-11-10
Doesn't Windows use scandisk/scandsk?  Sorry, I don't keep current on Windows stuff.

---

### Post by eliasmys1 on 2022-11-11
](*,)

---

### Post by TheFu on 2022-11-11
> **eliasmys1 said:**
> ](*,)

If you would run the first command in Post #8 above, we could provide a mount command or /etc/fstab entry so the storage is mounted inside Linux.

I could make a guess and say to try these 2 commands, 
```
sudo mkdir /mnt/temporary
sudo mount -t auto /dev/sdb1  /mnt/temporary \
     -o uid=1000,nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,gid=1000,fmask=0002,dmask=0002,nofail,users
```

That's a temporary way. If it works, we can move those options into the fstab, so it is mounted automatically.  Actually, all those options just make it show the main user of the system can have read-write access and performance doesn't suffer, like it would with the default options. 

The use of the device file, /dev/sdb1, isn't good and really needs to be changed to either a UUID or LABEL instead.  The device filename can change from boot to boot. Not too likely with just 1 disk, but if another is added, they will swap places every once in a while.  By using a the UUID or LABEL, that concern is handled forever.  The gparted tool can set a LABEL on a file system. That would be best.  Then you can replace the device filename with a "LABEL=WDEXT" everywhere. For example, 
```
sudo mount -t auto LABEL=WDEXT  /mnt/temporary  .... 
```

When the final settings are known, you'll probably want to mount the storage to /media/external, or something like that.  Once the fstab is setup, this USB storage will be just like internal storage, so don't power it off or unplug it and walk away, unless the entire computer is powered off first. Data corruption is likely if care isn't taken.

The method of using a point-n-click technique to mount NTFS will be slower, perhaps 30% slower.

---

### Post by eliasmys1 on 2022-11-11
Thank you for your reply, but I prefer to use my HardDrive as an external one, as it is designed to be. I am, really, considering, right now, to give it to a Data Recovery Center, here, where I live, to check it for me. I hope they find some solution.

---

### Post by eliasmys1 on 2022-11-18
GOOD NEWS, EVERYBODY! :D It seems to be a problem of the filesystem of the HardDrive. I asked a service for broken drives, here, where I live, and they told me I should have the disk have a filesystem supported both by Ubuntu and Windows. I found the solution (I hope, at least!)! I formatted my HardDrive, after backupping the files, into an exFAT filesytem, which, to my knowledge, is a filesystem supported both by Ubuntu and Windows. I don't know if there are any problems with this method, but, to the moment, everything works fine. Now, I'm done formatting the HardDrive and I transfer the old files on it. When the process is done and I connect it to my Ubuntu PC, I will let you know how everything has gone. Thank you for your help, everyone!

---

### Post by eliasmys1 on 2022-11-18
Finally, everything is OK and done! :D :D :D

---

### Post by TheFu on 2022-11-18
exFAT is one of the worst choices for many reasons. The only worse choice is FAT32.

For spinning HDDs or SSDs that need to be connected to other computers, choose NTFS.  Of course, it would be better to choose a native Linux file system if the drive is only connected to Linux, then access those files over the network using NFS,  sftp, sshfs, or CIFS.  That's the order of preference, btw.

exFAT isn't journaled.  That's a huge downside and reason enough to be avoided.  exFAT should only be used on small, flash memory storage, like microSD or those little USB thumb-drives where having fewer writes matters.  Journaled file systems were a huge leap forward in file systems. All the modern file systems use it for good reason.

BTW, don't expect Linux to be able to run file system checks on exFAT or NTFS or FAT32.  You'll need Windows for those things.  For native Linux file systems, the 'fsck' program can check the file system and perform repairs.  Using a journaled file system is helpful for fsck being able to better correct any file system errors. Without it, the ability to recover from power issues or just having the connection yanked out is greatly limited.  Beware.  Always use the "eject" option or "umount" the file system before disconnecting any storage.

---

