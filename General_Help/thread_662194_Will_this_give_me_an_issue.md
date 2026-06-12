---
title: "Will this give me an issue?"
date: 2008-01-08
forum: General Help
---

### Post by Hawk__0 on 2008-01-08
Ok, so my intentions are to move my current home folder to a different hard drive, and have it mount by itself when i boot up my pc.  what I have done this far:

-formatted the other disk as ext3
-mounted it as /home/steve2 (my current home folder is /home/steve)

currently i am copying all the contents of /home/steve to /home/steve2

I have edited fstab, as such:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3d27f7f0-c4a3-4045-a629-9dd45b80cbe0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=548ac3b6-c02f-49e0-a81c-7547f76fef4a none            swap    sw              0       0
/dev/sdc0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
**/dev/hdb1       /home/steve2    ext3    defaults,auto   0       0**

```

the **main question**: when it is done copying... and i change fstab's entry to /home/steve and remove my old /home/steve and then rename /home/steve2 to /home/steve, will i experience any issues?

thanks in advance!!


EDIT: Also, what about the links in 7.10 to "pictures", "documents" etc, folders? will they still work if they are copied?

---

### Post by Zimmer on 2008-01-08
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Info at bottom of page gives advice for fstab entry... have a read, I hope that helps.
Regards
Zimmer

---

### Post by Hawk__0 on 2008-01-09
ok well i already pretty much did everything there.  i just hope that when i rename steve to steve3, then steve2 to steve, and reboot, that i do not have issues. haha

---

### Post by geirha on 2008-01-09
You might experience some issues if you are logged in as user steve. It's safest to do this last part in recovery mode or from the ubuntu CD.

Make sure the new filesystem currently mounted as /home/steve2 is owned by the user steve:
```
ls -ld /home/steve2
```
if it isn't, run ```
sudo chown steve:steve /home/steve2
```

And, you won't be able to move /home/steve2 to /home/steve while it is mounted, so just create an empty /home/steve and only change the fstab-entry.

BTW, it's better to put the whole /home on a seperate partition, rather than just the one homedir. Though, both ways will work :)

---

### Post by Hawk__0 on 2008-01-09
oh man, i should make the whole home on a sep part. hm.  i might have done that, but i will have to check.

---

