---
title: "Strange huge file on Desktop"
date: 2008-02-25
forum: General Help
---

### Post by Fixman on 2008-02-25
Wether I run ```
ls -lha ~/Desktop
```The following appears:
```

drwxr-xr-x  3 martin martin 4.0K 2008-02-26 01:13 .
drwxr-xr-x 85 martin martin 4.0K 2008-02-26 02:02 ..
-rw-r--r--  1 martin martin  352 2007-12-13 19:21 asd.htm~
-rw-r--r--  1 martin martin 4.6K 2007-12-29 22:36 Camino a El Cairo
-rw-r--r--  1 martin martin 1.9K 2007-12-20 14:30 .directory
lrwxrwxrwx  1 martin martin   20 2007-12-20 15:40 GLP -> /home/martin/prg/GLP
[COLOR="SeaGreen"]-rw-------  1 martin martin 5.8G 2008-02-08 14:33 .hola.t.swp[/COLOR]
drwx------  5 martin martin 4.0K 2007-12-20 14:30 .kde
-rw-r--r--  1 martin martin 1.7K 2007-12-13 18:42 kdevelop_c_cpp.desktop
-rw-r--r--  1 martin martin   34 2008-01-26 21:57 .~output
-rw-r--r--  1 martin martin    0 2007-12-12 16:51 problema~
-rw-r--r--  1 martin martin    0 2007-12-18 16:23 sdf.htm~
-rw-r--r--  1 martin martin  360 2008-01-28 11:29 StarCraft.desktop
-rw-r--r--  1 martin martin  261 2007-11-19 20:01 TopCoder.desktop
-rw-r--r--  1 martin martin  273 2007-12-14 15:19 WoW~

```

What is this file hola.t.swp?

---

### Post by pointone on 2008-02-26
*.swp usually indicates a swap file.

Post the output of "cat /proc/swaps"; it may be a Linux swap file.

It could also be a swap file for Photoshop / GIMP or some other image manipulating software. Have you been editing any large images lately?

---

### Post by Fixman on 2008-02-26
```

martin@Ubuntu:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       2883656 0       -1

```

I have been editing large files, but not that large. Its safe if I delete that file?

---

### Post by Fixman on 2008-02-26
Is it safe to delete?

---

### Post by Fixman on 2008-02-28
Is anybody there?

---

### Post by hyper_ch on 2008-02-28
post

```

cat /etc/fstab

```

---

### Post by Fixman on 2008-02-28
> **hyper_ch said:**
> post

```

cat /etc/fstab

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=faaed0b8-37e3-4b4a-b86e-d38b3eb64c61 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=11f622da-749f-4596-9e43-8f9216d7a0cc /media/Ubuntu64     ext3    defaults,noauto        0       2
# /dev/sdb1
UUID=BAFC9A5CFC9A12AD /media/WinVista     ntfs    defaults,noauto,umask=007,gid=46 0       1
# /dev/sda5
UUID=1d8ecd20-1878-4a5b-9fc8-092ab3c7dc52 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by Fixman on 2008-02-29
Help please! That file is eating my disk!

---

### Post by TheExplorer on 2008-02-29
Could be kinda Vista swap file or whatever. Not sure though.
You can:
1) Move it to another location (better to another partition)
2) Try booting both into linux and vista
3) If everything's ok then just delete this file

---

### Post by chewearn on 2008-02-29
The file doesn't seemed to be linux swap.  Just rename it to something else; see if anything is wrong.  Run some of your usual apps.  Once you have convinced yourself it  is save, just delete.

---

