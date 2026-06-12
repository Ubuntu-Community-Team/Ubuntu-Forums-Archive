---
title: "Windows doesn't work but ubuntu does"
date: 2016-05-25
forum: General Help
---

### Post by Acharn on 2016-05-25
I normally use Windows 7 because I'm addicted to one game that still does not run on Wine. I like to keep Linux on hand just because I like Linux. Yesterday I installed Ubuntu 15.10 on a usb stick and used it for several hours. I installed a number of programs and am really happy with the performance from a Sandisk USB 3.0 stick. I shut down normally and went to bed. This morning when I tried to start up as usual (in Windows 7) I got a message "No such device." I tried booting from the Windows installation disk and succeeded, but neither the mouse nor the keyboard worked. I tried the Falcon Four Ultimate Boot CD, but their MiniXP interface had the same problem -- it didn't respond to either the mouse or the keyboard. The CD menu did respond to the keyboard, but none of the diagnostics seemed helpful. Both mouse and keyboard work in the BIOS setup window, but I don't see anything there that changed

I booted Ubuntu from the usb stick, and that's what I'm using now. Very strange. The Disk utility shows the HDD is in perfect health. I'm able to access the /dev/sda partitions from Ubuntu, and read files as before. Both mouse and keyboard work fine.

I have an AMD A10-5800K AGP on a Gigabyte GA-F2A75M-HD2 motherboard with 8 GB RAM. Keyboard and mouse are both connected by USB 2.0. The HDD is a Western Digital Blue 1 Terabyte SATA. The machine is not overclocked. I searched for answers to this but didn't find anything. I'm hoping it's something I can fix myself, because I'm afraid the technician would keep it for several days. Any suggestions?

---

### Post by oldfred on 2016-05-25
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Acharn on 2016-05-26
OK, first the link to the report is: [http://paste.ubuntu.com/16701574](http://paste.ubuntu.com/16701574)

Now I'll go read the other link you gave me. I forgot to mention before, I have my BIOS set to legacy boot only, not UEFI. I think it was because of problems I was having booting from usb a few years ago.

---

### Post by yancek on 2016-05-26
The end of the boot repair script tells you to set the smaller usb drive (29GB) to frist boot priority in the BIOS.  That should boot Ubuntu as it has Grub code in the MBR of that disk and also has an entry for windows in the grub.cfg file.  Does that not work for you?  If not, what exactly happens when you select the windows entry?

The very first line in the boot repair output tells you "install-mbr/Testdisk is installed in the MBR of /dev/sda.".  I would suggest using the windows installation DVD and select the "Repair" option to fix the MBR and put windows code there.

---

### Post by oldfred on 2016-05-26
Grub really only boots working Windows.
So if Windows is hibernated or needs chkdsk, then you cannot boot it from grub menu. And all Windows after 7 are by default hibernated, if the fast start up setting is on.

Follow Yancek's suggestions.

Not sure what boot loader test disk installs. Boot-Repair will install syslinux which is a Windows type boot loader and may work. 
Or you may need f8 to get into Windows own internal repair console or safe mode to make fixes. You normally do not have time after booting Windows from grub menu to press f8 as it directly switches to Windows.
Best to have & use Windows repair flash drive.

Other link is in my signature and for those with UEFI. You do not have UEFI.

---

### Post by Acharn on 2016-05-26
This is not an option. I am able to boot the Windows Installation DVD, but when it arrives at the opening screen (where the choice of language is displayed) there is no mouse or keyboard. I an not able to interact with the program in any way. At this point the only thing I can do is reboot. I cannot enter into Repair mode. Thanks anyway.

Unfortunately, it's a little late for me to create a repair usb. I'll try copying the syslinux MRB over to /dev/sda and see if that helps. It's maddening because I've been using this installation of Windows 7 for at least a year, and have booted up into Repair mode from the DVD a few times and both mouse and keyboard worked fine. In fact I used this DVD to non-destructively install the current Windows 7. The process of installing Ubuntu 15.10 on the USB 3.0 stick did something I think, but I can't imagine what. I did the same installation back when I first got the usb and had no problem afterward.

---

### Post by oldfred on 2016-05-26
I have had system that required USB port setting turned on in BIOS for keyboard & mouse to work.
But keyboard & mouse worked in XP & Ubuntu as they used their own drivers, it was only in grub that relied on BIOS for driver that had issues.

Might check BIOS settings, but sounds more like a Windows issue.

---

### Post by Acharn on 2016-05-26
A thought occurred to me while I was dozing this morning. Back in the "good old days" we had to format drives with fdisk before we could install operating systems. One of the things I remembered having to do was mark one partition as "active." That was the partition that contained the OS code that the boot loader would install. If something changed the partition table on /dev/sda so that it was not marked "active" (I may have the wrong word here, it's been a long time), would the boot loader report that there was no device? The output from 'sudo fdisk -l' is:
```

<snip data about RAM>

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x33db4aa9

Device     Boot      Start        End   Sectors   Size Id Type
/dev/sda1  *            63  650423654 650423592 310.1G  7 HPFS/NTFS/exFAT
/dev/sda2        650423655 1302084314 651660660 310.8G  7 HPFS/NTFS/exFAT
/dev/sda3       1302084315 1953520064 651435750 310.6G  7 HPFS/NTFS/exFAT

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.




Disk /dev/sdb: 29.2 GiB, 31376707072 bytes, 61282631 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf0ba7b47

Device     Boot   Start      End  Sectors  Size Id Type
/dev/sdb1  *       2048  3999743  3997696  1.9G 82 Linux swap / Solaris
/dev/sdb2       4001790 61282303 57280514 27.3G  5 Extended
/dev/sdb5       4001792 61282303 57280512 27.3G 83 Linux

```
I'm not interested in /dev/sdb -- that's my ubuntu usb stick and it boots and works fine. My question, can anybody tell me if the "ID" column of /dev/sda means anything? I can't believe the error messages about the partitions not starting on physical boundaries have anything to do with anything -- the partitions were set up the way they are years ago. As you can see I'm floundering here. fdisk always scared me and I don't want to start playing with it on my HDD unless I have to. Are there other less dangerous tools? 

I still don't understand how it is possible for a bootable DVD (my Windows Installation Disk) to change its behavior.

---

### Post by oldfred on 2016-05-26
Windows calls it active partition. Linux calls it boot flagged partition and you have the * on sda1.
Windows uses the boot flag in the MBR for the Windows boot code in the MBR to know which partition to jump to, to find more Windows boot code.
Grub does not use boot flag but looks for specific files to use to boot with.
 The id is the format type code - 07 is NTFS.

All new partitioning software now starts partitioins at sector 2048, the first sector as 63 was back with XP.
But you have a new 4K drive and will have poor performance with your configuration.

       Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector) 
   Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by Acharn on 2016-05-28
Thank you for the information. I don't know why the partitions don't start on "physical boundary." As far as I know the only system that has ever been installed on this drive was OEM Windows 7, installed in late October 2013. I don't think that has anything to do with my problem, which has to do with the mouse and keyboard apparently not being detected when I boot from a CD using Microsoft but are detected booting with grub , and also the boot loader not detecting the hard drive in Windows, but not having any problem in Linux. I have used this Windows Installation DVD to repair Windows, but suddenly it stopped working. What would have to change so a CD would stop loading drivers? My first thought was that the DVD player was broken (that's happened a few times over the years), but Linux CDs and DVDs boot fine, so that's not it. Could something have changed the BIOS ROM so it prevents Windows from booting? Seems impossible.

---

### Post by oldfred on 2016-05-28
It almost had to have an XP install that was updated to Windows 7. Only older Windows like XP used sector 63 as first sector.
It may have been a newer Windows 7 system originally configured for XP that many down graded to, but then reset to Windows 7??

It does seem very strange that system works ok with Linux but not with Windows.

But not detecting boot loader is most often a flash drive or DVD configuration issue. Even ones that worked before can get corrupted and need resetting or replacing.

---

### Post by Acharn on 2016-05-28
I have to admit I can't be sure it wasn't originally XP. I ordered the parts based on a DIY article at Toms Hardware and intended to assemble them myself. I told the shop I didn't want them to install Windows, because I intended to install Ubuntu. When I went to pick them up they had already assembled the parts and installed Windows. When I took delivery on 1 November it was running Windows 7, but it's possible they installed XP first, and then decided to install Win 7. As it happens I decided to keep Windows because I'm addicted to the Medieval-Total War game and have never been able to get it to run under wine. From time to time I cranked up the Ubuntu live CD, and then for a while ran a usb stick with persistence, and then did a straight installation to a usb stick which works better. I'm currently using a Sandisk Extreme USB 3.0 32GB and it's as comfortable as having the Ubuntu on a hard drive.

Well, tomorrow I'll take the box back to the shop that first built it and see what they can do. I've backed up the data that's important to me and if they decide to reformat ind install Windows 10 so be it. I only run freeware or games that I already have an install disk for, so it might actually be good to get rid of all the cruft.

---

