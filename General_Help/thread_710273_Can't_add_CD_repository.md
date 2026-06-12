---
title: "Can't add CD repository"
date: 2008-02-28
forum: General Help
---

### Post by maarten12 on 2008-02-28
ello, 
I was trying to add my Ubuntu cd as a repository, but it seemed it didn't work. so, I thougt: "let's do it manual." So, i did sudo apt-cdrom add and it says: E: cannot mount the volume... i tried a lot of options and when i nearly gave up, i did: sudo apt-cdrom -c=/etc/fstab add it says:
E: Syntaxfout /etc/fstab:14: Extra garbage at the end of the file.
now I cant even fully update!
here is my fstab: 

```

maarten@maarten-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=03517179-d067-46ad-9576-e2aca6ad5a13 /               ext3    errors=remount-ro 0       1
# /dev/sda1
UUID=14E48065E4804AC6 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=F484C10484C0C9F6 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=80b2c943-c08c-4c3b-93e6-e20f2ed4cd79 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

and here are my permissions in /media
```

maarten@maarten-desktop:~$ ls -la /media
totaal 40
drwxr-xr-x  5 root root     4096 2008-02-28 15:19 .
drwxr-xr-x 22 root root     4096 2008-02-25 17:45 ..
lrwxrwxrwx  1 root     999     6 2008-02-23 13:59 cdrom -> cdrom0
drwxr-xr-x  2 root     999  4096 2008-02-23 13:59 cdrom0
-rw-r--r--  1 root root        0 2008-02-28 15:19 .hal-mtab
drwxrwx---  1 root plugdev 24576 2008-02-28 13:17 sda1
drwxrwx---  1 root plugdev  4096 2008-02-28 13:17 sda2

```

can anyone please help?:confused:

---

### Post by stooshbunutu on 2008-02-29
isn't the cd on the package source list already by default?

---

### Post by maarten12 on 2008-03-01
Well, not that I know. Anyway, it can't say it can add the repository

---

