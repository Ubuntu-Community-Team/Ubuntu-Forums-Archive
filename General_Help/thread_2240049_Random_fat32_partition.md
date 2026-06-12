---
title: "Random fat32 partition"
date: 2014-08-17
forum: General Help
---

### Post by mateojonsonguynn on 2014-08-17
Hello. I am running a dual-install of windows XP and ubuntu. I did not set the swap space partition and want to do it now. However, I have maxed out my 4 partition space. I have 2 questions: 1, can I make my linux partition extended without losing any data and 2, there is a random 3GB Fat32 partition on my drive. I could use this instead of extending linux, but I don't know what it is... Some space is used. Does anyone know what it is?

---

### Post by Mark Phelps on 2014-08-17
An Extended partition is simply a container that holds other partitions and no, you can't convert an existing Logical or Primary partition to Extended.

Don't know what the Fat32 partition is, so why don't you do "sudo fdisk -lu" (Lowercase L, not a one) and post the output.  You can't use it for Swap anyway, as it would have to be reformatted.

---

### Post by mateojonsonguynn on 2014-08-17
I know. I was going to reformat it to swap. I wanted to know what it was so I can know if important data will be lost in reformatting.

The partition is dev/sda3. It is not boot, the Id is "db", and the system is "CP/M / CTOS / ..."

---

### Post by ajgreeny on 2014-08-17
Is there anything in that fat32 partition?  Have a look in nautilus; that fat32 partition should show in the left hand pane and be readable by you.

---

### Post by mateojonsonguynn on 2014-08-17
The partition has data in it (I know that from GParted), but wont show up in Nautilius. I have a Dell Inspiron 6000. I've read about Dell putting a "hidden" partition on some of their laptops, do you think this might be it?

---

### Post by mateojonsonguynn on 2014-08-17
bump!

---

### Post by oldfred on 2014-08-17
Some systems originally just had an old DOS FAT based partition.

You can convert partitions from primary to logical if you follow all the partition rules. And fixparts lets you within those rules change a partition.
Windows has to boot from primary, and all logical have to be within one extended. There may be some more rules but not sure of all of them.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Be sure to have a working live installer as you may have to reinstall grub and/or edit fstab. UUIDs may change, requiring edits to update those.

Good backups with any system change are always required.

---

