---
title: "Hard Drive Partition"
date: 2008-06-16
forum: General Help
---

### Post by nigel_salvador on 2008-06-16
On one of my hard drives there is a partition with an ntfs filesystem and according to GParted the partition has a key icon beside it, which suggests that it is lock. How do I unlock the partition so that I can resize it. Pleeeeeeeeeeease help. Thanks

---

### Post by geirha on 2008-06-16
The key symbol probably means it is mounted. If that is the case, unmount it and all other partitions on that drive. If I remember correctly, you can right click the partition in gparted and unmount from there.

---

### Post by nigel_salvador on 2008-06-16
Yes but when I do that it does not allow me the option to Resize/Move and I need to increase the size of this partition so that I have more room to store my mp3s.

---

### Post by ChameleonDave on 2008-06-16
> **nigel_salvador said:**
> Yes but when I do that it does not allow me the option to Resize/Move and I need to increase the size of this partition so that I have more room to store my mp3s.
NTFS should only be used as a Windows partition.  I advise against using it for general storage, as the technology is a Microsoft trade secret.  It is likely to cause problems.  Use a FAT or Ext partition instead for that.

And, of course, make sure partitions are unmounted before manipulating them.

---

### Post by bigken on 2008-06-16
try using the gparted live cd

---

### Post by geirha on 2008-06-16
> **nigel_salvador said:**
> Yes but when I do that it does not allow me the option to Resize/Move and I need to increase the size of this partition so that I have more room to store my mp3s.

All partitions on the drive you intend to do changes on need to be unmounted. There aren't any other parititons with a key-symbol? a swap partition perhaps?

Also, are you doing this from your installed system? It's generally best to boot into a live session to do this, the Ubuntu CD will do fine, or you can download and burn the [gparted livecd](http://gparted.sourceforge.net/livecd.php).

---

### Post by bigken on 2008-06-16
you also need to shrink  a partition to create some free space to resize your ntfs partition

---

