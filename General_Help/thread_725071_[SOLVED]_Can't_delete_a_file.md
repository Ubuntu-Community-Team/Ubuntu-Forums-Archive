---
title: "[SOLVED] Can't delete a file"
date: 2008-03-15
forum: General Help
---

### Post by unutbu on 2008-03-15
I'm trying to delete the folder 1988--1991.
I've search the web and ubuntuforums and was unable to find the answer:

```

farmer:~% cd /media/disk/Documents/
farmer:/media/disk/Documents% /bin/rm -rf 1988--1991/
/bin/rm: cannot remove directory `1988--1991//THINK Pascal Learning Folder/James': Directory not empty
[... more dirs, same error]

farmer:/media/disk/Documents% ls -l
total 3200
drwx------ 4 cyrano root   32768 2008-03-14 21:26 1988--1991
[...]

farmer:/media/disk/Documents% cd 1988--1991/THINK\ Pascal\ Learning\ Folder/James/
farmer:/media/disk/Documents/1988--1991/THINK Pascal Learning Folder/James% ls -la
total 64
drwx------ 2 cyrano root 32768 2008-03-14 20:35 .
drwx------ 4 cyrano root 32768 2008-03-14 20:35 ..
?--------- ? ?      ?        ?                ? James2.
?--------- ? ?      ?        ?                ? LearnP.

farmer:~% mount
[...]
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

farmer:/media/disk/Documents% fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 2048 MB, 2048728064 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992     1999749+   6  FAT16

farmer:~% sudo fsck.vfat -a /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 655 files, 3733/62484 clusters

farmer:~% /bin/rm -rf /media/disk/Documents/1988--1991/
/bin/rm: cannot remove directory `/media/disk/Documents/1988--1991//THINK Pascal Learning Folder/James': Directory not empty



```

---

### Post by banewman on 2008-03-15
Try it with sudo e.g.
sudo rm -rf /path/to/folder
:)

---

### Post by unutbu on 2008-03-15
Thanks, banewman, but no joy:
```

farmer:~% sudo rm -rf /media/disk/Documents/1988--1991/
[sudo] password for cyrano:
[...]
rm: cannot remove directory `/media/disk/Documents/1988--1991//THINK Pascal Learning Folder/James': Directory not empty

```

---

### Post by banewman on 2008-03-15
Tried without the / at the end?
sudo rm -rf /media/disk/Documents/1988--1991
:)

---

### Post by unutbu on 2008-03-15
When I view the offending files in emacs dired mode, I get something a little different:

```

  /media/disk/Documents/1988--1991/THINK Pascal Learning Folder/James:
  total used in directory 64 available 1880032
  drwx------ 2 cyrano root 32768 2008-03-14 20:35 .
  drwx------ 4 cyrano root 32768 2008-03-14 20:35 ..
  ?--------- ? ?      ?        ?                ? /media/disk/Documents/1988--1991/THINK Pascal Learning Folder/James/./James2.
  ?--------- ? ?      ?        ?                ? /media/disk/Documents/1988--1991/THINK Pascal Learning Folder/James/./LearnP.

```

I don't know if this helps...

---

### Post by chrisccoulson on 2008-03-15
I would suggest to run dosfsck on the volume, but it seems like you may have already tried that. However, it isn't clear whether you unmounted the volume before running dosfsck or not? If not, then I would unmount and try again:
```
sudo umount /media/disk
sudo dosfsck -a /dev/sdb1
```

---

### Post by unutbu on 2008-03-15
Thanks chrisccoulson and banewman. Here's the output with both suggestions put together. Unfortunately, still no dice.
```

farmer:~% sudo umount /media/disk/
farmer:~% sudo dosfsck -a /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 655 files, 3733/62484 clusters

farmer:~% sudo mkdir /media/disk
farmer:~% sudo mount -t vfat -o uid=1000 /dev/sdb1 /media/disk
farmer:~% sudo /bin/rm -rf /media/disk/Documents/1988--1991
/bin/rm: cannot remove directory `/media/disk/Documents/1988--1991//THINK Pascal Learning Folder/James': Directory not empty

```

---

### Post by chrisccoulson on 2008-03-15
Hmmmmm, strange. I'm not sure whether to dare to suggest this - but do you have a Windows box you could try it on? Maybe you could run checkdisk or whatever utility is available to do filesystem scans in Windows?

---

### Post by unutbu on 2008-03-16
Using Win XP.
Went to Start->Run->Open->"cmd"
```

chkdsk F:/r
The type of the file system is FAT.
Volume Serial Number is 9143-523E
Windows is verifying files and folders...
File and folder verification is complete.
Windows is verifying free space...
Free space verification is complete.
Windows has checked the file system and found no problems.

```
Delete using Windows file manager GUI... failed.
Also mounted under Gutsy, but rm -rf failed too.

I'm beginning to believe that nothing short of reformatting can remove this file.

---

### Post by unutbu on 2008-03-16
This works:
```
sudo umount /dev/sdb1
sudo mkfs.vfat -F 16 /dev/sdb1
```

Warning: For anyone reading this looking for a solution, be aware that this will erase all files on your stick. If you have U3, you will not lose it (darn :)). It's on a hidden partition(?) and will re-install itself the next time you stick the um... stick in a Windows machine.

---

