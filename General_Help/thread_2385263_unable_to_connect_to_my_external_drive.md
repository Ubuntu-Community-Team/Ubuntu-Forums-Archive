---
title: "unable to connect to my external drive"
date: 2018-02-18
forum: General Help
---

### Post by czgirb on 2018-02-18
I unplugged my external drive on 2/15
but when i re-connect it, it says:
> Error mounting /dev/sdb1 at /media/czgirb/500GB: Command-line `mount -t  "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1"  "/media/czgirb/500GB"' exited with non-zero exit status 32: mount: wrong  fs type, bad option, bad superblock on /dev/sdb1, missing codepage or  helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail  or so
Please help ...

I use Compaq CQ40-328TU and 16.04

---

### Post by czgirb on 2018-02-18
lsusb
> czgirb@ubuntu:~$ lsusb
Bus 002 Device 005: ID 0bc2:2300 Seagate RSS LLC Expansion Portable
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 064e:c108 Suyin Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
czgirb@ubuntu:~$ 


sudo fdisk -l
> czgirb@ubuntu:~$ sudo fdisk -l
[sudo] password for czgirb: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe05e4f1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    58595327    29296640   83  Linux
/dev/sda4        58595328   488396799   214900736   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
1 heads, 63 sectors/track, 15504336 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01bcefcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768127   488384032+  83  Linux
czgirb@ubuntu:~$ 


---

### Post by czgirb on 2018-02-18
dmesg | tail -n 20
> czgirb@ubuntu:~$ dmesg | tail -n 20
[ 2466.943937] sd 8:0:0:0: [sdb] Assuming drive cache: write back
[ 2466.948477] sd 8:0:0:0: [sdb] No Caching mode page found
[ 2466.948483] sd 8:0:0:0: [sdb] Assuming drive cache: write back
[ 2467.011678]  sdb: sdb1
[ 2467.062999] sd 8:0:0:0: [sdb] No Caching mode page found
[ 2467.063008] sd 8:0:0:0: [sdb] Assuming drive cache: write back
[ 2467.063015] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 2470.140738] sd 8:0:0:0: [sdb]  
[ 2470.140744] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2470.140747] sd 8:0:0:0: [sdb]  
[ 2470.140749] Sense Key : Medium Error [current] 
[ 2470.140753] Info fld=0x0
[ 2470.140755] sd 8:0:0:0: [sdb]  
[ 2470.140759] Add. Sense: Unrecovered read error
[ 2470.140761] sd 8:0:0:0: [sdb] CDB: 
[ 2470.140763] Read(10): 28 00 1d 04 00 57 00 00 f0 00
[ 2470.140773] end_request: critical medium error, dev sdb, sector 486801495
[ 2470.140807] JBD2: Failed to read block at offset 19
[ 2470.223880] JBD2: recovery failed
[ 2470.223890] EXT4-fs (sdb1): error loading journal
czgirb@ubuntu:~$ 


---

### Post by ajgreeny on 2018-02-18
I hope you either unmounted the drive or ejected it before you removed it or you may have caused this problem simply by unplugging it, particularly if any data was being written to it.

---

### Post by czgirb on 2018-02-18
> **ajgreeny said:**
> I hope you either unmounted the drive or ejected it before you removed it or you may have caused this problem simply by unplugging it, particularly if any data was being written to it.

I always ...** shutting down my system** => **unplugged the electrical switch** => **unplugged the external drive**

---

### Post by czgirb on 2018-02-19
Somebody ... please help ...

---

### Post by wildmanne39 on 2018-02-19
We are volunteers from all over the world, the person that can help probably is not online right now, please only bump your thread once every twelve hours to keep it in view.

---

### Post by dragonfly41 on 2018-02-19
Referring to your opening post ..

search this forum for "bad superblock" to read guides for recovery.

---

### Post by czgirb on 2018-02-19
> **dragonfly41 said:**
> Referring to your opening post ..

search this forum for "bad superblock" to read guides for recovery.

searched already ... but i do not know which one is (*sorry for my ubuntu knowledge is limited*)
would you mind to guides me by showing which one is ... please ...

---

