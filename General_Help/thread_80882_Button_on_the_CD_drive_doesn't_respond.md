---
title: "Button on the CD drive doesn't respond"
date: 2005-10-23
forum: General Help
---

### Post by discofro on 2005-10-23
I don't know if this was answered elsewhere, but here is my question.

When I have a CD in the drive, and I press the button on my drive, the drive does not respond. 

If I press the button when the drive is completely empty, it works.

The only way I can eject a disc is to do it within the OS by selecting 'Eject' from the right-click menu of the CD icon. Is this done on purpose, or is this a bug, or is this just something wierd with my drive?

Thanks.

---

### Post by zekolas on 2005-10-23
That is normal, when you put a cd in the drive, ubuntu will automaticly mount the cdrom drive, and it will not let you eject the drive untill the drive is unmounted, so just pushing the physical eject button on the drive won't actually unmount the cdrom drive.

So when you select eject from ubuntu it un mounts the drive then ejects the disk. If you ran the command 

```
umount /mnt/cdrom
```

that would cause linux to unmount the drive and you could then push the eject button on the drive.

---

### Post by BIGtrouble77 on 2005-10-23
[QUOTE=zekolas]That is normal, when you put a cd in the drive, ubuntu will automaticly mount the cdrom drive, and it will not let you eject the drive untill the drive is unmounted, so just pushing the physical eject button on the drive won't actually unmount the cdrom drive.

So when you select eject from ubuntu it un mounts the drive then ejects the disk. If you ran the command 

```
umount /mnt/cdrom
```

that would cause linux to unmount the drive and you could then push the eject button on the drive.[/QUOTE]
Or just right click on the mounted drive's desktop icon and choose umount.

---

### Post by orzechowskid on 2005-10-23
*That is normal, when you put a cd in the drive, ubuntu will automaticly mount the cdrom drive,*


would you happen to know why a CD might not get automounted sometimes?  I'm having a problem where I can put any of my data CDs into my drive one day have it show up on my desktop, but the next day Ubuntu will refuse to automount the exact same CD.

---

### Post by sb73542 on 2005-11-14
Probably HAL or gnome-volume-manager has crashed.  Rather common.

---

### Post by frodon on 2005-11-14
If you want to eject the CD, using the button, run this command :  ```
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'
```If you want to create an icon to eject the cd : [http://ubuntuforums.org/showthread.php?t=52768&highlight=cd+eject](http://ubuntuforums.org/showthread.php?t=52768&highlight=cd+eject)

---

