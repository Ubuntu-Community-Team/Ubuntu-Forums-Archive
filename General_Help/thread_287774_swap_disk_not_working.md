---
title: "swap disk not working"
date: 2006-10-29
forum: General Help
---

### Post by el_ricardo on 2006-10-29
when i set my xubuntu machine up, i added a *very* old IDE 850MB hard disc, and formated it in the SWAP file system, assuming ubuntu would utilize this automatically, the disk is at "/dev/hdd1", so i modified my fstab to this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       none            swap    sw              0       0
//192.168.0.2/SharedDocs /media/JILL     smbfs credentials=/root/.smbcredential$

```

/dev/hda5 is the swap partition that the ubuntu installer set up for me, the /dev/hdd1 line is the line i added, surely this should work?

also, now that i'm looking at it, whats with the "errors=remount-ro" about?

---

### Post by lloyd_b on 2006-10-29
The "fstab" entry looks fine.  Have you rebooted the machine since making that change (swap is only activated during startup - just adding the line to fstab won't make the system enable that swap space).

If you have rebooted, type the following command:

```
**swapon -s**
```

This will list all active swap spaces. If your new swap doesn't show in that list, try this:

```
**sudo swapon -a**
```

This will attempt to enable all swap spaces defined in "fstab".  If there's a problem with that swap partition, this should show an error message.

Lloyd B.

---

### Post by lloyd_b on 2006-10-29
Oh, I forgot....

The "errors=remount-ro" tells the system that if it encounters any errors on the partition during startup, to remount the partition as "read-only" so that "fsck" can be run on it to repair the errors.  

Lloyd B.

---

### Post by jwbirdsong on 2006-10-29
If (for some reason) after following lloyd_b advice the drive still isn't recognized....I'd try commenting out the ```
/dev/hda5       none            swap    sw              0       0
``` and see if it will recognize the drive as swap at all

---

### Post by el_ricardo on 2006-10-29
appears to be working now, i had rebooted after altering fstab the first time, i rebooted again and it worked lol, must have been a glitch somewhere at the startup, i dunno ....

---

