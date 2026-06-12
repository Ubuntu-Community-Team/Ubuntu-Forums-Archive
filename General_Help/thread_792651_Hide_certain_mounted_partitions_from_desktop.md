---
title: "Hide certain mounted partitions from desktop"
date: 2008-05-13
forum: General Help
---

### Post by musther on 2008-05-13
I have a data partition on a separate drive from my main system.  I have a /root partition, a /home partition, and a data partition mounted as /media/data.

The thing is, I don't want 'data' permanently visible on my desktop.  Is there a way to prevent this from showing on the desktop, but still allowing things like CDs and USB sticks from showing when mounted?

Cheers

---

### Post by ad_267 on 2008-05-13
Using gconf-editor you can prevent any volumes from showing up but this will not show flash drives and cd's etc. The only way I know to prevent the data partition from being shown on the desktop is to mount it somewhere other than in /media, eg at /data by modifying /etc/fstab

This thread might be useful: [http://ubuntuforums.org/showthread.php?t=393861](http://ubuntuforums.org/showthread.php?t=393861)

---

### Post by musther on 2008-05-13
Thanks, I thought they would be shown wherever they were mounted.  I've now mounted the relevant partition elsewhere and all is well.

Cheers

---

