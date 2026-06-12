---
title: "the only think i dislike about ubuntu"
date: 2005-09-16
forum: General Help
---

### Post by dunja on 2005-09-16
the root directory is cluttered up with symlinks and nonstandard linux/unix directories.  what can safely be removed?

```
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
```

---

### Post by PaganHippie on 2005-09-16
Granted, I'm no guru, but I don't see anything non-standard there.

---

### Post by dunja on 2005-09-17
from the linux filesystem structure standard:

```
/ -- the root directory
|
+-bin       Essential command binaries
+-boot      Static files of the boot loader
+-dev       Device files
+-etc       Machine-local system configuration
+-home      User home directories
+-lib       Shared libraries
+-mnt       Mount point of temporary partitions
+-proc      Process information pseudo-filesystem
+-root      Home directory for root
+-sbin      Essential system binaries
+-tmp       Temporary files
+-usr       Second major hierarchy
+-var       Variable data
``` 

the full document is here: [http://vinelinux.org/fsstnd-1.2.txt](http://vinelinux.org/fsstnd-1.2.txt)

---

### Post by dunja on 2005-09-17
i deleted all the symlinks and the initrd and srv directories.  waiting to see if it will cause any problems...

---

### Post by bsussman on 2005-09-17
the symlinks and non-conforming directories mostly have to do with items that belong in the boot directory. And grub's config is set up to find them in /boot!

Doesn't make a lot of sense to me - I wonder why the ubuntu configurers did that.

I bet if you boot all will go fine.

---

### Post by Xian on 2005-09-17
[QUOTE=dunja]i deleted all the symlinks and the initrd and srv directories.  waiting to see if it will cause any problems...[/QUOTE]
Removing those symlinks to /boot was not a good idea if they are used in your menu.lst. They are there as a convenience so that they always link to the latest kernel and initrd image. That way when you upgrade your kernel you can always be assured which version will be booted after the next shutdown.

Other than those files I don't see anything in your list that looks peculiar. Here are the contents of my root directory in Gentoo:

```
# ls /
bin   dev    lib         mnt   opt   root  suse  tmp  var
boot  etc  home        lost+found  ntfs  proc  sbin  sys   usr
```

---

### Post by dunja on 2005-09-17
[QUOTE=Xian]Removing those symlinks to /boot was not a good idea if they are used in your menu.lst. They are there as a convenience so that they always link to the latest kernel and initrd image. That way when you upgrade your kernel you can always be assured which version will be booted after the next shutdown.[/QUOTE]

nope, none of those are used in menu.lst with the default Hoary config.

---

### Post by Xian on 2005-09-18
Good, I'm glad you checked. The statement, "cluttered up with symlinks and nonstandard linux/unix directories" is not accurate as the two symlinks refer directly to the most recent kernel and initrd file, and the linux directories which are present are perfectly appropriate.

---

### Post by PaganHippie on 2005-09-18
So, as I understand it, you object to the fact that the Ubuntu developers have worked *very hard* to make things easier for users, especially newbs?

Geez, some people....  If I may make a suggestion?  Get over it.  And, modify the file system at your own risk.  If you're really that offended by the changes, try Slackware (which I also like *very much*, btw [for the control it allows over the install & config]).

---

### Post by TravisNewman on 2005-09-18
I don't think that was ever stated. The OP just wants a streamlined root directory, and doesn't like that Ubuntu doesn't have one. There are all kinds of things I dislike about Ubuntu, and there will always be. NO OS is for everyone.

Lets try to cool down here. The OP was asking a question, not bashing anything.

---

### Post by dunja on 2005-09-18
i deleted the symlinks with no ill-effects.  i originally deleted /initrd/, but got an error during boot, so i put it back.  /mnt/ and /opt/ are also empty, but i'll leave them just in case.  

here's what i have now:

```
 $ ls -al /
total 136
drwxr-xr-x   21 root root  4096 2005-09-18 13:07 .
drwxr-xr-x   21 root root  4096 2005-09-18 13:07 ..
drwxr-xr-x    2 root root  4096 2005-09-16 12:57 bin
drwxr-xr-x    3 root root  4096 2005-09-18 13:20 boot
drwxr-xr-x   11 root root 14960 2005-09-18 14:21 dev
drwxr-xr-x   11 root root 24576 2005-09-17 20:02 .dev
drwxr-xr-x  109 root root  4096 2005-09-18 14:22 etc
drwxr-xr-x    5 root root   128 2005-09-16 12:23 home
drwxr-xr-x    2 root root  4096 2005-09-18 13:07 initrd
drwxr-xr-x   16 root root  8192 2005-09-16 19:37 lib
drwxr-xr-x    2 root root 49152 2005-09-16 11:54 lost+found
drwxr-xr-x    7 root root  4096 2005-09-18 14:22 media
drwxr-xr-x    2 root root  4096 2005-09-18 12:27 mnt
drwxr-xr-x    2 root root  4096 2005-09-16 11:55 opt
dr-xr-xr-x   99 root root     0 2005-09-18 14:20 proc
drwxr-xr-x   14 root root  4096 2005-09-17 20:01 root
drwxr-xr-x    2 root root  4096 2005-09-16 12:57 sbin
drwxr-xr-x   10 root root     0 2005-09-18 14:20 sys
drwxrwxrwt    8 root root  4096 2005-09-18 14:22 tmp
drwxr-xr-x   13 root root  4096 2005-09-16 19:35 usr
drwxr-xr-x   14 root root  4096 2005-09-16 12:18 var
```

---

### Post by aysiu on 2005-09-18
Have you ever tried [GoboLinux](http://www.gobolinux.org/)? It has a really interesting file structure.

---

### Post by dunja on 2005-09-18
[QUOTE=aysiu]Have you ever tried [GoboLinux](http://www.gobolinux.org/)? It has a really interesting file structure.[/QUOTE]

no, i like linux's file structure.

---

