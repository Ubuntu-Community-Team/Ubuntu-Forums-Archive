---
title: "Wrong &quot;magic number&quot; + superblock = faulty usb HDD"
date: 2018-02-09
forum: General Help
---

### Post by smithbox on 2018-02-09
Hi all.
I have external HDD - 2TB, with 2 partitions.
```
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1             256 244100351 244100096 931.2G 83 Linux
/dev/sdb2       244100352 488199445 244099094 931.2G  6 FAT16
```
```
lsblkNAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 179.3M  1 loop /snap/brave/15
loop1    7:1    0 184.1M  1 loop /snap/brave/16
loop2    7:2    0  81.3M  1 loop /snap/core/3887
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0  58.7G  0 part 
&#9500;&#9472;sda2   8:2    0  58.6G  0 part 
&#9500;&#9472;sda3   8:3    0  58.6G  0 part /
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   4.9G  0 part [SWAP]
&#9500;&#9472;sda6   8:6    0  29.6G  0 part 
&#9500;&#9472;sda7   8:7    0  58.8G  0 part 
&#9492;&#9472;sda8   8:8    0  25.3G  0 part 
sdb      8:16   0   1.8T  0 disk 
&#9500;&#9472;sdb1   8:17   0 931.2G  0 part 
&#9492;&#9472;sdb2   8:18   0 931.2G  0 part 
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1   700M  0 rom  

```
Filesystem seems to be corrupted.
```
sdb1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-hbFLbkor/sdb1: unknown filesystem type ''.


sdb2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-hbFLbkor/sdb1: unknown filesystem type ''.
mount: /tmp/BootInfo-hbFLbkor/sdb2: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error.
```

[https://pastebin.com/p5phBCmg](https://pastebin.com/p5phBCmg)

```
dmesg | tail [ 6219.978208] sd 7:0:0:0: [sdb] tag#0 Sense Key : Medium Error [current] 
[ 6219.978211] sd 7:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[ 6219.978216] sd 7:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 1d 19 54 b6 00 00 01 00
[ 6219.978219] print_req_error: I/O error, dev sdb, sector 3905594800
[ 6219.978226] Buffer I/O error on dev sdb, logical block 488199350, async page read
[ 6544.569376] sd 7:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6544.569382] sd 7:0:0:0: [sdb] tag#0 Sense Key : Medium Error [current] 
[ 6544.569385] sd 7:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[ 6544.569390] sd 7:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 1d 19 54 a5 00 00 15 00
[ 6544.569393] print_req_error: I/O error, dev sdb, sector 3905594664

```
```
cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=3c9f1768-4adf-43a7-bb82-03b92c3ceb46 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=33704977-6cb2-4b6f-adc7-1271084d24fa none            swap    sw              0       0
/dev/disk/by-id/usb-OEM_Ext_Hard_Disk_0000D310318D-0:0-part1 /mnt/usb-OEM_Ext_Hard_Disk_0000D310318D-0:0-part1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-OEM_Ext_Hard_Disk_0000D310318D-0:0-part2 /mnt/usb-OEM_Ext_Hard_Disk_0000D310318D-0:0-part2 auto nosuid,nodev,nofail,x-gvfs-show 0 0

```
```
e2label /dev/sdbe2label: Bad magic number in super-block while trying to open /dev/sdb
Found a dos partition table in /dev/sdb
```
My question is, how to fix disk/partitions "magic number" to fix superblock to install filesystem on device to mount both partitions ???
Anyone knows ?

---

