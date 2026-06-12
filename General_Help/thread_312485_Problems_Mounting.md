---
title: "Problems Mounting"
date: 2006-12-04
forum: General Help
---

### Post by trianglemanwins on 2006-12-04
I am having problems mounting my ntfs and fat32 partitions.  When I first installed edgy it automatically put my ntfs partitions on my desktop.  I had some problems with one ntfs partition and reformatted it through windows.  I also added a sata fat32 drive.  Once i reformatted the ntfs partition ubuntu has been unable to mount the ntfs or the fat32.  They both show up in fdisk -l but their supposed mount folders are empty.  How can i fix this?

---

### Post by johnnymac on 2006-12-04
what happens if you issue:

```

sudo mount -a

```

---

### Post by trianglemanwins on 2006-12-04
it just says

```
mount: special device /dev/disk/by-uuid/8EB88949B88930AF does not exist
mount: unknown filesystem type 'usbdevfs'

```

---

### Post by taurus on 2006-12-04
What are the outputs of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by wgscott on 2006-12-04
The problem is that edgy decided to edit your /etc/fstab and replaced the device names with UUID serial numbers, and those UUID serial numbers change when you repartition.

I'm not sure why they did this, but the easiest way to undo the damage is to move /etc/fstab out of the way and copy /etc/fstab.pre-edgy into its place.


A similar problem took about 5 hours of my life that I will never have back. I wish they would TELL YOU when they mess with your configurations.  I thought that was the debian way.

---

