---
title: "Hard drive will not mount with permissions"
date: 2007-08-14
forum: General Help
---

### Post by donut2790 on 2007-08-14
My secondary hard drive is not accessible without entering my password when I first open it.  Is there a way to change this so anyone can open it?

---

### Post by logos34 on 2007-08-14
> **donut2790 said:**
> My secondary hard drive is not accessible without entering my password when I first open it.  Is there a way to change this so anyone can open it?

Yes, change fstab entry, permissions and/or owner (chmod, chown).  What is the filesystem type?

---

### Post by bodhi.zazen on 2007-08-14
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by donut2790 on 2007-08-14
Got it!  Thank you very much!

---

### Post by asnd16 on 2008-02-15
I have been having this issue as well . . . it just switches to read-only after about five minutes. . . It really pisses me off.  . I thought it was the torrents I was downloading so I have found that when it happens I simply unplug then re-plug remove the torrent and it stops. . But for some reason it switches . . and just started two or three days ago . .

---

