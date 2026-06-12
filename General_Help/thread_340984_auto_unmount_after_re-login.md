---
title: "auto unmount after re-login"
date: 2007-01-18
forum: General Help
---

### Post by FAT_C on 2007-01-18
i got a problem for mounting a hard drives.
when ubuntu starts up, its auto mount my all other hard drives(which are in FAT32 and NTFS under windows OS). 
However, when i logout and login again, those mounted hard drives unmount by itself(automatically)~!!](*,) ](*,) 

why would this happen?? i dont want it this way. how can i still get hard drives mounted after re-login??

p.s. i just install KDE from gnome, and this happen under KDE environments (dont know if gnome also has the same problem or not)

---

### Post by kidders on 2007-01-18
Hi there,

This is an odd problem! KDE can't unmount volumes on its own, because doing so normally requires access to the root account. It would have to ask you for a password before it could "sudo umount" anything. Perhaps you have tweaked or installed something that is handling this for you?

What /etc/fstab options are you using to have the FAT & NTFS filesystem mounted automatically?

---

### Post by FAT_C on 2007-01-18
sorry for the late reply

btw, how to check the /etc/fstab ??
i saw the file there

---

### Post by kidders on 2007-01-19
> **FAT_C said:**
> btw, how to check the /etc/fstab ??I'm just curious about what's in it. I'm assuming you altered /etc/fstab to have your non-Ubuntu filesystems mounted automatically at boot. I was hoping to see whether the changes you made would permit the kind of behaviour you described in your o/p.

Chances are however that they do not ... are you sure your disks are mounting & unmounting as your described?

---

