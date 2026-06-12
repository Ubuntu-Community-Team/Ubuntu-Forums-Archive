---
title: "Can Ubuntu Read NTFS"
date: 2007-02-19
forum: General Help
---

### Post by amdalex on 2007-02-19
Can Ubuntu read from a NTFS partition?:confused:

---

### Post by xopher on 2007-02-19
Short answer for a short question: Yes

how to do this?

1. Check what the partition's called: ```
sudo fdisk -l
```
2. Create a folder where you mount the partition: ```
sudo mkdir /media/hda2
```
3. Mount the partition: ```
sudo mount /dev/hda2 /media/hda2
```

For mor information abour mounting and preserving the mount after a reboot check: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by amdalex on 2007-02-19
Thankyou for your help.

---

### Post by Resurrection on 2007-02-19
To avoid giving it the mount command every time you want to use it, you will need to add it to your fstab.

```
sudo gedit /etc/fstab
```

You would need to add a line to it, something similar to:

```
/media/hda2    /media/hda2  ntfs    ro,nls=utf8,umask=007 0    0
```

Which should always mount your NTFS drive for every user automatically on startup with read-only access.  This assumes you have a directory at /media/hda2 already.  Linux support for writing to NTFS is still not rock solid just yet.

[NTFS-3g]("http://www.ntfs-3g.org/") is working on it, but its not perfected.

An explanation of fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by taurus on 2007-02-19
> **Resurrection said:**
> 
```
sudo gedit /etc/fstab
```


Please try to use gksudo when you use gedit and you also need a mount point to mount it to.

```
gksudo gedit /etc/fstab
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Resurrection on 2007-02-19
Right you are of course taurus about gksudo, I tend to forget that one myself.  Thanks.  Edited for the mount point.

---

### Post by CocoAUS on 2007-02-19
Windows also has a driver for Ext2 which works just dandy with Ext3.  I use the driver to grab files from my larger drive so I don't need to keep anything (except Windows itself, of course) formatted in NTFS.  If you can, I'd suggest doing that.

---

