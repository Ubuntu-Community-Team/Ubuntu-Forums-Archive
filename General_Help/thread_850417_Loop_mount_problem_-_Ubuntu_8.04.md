---
title: "Loop mount problem - Ubuntu 8.04"
date: 2008-07-05
forum: General Help
---

### Post by persistentstubborn on 2008-07-05
I'm trying to insert a DOS utility program into freedos image, according to these instructions:

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

I also tried it with a bootable iso image prepared instead of floppy, if that matters, with the same error result.

There is loop listed in modules
```

persistentstubborn@persistentstubborn-desktop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

**loop**
fuse
lp
```

But cat /proc/filesystems shows there is no loop filesystem supported after boot.

I did try modprobe, too, and it appears in /proc/filesystems after it.

```
persistentstubborn@persistentstubborn-desktop:~$ sudo modprobe loop
[sudo] password for persistentstubborn: 

```

```
persistentstubborn@persistentstubborn-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
vfat                   14464  1 
...
loop                   18948  0 
...
fuse                   50580  1 

```

There is enough space where I mount it (it's either a separate ext3 /tmp partition of 120 MB, or completely empty ext3 partition of 12GB):

```
persistentstubborn@persistentstubborn-desktop:~/Public/ftp$ df /tmp
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7                85528      5790     75322   8% /tmp
```

Every time i do, I got the answer [color=red]No space left on device[/color]

```
persistentstubborn@persistentstubborn-desktop:~/Public/ftp$ sudo cp sp8126.exe /tmp/bootiso/
cp: writing `/tmp/bootiso/sp8126.exe': [color=red]No space left on device[/color]
persistentstubborn@persistentstubborn-desktop:~/Public/ftp$ df /tmp
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7                85528      5790     75322   8% /tmp
persistentstubborn@persistentstubborn-desktop:~/Public/ftp$ df /tmp/bootiso/
Filesystem           1K-blocks      Used Available Use% Mounted on
/home/persistentstubborn/Public/ftp/FDSTD.288
                          2863      2860         3 100% /tmp/bootiso
persistentstubborn@persistentstubborn-desktop:~/Public/ftp$ 

```

I change the partitions, but even 12 GB separate free partition isn't large enough.

What am I doing wrong?

---

### Post by mempman on 2008-07-05
```

persistentstubborn@persistentstubborn-desktop:~/Public/ftp$ sudo cp sp8126.exe /tmp/bootiso/
cp: writing `/tmp/bootiso/sp8126.exe': No space left on device

```

Whenever I mount an *iso or any image via loop device, the mounted file is like a virtual cd drive.  What I get from what you are doing is that you are trying to write onto your virtual iso(virtual cdrom).

---

### Post by persistentstubborn on 2008-07-05
> **mempman said:**
> ```

persistentstubborn@persistentstubborn-desktop:~/Public/ftp$ sudo cp sp8126.exe /tmp/bootiso/
cp: writing `/tmp/bootiso/sp8126.exe': No space left on device

```

Whenever I mount an *iso or any image via loop device, the mounted file is like a virtual cd drive.  What I get from what you are doing is that you are trying to write onto your virtual iso(virtual cdrom).

You are probably right, but I'm just following the instructions from the a.m. link. Besides, what is the way I can add required exe file (DOS utility for COMPAQ PC) to freedos image/file/diskette and burn it into CD?

---

### Post by wangjiaji on 2008-09-07
I'm having the same problem, anybody could help?

---

