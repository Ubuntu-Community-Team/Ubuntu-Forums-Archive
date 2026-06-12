---
title: "Problems with mounting hard drive"
date: 2017-10-12
forum: General Help
---

### Post by redefine+40 on 2017-10-12
Hi,

I have inherited a WD Red (NAS) drive , 4 TB, from a computer that was running Ubuntu. The old computer had to shut down instantaneously without any chance to back up data. 
I have installed Ubuntu on a new computer. Now, I want  to retrieve data from the 4 TB drive. 
When I connect it, the system doesn't know what to do with it. 
I know that this probably was in use as a boot drive for Ubuntu, but now  I have set up Ubuntu to boot from another drive when I configured my new system. However, if I have this drive hooked  up, Ubuntu doesn't boot at all. It then stays on the "booting from hard  drive" screen forever. 

I list the outputs of some commands that I used to investigate the drive status. 

**df -h**    (doesn't list the drive)
**lsblk** lists the drive as /dev/sdc and shows that it has partitions (sdc2 and sdc3). Doesn't show a mount point.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

   **sudo parted /dev/sdc unit s print**
 Model: ATA WDC WD40EFRX-68W (scsi)
 Disk /dev/sdc: 7814037168s
 Sector size (logical/physical): 512B/4096B
 Partition Table: gpt
 Disk Flags:  
 
 
 Number  Start     End          Size         File system  Name  Flags
  2      1050624s  1550335s     499712s
  3      1550336s  7814037133s  7812486798s                     lvm
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

   

**dmesg | tail**
 [  190.857967] scsi 0:0:1:0: SATA: enclosure_logical_id(0x500605b00652f970), slot(0)
 [  190.858160] scsi 0:0:1:0: atapi(n), ncq(y), asyn_notify(n), smart(y), fua(y), sw_preserve(y)
 [  190.893931] sd 0:0:1:0: Attached scsi generic sg4 type 0
 [  190.898593] sd 0:0:1:0: [sdc] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
 [  190.898596] sd 0:0:1:0: [sdc] 4096-byte physical blocks
 [  190.902436] sd 0:0:1:0: [sdc] Write Protect is off
 [  190.902439] sd 0:0:1:0: [sdc] Mode Sense: 7f 00 10 08
 [  190.903383] sd 0:0:1:0: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA
 [  190.953075]  sdc: sdc2 sdc3
 [  190.963859] sd 0:0:1:0: [sdc] Attached SCSI disk
 -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 
 **sudo fdisk /dev/sdc**
 **p**
 disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: gpt
 Disk identifier: B9EE12BE-3831-438D-B4D4-B9C4A8FFCCB6
 
 
 Device       Start        End    Sectors  Size Type
 /dev/sdc2  1050624    1550335     499712  244M Linux filesystem
 /dev/sdc3  1550336 7814037133 7812486798  3.7T Linux LVM

  **i 2**
 Device: /dev/sdc2
           Start: 1050624
             End: 1550335
         Sectors: 499712
            Size: 244M
            Type: Linux filesystem
       Type-UUID: 0FC63DAF-8483-4772-8E79-3D69D8477DE4
            UUID: 9CCE7339-B3DB-4AB0-9B4B-690D6189600F
 
 
 **i 3**
 Device: /dev/sdc3
           Start: 1550336
             End: 7814037133
         Sectors: 7812486798
            Size: 3.7T
            Type: Linux LVM
       Type-UUID: E6D6D379-F507-44C2-A23C-238F2A3DF928
            UUID: 9FF32069-D751-4144-96D7-D135DA55E846
 
 
 
 
 -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
 
 
 **sudo mke2fs -n /dev/sdc**
  mke2fs 1.42.13 (17-May-2015)
  Found a gpt partition table in /dev/sdc
  Proceed anyway? (y,n) y
  Creating filesystem with 976754646 4k blocks and 244195328 inodes
  Filesystem UUID: 43624be8-77e3-430a-8e0b-5e76869d5caa
  Superblock backups stored on blocks:  
      32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,  
      4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,  
      102400000, 214990848, 512000000, 550731776, 644972544
  
 
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**sudo e2fsck -f /dev/sdc**
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

same output when i use sdc2 or sdc3 instead of sdc.

I tried using 8193 and 32768 as superblocks and get the same out put as above. The only exception is with sdc2 where I get an extra message about invalid argument. see below. 

**sudo e2fsck -f -b 32768 -y /dev/sdc2**
e2fsck 1.42.13 (17-May-2015)
e2fsck: Invalid argument while trying to open /dev/sdc2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**sudo gdisk -l /dev/sdc**

GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 7814037168 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): B9EE12BE-3831-438D-B4D4-B9C4A8FFCCB6
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1050591 sectors (513.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         1050624         1550335   244.0 MiB   8300  
   3         1550336      7814037133   3.6 TiB     8E00  

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I  have absolutely no idea what to do to mount it to retrieve the data. 

Please help.

Thanks.

---

### Post by redefine+40 on 2017-10-17
I am wondering if someone around be generous and help me out here!
Thanks.

---

