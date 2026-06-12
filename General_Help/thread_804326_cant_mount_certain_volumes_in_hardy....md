---
title: "cant mount certain volumes in hardy..."
date: 2008-05-23
forum: General Help
---

### Post by jorik42 on 2008-05-23
so, i recently updated to hardy 8.04, and have encountered an interesting problem; the computer doesnt auto-mount certain volumes.  i have a fat32 (just formatted) and a ntfs (that was formatted like 2 days ago); everytime i plug them in, i get an error message that says:

     Cannot mount Volume
     invalid mount option when attempting to mount the volume '<name>'

the same volumes mount just fine in ubuntu 7.10 (on my eeepc).  any ideas whats going on?

jorik

---

### Post by sharks on 2008-05-23
you need to put an entry for them into your /etc/fstab. First find out what the device name is with sudo fdsik -l The device name will be the entry with NTFS next to it.

use that to put an entry into the /etc/fstab something like:

/dev/sda /media/mountpoint ntfs-3g defaults 0 0

Edit:
 [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) that is relevant to the fstab entry:
/dev/<your partition> /media/<mount point> ntfs-3g defaults,locale=en_US.utf8 0 0

---

### Post by sharks on 2008-05-23
first go to terminal , type /etc/fstab then change it.

---

