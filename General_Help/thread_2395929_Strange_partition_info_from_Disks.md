---
title: "Strange partition info from Disks"
date: 2018-07-08
forum: General Help
---

### Post by ra7411 on 2018-07-08
My current install has worked fine for over a year.
I put Home in a partition separate from the Ub 16.04 o/s.[ATTACH=CONFIG]280321[/ATTACH]

On Disks, it has always shown a large unallocated space, which is actually where I have /Home, and which shows up correctly in Gparted.

The attached pic shows what I'm asking about.
Any ideas ?

---

### Post by leopheard on 2018-07-08
I literally came on here to post the pretty much exact same question.

I remember when I made this setup in 2014 using Lubuntu on a 450GB or so drive, it created 3 partitions. One was the boot section in FAT32, the other the main data under EXT4 and now I also have an unallocated 7.8GB unmounted partition that it's telling me it can't read. I think this was an original swap file space, which would also explain why the laptop is starting to run slower?

Can anyone else clarify this and if I can just wipe the partition and recreate the swap file? Is there anything else I need to do first? I'm going to try a force fsck on it from the command line obviously.

What does Gparted say with yours?

Edit: fschk shows this:

fsck from util-linux 2.27.1
e2fsck 1.43.1 (08-Jun-2016)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda3


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

---

### Post by oldfred on 2018-07-08
I have not been a fan of disks, but it may be showing some issue with partition table.
Post all of these, slight differences with what each reports may tell something:
sudo fdisk -lu
sudo parted -l
sudo gdisk -l /dev/sda

@ leopheard
Better to start your own thread, as different issue.
You cannot run fsck on swap, swap is just unformatted space. And fsck is only for the ext2, ext3 & ext4 family of formats although some add ins for other formats.
If you encrypted /home or system, your swap will show an error in gparted as it cannot (nor should it) see your swap partition.

---

### Post by ra7411 on 2018-07-09
> **oldfred said:**
> I have not been a fan of disks, but it may be showing some issue with partition table.
Post all of these, slight differences with what each reports may tell something:
sudo fdisk -lu
sudo parted -l
sudo gdisk -l /dev/sda



ok:

```
ra@ra-main:~$** sudo fdisk -lu**
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x39beeb72

Device     Boot     Start        End    Sectors  Size Id Type
/dev/sda1  *         2048   97656831   97654784 46.6G 83 Linux
/dev/sda2        97658878 3907028991 3809370114  1.8T  5 Extended
/dev/sda5        97658880  115234815   17575936  8.4G 82 Linux swap / Solaris
/dev/sda6       115236864 3907028991 3791792128  1.8T 83 Linux




Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc7bdc820

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1        2048 3907028991 3907026944  1.8T 83 Linux


Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5e9ccc05

Device     Boot      Start        End    Sectors  Size Id Type
/dev/sdc1             4096 3866068991 3866064896  1.8T 83 Linux
/dev/sdc2       3866068992 3907028991   40960000 19.5G 83 Linux
ra@ra-main:~$ 
```


```
ra@ra-main:~$** sudo parted -l**
[sudo] password for ra: 
Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  50.0GB  50.0GB  primary   ext4            boot
 2      50.0GB  2000GB  1950GB  extended
 5      50.0GB  59.0GB  8999MB  logical   linux-swap(v1)
 6      59.0GB  2000GB  1941GB  logical   ext4


Model: ATA Hitachi HUA72202 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      2097kB  1979GB  1979GB  primary  ext4
 2      1979GB  2000GB  21.0GB  primary  ext4
```


```
ra@ra-main:~$** sudo gdisk -l /dev/sda**
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
[B]Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. [/B]
***************************************************************

Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6E122F73-F47D-4A9B-9E37-3FD920D8A8AF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 6253 sectors (3.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        97656831   46.6 GiB    8300  Linux filesystem
   5        97658880       115234815   8.4 GiB     8200  Linux swap
   6       115236864      3907028991   1.8 TiB     8300  Linux filesystem
ra@ra-main:~$ 
```

I bolded the only odd thing that I could notice.

xxxxx

---

### Post by oldfred on 2018-07-09
Yes the invalid gpt is an issue.
It used to be no partition tools worked at all with that error.

That error is usually caused by using Windows to convert a gpt drive to MBR as Windows always leaves the backup gpt partition table. Once advantage of gpt is that it has a backup, MBR does not.

You can fix it with fixparts. You can use gdisk, but easier with fixparts.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 
    
If only running Ubuntu and not Windows on a drive, I prefer to use gpt. And I converted first drive back in 2010.
Issue is only that if you also have Windows on same drive, then partitioning must match how Windows is installed. Windows only boots from MBR with BIOS and only from gpt with UEFI. 
Ubuntu can boot from gpt with BIOS if you add a tiny 1 or 2MB unformatted partition with bios_grub flag.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
            
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by ra7411 on 2018-07-10
>That error is usually caused by using Windows to convert a gpt drive to  MBR as Windows always leaves the backup gpt partition table. Once  advantage of gpt is that it has a backup, MBR does not.<

There's no Windows install on the HD, or on the other 2 HDs on the machine - I don't know how the problem developed. Maybe from a Grub rescue disk used a long time ago?

My machine uses BIOS.  I do not want to botch my partitions. 

sudo fixparts /dev/sda gave:

ra@ra-main:~$ sudo fixparts /dev/sda
[sudo] password for ra: 
FixParts 1.0.1

Loading MBR data from /dev/sda

MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit


So, what's the best way to get Disks able to "see"  the sda6 partition?

---

### Post by oldfred on 2018-07-10
Did fixparts not give same error message that gdisk gave?
Or did you do a write from gdisk and that fixed it?

Did you do the w write from fixparts. That should update MBR and erase gpt data.
Run the gdisk command again to see if it still shows error.

---

### Post by ra7411 on 2018-07-10
Below is  what gdisk gives. Should I "convert your MBR partitions
to GPT format" ?

I'm reluctant to do anything that might wreck these partitions.

ra@ra-main:~$ sudo gdisk /dev/sda 
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to ra@ra-main:~$ sudo gdisk /dev/sda 
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************

---

### Post by oldfred on 2018-07-10
Do not convert to gpt. Use q to exit.

But did not fixparts see the same invalid gpt?

It may pay to backup current partition table & save to another drive.
       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ sdX.txt
sudo sfdisk -d /dev/sdb > parts_sdb.txt 

Did you read the section on converting from gpt to MBR? I would do that and if partitions look correct then write them, if not exit.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by ra7411 on 2018-07-10
>Did you read the section on converting from gpt to MBR? I would do that and if partitions look correct then write them, if not exit. <

I read through it and it's material that I'm unfamiliar with and reluctant to mess with.

I ran:

ra@ra-main:~$ sudo sfdisk -d /dev/sda6 >parts_ sda6.txt
/dev/sda6: device contains a valid 'ext4' signature; it is strongly recommended to wipe the device with wipefs(8) if this is unexpected, in order to avoid possible collisions
sfdisk: failed to dump partition table: Success

I have no idea how to correct the situation, and since the install runs ok, maybe I should leave well enough alone.

---

### Post by ra7411 on 2018-07-10
Update:
I did a reboot, and just like magic, Disks is now showing all the sda partitions just like it should.
We'll see how long this lasts.

Thanks for the help.

---

### Post by oldfred on 2018-07-10
Not sure what may have fixed it?

But command to backup partition table was for entire drive like sda, not a partition like sda6.

---

