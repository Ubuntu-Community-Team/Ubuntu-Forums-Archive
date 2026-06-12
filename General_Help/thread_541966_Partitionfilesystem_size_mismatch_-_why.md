---
title: "Partition/filesystem size mismatch - why?"
date: 2007-09-03
forum: General Help
---

### Post by geekphreak on 2007-09-03
I am trying to figure out how much space I really have, as parted, cfdisk, nautilus and system monitor are showing different values.

Disk /dev/hda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  3002MB  3002MB  primary  linux-swap        
 3      3002MB  16.3GB  13.3GB  primary  reiserfs          
 2      16.3GB  80.0GB  63.8GB  primary  reiserfs          

Partition 3 is my /, and partition is my VirtualBox partition, with virtual disks and all data that is shared between Ubuntu and VirtualBox virtual machine.
Nautilus and system monitor are showing VirtualBox partition as 42GB total, and not 
63.8GB.

Why did this mismatch occur and is there a way to fix the situation? 
Thanks!

---

