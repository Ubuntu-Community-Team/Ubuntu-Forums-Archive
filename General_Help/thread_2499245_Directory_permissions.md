---
title: "Directory permissions"
date: 2024-07-20
forum: General Help
---

### Post by forceofgravity on 2024-07-20
This is a bit  off topic, but I will continue in the same thread. Partition /dev/sda9 (ntfs) is mounted to location /media/myusername/DataVolume. I've problems to access there for example with gThumb.
Permissions are:
drwxr-xr-x   3 root root  4096 Jul 19 20:54 media
drwxr-x---+  3 root root 4096 Jul 20 09:07 myusername
drwxrwxrwx  1 myusername myusername 4096 Jul 15 15:57 DataVolume

Files and subfolders in the volume: drwxr-xr-x  1 myusername myusername

The folder /media/myusername is ACL, which is new to me.

Apparently the problem is related to permissions of folders /media or /media/myusername. What is official way to fix this?

---

### Post by QIII on 2024-07-20
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2499221](https://ubuntuforums.org/showthread.php?t=2499221)

It is best to deal with only one issue in any thread.  Multi-topic threads get muddled and confusing when people start to address more than one issue per thread.

---

### Post by yancek on 2024-07-20
Those permissions are Linux filesystem permissions and don't mean much for a windows (ntfs) filesystem.  You need to put your setting in the /etc/fstab file of Ubuntu if you want the windows partition available always.  You don't use standard rwx type permissions but rather umask, fmask and dmask.  The link below has a basic explanation but you may want to investigate and find more detailed information.  You might first check as you probably have ntfs-3g and/or fuse already installed.  If you edit the /etc/fstab file as explained, you need the partition number not the drive as shown on the page.  In that example, it should be sdb1 not sdb.

[https://linuxconfig.org/changing-file-permissions-on-ntfs-partitions-in-linux](https://linuxconfig.org/changing-file-permissions-on-ntfs-partitions-in-linux)

This may not actually be the problem as you have neglected to indicate which version of windows you are using or whether it is hibernated nor have you indicated what 'problems' specifically you are having??

---

### Post by forceofgravity on 2024-07-20
I don't know is this problem related to file permissions or how the partition is mounted, but

[LIST]
[*]By using gnome files (nautilus) the /dev/sda9 is shown in the Other Locations with name 'Data volume' and I can access to there. This is just like it should be. 
[*]With LibreOffice File->Open->Other Locations the 'Data volume' is not available/visible. 
[*]With LibreOffice File->Open and navigating /media -> /media/myusername/ -> /media/myusername/Data volume I can access to the partition and open/modify files. 
[*]With gThumb I can't access to the partition. By choosing /media it gives error "Error opening directory '/media': Permission denied". 
[/LIST]

I would like see the 'Data volume' in Other Locations also by using software like LibreOffice and have access there with gThumb and other similar software.

The volume is mounted in /etc/fstab with parameters:
/dev/disk/by-uuid/4E62065962064665 /media/myusername/Data\040volume auto nosuid,nodev,nofail,x-gvfs-show 0 0

The permissions are:
drwxr-xr-x   3 root root  4096 Jul 19 20:54 media
drwxr-xr-x+  3 root root 4096 Jul 20 16:56 myusername
drwxrwxrwx  1 root root 4096 Jul 15 15:57 'Data volume'

This is new installation of 24.04 so some packages might be missing. I didn't have the problem with 20.04.


```
$apt list --installed | grep ntfs*

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libntfs-3g89t64/noble,now 1:2022.10.3-1.2ubuntu3 amd64 [installed,automatic]
ntfs-3g/noble,now 1:2022.10.3-1.2ubuntu3 amd64 [installed,automatic]

$apt list --installed | grep fuse

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fuse3/noble,now 3.14.0-5build1 amd64 [installed,automatic]
gvfs-fuse/noble,now 1.54.0-1ubuntu2 amd64 [installed,automatic]
libfuse3-3/noble,now 3.14.0-5build1 amd64 [installed,automatic]

```

---

### Post by Morbius1 on 2024-07-20
You are using the wrong "list" command.

Run:
```
snap list
```

gThumb is a snap.

You can't use a snap anywhere you please. That would be Chaos with a capital C.

Open the App Center and search for gThumb. At the bottom of the description it tells you how to use the "sudo snap connect ... " command/

---

### Post by forceofgravity on 2024-07-20
> **Morbius1 said:**
> 
Open the App Center and search for gThumb. At the bottom of the description it tells you how to use the "sudo snap connect ... " command/

Things are settling down. I ended up to gThumb page in App Center and found that instruction. Before using snap I decided to uninstall gThumb with App Center and reinstall it with command line.
```
sudo apt install gthumb
```
It solves the access problem and gThumb found also my old image catalogs which have been missing since App Center installation. There is some package differences whether gThumb is installed with App Center or by using apt.

The 'Data volume' is still missing from LibreOffice File->Open->Other Locations, but it is available for example in Document Viewer and Image Viewer. Strange...

Thanks for your advice!

---

