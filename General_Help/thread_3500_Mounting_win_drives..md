---
title: "Mounting win drives."
date: 2004-11-06
forum: General Help
---

### Post by tvlad on 2004-11-06
Ubuntu didn't automatically detect my drives and mount them so i used the root console, created the necessary dirs in /media, chmoded all to 755 just to be sure, but whenever i do mount a share in one of those dirs it changes the permisions into a 500, and i have no idea why.

This is one entry from /etc/fstab, i don't think i did anything wrong here :
             /dev/hda7       /media/Vld4     ntfs    ro,auto,user    0       0

---

### Post by iarwaith on 2004-11-06
Try changing "ro" to "rw" perhaps?

Otherwise you're setting the mount as read only.

Cheers.

---

### Post by FLeiXiuS on 2004-11-06
[QUOTE=iarwaith]Try changing "ro" to "rw" perhaps?

Otherwise you're setting the mount as read only.

Cheers.[/QUOTE]


Incorrect, currently there is no stable release for the Linux-NTFS project which will enable you to read / write data to the ntfs file system.  You will need to patch your kernel.  Complete instructions and more information can be found at: [http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)

---

### Post by Rancoras on 2004-11-06
[QUOTE=tvlad]This is one entry from /etc/fstab, i don't think i did anything wrong here :
             /dev/hda7       /media/Vld4     ntfs    ro,auto,user    0       0[/QUOTE]

Try this line in your fstab:

```
/dev/hda7       /media/Vld4     ntfs      ro,uid=1000,gid=1000   0   0
```

---

### Post by tvlad on 2004-11-06
Thanks rancoras, i hadn't thought of specifying the gid and uid, but shouldn't the user flag have had the same effect ?

---

### Post by stodge on 2004-11-06
I usually do noauto,user for mounting FAT32 partitions.

---

### Post by Rancoras on 2004-11-06
[QUOTE=tvlad]Thanks rancoras, i hadn't thought of specifying the gid and uid, but shouldn't the user flag have had the same effect ?[/QUOTE]

Not sure, I just know that line works :D

---

### Post by tvlad on 2004-11-07
I Also added umask=0022, i know i can't write on those shares, but i like to be able to write TO them once i copy them over to Ubuntu.

---

