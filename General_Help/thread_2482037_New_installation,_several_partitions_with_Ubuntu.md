---
title: "New installation, several partitions with Ubuntu"
date: 2022-12-17
forum: General Help
---

### Post by daanheuvelbeuk on 2022-12-17
While trying to get Ubuntu in the air again on my new computer I saw that the physical hard disk with Ubuntu and its data had 4 partitions with Ubuntu on it. 
/dev/sdb3 originally containing Ubuntu
/dev/sdb5 with a new installation? 
/dev/sdb6 also with a new installation.
/dev/sdb7 also with a new installation.

This is probably caused by me while installing Ubuntu on the hard drive in previous weeks, and letting the installation program decide where to install Ubuntu. AFAIS it created new partitions where it installed Ubuntu on, instead of reusing the original partition. 

What do I do? Format sdb3 to ext4 and assign / to it? And what about sdb5, sdb6 and sdb7, just format it to ext4 and hope to add it back to /home in the future?

I formatted /dev/sdb3 to Ext4 and assigned / to it. Hope this gets the intended OS.
I formatted /dev/sdb5, /sdb6 and /sdb7 to Ext4 and assigned /free1, /free2 and /free3 to it, as I could not assign /home three times. And I hope my original data will be accessible in my /home.

And now I am in a Minmal BASH like editing situation. Grrr. Finding my way out of this hole.

That is not going to happen today. I wanted to try to solve my Minimal Bash line editing problem using [https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/). But when I started my Live CD session (using an USB dongle) and started to try Ubuntu I got a yellow screen where I could not distinguish the letters. So I stopped that. Anyone know what I can do? 

I start in a GRUB line editing mode. What steps can I take?

---

### Post by TheFu on 2022-12-17
I suspect the storage was using MBR partitioning, not GPT.  So, when you touched on of the partitions, you destroyed an "extended primary partition" which was holding a few logical partitions inside.  

Listing device names doesn't tell us what actually happened. Rather than try to describe what you have, please, always, always, run some specific commands and post the exact command along with the exact output for others to interpret.  Perhaps your reading of the information wasn't correct.  Just sayin'.  

It is likely you'll be running a new install.  Boot into a "Try Ubuntu" environment and run 'lsblk -e 7 -o name,size,type,fstype,mountpoint' and 'sudo parted -l' commands to gather some information.  We might need some other commands to really know what is going on if you used a volume manager too. Can't tell yet.

When I'm doing a fresh install, I find the Ubuntu installer not-so-great and toggle over to a different tty to do partitioning and lots of other storage work before toggling back to the installer to connect the new storage in a way that the installer recognized.  Other distros have much better storage setup wizards.  I can only guess that Canonical thinks keeping it simple is more important than making more complicated storage easy to setup.  IDK.

Run the requested commands. Post the output. Hopefully, someone can help.  You might want to run the boot-info script or the system-info script from the Ubuntu Forums Github page to provide more complete information which will get better help.  [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) has instructions for a 1-line, copy/paste, way to get the script and run it.

---

### Post by VMC on 2022-12-17
Yes, as TheFu said, I 'try ubuntu', and have my partition setup before hand, then select "Something Else" when installing and select my own partitions.

---

### Post by daanheuvelbeuk on 2022-12-30
It took some time, and I did not get the results during "Try Ubuntu" (my monitor becomes almost monochrome yellow), but here is what you asked for after a fresh installation.

The result from 'lsblk -e 7 -o name,size,type,fstype,mountpoint':
```

NAME          SIZE TYPE FSTYPE MOUNTPOINT
sda         931,5G disk        
&#9500;&#9472;sda1        100M part vfat   
&#9500;&#9472;sda2         16M part        
&#9500;&#9472;sda3      195,2G part ntfs   
&#9500;&#9472;sda4       97,7G part ntfs   
&#9500;&#9472;sda5      146,5G part ntfs   
&#9500;&#9472;sda6       97,7G part ntfs   
&#9492;&#9472;sda7      394,4G part ntfs   
sdb           3,6T disk        
&#9500;&#9472;sdb1        189M part vfat   
&#9500;&#9472;sdb2       14,9G part swap   [SWAP]
&#9500;&#9472;sdb3       78,8G part ext4   /
&#9500;&#9472;sdb4        2,4T part ext4   /home
&#9500;&#9472;sdb5      412,5G part ext4   /free2
&#9500;&#9472;sdb6      394,6G part ext4   /free3
&#9492;&#9472;sdb7      404,3G part ext4   /free1
sdc           3,6T disk        
&#9500;&#9472;sdc1      155,3G part ntfs   /media/macamba/Seagate Windows USB Disk
&#9500;&#9472;sdc2        5,6G part vfat   
&#9492;&#9472;sdc3        3,5T part ext4   /media/macamba/Seagate USB
sr0          1024M rom         
nvme0n1     931,5G disk        
&#9500;&#9472;nvme0n1p1   100M part vfat   /boot/efi
&#9500;&#9472;nvme0n1p2    16M part        
&#9500;&#9472;nvme0n1p3 930,8G part ntfs   
&#9492;&#9472;nvme0n1p4   605M part ntfs   
```

The result from 'sudo parted -l':
```

Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16,8MB               Microsoft reserved partition  msftres
 3      123MB   210GB   210GB   ntfs         Basic data partition          msftdata
 4      210GB   315GB   105GB   ntfs         Basic data partition          msftdata
 5      315GB   472GB   157GB   ntfs         Basic data partition          msftdata
 6      472GB   577GB   105GB   ntfs         Basic data partition          msftdata
 7      577GB   1000GB  423GB   ntfs         Basic data partition          msftdata


Model: ATA WDC WD4003FFBX-6 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  199MB   198MB   fat32                 boot, esp
 2      199MB   16,2GB  16,0GB  linux-swap(v1)        swap
 3      16,2GB  101GB   84,6GB  ext4
 4      101GB   2700GB  2599GB  ext4
 7      2700GB  3134GB  434GB   ext4
 5      3134GB  3577GB  443GB   ext4
 6      3577GB  4001GB  424GB   ext4


Model: Seagate Backup+ Hub BK (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  167GB   167GB   ntfs         Basic data partition  msftdata
 2      167GB   173GB   5999MB  fat32                              boot, esp
 3      173GB   4001GB  3828GB  ext4         Basic data partition  msftdata


Model: KINGSTON SNVS1000G (nvme)
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16,8MB               Microsoft reserved partition  msftres
 3      123MB   1000GB  999GB   ntfs         Basic data partition          msftdata
 4      1000GB  1000GB  634MB   ntfs                                       hidden, diag

```

The requested output of Github system-info script can be found on [https://termbin.com/y5pi](https://termbin.com/y5pi)

---

### Post by TheFu on 2022-12-30
I'm confused by all the partitions.  There more more flexible methods in Linux, like LVM2. Basically, I have 3 partitions, a boot, efi, and everything else.  With LVM, at least last time I used it, a separate boot partition was required.

Inside the larger partition, I setup an LVM PV, VG, then allocate LVs from the VG for the size I need for the next few months only.  LVs are like super-flexible partitions and on an LV (logical volume) is where a file system is placed.  Extending an LV, is 1 command, while running.

On some of my systems, I'm using less than 50% of the physical storage because the need to grow into it hasn't happened.
Also, that unallocated VG space can be used to create snapshots, which is part of a backup process that doesn't have any file corruption, since the snapshot holds the running system data while the backups pull from the static data that is frozen.  This is how enterprises backup running DBMS and other systems without downtime.

LVM2 has been around over 20 yrs, so 99.999% of the time when you see someone say "LVM", they are talking about the same thing.  Also, LVM2 commands are the same across all Linux systems, so the distro doesn't matter.  RHEL, SuSE, Ubuntu, or any other Linux in the last 10 yrs uses the same stuff for LVM. Any tutorial is as good as the next, if it makes sense to you.

Anyways, check out LVM if you need non-trivial storage management and if you use LVM, size the LVs for what you need now, not what you might need in 6 months.

A few days ago, I needed some more space in my HOME on a desktop system that I try to keep light and small.  Because the VG had some space available, extending the home LV was trivial:
```
$ sudo lvextend -r -L+4G  /dev/mapper/vgubuntu--home
```
Less than 2 seconds later, I was seeing 4GB more storage available on the in-use, mounted, file system.  I don't like wasted space that isn't needed. Best to not even mount it.

---

### Post by daanheuvelbeuk on 2023-01-04
> **TheFu said:**
> I'm confused by all the partitions. 

Thanks for taking the time to help me. The number of partitions of my Ubuntu drive is probably caused by me installing Ubuntu while not choosing "Something else" during installation. I think the installation program took some space of my home drive each time, so now I have those several extra partitions. 

I think I have a solution for my whoes. Back up the data in my /home, install again, but now deleting /home, /free, /free1, /free2, and creating one new /home partition. I think this problem will be solved. Now I only have to find out how to copy data while preserving (date) attributes. I just ran a history and found the command I used the last time I made a backup (cp -pnrv).

---

### Post by TheFu on 2023-01-04
> **daanheuvelbeuk said:**
> Thanks for taking the time to help me. The number of partitions of my Ubuntu drive is probably caused by me installing Ubuntu while not choosing "Something else" during installation. I think the installation program took some space of my home drive each time, so now I have those several extra partitions. 

I think I have a solution for my whoes. Back up the data in my /home, install again, but now deleting /home, /free, /free1, /free2, and creating one new /home partition. I think this problem will be solved. Now I only have to find out how to copy data while preserving (date) attributes. I just ran a history and found the command I used the last time I made a backup (cp -pnrv).

a) always use "something else"
b) sudo  rsync -avz SOURCE TARGET

A single copy isn't a backup.  Backups with multiple versions are easy to make and relatively efficient if the correct tool is used.  cp/rsync/tar shouldn't be used directly as backup tools.  Use something that handles the versioning for you.  rsnapshot, rbackup, rdiff-backup, back-in-time .... there are lots of tools for this.  I use rdiff-backup.  The other 3 use a mix of librsync and hardlinks to keep versioned file storage requirements small.  Alas, they only maintain the last owner, group, permissions, ACLs and xattrs for each file.  Only rdiff-backup also versions those changes over revisions too.

If it isn't clear, all backup tools must run with root privileges to maintain all those things. Normal Unix permissions always apply, so to retain correct file ownership, the 0 uid must be used, regardless.

---

