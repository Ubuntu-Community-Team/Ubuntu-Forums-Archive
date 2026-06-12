---
title: "Cannot mount hard drive?"
date: 2006-11-29
forum: General Help
---

### Post by Globox on 2006-11-29
I just installed Ubuntu on my SATA drive, and after it was finished I plugged in my IDE drive (which was completely blank).

Using gparted I formated the IDE drive to ext3. Following this tutorial ([http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)) I attempted to mount the drive, but whenever I use the command:
```
sudo mount -a
```
It returns this error:
```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
What am I doing wrong?

My fstab line looks like this:
```
/dev/hda1 /media/shared ext3 defaults 0 0
```

---

### Post by mgmiller on 2006-11-29
OK, you have formatted the drive, now you need to create a mount point for it and then mount it.  You could either manually edit /etc/fstab, or try installing the graphical mounter:
```
sudo apt-get install pysdm
```

This should put an entry in System>Administration>storage device manager that will graphically let you define a mount point and mount the drive.

---

### Post by taurus on 2006-11-29
Try

```
/dev/hda1  /media/shared  ext3  defaults  0  1
```
Otherwise, what is the output of this command from a terminal?

```
sudo fdisk -l
```

---

