---
title: "Permissions problem in Hardy..."
date: 2008-05-21
forum: General Help
---

### Post by ashwinidhiman on 2008-05-21
I am using Ubuntu Hardy Heron. I have mounted some FAT32 partitions whose owner is root but I can't even change the permissions of the partitions even through the command line as root.
The filesystem table is 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=222f0e0e-874a-4855-860c-14502b2e5845 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1322-BF10  /extra          vfat    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=eaf072ac-3b53-4f98-acbc-8b4924ad84bd /home           ext3    relatime        0       2
# /dev/sda7
UUID=45CF-A040  /myall          vfat    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=76C8EEADC8EE6AB7 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6

The ls -l commmand when run on /myall gives the following output:

drwxrwx--- 18 root plugdev  16384 2008-04-30 19:09 My Documents
drwxrwx---  9 root plugdev  16384 2007-02-16 12:05 Photoshop
-rwxrwx---  1 root plugdev  86016 2007-07-06 14:54 FileSplitter.exe
-rwxrwx---  1 root plugdev    159 2007-12-13 01:15 FileSplitter.ini
drwxrwx---  7 root plugdev  16384 2007-08-17 00:11 java
drwxrwx---  4 root plugdev  16384 2007-02-13 23:12 Linux
-rwxrwx---  1 root plugdev 269085 2007-10-14 03:11 make-sfd.otp


I can't change the owner, neither can I change the permissions of the /myall,/extra and /windows partitions.
I am not able to share anything from any of these folders/partitions.
Please someone help me out.

---

### Post by danwood76 on 2008-05-21
Edit the fstab file and change the vfat line to be:
```

UUID=45CF-A040 /myall vfat defaults 0 0

```
that should open it up with write privelages, the umask and gid set the user and group permissions.

---

### Post by ibuclaw on 2008-05-21
The Permissions are set with the **umask=007** option in the fstab line.

The permissions are reverse proportionate to the chmod numbers.
ie:
0=7
3=4
4=3
7=0

If you are trying to change the permissions of certain folders within the FAT partition, unfortunately this cannot be done with **all** DOS based filesystems.

There is the fstab permission and that is it!

Though, to change the owner of the FAT drive to you, add this to the options of your fstab line.

```
defaults,umask=007,**uid=**gid=46
```

Regards
Iain

---

