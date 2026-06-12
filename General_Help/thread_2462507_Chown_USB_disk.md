---
title: "Chown USB disk?"
date: 2021-05-22
forum: General Help
---

### Post by daanheuvelbeuk on 2021-05-22
A while back I formatted an external Seagate USB disk and now I have a problem with writing to the disk. It is owned by root, and I can not CHOWN it. I tried some permutations.

If I go one directory lower and do a 
```
chown daan '/Seagate USB'
chown: cannot access '/Seagate USB': No such file or directory
```

So I have my commands crossed. What do I need to do to be able to backup to my disk?

---

### Post by &amp;KyT$0P# on 2021-05-22
First make sure the USB disk is mounted.  Then open Terminal **in the directory that's the exact mount point of the USB disk** and run -
```
sudo chown daan: .
```

---

### Post by Holger_Gehrke on 2021-05-22
A hint why your command didn't work: a path beginning with '/' is an absolute path beginning at the root of the file system tree.
```
chown daan '/Seagate USB'
``` would change the ownership of 'Seagate USB' located in the root directory. Either leave off the '/' or give the correct absolute path (probably something like '/media/daan/Seagate USB/').

Holger

---

### Post by Dennis N on 2021-05-22
You probably don't have the right path to the disk's filesystem. In Ubuntu, external USBs mount at /media/<username>/<mountpoint-folder-name>

Find that folder name, then you can formulate your command. You should also use the -R option with chown to make it apply to the folder contents as well as the folder. And, you can change the group owning the filesystem at the same time. The chown command is for ext formatted filesystems (usually ext4).

If daan is your user name:
```
sudo chown -R daan:daan /media/daan/<mountpoint-folder-name>
```

---

### Post by TheFu on 2021-05-22
chown has 3 requirements:
[LIST]
[*]can only be run using sudo/root
[*]the file system must be a native Linux with POSIX permission support. This means it will never work on NTFS nor FAT32 nor exFAT file systems.
[*]the file system must be mounted read-write
[/LIST]

So, the first things to check are those three.

---

### Post by daanheuvelbeuk on 2021-05-23
Thanks for the help. The sudo chown daan: . did work.

---

### Post by TheFu on 2021-05-23
> **daanheuvelbeuk said:**
> Thanks for the help. The sudo chown daan: . did work.

For the future, there are help pages for almost every command on your Linux system. manpages.
$ man chown

```
NAME
       chown - change file owner and group

SYNOPSIS
       chown [OPTION]... [OWNER][:[GROUP]] FILE...
       chown [OPTION]... --reference=RFILE FILE...
```

Optional parameters are are in brackets, [].  An important note in the manpage:
```
       Owner is unchanged if missing.  Group is unchanged if missing, but changed to login  group  if
       implied  by  a ':' following a symbolic OWNER.  OWNER and GROUP may be numeric as well as sym&#8208;
       bolic.
```

So, as long as the FILE is correctly specified, it should work. Adding a colon, like *user1:* isn't necessary. There is an EXAMPLES section for clarity.

It is possible to use **chown** rather than **chgrp** for group stuff, but only root or the file owner can accomplish that.  Directories are considered files, BTW.

---

