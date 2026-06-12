---
title: "[SOLVED] Help: Can't mount my WinXP-ntfs drive"
date: 2006-11-09
forum: General Help
---

### Post by CowzRule on 2006-11-09
I can't get my ntfs-winxp drive mounted.
First here is the output of:
> sudo fdisk -l
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    c  W95 FAT32 (LBA)

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS
/dev/hda2            4866        7200    18755887+  83  Linux
/dev/hda3            7201        7396     1574370    f  W95 Ext'd (LBA)
/dev/hda4            7397        9729    18739822+  83  Linux
/dev/hda5            7201        7396     1574338+  82  Linux swap / Solaris

So, to mount my ntfs drive I did:
> sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o ls=utf8,umask=0222
And here's what I get:
> mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Can anyone help me get this fixed?

---

### Post by yabbadabbadont on 2006-11-09
Make sure that you have the ntfs related kernel modules loaded or you won't have support for ntfs.

---

### Post by aysiu on 2006-11-09
> **CowzRule said:**
> 
And here's what I get: ```
sudo mkdir /media/windows
**sudo mount /dev/hda1 /media/windows/ -t ntfs -o ls=utf8,umask=0222**
```

Can anyone help me get this fixed? You're missing a character in your options there. It should read: ```
sudo mount /dev/hda1 /media/windows -t ntfs -o **n**ls=utf8,umask=0222
```

> **yabbadabbadont said:**
> Make sure that you have the ntfs related kernel modules loaded or you won't have support for ntfs. What? I've never had to add extra kernel modules to get read access to NTFS...

---

### Post by yabbadabbadont on 2006-11-09
> **aysiu said:**
> You're missing a character in your options there. It should read: ```
sudo mount /dev/hda1 /media/windows -t ntfs -o **n**ls=utf8,umask=0222
```

 What? I've never had to add extra kernel modules to get read access to NTFS...
Yep, he's missing the 'n' of 'nls'.  Good catch.

Since the default ubuntu kernels all seem to be fully modularized, I assumed that ntfs support would have been compiled as modules too.  Oh well, if I was always right, I would be unbearable.  :D

EDIT: Hey!  No fair editing your post while I'm replying to it.  :P

---

### Post by roachk71 on 2006-11-09
You might need to install** libntfs8**, **libntfs-gnomevfs** and **ntfsprogs** through Synaptic. With these libraries and tools installed, you'd get safe read access to your ntfs partitions, but limited (and potentially unsafe) write access.

Let me know whether or not GNOME allows you to show them in the Computer section from your Places menu; an additional fstab entry may or may not be needed after this.

---

### Post by CowzRule on 2006-11-09
Hey thanks for the replies :)
> **aysiu said:**
> You're missing a character in your options there. It should read:
Code:
sudo mount /dev/hda1 /media/windows -t ntfs -o **n**ls=utf8,umask=0222
> **roachk71 said:**
> You might need to install **libntfs8, libntfs-gnomevfs** and **ntfsprogs** through Synaptic. With these libraries and tools installed, you'd get safe read access to your ntfs partitions, but limited (and potentially unsafe) write access.
Did both of those, still got the same error
> **roachk71 said:**
> Let me know whether or not GNOME allows you to show them in the Computer section from your Places menu; ...
Nope and "/media/windows" is empty.
> **roachk71 said:**
> ...an additional fstab entry may or may not be needed after this.
Heres's my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=6c625275-666c-43b5-ab72-527dae25f926 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=81b9da44-10a5-491d-a4e9-6056602c305e /home           ext3    defaults        0       2
# /dev/hda1
UUID=0AF4883EF4882E4F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=3770-376F  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=79057cb7-f38c-45be-9f60-70d57d03483b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

---

### Post by aysiu on 2006-11-09
Looks, then, as if /dev/hda1 is already mounted, which is why you can't mount it to /media/windows

It's already mounted at /media/hda1

---

