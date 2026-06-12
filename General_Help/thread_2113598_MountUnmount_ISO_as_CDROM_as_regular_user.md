---
title: "Mount/Unmount ISO as CDROM as regular user"
date: 2013-02-07
forum: General Help
---

### Post by Freecore on 2013-02-07
Hello there,

I'm using Ubuntu 12.04.

I hope this can be done, I want to mount and unmount ISO files as if CDs so I can manage these like a normal user (whitout root privileges).

I'll explain myself: when you put a CD in the CDROM Ubuntu automatically mounts it and you can eject it from Nautilus, I want a command or so so I can do that whit ISO files, whitout doing a script with gksudo.

Somethig weird happens when I try to do this via the terminal:

```
sudo mount -t iso9660 -o loop path/to/ISO /media/isomount
```

Nautilus shows it as a hard device in Devices area with the name of the ISO (the icon is the same as floppy), but here's the weird thing: I can eject it like a regular user from nautilus, so is what I want, but when I do this for a second time (sudo mount -t ...) it shows in Nautilus twice, it appears in Devices with the name of the ISO but whitout the eject option, and it appears up to filesystem (/) where is the home folder and the documents, here it's with the name "isomount", the icon of CDs and the eject button but when I try to eject from Nautilus it says that it isn't in fstab and I'm not root user.

Why is that happening? And why the first time it happens different?

I would be gratefull if someone have an idea to solve this or have a better idea in how to mount ISOs without doing a sudo or gksudo, maybe a nautilus script.

Can that be done?

---

