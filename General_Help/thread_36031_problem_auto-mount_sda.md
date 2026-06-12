---
title: "problem auto-mount sda"
date: 2005-05-21
forum: General Help
---

### Post by Gandalf on 2005-05-21
Hello,
i have an external HDD plugged with USB, but i have a problem mounting it on startup,
in fstab i have
```

/dev/sda2       /media/WAEL_FAT vfat    defaults,uid=1000,gid=1000,umask=000,iocharset=utf8     0       0

```

on ubuntu boot, before the hotplug step i find, cannot mount sda, sda don't exist

and i have to manually type
sudo mount /media/WAEL_FAT  but it's annoying because i share it with NFS if i mount it using NFS before it's mounted i cannot remount before i restart the server and i mount it first, otherwise i get on the PC that mount it using NFS:
 sudo mount /media/WAEL_FAT/
mount: 192.168.3.2:/media/WAEL_FAT failed, reason given by server: Permission denied
no way to get the permission, without restarting the server, i even tried sudo exportfs -a on the server nothing changed !!! :(

---

### Post by Kyral on 2005-05-21
I have the same problem with my SATA HD. It seems that USB and SCSI drives are handled by hotplug. I just mount it as soon as I get into GNOME. I supposed you could insert a command into a bootscript to mount it AFTER HotPlug is active, but I dunno how to do that.

 As for the NFS part, I don't know

---

### Post by Gandalf on 2005-05-22
so any suggestion guys? it seems that i'm not the only one having this!

---

### Post by hippyjim on 2005-09-23
I used webmin to set up a "mount -a " as the very last bit to run at startup.

It sometimes works, but then, sometimes my USB HDD isn't recognised at all.

---

