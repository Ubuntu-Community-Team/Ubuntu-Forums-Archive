---
title: "altered &quot;volume settings&quot; for flash drive, now it won't mount"
date: 2007-05-14
forum: General Help
---

### Post by djaya2 on 2007-05-14
I thought I would try altering my flash drive's mount point by right-clicking on the flash drive on the desktop, clicking on the "Volume" tab, and entering the info there (rather than editing /etc/fstab).  I made the mountpoint /media/flash. Now my flash drive won't mount when I hotplug it.  I get the message "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)".  Because the drive won't mount, I can't undo what I did the same way (by right-clicking on the drive on the desktop).  I tried making an entry for the flash drive in my fstab, but that didn't help.  So now my flash drive won't mount.

Two questions:

1.  Where is the file that stores the info I entered so I can change it?
2.  What is wrong with the mountpoint I entered anyway?  My other mountpoints contain the "/" character.  For example /media/winxp.

Thanks.

---

### Post by jazzgossen on 2007-06-20
Did you find a solution to your problem yet? I just encountered the exact same thing.

---

### Post by jazzgossen on 2007-06-20
Actually, I just found the solution in [this thread.]("http://ubuntuforums.org/showthread.php?t=376404") You need to edit /system/storage/volumes/_org_freedesktop_Hal_devices_volume_uuid_2463_ABF7/mount_point in gconf-editor.

---

