---
title: "Internal IDE Permissions"
date: 2008-01-14
forum: General Help
---

### Post by timboellis on 2008-01-14
I used to have a 500gb external drive, however I decided to put this into my PC as a secondary IDE, however it always asks for admin user name unable to make it like any normal drive like before where anyone can access it , it still has the daa on it so cannot format it, 

If this helps...
[PHP]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00077a74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3   *           1       30401   244196001    5  Extended
/dev/sda5           30119       30401     2273166   82  Linux swap / Solaris
/dev/sda6               1       30118   241922740+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14310072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488391041    c  W95 FAT32 (LBA)
[/PHP]

---

### Post by dgray_from_dc on 2008-01-14
Where is it mounted?  What user owns it?

Go to the mount point, and use the **[COLOR="Blue"]ls -l[/COLOR]** command and post the result.

You should be able to use the chmod command to give other users permission to use it.

```
chmod -R 0777 [COLOR="Blue"]*/directory where drive is mounted*[/COLOR]
```

---

### Post by timboellis on 2008-01-14
drwx------    8 tim root    32768 2007-12-27 19:49 Documents
-rwx------    1 tim root 16289087 2008-01-14 19:24 evolution-backup.tar.gz
-rwx------    1 tim root     2965 2008-01-09 23:22 I1001.pdf
drwx------   10 tim root    32768 2008-01-13 00:52 ID_Pollard
?---------    ? ?   ?           ?                ? kelly
drwx------ 1748 tim root   229376 2008-01-13 00:51 MP3
drwx------   15 tim root    32768 2008-01-13 00:06 Pictures
drwx------    4 tim root    32768 2008-01-01 22:48 Software
-rwx------    1 tim root   229108 2008-01-13 03:57 tux_Apple-Linux.jpg
drwx------    7 tim root    32768 2008-01-06 02:23 Web Site Backups

---

### Post by taurus on 2008-01-14
Try something like

```
sudo umount /dev/sdb1 
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```

---

### Post by timboellis on 2008-01-14
Spot on that should be now I assume


drwxrwxrwx   12 root root    32768 1970-01-01 01:00 .
drwxr-xr-x    5 root root     4096 2008-01-14 23:25 ..
drwxrwxrwx    8 root root    32768 2007-12-27 19:49 Documents
-rwxrwxrwx    1 root root 16289087 2008-01-14 19:24 evolution-backup.tar.gz
-rwxrwxrwx    1 root root     2965 2008-01-09 23:22 i1001.pdf
drwxrwxrwx   10 root root    32768 2008-01-13 00:52 ID_Pollard
?---------    ? ?    ?           ?                ? /media/sdb1/kelly
drwxrwxrwx 1748 root root   229376 2008-01-13 00:51 mp3
drwxrwxrwx   15 root root    32768 2008-01-13 00:06 Pictures
drwxrwxrwx    4 root root    32768 2008-01-01 22:48 Software
drwxrwxrwx    6 root root    32768 2008-01-04 10:09 .Trash-root
drwxrwxrwx    2 root root    32768 2008-01-13 00:57 .Trash-tim
drwxrwxrwx    2 root root    32768 2008-01-08 18:26 .Trash-ubuntu
-rwxrwxrwx    1 root root   229108 2008-01-13 03:57 tux_Apple-Linux.jpg
drwxrwxrwx    7 root root    32768 2008-01-06 02:23 Web Site Backups

---

