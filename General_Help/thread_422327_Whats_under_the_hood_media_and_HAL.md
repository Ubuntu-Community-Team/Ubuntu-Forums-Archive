---
title: "Whats under the hood?: /media and HAL"
date: 2007-04-25
forum: General Help
---

### Post by Otvald on 2007-04-25
I have fiddled with an external USB HD, and was annoyed about the default permisions for the automounted USB device (only root have write access).

When the USB is unmounted, there is an empty file under /media/.hal-mtab

Once I plug the USB device, the file will be initialized with the settings (and permissions) for the newly plugged USB device. *Where* :confused: are the permissions and configuration, i.e. mountpoint name defined?

Btw: I use kubuntu (KDE)
My workaround: I started konqueror in root mode ```
kdesu konqueror
``` This allowed me to alter the permissions on the mounted device (as well as modify the mount name).... However I have no clue about what went on under the hood... Where where those changes stored? :-k

---

### Post by bvmou on 2007-04-25
Please google this but I resolved a similar problem with 

```
sudo chmod -R 777 /media/my-backup-usb-harddisk
```

I think this makes the permissions universal (and if anyone wants to read my boring work pdf's, that is punishment in itself.)  You can then lock them down again with other options to chmod.

The general info for mountpoints is in mtab (again google to be sure), filesystems in fstab, and there is a user-permission file for pluggable devices called plugdev.

Incidentally I have had weird (for me) USB mass storage problems with both Feisty and Debian Lenny and have had to use pmount for things that used to be automatic.  I am not nearly expert enough to say whether these are problems but I am curious as to the technical explanation.

---

### Post by Otvald on 2007-04-25
> ```
sudo chmod -R 777 /media/my-backup-usb-harddisk
```
But will this be persistent? Once the device is unmounted, the mount point is removed (and thus the permissions)

> The general info for mountpoints is in mtab (again google to be sure), filesystems in fstab, and there is a user-permission file for pluggable devices called plugdev.

Since the mountpoint is dynamically created (i.e. does not exists until the USB device is mounted), I believe I cannot use entries in fstab (as this will conflict the automounting). Also it seemed that the mtab was modified when USB was plugged/unplugged.

---

### Post by bvmou on 2007-04-25
I came across your problem looking for answers to similar problems, these are more terms to google than advice.  Maybe use the UUID in fstab to avoid redundant or generic device names?

---

