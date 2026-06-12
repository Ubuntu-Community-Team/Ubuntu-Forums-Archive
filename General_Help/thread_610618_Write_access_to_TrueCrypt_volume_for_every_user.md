---
title: "Write access to TrueCrypt volume for every user"
date: 2007-11-12
forum: General Help
---

### Post by vbtricks on 2007-11-12
Salut,

I've got a FAT32 formatted TrueCrypt volume which can be read from when mounted as root by every user of the system. But writing does not seem to work. I tried setting the group-property (and the linked permissions) of the mount point to the group of users which should be able to write to it.
If I set the properties before the TrueCrypt volume is mounted to it, the group is set back to root when I mount the volume as root. If I unmount it again, the group-property is the desired one again.
My tries to set the group-property when the volume was mounted resulted in a "permission denied" (although I've done this as root).

Any suggestions how to mount the volume, so that every user on the system can write to it?


Thanks in advance,

Stefan

---

### Post by StevenHarper on 2007-11-25
Yes to do this mount with the -u switch

```
truecrypt -p **** -u /home/steven/aCrypt /media/mountpoint
```

the -u switch only works with FAT crypts and wont work with EXT2 or EXT3

If you don't know of it, I have made and packaged a GUI for TrueCrypt on Ubuntu called **Easy Crypt**

[http://ubuntuforums.org/showthread.php?t=585578](http://ubuntuforums.org/showthread.php?t=585578)

This has been accepted to be in the archives and will be included in Hardy Heron

Steve

---

### Post by vbtricks on 2007-11-26
Salut,

well, it's really nice that you developed a gui for TrueCrypt, but have you read my posting?

I did not have any problems using TrueCrypt at the command line. I wanted all users to have write access to a mounted FAT32 volume.


Stefan

---

