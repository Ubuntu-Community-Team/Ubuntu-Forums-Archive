---
title: "How do I use a USB device within GRUB?"
date: 2007-10-10
forum: General Help
---

### Post by Donkor on 2007-10-10
I've got a USB floppy drive.  Ubuntu sees it fine and mounts it under /media/disk/.  I put it in GRUB with the following (basically just copied/pasted another section and changed the title/root around):

> 
title           USB Floppy
root            /media/disk/
savedefault
makeactive
chainloader     +1


But I get an error when trying to boot from it.  
> 
Error 11: Unrecognized device string


Any ideas?

---

### Post by erlingerle on 2007-10-10
The root of the USB-key will be something like /dev/sda (unless that is your harddrive)

If that works I dont know.... Never booted from usb stick :/

---

### Post by dabl on 2007-10-10
Maybe a little help in here:

[http://ubuntuforums.org/showthread.php?p=3487407#post3487407](http://ubuntuforums.org/showthread.php?p=3487407#post3487407)

:)

---

### Post by Donkor on 2007-10-10
> **dabl said:**
> Maybe a little help in here:

[http://ubuntuforums.org/showthread.php?p=3487407#post3487407](http://ubuntuforums.org/showthread.php?p=3487407#post3487407)

:)

I did what your post said, and added the following line to /etc/fstab:
> UUID=F0C3-BD35 /media/usbfloppy vfat user,atime,rw,nodev,nosuid 0 0

but now it doesn't mount at all.  The info I got from your two commands was
> 
SEC_TYPE="msdos" UUID="F0C3-BD35" TYPE="vfat" 

Disk /dev/sdb: 1 MB, 1474560 bytes
3 heads, 53 sectors/track, 18 cylinders
Units = cylinders of 159 * 512 = 81408 bytes


---

### Post by dabl on 2007-10-10
Hmmmm -- looks like a reasonable mount line for fstab.

Don't forget you need to put a formatted diskette in it -- empty floppy drives won't mount.

Did you manually make the mount point "/media/usbfloppy"?

There isn't any other device trying to be /dev/sdb, is there?  Check it with ```
blkid 
```

Have you attempted to manually mount it -- you might get an informative error message if you do that.

```
sudo mount -t vfat /dev/sdb /media/usbfloppy
```

HTH! :)

---

### Post by milton1 on 2007-10-10
/media/disk is not a valid root device. try this:

root (sd1,0)

remember, grub indexes from zero, so /dev/sdb1 will be (sd1,0)

---

### Post by Donkor on 2007-10-10
> **milton1 said:**
> /media/disk is not a valid root device. try this:

root (sd1,0)

remember, grub indexes from zero, so /dev/sdb1 will be (sd1,0)
I tried both that and sd0, and both times got 
> Error 23: Error while parsing number.

I was able to mount it to /media/usbfloppy, but I'm just not sure what should be put in the grub menu to boot from it.

---

