---
title: "USB drive for multiple users"
date: 2007-06-12
forum: General Help
---

### Post by jalfan on 2007-06-12
Again, I run into a problem that I cannot find problem resolution for... maybe I'm looking in the wrong place.

I have a 250GB WD MyBook USB drive.  Both my wife and I use the computer, but we like different things so I have 2 accounts set up on the computer.  We log in at different times of the day and rarely reboot. 

Whoever logs onto the computer first gets permissions for the drive and no other user is allowed acces to the drive (without rebooting) -including root.

I am not very familiar with /etc/fstab but I did see someones post somewhere about changing that file.  I did the changes and still something worked, but it is not anymore.

I have done other updates, and I looked back at the file recently and the lines I changed were commented out.

I didn't want to uncomment them because I was unaware of what changes were made and I don't want my computer to blow up:D!

I had formatted the drive as FAT32 so it could be used in linux as well as with windows (assuming my wife eventually wants me to re-install it).

The commented line for /dev/sda1 is my USB drive as I was prompted to enter into the file from someone else's post.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 /media/GERALD vfat umask=0,user,iocharset=iso8859-1,codepage=850,noauto,quiet 0 0
UUID=40b924e1-0163-478e-8f5e-f5c8c13d3b5e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e1aadebf-7e8a-4a3e-8ecc-05bdc88ab76f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Thanks in advance for any help!

TTFN

---

### Post by jazzgossen on 2007-06-28
You *shouldn't* have to edit fstab to get what you want, as this is supposed to be handled by the hal daemon. I'm having similar trouble myself, though, and this doesn't seem to work right for a lot of people. Try looking at [this thread]("http://ubuntuforums.org/showthread.php?t=232428&highlight=usb+users+permissions") and see if that helps.

---

### Post by jalfan on 2007-06-29
Thanks for the link, I wasn't able to make it all the way through the thread, but it did help.  I changed my fstab to match this comment from gostal

> **gostal said:**
> ```
/dev/device /mnt/mountpoint vfat rw,user,uid=1000,iocharset=iso8859-1,umask=007 0 0
```

but I changed uid=1000 to gid=100 (since in my situation I want it to be a shared drive) and this seems to work when I use the switch users option.

Thanks again,

-jalfan

---

