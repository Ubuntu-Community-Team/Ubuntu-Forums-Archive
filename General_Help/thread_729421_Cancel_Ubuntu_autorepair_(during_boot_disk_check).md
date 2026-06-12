---
title: "Cancel Ubuntu autorepair (during boot disk check)"
date: 2008-03-19
forum: General Help
---

### Post by Anas&#1616;&#1616; on 2008-03-19
Hello everybody,

I have a dual boot system, Each time I boot ubuntu it checks the whole hard drive and autorepaire some folders or files, changing their names to numbers like 001 and 000 and makes them unaccessible in windows

(the file system in these partitions is FAT32)

is there a way to configure ubunto not to auto rename files and folders.

---

### Post by Pres-Gas on 2008-03-19
I am going to guess and say that your /etc/fstab file has those FAT32 partitions listed in them.  If you read the man page for fstab, you should see that there is an explanation of each field.  The 6th field deals with the file system checker.  Is your FAT32 partitions 6th field a number greater than 0?  If they are, then they are being fsck-ed.  You will want to edit this file and change the 6th field to 0 for ONLY the FAT32 partitions (shown in the 3rd field).

If this is not the case, post back.

---

