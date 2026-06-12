---
title: "Error when mounting USB harddisk!"
date: 2008-04-16
forum: General Help
---

### Post by LasseNC on 2008-04-16
Hello people! Whenever I try to mount my Maxtor USB harddrive I get this error!

[http://stalkerzone.dk/upload/Screenshot2.png](http://stalkerzone.dk/upload/Screenshot2.png)

The error message is quite elaborate, but even though, I'm pretty unsure of which action I should take towards this.

Any help will be appreciated :)

Kind regards, Lasse

---

### Post by pytheas22 on 2008-04-16
It looks like the drive is formatted as NTFS and Ubuntu thinks there might be some corruption with the file system, so it doesn't want to automount it.  As the message indicates, you could try to force it to mount with the command:

```
mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

but there's some risk involved so don't do this if you have non-recoverable files on the USB stick.

Another option is to try to access the drive from Windows and see what happens.  You could run chkdsk in Windows to see if any corruption is found.

If the drive works fine in Windows, I would back up any important files and try force mounting it in Ubuntu.  It could be that everything is fine and you are getting this error message only because the Linux NTFS driver is still sort of new and sometimes makes mistakes, so the only way to know for sure is to try reading and writing the drive.  You could also try reformatting the drive to FAT32, which would work a lot better than NTFS.

---

