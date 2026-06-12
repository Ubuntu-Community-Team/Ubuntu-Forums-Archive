---
title: "&quot;An error occurred while mounting..press S to skip or M for manual recovery&quot;"
date: 2013-10-10
forum: General Help
---

### Post by QWDCepe on 2013-10-10
I had been auto-binding several directories on a separate partition to be automatically in my home directory, and it seemed to be working for a while until at some point (I think I lost power completely and the system was shut down improperly) I got the error:

> An error occured while mounting [FONT=Verdana]/media/beezwings/Beezfiles/Music[/FONT]
Press S to skip mounting or M for manual recovery...

My fstab file is as follows:

> # /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=0ad07b4c-f504-496a-ba17-e09f9685d66d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation




/media/beezwings/Beezfiles/Music /home/beezwings/Music auto bind
/media/beezwings/Beezfiles/Videos /home/beezwings/Videos auto bind
/media/beezwings/Beezfiles/Pictures /home/beezwings/Pictures auto bind
/media/beezwings/Beezfiles/Downloaded /home/beezwings/Downloads auto bind
/media/beezwings/Beezfiles/Jess /home/beezwings/Documents auto bind

I'm pretty new to linux and ubuntu, so please walk me through the steps slowly, thanks!

---

### Post by maestrobwh1 on 2013-10-11
I'd start by commenting out anything in fstab other than your root device and swap.

Then boot normally.  

However, I have had weird things happen where a kernel updated  or some other essential file/package.  My bind looks like this in fstab
```

UUID=78F7-0DEB  /media/FAT_3  vfat      rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks 0 0
/media/FAT_3/MacLibrary/iTunes/Music    /home/ubuntu/Music      none    bind 0 0
```

"none" seems to work well here for the filesystem type and the latter two zeros just tell fstab never to check.  I have always had two numbers at the end (0 0) unless it is the root drive (0 1)

I' make each line 
/media/beezwings/Beezfiles/Music /home/beezwings/Music **none** bind **0 0**

then do

```
mount -a 
```

---

### Post by cdoebbler on 2013-11-08
I have the same problem, but a different /etc/fstab:

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
show 0 0

any ideas what is wrong here?

---

### Post by dannyboy79 on 2013-11-08
are you certain the separate partition is being mounted to the same location everytime, being /media/beezwings/Beezfiles/Music and the others? i don't see anwhere in your fstab your other partition being mounted

---

### Post by XBNCPRk on 2013-11-08
> **cdoebbler said:**
> I have the same problem, but a different /etc/fstab:

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
show 0 0

any ideas what is wrong here?


A) there should be more to your fstab file than that, and 
B) thou shalt not hijack someones thread ;)

---

