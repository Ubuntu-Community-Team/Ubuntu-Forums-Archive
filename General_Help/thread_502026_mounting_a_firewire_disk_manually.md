---
title: "mounting a firewire disk manually"
date: 2007-07-16
forum: General Help
---

### Post by finite9 on 2007-07-16
how do I mount an external firewire drive manually?  I dont know which device under /dev/ I should mount.  i do know how to use mount however!  just someone tell me which device it is!!  ieee1394, 1394 or firewire device names do not exist in my /dev directory (running ubuntu 7.04 amd64)

I run a server, and automount only works if I log into gnome.  I do not log in, hence its not automounted.  the disk does work fine though after login, but only for the gnome session, not the other tty's.

---

### Post by brent113 on 2007-07-17
I'm not sure if this is exactly what you're looking for, but I'll try:

To list harddrives, your options are:

```
fdisk -l
```

or

```
sudo lshw -C disk
```

or if you have GParted installed (not by default) you can use it's interface

---

### Post by finite9 on 2007-07-17
yes it was! thanks for the help.  I gota bit confused because fdisk -l shows only my firewire disk and says it is sda1, and I have now mounted this successfully, but why does it say it's sda?  I thought that naming convention was used for scsi or sata discs.  Shouldn't firewire disks have another denomination?

---

### Post by brent113 on 2007-07-17
well, the way i understand it, it's hda for ide, and pretty much sda for everything else.

---

