---
title: "Yet another grub rescue thread"
date: 2013-09-07
forum: General Help
---

### Post by guscavge on 2013-09-07
Apologies for creating another thread about what seems a very common problem. I've read through previous ones but none gave me a good answer for my case.

I run Windows 7 on one partition, Ubuntu 13.04 on another. Every time I turn on the computer I get a screen asking which partition I want to boot: Ubuntu, Windows, or a couple of recovery and safety ones. This morning, out of tiredness, I picked a strange "Acer Recovery" partition, but made sure to exit it and restart the computer as soon as I could.

However, I have not been able to get the system to work since then. All I get is a black screen that reads "error: no such partition", and prompts a grub rescue.

What does one do in this situation? Any way of recovering both Windows and Ubuntu without a dreadful re-installation?

Thanks in advance

---

### Post by zero2xiii on 2013-09-07
Hay,

If possible, get into a live environment (CD or USB will be fine) and then run the following so we can see what is going on in your system. Please post the output of each command in code tags separately.

```
lsblk #list block devices
df -h #display current disk usage and mount locations. **I Think this will not provide much except the live environment but include it just to be safe
sudo parted -l #List partition layouts on all block devices

```

This should give us the information we need to understand what is going on and helping you to recover your system if it is still possible.

Cheers

---

### Post by guscavge on 2013-09-07
Thanks for the quick answer. 

I don't have an Ubuntu CD or USB with me at the moment, but I hopefully will within the next 8 hours. I'll do as you say then, and post the results

---

### Post by grahammechanical on 2013-09-07
I suspect that the boot menu is a Windows/Acer menu and not Grub. I would be very surprised if Grub gave an option to load to Acer Recovery. I may be wrong. It may be that a Windows/Acer menu is chainloading into Grub to load Ubuntu and that is why you are seeing Grub Rescue. Something was changed. What was it? Can you load into Windows? You do not make it clear that you can.

Regards.

---

### Post by oldfred on 2013-09-07
Often the first thing the Vendor recovery does is rewrite partition table. And since Windows does not know Linux partitions, your Linux partition was deleted. Often it now is just unallocated space and using testdisk and restoring missing partition will fully restore your system.

Testdisk is in the repository, so you can add it to your Live version installer or Testdisk is on most Linux repairCDs.

       [https://help.ubuntu.com/community/DataRecovery#Lost_Partition]("https://help.ubuntu.com/community/DataRecovery#Lost")


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by guscavge on 2013-09-07
> **grahammechanical said:**
> Something was changed. What was it? Can you load into Windows? You do not make it clear that you can.

Regards.
I'm almost certain that nothing changed. As soon as Acer Recovery loaded, I clicked on 'Exit'.

Until this morning, I could start up my computer on Ubuntu, windows 7, windows safe mode, Acer Recovery, and one more mode I can't remember. Since the Acer Recovery incident, I can't open any of these modes. As soon as I boot the computer I get the "grub rescue" message.

Anyway, for the time being I'll try what zero2xiii suggests. I should have results within 15 minutes or so

---

### Post by guscavge on 2013-09-07
OK, here are the results of what **zero2xiii** suggested:

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 596.2G  0 disk 
&#9500;&#9472;sda1   8:1    0    13G  0 part 
&#9500;&#9472;sda2   8:2    0   100M  0 part 
&#9500;&#9472;sda3   8:3    0 309.7G  0 part 
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7.7G  0 part [SWAP]
sdb      8:16   1   3.7G  0 disk 
&#9492;&#9472;sdb1   8:17   1   3.7G  0 part /cdrom
sr0     11:0    1     6G  0 rom  /media/ubuntu/PES2012
loop0    7:0    0 757.3M  1 loop /rofs



```

```
Filesystem      Size  Used Avail Use% Mounted on
/cow            3.8G   87M  3.8G   3% /
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           776M  876K  775M   1% /run
/dev/sdb1       3.8G  793M  3.0G  21% /cdrom
/dev/loop0      758M  758M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           3.8G  940K  3.8G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            3.8G  148K  3.8G   1% /run/shm
none            100M   28K  100M   1% /run/user
/dev/sr0        6.1G  6.1G     0 100% /media/ubuntu/PES2012


```

The final one gave some problems, apparently. But here it goes anyway:
```
Model: ATA TOSHIBA MK6465GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.0GB  14.0GB  primary   ntfs            diag
 2      14.0GB  14.1GB  105MB   primary   ntfs            boot
 3      14.1GB  347GB   333GB   primary   ntfs
 4      347GB   640GB   294GB   extended
 5      632GB   640GB   8243MB  logical   linux-swap(v1)


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 3999MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  3999MB  3995MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

---

### Post by oldfred on 2013-09-07
Your space in the extended from 347 to start of swap at 632 is classic what Windows does. Partition is still there, just erased from partition table. All you need to do is get it back into partition table with testdisk, parted or sfdisk. Testdisk is usually the easiest as the other require you to input either  approximate sector start or exact sector start.

---

### Post by guscavge on 2013-09-07
> **oldfred said:**
> Your space in the extended from 347 to start of swap at 632 is classic what Windows does. Partition is still there, just erased from partition table. All you need to do is get it back into partition table with testdisk, parted or sfdisk. Testdisk is usually the easiest as the other require you to input either  approximate sector start or exact sector start.

Cheers, that seems good enough.

But (apologies for the retarded question) how do I manage to install/run Testdisk when I'm not able to start Ubuntu at all? Is there any way to run it from a USB drive like I'm doing with Ubuntu at the moment?

---

### Post by oldfred on 2013-09-07
It is in repository. Just run this from your live installer.

sudo apt-get install testdisk

It will not be saved on reboot but will work as long as you are in your live system.

---

### Post by guscavge on 2013-09-07
Thank you again, **oldfred**. I will update on the results

---

### Post by guscavge on 2013-09-08
OK, after a quick search this is what I get:

```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
     Partition               Start        End    Size in sectors
>D HPFS - NTFS              0  32 33  1697  43 10   27262976 [PQSERVICE]
 D HPFS - NTFS           1697  43 11  1709 233 60     204800 [SYSTEM RESERVED]
 D HPFS - NTFS           1709 233 61 42139 100 34  649499545 [Acer]
 D Linux                42139 118 28 76823  35 12  557193216
 D Linux Swap           76823  35 13 77825  69 52   16099312







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continueubuntu@ubuntu:~$ 
NTFS, 13 GB / 13 GiB


```
What now? The guides I have seen so far don't really explain the next step...

---

### Post by guscavge on 2013-09-08
Did a deeper search, and the results are less than promising:

```
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63

The harddisk (640 GB / 596 GiB) seems too small! (< 2805 GB / 2612 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                59389 212 24 94073 129  8  557193216
   Linux                59391 222 32 94075 139 16  557193216
   Linux                59393 102 38 94077  19 22  557193216
   Linux                59393 232 40 94077 149 24  557193216
   Linux                59394 107 42 94078  24 26  557193216
   Linux                59396 215 20 94080 132  4  557193216
   Linux                59397  25 21 94080 197  5  557193216
   Linux                59401 143  7 94085  59 54  557193216
   HPFS - NTFS          175929  41 36 341040 164 22 2652515951


[ Continue ]
EXT4 Large file Sparse superblock Recover, 285 GB / 265 GiB
```
Is there still hope?

---

### Post by oldfred on 2013-09-08
This is your LInux partition.
  D Linux                42139 118 28 76823  35 12  557193216

Use T & Change type to L as it must be logical.

---

### Post by guscavge on 2013-09-08
> **oldfred said:**
> This is your LInux partition.
  D Linux                42139 118 28 76823  35 12  557193216

Use T & Change type to L as it must be logical.

Thank you, I will do that.

One further question, although it is not entirely Ubuntu-related:

Do I need to change something in the Windows partition too? I would still like to have a dual booting system with Ubuntu and Windows if possible...

---

### Post by oldfred on 2013-09-08
Many dual boot without issues. Of course there are a few exceptions, but most of those can be resolved.

It is best to always have a repairCD or liveCD/DVD/flash repair drive for the current version of every operating system you have installed. Then making repairs is a lot easier than tying to scramble around after it breaks.

---

### Post by guscavge on 2013-09-08
Nothing, I'm afraid I turned the Linux partition into a logical one, restarted, and got the same grub rescue message. Still can't open either one of my operating systems...

---

### Post by oldfred on 2013-09-08
From liveCD does it show your Linux partition correctly now?

If so you may just need a reinstall of grub. And that is easiest with Boot-Repair but you can do it from live installer with a few commands.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
      
 Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by guscavge on 2013-09-08
> **oldfred said:**
> From liveCD does it show your Linux partition correctly now?

I don't think so, no.

The Ubuntu Partition Editor shows what used to be the Windows partition as "unallocated". The other partition, which should be the Ubuntu one, shows up as having file system "ext4", but its status is "not mounted". I don't know what to make of that.

The Bootinfo report is here:
[http://paste.ubuntu.com/6079868/](http://paste.ubuntu.com/6079868/)

---

### Post by zero2xiii on 2013-09-08
> **guscavge said:**
> I don't think so, no.

The Ubuntu Partition Editor shows what used to be the Windows partition as "unallocated". The other partition, which should be the Ubuntu one, shows up as having file system "ext4", but its status is "not mounted". I don't know what to make of that.

The Bootinfo report is here:
[http://paste.ubuntu.com/6079868/](http://paste.ubuntu.com/6079868/)

"Not mounted" means it is not mounted, you should be able to atleast get ubuntu back so far using boot repair and repairing grub. The unallocated section of the drive you say contains windows mean that is probably still lost, try and recover that as well first before repairing grub.

Just my two cents.

EDIT:
Actually, after reading the boot info post, you can go ahead and repair grub. Everything seems to be fine:

> sda1: __________________________________________________________________________

    [B]File system:       ntfs
    Boot sector type:  Windows Vista: NTFS[/B]
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    **File system:       ext4**
    Boot sector type:  -
    Boot sector info: 
    **Operating System:  Ubuntu 13.04** 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 30398 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

---

### Post by guscavge on 2013-09-08
OK then. This inexperienced Ubuntu user is going out on a voyage to try to repair grub. Wish me luck! I'll be back with an update as soon as I can

(Thanks to everyone once more)

---

### Post by guscavge on 2013-09-08
I just used Boot Repair to try to fix the GRUB (I chose the recommended repair).

Then I restarted the computer and just got a message stating "missing operating system", "no boot filename received" and "no bootable device -- insert boot disk and press any key". Still no luck starting up windows or Ubuntu...

EDIT: the latest report I got from Boot Repair is this: http://paste.Ubuntu.com/6080331

---

### Post by oldfred on 2013-09-08
Now all your other partitions are gone??
Did you delete them in testdisk.

A few BIOS have to have a boot flag on a primary partition (as if booting Windows) or they give a no operating system found error. Windows requires a boot flag on a primary partition. Grub does not use nor need one, but we suggest a boot flag on sda1 thru sda4 just because of the BIOS that seem to need it.

---

### Post by guscavge on 2013-09-08
I did not delete anything on testdisk, not to my knowledge. In fact, the previous report from Boot Repair seemed quite normal, and I haven't opened testdisk since.

Regarding the boot flag, how would I go about it? Do I do that on testdisk? I seem to recall that none of the partitions appeared on testdisk as "primary bootable", is that what I have to change?

---

### Post by oldfred on 2013-09-08
You can use gparted, manage flags. But the Bootinfo report did not show anything but the extended partition and the Linux partition. 
Before doing anything make sure you partitions are correct.

---

### Post by guscavge on 2013-09-09
Well, at least Testdisk shows the same partitions it did 22 hours ago. That seems normal enough:

```
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
     Partition               Start        End    Size in sectors
>D HPFS - NTFS              0  32 33  1697  43 10   27262976 [PQSERVICE]
 D HPFS - NTFS           1697  43 11  1709 233 60     204800 [SYSTEM RESERVED]
 D HPFS - NTFS           1709 233 61 42139 100 34  649499545 [Acer]
 D Linux                42139 118 28 76823  35 12  557193216
 D Linux Swap           76823  35 13 77825  69 52   16099312







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 13 GB / 13 GiB


```

EDIT: And just to be sure, GParted also shows the same pattern it showed yesterday. The Ubuntu partition seems to be there (although now it's classed as "boot"), whereas what should be the Windows partition shows up as unallocated.

---

### Post by oldfred on 2013-09-09
Now testdisk is showing all the partitions but the D is deleted. You have to use T and change to P or L. Windows has to be P as it only boots from primary partitions.

---

### Post by guscavge on 2013-09-09
> **oldfred said:**
> Now testdisk is showing all the partitions but the D is deleted. You have to use T and change to P or L. Windows has to be P as it only boots from primary partitions.

Just to be sure: when I click on 'T' to 'change type', TestDisk offers me many different partition types. I would want to select the type that the partition was originally, right? That would be NTFS?

---

### Post by guscavge on 2013-09-09
> **guscavge said:**
> Just to be sure: when I click on 'T' to 'change type', TestDisk offers me many different partition types. I would want to select the type that the partition was originally, right? That would be NTFS?

Never mind about that, I realised how stupid my question was.

Anyway, I did as suggested and something seems to have change. I now turned my computer back on and got nothing but a black screen with an intermittent underscore on the top-left corner. (Before I did what **oldfred **said, I got a message reading "missing operating system" instead).

Anything else I should/could do here?

---

### Post by oldfred on 2013-09-09
Did you have Video issues before booting Ubuntu? That seems like a video issue. Did you have to use nomodeset?
It may also not have Windows in grub menu, so you would not get grub menu by default.
Try holding shift key from BIOS until menu appears.

Or from liveCD does it now show all your partitions?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by guscavge on 2013-09-09
Never had video issues to my knowledge. 

I will try holding shift until a menu appears in a moment.

The thing that bothers me is that I've opened TestDisk once more, searched through my partitions, and all of them appear with a 'D' next to them, just like before. Either I'm doing this completely wrong, or I am no longer able to change the partition types...

---

### Post by oldfred on 2013-09-09
IF they are d then they are still deleted. I have not used that function with testdisk. Do you have to do a save?

If you know start & size we litterally can force a new partition table. But it is difficult as testdisk uses the old CHS - cylinders, heads, sectors where all systems now just use sectors and a bit of math is involved to convert. Never done it but one or two threads were posted years ago where those who really understood drive layout did manually modify partitions.

You can also try parted rescue but again have to have a good idea of start & end of partition on drive. It only searches regions near your suggested start for beginning of partition.

---

### Post by guscavge on 2013-09-09
Oh dear, that does not sound good. 

But TestDisk tells you where the partitions start and what size they have, does it no? Would it not be possible to just extract that data into GParted, and try to rescue them from there?

---

### Post by oldfred on 2013-09-09
Looking at testdisk screens is a write command. Have you used that after changing partitions to be correct?

---

### Post by guscavge on 2013-09-09
> **oldfred said:**
> Looking at testdisk screens is a write command. Have you used that after changing partitions to be correct?

Yes. After changing the partitions to 'Logical' and 'Primary', I selected 'Write'

---

### Post by oldfred on 2013-09-09
And then from fdisk post this.

sudo fdisk -lu

---

### Post by guscavge on 2013-09-09
> **oldfred said:**
> And then from fdisk post this.

sudo fdisk -lu

This is the result

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9489ed4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        27469824   676969368   324749772+   7  HPFS/NTFS/exFAT
/dev/sda2       676970469  1234177559   278603545+   f  W95 Ext'd (LBA)
/dev/sda5       676970496  1234163711   278596608   83  Linux

Disk /dev/sdb: 3999 MB, 3999268864 bytes
82 heads, 18 sectors/track, 5292 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000037a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7811071     3901504    c  W95 FAT32 (LBA)


```

---

### Post by oldfred on 2013-09-09
You still are missing two NTFS. Swap is also missing but I would not worry about it. It has no data, can easily be recreated, but may need a minor edit to fix UUID in fstab as final repair.

If this had been in sectors it would have been a lot easier to repair as then we would know exact beginning & end. In MB & GB it only give approximates.
>  Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.0GB  14.0GB  primary   ntfs            diag
 2      14.0GB  14.1GB  105MB   primary   ntfs            boot
 3      14.1GB  347GB   333GB   primary   ntfs
 4      347GB   640GB   294GB   extended
 5      632GB   640GB   8243MB  logical   linux-swap(v1)

  >     
Device Boot      Start         End      Blocks   Id  System
/dev/sda1        27469824   676969368   324749772+   7  HPFS/NTFS/exFAT
/dev/sda2       676970469  1234177559   278603545+   f  W95 Ext'd (LBA)
/dev/sda5       676970496  1234163711   278596608   83  Linux



You have recovered Linux but lost Windows.

---

### Post by guscavge on 2013-09-10
Well, I can't say I ever loved Windows anyway.

Just two more questions if you don't mind, **oldfred **(or anyone patient enough to answer):

1- Is it feasible to recover some files from what used to be my Windows partition? Thankfully I had backups of pretty much everything, but I would like to be sure if possible.

2- How do I go about recovering my old Ubuntu partition? I still can't get my laptop to start up Ubuntu

---

### Post by oldfred on 2013-09-10
Did testdisk deeper search show files? and which NTFS is it showing? You had diag (Vendor recovery?), boot & main install of Windows.
If it recovered the correct partition for Linux you may need to run fsck from liveCD and reinstall grub. If not then deeper search?
Is hard drive failing as testdisk usually just writes new partition table and you are good. From Disks or Disk Utility  what does it say about drive?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by guscavge on 2013-09-10
> **oldfred said:**
> Did testdisk deeper search show files? 
TestDisk deeper search does show some files. An example:

```
 P HPFS - NTFS           1709 233 61 42139 100 34  649499545 [Acer]
Directory /

>dr-xr-xr-x     0     0         0  1-Sep-2013 16:03 .
 dr-xr-xr-x     0     0         0  1-Sep-2013 16:03 ..
 dr-xr-xr-x     0     0         0 15-Oct-2011 16:19 Intel
 dr-xr-xr-x     0     0         0 15-Oct-2011 17:08 $Recycle.Bin
 dr-xr-xr-x     0     0         0 15-Oct-2011 16:24 book
 -r--r--r--     0     0      8192 30-Aug-2010 09:47 BOOTSECT.BAK
 dr-xr-xr-x     0     0         0  2-Jun-2012 10:26 found.000
 -r--r--r--     0     0 6183485440  6-Sep-2013 13:47 hiberfil.sys
 -r--r--r--     0     0        40 31-Aug-2012 15:34 log.txt
 dr-xr-xr-x     0     0         0 15-Oct-2011 17:08 OEM
 -r--r--r--     0     0 8244649984  6-Sep-2013 13:47 pagefile.sys
 dr-xr-xr-x     0     0         0 14-Jul-2009 03:20 PerfLogs
 dr-xr-xr-x     0     0         0 13-Mar-2013 11:33 Program Files
 dr-xr-xr-x     0     0         0 13-Jul-2013 10:07 Program Files (x86)
                                                   Next

```
Can something like that be rescued at all? If not, I'm happy to start all over again with a clean installation of Ubuntu, and forget about the Windows partition

---

### Post by guscavge on 2013-09-10
OK, so I completed another Deeper Search. These are the results:

```
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0  32 33  1697  43 10   27262976 [PQSERVICE]
 D HPFS - NTFS           1697  43 11  1709 233 60     204800 [SYSTEM RESERVED]
 D HPFS - NTFS           1709 233 60  1722 169 46     204800
 D HPFS - NTFS           1709 233 61 42139 100 34  649499545 [Acer]
 D HPFS - NTFS           1709 233 61 77825  37 36 1222791168 [Acer]
 D Linux                42139 118 28 76823  35 12  557193216
 D HPFS - NTFS          42157 144 36 43854 155 13   27262976
 D HPFS - NTFS          72443 157 35 74140 168 12   27262976
 D Linux Swap           76823  35 13 77825  69 52   16099312
  
```
I would post which files are present but it seems to have frozen at the moment...

---

### Post by guscavge on 2013-09-10
> **oldfred said:**
> 
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Strange result with this.

When I try e2fsck, it tells me that the partition is in use.
And yet when I try to unmount the partition, it says that it is not mounted :confused:

---

### Post by oldfred on 2013-09-10
Post #42 is showing all the partitions as deleted. And you have some overlaps so you can only undelete the correct set of non-overlapping partitions.

With liveCD, you have to make sure you have also unmounted swap with swap-off. Swap is usually in the extended partition and is used by most liveCD to speed things up. But having swap mounted, mounts extended partition and then all partitions in extended are not available.

```
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0  32 33  1697  43 10   27262976 [PQSERVICE]
 [COLOR=#ff0000]D HPFS - NTFS           1697  43 11  1709 233 60     204800 [SYSTEM RESERVED][/COLOR]
 D HPFS - NTFS           1709 233 60  1722 169 46     204800
 [COLOR=#ff0000]D HPFS - NTFS           1709 233 61 42139 100 34  649499545 [Acer][/COLOR]
 D HPFS - NTFS           1709 233 61 77825  37 36 1222791168 [Acer]
[COLOR=#ff0000] D Linux                42139 118 28 76823  35 12  557193216[/COLOR]
 D HPFS - NTFS          42157 144 36 43854 155 13   27262976
 D HPFS - NTFS          72443 157 35 74140 168 12   27262976
 [COLOR=#ff0000]D Linux Swap           76823  35 13 77825  69 52   16099312[/COLOR]

```

Change * on first partition to P, change second partition (system reserved) to * as that is your boot partition for Windows. Make sure first partition stays undeleted and undelete all red partitions. Linux & linux swap must be logical. and hten save all those changes.

---

### Post by guscavge on 2013-09-11
> **oldfred said:**
> ```
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
     Partition               Start        End    Size in sectors
>* HPFS - NTFS              0  32 33  1697  43 10   27262976 [PQSERVICE]
 [COLOR=#ff0000]D HPFS - NTFS           1697  43 11  1709 233 60     204800 [SYSTEM RESERVED][/COLOR]
 D HPFS - NTFS           1709 233 60  1722 169 46     204800
 [COLOR=#ff0000]D HPFS - NTFS           1709 233 61 42139 100 34  649499545 [Acer][/COLOR]
 D HPFS - NTFS           1709 233 61 77825  37 36 1222791168 [Acer]
[COLOR=#ff0000] D Linux                42139 118 28 76823  35 12  557193216[/COLOR]
 D HPFS - NTFS          42157 144 36 43854 155 13   27262976
 D HPFS - NTFS          72443 157 35 74140 168 12   27262976
 [COLOR=#ff0000]D Linux Swap           76823  35 13 77825  69 52   16099312[/COLOR]

```

Change * on first partition to P, change second partition (system reserved) to * as that is your boot partition for Windows. Make sure first partition stays undeleted and undelete all red partitions. Linux & linux swap must be logical. and hten save all those changes.
No can do. I get a 'Structure: Bad' message as soon as I set things up like you say.

Looking at it closer, the 'Structure: Bad' message appears if I try to change either of these two partitions:

```
D HPFS - NTFS           1709 233 61 77825  37 36 1222791168 [Acer]
 D Linux                42139 118 28 76823  35 12  557193216


```

---

### Post by oldfred on 2013-09-11
the Acer that ends with 77825 is the NTFS partition before you shrank it for Linux. Since Linux partition starts at 42139 you need the acer with an end of 42139 which is the one in red that I highlighted. That structure will then be ok. 
The three numbers are the CHS - cylinders,heads, sectors of each partition and show start & end. They cannot overlap in a valid structure.

---

### Post by guscavge on 2013-09-11
> **oldfred said:**
> the Acer that ends with 77825 is the NTFS partition before you shrank it for Linux. Since Linux partition starts at 42139 you need the acer with an end of 42139 which is the one in red that I highlighted. That structure will then be ok. 
The three numbers are the CHS - cylinders,heads, sectors of each partition and show start & end. They cannot overlap in a valid structure.

I think the problem is with the number of partitions I try to save. 

If I make PQSERVICE the primary partition, SYSTEM RESERVED the primary bootable, and then try to save the other 3 (Linux, Linux Swap + Acer), I get an error message. I can save any four partitions, but not 5

---

### Post by oldfred on 2013-09-11
You just have to be sure to not try to save one's that overlap.

---

### Post by guscavge on 2013-09-11
This looks promising:

**Oldfred**, I made the changes you suggested. I then re-booted the computer, and it went straight into Windows 7. The OS works fine, all my files are there... Thank you for that.

But I never got an option to start Ubuntu instead of Windows 7. Is there something I need to re-set to get that option?

---

### Post by oldfred on 2013-09-11
It could just be that you have the Windows boot loader in the MBR and need to reinstall grub2's boot loader.
Also now might be a good time to backup anything in Windows before doing anything else.

Again post this to see if all partitions are shown and details by sector.
sudo fdisk -lu

You can use Boot-Repair or just reinstall grub to MBR from Live installer.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2  info quick & full chroot version - method 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD

---

### Post by guscavge on 2013-09-11
I just backed up all my important Windows files, just in case.

sudo fdisk -lu gives me this result:
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9489ed4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488    7  HPFS/NTFS/exFAT
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   676969368   324749772+   7  HPFS/NTFS/exFAT
/dev/sda4       676969398  1250274689   286652646    f  W95 Ext'd (LBA)
/dev/sda5       676970496  1234163711   278596608   83  Linux

Disk /dev/sdb: 3999 MB, 3999268864 bytes
82 heads, 18 sectors/track, 5292 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000037a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7811071     3901504    c  W95 FAT32 (LBA)

```

The Bootinfo report is here:
[http://paste.ubuntu.com/6094213/](http://paste.ubuntu.com/6094213/)

---

### Post by oldfred on 2013-09-11
You have a couple of minor issues. Testdisk still uses CHS, and sometimes rounds wrong and creates extended partition beyond end of drive. You need to use fixparts to correct that and write corrent end sector to extended partition.
>  /dev/sda4 ends after the last sector of /dev/sda


You do not have swap and fstab still calls for old swap UUID. It will give a boot error on that but should boot after you run fixparts. You then can create new swap and update fstab entry with new UUID.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc. This creates text file you can use to restore current partition table.
sudo sfdisk -d /dev/sdX > parts.txt

You can use gparted to create new swap partition and then list partitions UUIDs and edit fstab. You will have to create partition using liveCD, but then can boot into system still with swap error and update fstab.

To see UUID of new swap:

        sudo blkid -c /dev/null -o list
Then replace UUID in fstab with above entry:
      
 sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a

---

### Post by guscavge on 2013-09-12
I switched on my computer this morning and both Windows and Ubuntu were working smoothly. The only issue is that the start-up menu showed one Ubuntu partition and two different Windows ones, probably due to the issues you mention.

In any case, I will try to follow your advice after the weekend as soon as I have time.

In the meantime, I can only thank **oldfred**. You are a true legend, hats off to you

---

