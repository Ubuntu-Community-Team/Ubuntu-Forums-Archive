---
title: "Deleted partition, recovered it, need to boot!"
date: 2014-04-13
forum: General Help
---

### Post by Nabru on 2014-04-13
Hello,

I accidently deleted my Ubuntu partition and managed to recover it using TestDisk via Live CD. Now I need help booting to said partition. After I lost my Ubuntu partition I ran Windows recovery, and typed the next command into the CMD

```
[COLOR=#333333][FONT=Verdana]bootrec /fixmbr[/FONT][/COLOR]
```

This enabled me to boot Windows, download Live CD, run TestDisk and recover the lost partition.

Now I need help with the last step - how do I include my exsisting (recovered) Ubuntu installlation into the boot?

Help truly appreciated!

---

### Post by dragonfly41 on 2014-04-13
I would hope that boot-repair (from Software Centre) would help you with final lap.

---

### Post by Bashing-om on 2014-04-13
Nabru; Hi !  Welcome to the forum.

You are doing good work; to continue, let's see about (re-)installing grub to the MBR of the booting drive.
1st step is to know what the hard disk partitioning is:
Boot the liveDVD to terminal and post back the terminal command outputs:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

``` 
Then we know where to direct the installer to place grub.
Once grub is properly installed, you may boot the operating system, update grub to pick up Windows and from that chainload Windows booting to that of ubuntu grub's boot menu.

Hopefully ->
[INDENT][INDENT]this ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by oldos2er on 2014-04-13
You can restore grub with [boot repair]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by oldfred on 2014-04-13
If partition was fully recovered, you may just need to reinstall grub to MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

You may have to review if UUIDs changed and if so update fstab & totally reinstall grub2.
      
 sudo blkid -c /dev/null -o list

---

### Post by Nabru on 2014-04-13
> **Bashing-om said:**
> Nabru; Hi !  Welcome to the forum.

You are doing good work; to continue, let's see about (re-)installing grub to the MBR of the booting drive.
1st step is to know what the hard disk partitioning is:
Boot the liveDVD to terminal and post back the terminal command outputs:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

``` 
Then we know where to direct the installer to place grub.
Once grub is properly installed, you may boot the operating system,  update grub to pick up Windows and from that chainload Windows booting  to that of ubuntu grub's boot menu.

Hopefully ->[INDENT][INDENT]this ain't nothing but a thing
[/INDENT]
[/INDENT]


Thank you for the answer! Here-s what those commands output.

```
sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d58a3c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   234438655   117115904    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x036cb6d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 8027 MB, 8027897856 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15679488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0acee59c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    15679487     7838720    b  W95 FAT32
```

```
sudo parted -l

Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   120GB  120GB  primary  ntfs


Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End    Size    File system     Name  Flags
 1      134MB  325GB  325GB   ntfs
 2      325GB  437GB  111GB   ext4
 3      437GB  445GB  8525MB  linux-swap(v1)
 4      445GB  500GB  54.8GB  ntfs


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdc: 8028MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8028MB  8027MB  primary  fat32        boot
```

```
sudo parted /dev/sda unit s print

Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End         Size        Type     File system  Flags
 1      2048s    206847s     204800s     primary  ntfs         boot
 2      206848s  234438655s  234231808s  primary  ntfs
```

```
sudo parted /dev/sdb unit s print

Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sdb: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start       End         Size        File system     Name  Flags
 1      262184s     635643016s  635380833s  ntfs
 2      635645952s  853080063s  217434112s  ext4
 3      853080064s  869730303s  16650240s   linux-swap(v1)
 4      869730304s  976773133s  107042830s  ntfs
```


> **oldos2er said:**
> You can restore grub with [boot repair]("https://help.ubuntu.com/community/Boot-Repair").

Hi, I nstalled BootReapir but I-m getting this error.

```
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
```

---

### Post by Bashing-om on 2014-04-13
Nabru; Well.

As you now know, sdb is partitioned under the GPT scheme. That puts things a bit out of my depth of experience.
From what I do understand, GPT partitions require a "small" boot partition, as confirmed by:
> 
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.


Others will have to advise on a best practice to create this required boot partition and preserve the Windows' data on the current 1st partition.

[INDENT][INDENT]when I do not know
[INDENT][INDENT]I'll tell you straight up
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-13
Since you have two drives, you want to keep the Windows boot loader on sda, but install grub just to sdb.
Boot-Repair usually installs grub to the MBR of every drive with its auto repair. Use advanced options and choose Windows and install its boot loader to sda.

Before installing grub to sdb, use gparted from live installer to create a 1 or 2MB unformatted partition and add the bios_grub flag. It can be anywhere on drive so just shink last partition or LInux partition by 1 or 2MB.
Then boot-Repair can correctly install grub2's boot loader to sdb, again with manual options.

       In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02.

If using gpt, often good to also have gdisk which is fdisk for gpt partitioned drive.
       sudo apt-get install gdisk
      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Nabru on 2014-04-13
> **oldfred said:**
> Since you have two drives, you want to keep the Windows boot loader on sda, but install grub just to sdb.
Boot-Repair usually installs grub to the MBR of every drive with its auto repair. Use advanced options and choose Windows and install its boot loader to sda.

Before installing grub to sdb, use gparted from live installer to create a 1 or 2MB unformatted partition and add the bios_grub flag. It can be anywhere on drive so just shink last partition or LInux partition by 1 or 2MB.
Then boot-Repair can correctly install grub2's boot loader to sdb, again with manual options.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02.

If using gpt, often good to also have gdisk which is fdisk for gpt partitioned drive.
sudo apt-get install gdisk

GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I followed your steps and it works. Thank you very much, I thought I lost months of work. Thank you!

> **Bashing-om said:**
> Nabru; Well.

As you now know, sdb is partitioned under the GPT scheme. That puts things a bit out of my depth of experience.
From what I do understand, GPT partitions require a "small" boot partition, as confirmed by:


Others will have to advise on a best practice to create this required boot partition and preserve the Windows' data on the current 1st partition.
[INDENT][INDENT]when I do not know[INDENT][INDENT]I'll tell you straight up
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for the help anyway!

---

### Post by Bashing-om on 2014-04-13
Nabru; Hey.

Great ! Pleased it has all worked out.
All thanks to oldfred, once more he has taught me a thing or three.

Once more
[INDENT][INDENT]it is all in the process of learning
[/INDENT][/INDENT]

---

