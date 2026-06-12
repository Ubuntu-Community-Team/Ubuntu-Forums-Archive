---
title: "snap servise"
date: 2022-12-28
forum: General Help
---

### Post by 842qxgs2 on 2022-12-28
Hi all.
[FONT=inherit][FONT=inherit][FONT=inherit]
[COLOR=#232629][FONT=inherit]I'm interested in how the snap service works in my particular case. We have on the computer all the files from the 
packages.debian.org/sid/amd64/snapd/filelist list with saving paths,plus snapd package manager to /var/lib/dpkg/info as an example one string: 
2022-02-23 15:48:54.0000000000 /usr/lib/udev/snappy-app-dev 
All files are modified, with the same date, with zeros at the end. What does this mean? Did the user change the modification date?[/FONT][/COLOR][/FONT][/FONT]
[/FONT]
[FONT=inherit][COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][FONT=inherit]
[/FONT]
[/FONT][/COLOR]
[/FONT]

---

### Post by #&amp;thj^% on 2022-12-28
It's kind of a double edged sword, IE: There are 3 kind of "timestamps":
[list]
    [*]Access - the last time the file was read
    [*]Modify - the last time the file was modified (content has been modified)
    [*]Change - the last time meta data of the file was changed (e.g. permissions)[/list]

To display this information, you can use *stat* which is part of the coreutils.

stat will show you also some more information like the device, inodes, links, etc.

Remember that this sort of information depends highly on the filesystem and mount options.
Now an Example using stat:
```
stat /etc/default/grub
  File: /etc/default/grub
  Size: 1323      	Blocks: 8          IO Block: 4096   regular file
Device: 0,26	Inode: 562717      Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-12-27 14:51:47.778026957 -0700
Modify: 2022-12-27 09:31:05.865391179 -0700
Change: 2022-12-27 09:31:05.865391179 -0700
 Birth: 2022-12-27 07:14:24.858034120 -0700

```
Or with a slight change:
```
stat /home/me
  File: /home/me
  Size: 998       	Blocks: 0          IO Block: 4096   directory
Device: 0,26	Inode: 562981      Links: 1
Access: (0700/drwx------)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2022-12-28 07:20:09.020335340 -0700
Modify: 2022-12-28 07:18:20.150421127 -0700
Change: 2022-12-28 07:18:20.150421127 -0700
 Birth: 2022-12-27 07:17:26.594922586 -0700


```
I have no Snaps to show you you'll have to play around with yours.

---

