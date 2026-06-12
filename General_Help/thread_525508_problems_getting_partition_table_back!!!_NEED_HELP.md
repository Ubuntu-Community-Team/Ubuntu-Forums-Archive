---
title: "problems getting partition table back!!! NEED HELP!!!"
date: 2007-08-14
forum: General Help
---

### Post by elmo541992 on 2007-08-14
i need help...

i know my mbt and partition table is gone, but im having trouble getting it back. i do sudo fdisk -l /dev/sdb, and i get this:
Code:

max@max-desktop:~$ sudo fdisk -l /dev/sdb 

Disk /dev/sdb: 41.1 GB, 41121316864 bytes 
255 heads, 63 sectors/track, 4999 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

Disk /dev/sdb doesn't contain a valid partition table

this info i know is correct. i also know that the layout of my partitions are something like this:

~38gb ext3
~1.5gb swap

but, when i use gpart, it detects the swap drive, but not the ext3 part. i can still use this info it spit out at me to assume the sectors of the ext3 part. so then i continue to parted. heres what i get:
Code:

max@max-desktop:~$ sudo parted /dev/sdb

GNU Parted 1.7.1

Using /dev/sdb

Welcome to GNU Parted! Type 'help' to view a list of commands.

(parted) unit s                                                           

(parted) rescue

Error: Unable to open /dev/sdb - unrecognised disk label.                 

(parted)

i get the same error when i tell it to print, too. how can i get around this??? and so you know, im 64-bit, and i used the feisty install on another hard drive. also, if theres a way to just get files off of it, that would be fine too.
__________________

---

### Post by elmo541992 on 2007-08-14
i also have access to windows on this comp if that helps.

---

### Post by elmo541992 on 2007-08-15
can anyone help???

---

### Post by confused57 on 2007-08-15
Maybe testdisk can help, as described by Herman in this thread:
[http://ubuntuforums.org/showpost.php?p=3111611&postcount=27](http://ubuntuforums.org/showpost.php?p=3111611&postcount=27)

---

### Post by elmo541992 on 2007-08-16
Thanks confused57, Turns out that testdisk worked alot better than fdisk.  Thank you!!

---

