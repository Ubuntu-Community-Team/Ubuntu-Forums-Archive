---
title: "can't copy files from Ubuntu to windows"
date: 2007-03-30
forum: General Help
---

### Post by jaind on 2007-03-30
hello,

I have a dual booting laptop with a 3 windows and 1 ubuntu partition.
i want to copy some files(for backup purposes) from ubuntu to windows. the windows partition is FAT32 and i have read and write permissions in ubutu. 

The data i want to copy is about 6 GB. However, nautilus gives errors in some files, so i skip those and its all going fine. but the file copying operation stops after copying only some of the files(~400MB)...

Any ideas??

~~

---

### Post by Maestro23 on 2007-03-30
> **jaind said:**
> hello,

I have a dual booting laptop with a 3 windows and 1 ubuntu partition.
i want to copy some files(for backup purposes) from ubuntu to windows. the windows partition is FAT32 and i have read and write permissions in ubutu. 

The data i want to copy is about 6 GB. However, nautilus gives errors in some files, so i skip those and its all going fine. but the file copying operation stops after copying only some of the files(~400MB)...

Any ideas??

~~

Try copying a little at a time.  Also remember that max file size(one file) on a FAT32 partition is 4GB.

---

### Post by acormack on 2007-03-30
The problem could be a bug in Nautilus.  Have you copying from the command line using something like:

cp -r /home/mydata /mnt/cdrive/

to copy all files under /home/mydata to the mount of your windows directory?

Does it get any errors?


Alec

---

