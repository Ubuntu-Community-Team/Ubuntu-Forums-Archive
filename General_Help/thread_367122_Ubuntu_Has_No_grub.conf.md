---
title: "Ubuntu Has No grub.conf"
date: 2007-02-21
forum: General Help
---

### Post by CarlosinFL on 2007-02-21
I was looking in /boot/grub and I can't seem to find grub.conf. How can the system boot w/o the grub.conf file?

```
carlos@lptp:/boot/grub$ ls -la
total 196
drwxr-xr-x 2 root root   4096 2007-02-21 19:25 .
drwxr-xr-x 3 root root   4096 2006-12-13 18:54 ..
-rw-r--r-- 1 root root    197 2006-11-29 20:08 default
-rw-r--r-- 1 root root     15 2006-11-29 20:08 device.map
-rw-r--r-- 1 root root   7508 2006-11-29 20:08 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2006-11-29 20:08 fat_stage1_5
-rw-r--r-- 1 root root     16 2006-11-29 20:08 installed-version
-rw-r--r-- 1 root root   8128 2006-11-29 20:08 jfs_stage1_5
-rw-r--r-- 1 root root   3917 2007-02-21 19:25 menu.lst
-rw-r--r-- 1 root root   3910 2006-12-13 18:55 menu.lst~
-rw-r--r-- 1 root root   6804 2006-11-29 20:08 minix_stage1_5
-rw-r--r-- 1 root root   9076 2006-11-29 20:08 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2006-11-29 20:08 stage1
-rw-r--r-- 1 root root 105652 2006-11-29 20:08 stage2
-rw-r--r-- 1 root root   8764 2006-11-29 20:08 xfs_stage1_5

```

I also tried looking around in case it was in an "unusual" spot and I was unable to find it. Anyone care to help me out or explain why I can't find it.

Thanks!

---

### Post by Xzenome on 2007-02-21
Doesn't it just use menu.lst?

---

### Post by JohnPhys on 2007-02-21
I could be wrong, but I think the stuff you are looking for is in menu.lst.

---

### Post by CarlosinFL on 2007-02-21
Menu.lst and Grub.conf are two totally separate files in Debian. I know nothing about Ubuntu but that does not make sense to me...

---

### Post by MetalMusicAddict on 2007-02-21
Carwill. What, besides finding the file, are you trying to accomplish?

---

### Post by Maestro23 on 2007-02-21
Is this what you are looking for: 

/usr/src/linux-headers-2.6.17-11/debian/examples/kpkg_grub.conf

---

