---
title: "ISO files under Linux"
date: 2006-11-23
forum: General Help
---

### Post by Tilex on 2006-11-23
OK so I have these 3 ISO files for MatLab.  I want to install this program.  Under Windows, I would have mounted the ISO files one at the time on a virtual drive, and I would have executed the setup wizard that way.

Under Linux though, it is the first time I do this.  Can we mount the ISO's?  If yes, how?  Or can I simply extract the ISO files and run the setup from there on?  If yes, how?

Thanks!

---

### Post by groggyboy on 2006-11-23
to mount iso files (replacing file.iso with the path to your iso):
```
sudo modprobe loop
sudo mount file.iso -t iso9660 -o loop /media/cdrom
```

to unmount:
```
umount /media/cdrom
```

Is MatLab a windows program?  If so, you'll want to install Wine as well (and hope it works).

---

### Post by Tilex on 2006-11-23
Thanks for the quick reply, I'll try that out later when I've time and post my results...

No, it is the Linux versio of Matlab so it should work fine..

---

### Post by DavidTangye on 2006-11-23
> **groggyboy said:**
> to mount iso files (replacing file.iso with the path to your iso):
```
sudo modprobe loop
sudo mount file.iso -t iso9660 -o loop /media/cdrom
```

1.modprobe loop should not be required, because the loop driver should already be installed, unless you have hacked a distro.
2./media/cdrom is where your cd drive is mounted. Better to 
```
sudo -i
cd (iso directory)
mkdir xyx.iso.mnt
mount xyz.iso  -t iso9660 -o loop xyx.iso.mnt

```
ie xyz.iso.mnt is the mount point for xyz.iso

This way you can also mount as many other isos as you wish at the same time, each to their own mount point.

---

### Post by hardyn on 2006-11-23
3 iso's eh?...   maybe next time don't tell us the contents of the disk?

---

### Post by DavidTangye on 2006-11-24
> **hardyn said:**
> 3 iso's eh?...   maybe next time don't tell us the contents of the disk?

"I don't understand a word you just said.:???: "<<Napoleon Dynamite

---

