---
title: "Mount for other user that root"
date: 2007-03-04
forum: General Help
---

### Post by koma77 on 2007-03-04
Sometimes I mount an NTFS-partition from within Ubuntu. 
I do that like this:

```
sudo mount /dev/sda1 /mnt
```

It works fine, but the resulting mount point is only available to the root user. So I kind of end up doing a 

```
sudo nautilus
```

just to be able to browse the files. It's not a good way, I know.

Which way is the best way to mount a partition so that my normal user can use it?

---

### Post by sriram on 2007-03-04
why dont u mount it permanantly in /media/dir and mount it on every boot
?

---

### Post by Ramses de Norre on 2007-03-04
Specify a mountoption umask=0000 and make the mount point rwx for your user.

---

### Post by Billyum on 2007-03-04
Hi! 

I have the same problem with a portable drive.

Ramses, your solution sounds good, but your instructions are a bit cryptic. Could you expand on that, please?

BTW, my mount point is owned by my regular user account, but after mounting the drive, it is owned by root.

Thanks,

Billyum

---

### Post by Ramses de Norre on 2007-03-04
In fstab you can specify mountoptions, it's the column that reads "defaults,errors=remount-ro" for /, you need to put "umask=0000" in that column for the drive you want all users to have access too.

---

### Post by Billyum on 2007-03-04
Thanks for your quick reply, Ramses. :-)

I found the fstab file, but I am lost. The mount point I know, but what file system do I enter? What type? Auto?

This drive plugs in with a PCMCIA (sp?) card. When it is plugged in, it is identified as /dev/sda1. Is that the file system?

Still mysterious.

Many thanks,

Billyum

---

### Post by Ramses de Norre on 2007-03-04
Post the output of **sudo fdisk -l** when the drive is plugged in, that will reveal the file system.

---

### Post by Billyum on 2007-03-05
Here is the fdisk -l output:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         994     7984273+   b  W95 FAT32

How is this for the fstab entry?

/dev/sda1    /mnt/extdrv    vfat    rw,users,umask=000    0    0

Many thanks,

Billyum

---

### Post by Ramses de Norre on 2007-03-06
That should work, you might want to add another '0' to umask.

---

