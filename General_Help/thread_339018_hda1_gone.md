---
title: "hda1 gone ?"
date: 2007-01-15
forum: General Help
---

### Post by woopud on 2007-01-15
I had installed Windows Vista on my laptop and then Ubuntu Edgy but now Vista doesn't show up in Grub it goes directly to Ubuntu.  I don't really care about Vista but now i'm missing half of my harddrive, is there a way from within Ubuntu to claim the rest of my harddrive and reformat it ?

Bert

---

### Post by Wordcrasher on 2007-01-15
Use fdisk or cfdisk to reformat Vista partition and then mount it wherever you want.

---

### Post by taurus on 2007-01-15
The partition is still there; you just need to mount it before you can access it.

```
sudo fdisk -l
```

---

### Post by woopud on 2007-01-15
```
woopud@woopud-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3995    32089806    7  HPFS/NTFS
/dev/hda2   *        3996        7157    25398765   83  Linux
/dev/hda3            7158        7296     1116517+   5  Extended
/dev/hda5            7158        7296     1116486   82  Linux swap / Solaris

```

How do I go about formatting and mounting it ?  

Bert

---

### Post by taurus on 2007-01-15
So you want to format /dev/hda1 to ext3 filesystem?

```
sudo mke2fs -j /dev/hda1
gksudo gedit /etc/fstab
```
Then, add this line to the end of it.

```
/dev/hda1   /media/hda1   ext3   defaults   0   1
```
Save the change.  Then create a new mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```

---

