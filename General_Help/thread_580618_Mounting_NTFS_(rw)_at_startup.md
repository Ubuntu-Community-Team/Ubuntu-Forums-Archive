---
title: "Mounting NTFS (rw) at startup"
date: 2007-10-18
forum: General Help
---

### Post by jeremyk@bellsouth.net on 2007-10-18
How would I mount my NTFS partition (rw) at startup in Gutsy?  I can access it through Gnome, but I have to click on Places / Computer / <ntfs-partition> each time to mount the drive (then provide root password).  I would like to mount it on startup so it's always available.

---

### Post by dcstar on 2007-10-19
> **jeremyk@bellsouth.net said:**
> How would I mount my NTFS partition (rw) at startup in Gutsy?  I can access it through Gnome, but I have to click on Places / Computer / <ntfs-partition> each time to mount the drive (then provide root password).  I would like to mount it on startup so it's always available.

Install the **pysdm** package, then in System-Administration-Storage Device Manager you can set that partition to mount automagically.

Note that the mount point must exist, so you may have to do this in a terminal beforehand:

```
sudo mkdir /myntfs
```
to create the mount point (and use whatever name you like - it's your system) to use.

The Storage Device Manage will make the necessary modifications to your /etc/fstab file to mount the partition on start up.

---

