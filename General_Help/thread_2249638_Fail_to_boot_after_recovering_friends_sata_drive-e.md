---
title: "Fail to boot after recovering friends sata drive-every good deed etc etc"
date: 2014-10-23
forum: General Help
---

### Post by debiant on 2014-10-23
Hello,

I helped a friend get their data back from a SATA SD drive after the laptop was fire damaged.  I'm guessing that I didn't unmount it properly?

I've tried to boot into recovery mode-I got this error:

/mnt/8E76E34 etc(name of sata driive that had laptop windows on it)
not ready
press S for skip, R fo retry (or something like that! Various options)

8E76E3...is the name of the SATA drive I no longer have that is "not ready".
I've tried to find it using FDISK, searching in /mnt/ /dev everywhere I can think of-I tried umount then the drive name and I've tried "locate" and "find" commands to try and find any referrence to it anywhere in the system.  Absolutely nothing.
No big disaster, I back stuff up a lot and I got everything else I need using a live CD but it a complete re-install to get my Linux box back and you know how when you get it all just right?  
And its nice to fix stuff! You always learn something new!
;)

Any suggestions please, I'd love to fix this and keep my Ultimate Edition 4.2 set up as it was!!!

---

### Post by Bashing-om on 2014-10-23
debiant; Hi !

Show us what there is to work with:
Boot up the liveDVD(USB) to "try ubuntu" mode and
Post back - Between Code Tags - the output of terminal commands:
```

sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
sudo blkid -c /dev/null

``` and we know then what it will take to try and boot the install.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by debiant on 2014-10-23
Hi Bashin-om,
I'll do that right now :p

I used a TAILS disk to get my stuff recovered just in case, a proper Ubuntu disk just downloading...

Hi Bashing-om
This is sda-linux disk, sdb a windows sd disk and sdc is the usb...

```
sudo fdisk -lu:

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00044ce5

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048   9764863   9762816   4.7G 82 Linux swap / Solaris
/dev/sda2       9766910 976771071 967004162 461.1G  5 Extended
/dev/sda5       9766912 976771071 967004160 461.1G 83 Linux

Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x103cb484

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdb1  *      2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sdb2       206848 500115455 499908608 238.4G  7 HPFS/NTFS/exFAT

Disk /dev/sdc: 14.8 GiB, 15846080512 bytes, 30949376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00152404

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 30949375 30947328 14.8G  c W95 FAT32 (LBA)
```

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  5000MB  4999MB  primary   linux-swap(v1)  boot
 2      5001MB  500GB   495GB   extended
 5      5001MB  500GB   495GB   logical   ext4


Model: ATA M4-CT256M4SSD2 (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   256GB  256GB  primary  ntfs


Model:  USB DISK 3.0 (scsi)
Disk /dev/sdc: 15.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.8GB  15.8GB  primary  fat32        boot, lba
```

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start     End         Size        Type      File system     Flags
 1      2048s     9764863s    9762816s    primary   linux-swap(v1)  boot
 2      9766910s  976771071s  967004162s  extended
 5      9766912s  976771071s  967004160s  logical   ext4
```

```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="fa226747-bfd4-4ae2-8545-78b619e1cc95" TYPE="swap" PARTUUID="00044ce5-01" 
/dev/sda5: UUID="024b1d64-eb74-4d2a-8ac8-23aa3d5e2fb4" TYPE="ext4" PARTUUID="00044ce5-05" 
/dev/sdb1: LABEL="System Reserved" UUID="FC4CB1394CB0F00E" TYPE="ntfs" PARTUUID="103cb484-01" 
/dev/sdb2: UUID="4A20F1E220F1D4C3" TYPE="ntfs" PARTUUID="103cb484-02" 
/dev/sdc1: LABEL="UBUNTU 14_1" UUID="668B-B0B2" TYPE="vfat" PARTUUID="00152404-01"
```

---

### Post by Bashing-om on 2014-10-23
debiant; Wow;

Upfront I have never encountered such a linux configuration .. 'sda1' as swap and as a primary partition, and boot code installed there ???
Normally I expect the operating system to be installed to 'sda1' and marked 'Boot' When 'buntu is the sole operating system installed onto the hard drive. (swap in the extended partition as a logical partition).

I am having my difficulties wrapping my mind around this.
How about we see what grub can tell us about how it is booting ?
Boot the install to the grub boot menu; press the 'c' key for a command line -> grub terminal;
Do terminal command:
```

set

```
In that output post back what is in the lines starting with
prefix=
root=

Grub's config files must reside on sda5 and I bet we still boot (hd0,msdos5) , but confirmation would be nice.

[INDENT][INDENT]we will do this
[/INDENT][/INDENT]

---

### Post by debiant on 2014-10-24
Hi Bashing-om,
Now how did I manage to do that?  I am still learning but I do love playing with it!  This is interesting-I'm not in any pain here-still getting all my e-mails on a laptop, nothing lost, but I do appreciate your help because I'm learning something :p
```
Prefix=(hd0,msdos5)/boot/grub
root=hd0,msdos5
```

I mucked up the install, didn't I?
:rolleyes:

---

### Post by Bashing-om on 2014-10-24
debiant; Well,

Yes and no on the mucking up - It works does it not ? ; so can not be toooo bad.
But as this is a fresh install, I would and do recommend that we (RE-)install to the conventional partitioning - to avoid problems in comprehension of the linux file system in the future.

For now, if you desire to continue this "learning experience" we can see about booting up the 'buntu install and see about fixing it permanently .

Let's see if ubuntu boots !
I want that you boot back to the grub prompt ( 'c' key at the grub boot menu );
Grub terminal commands:
```

linux (hd0,msdos5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,msdos5)/initrd.img
boot

```
As bios has found and handed off the booting to the boot code ( we know because of -> "Prefix=(hd0,msdos5)/boot/grub" is found), here above we are telling grub where the config files are. IF " /boot/grub/grub.cfg " is in a consistent state, ubuntu should boot !

ELSE: we find out why not and what other steps we must take.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by debiant on 2014-10-24
It worked for a while!!!

I've got Mint 17 Mate version, and I'm loving it.
sda1 is /boot/efi, sda2 is ext4!!!
):P

Thank you Bashing-om!

---

### Post by Bashing-om on 2014-10-24
debiant; Hey hey !

Great ya got it fingered out, and all is pretty.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and we have another adventure
[INDENT][INDENT][INDENT]some other time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

