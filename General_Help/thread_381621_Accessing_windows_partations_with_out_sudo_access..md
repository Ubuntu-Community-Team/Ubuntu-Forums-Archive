---
title: "Accessing windows partations with out sudo access."
date: 2007-03-11
forum: General Help
---

### Post by cooldudevamsee on 2007-03-11
Hi,

I am using edgy release, my ubuntu is automounting windows partaions at boot time under root.  I want to give other users who don't have sudo access to these windows partations. I have edited fstab file options column to  "auto,user"  but still its asking root auth even to create or modify a file. Please help me out from this situation. thanks.

---

### Post by bonzodog on 2007-03-11
The situation is that without sudo access, they will not be able to write to the drive. They can read from it though.

---

### Post by ciscosurfer on 2007-03-11
> **cooldudevamsee said:**
> Hi,

I am using edgy release, my ubuntu is automounting windows partaions at boot time under root.  I want to give other users who don't have sudo access to these windows partations. I have edited fstab file options column to  "auto,user"  but still its asking root auth even to create or modify a file. Please help me out from this situation. thanks.

> **bonzodog said:**
> The situation is that without sudo access, they will not be able to write to the drive. They can read from it though.Is the Windows drive or partition NTFS or FAT.  FAT is read/write capable by default.  NTFS requires special drivers (like NTFS-3G) to be read/write capable.  Otherwise, by default FAT can read and write, and NTFS can only be read from (sorry for the dangling preposition :-)).

---

### Post by bapoumba on 2007-03-11
Thread moved to "General Help".

---

### Post by cooldudevamsee on 2007-03-11
All of them are FAT32 Partations. But the problem is they are automounted at the boottime as root user. Other users have read access to these partations but they can't create or modify or delete files on windows partations.

I want others users be able to manipulate files on windows partations without requiring sudo access.

vamsee@vamsee-desktop:/media$ ls -la
total 66
drwxr-xr-x 10 root root  4096 2007-03-11 23:08 .
drwxr-xr-x 21 root root  4096 2007-02-24 19:10 ..
lrwxrwxrwx  1 root root     6 2007-01-07 14:45 cdrom -> cdrom0
dr-xr-xr-x  1 root root  2048 2006-02-18 17:34 cdrom0
lrwxrwxrwx  1 root root     7 2007-01-07 14:45 floppy -> floppy0
drwxrwxrwx  2 root root  4096 2007-01-07 14:45 floppy0
drwxr-xr-x 31 root root  8192 1970-01-01 05:30 sda1
drwxr-xr-x 18 root root  8192 1970-01-01 05:30 sda5
drwxr-xr-x 19 root root  8192 1970-01-01 05:30 sda6
drwxr-xr-x 15 root root 16384 1970-01-01 05:30 sda7
drwxr-xr-x 25 root root  8192 1970-01-01 05:30 sda8
drwxr-xr-x  2 root root  4096 2007-03-07 05:28 ud


This is how /media folder looks like.

---

