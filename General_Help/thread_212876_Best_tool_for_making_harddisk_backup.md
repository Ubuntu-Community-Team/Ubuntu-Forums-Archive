---
title: "Best tool for making harddisk backup"
date: 2006-07-10
forum: General Help
---

### Post by driesel on 2006-07-10
Hi,

Since I'm quite concerned about keeping my Ubuntu 6.06 configuration safe, I really want to make an entire harddisk backup.
I've been googling on the matter a while, but I really can't figure out what to do.

So here's my question:

What's the best Ubuntu 6.06 tool for making harddisk images?
What tool lets me put the recovered data back on a new harddisk (in the eventuality that my current drive gets broken)?
What are the obstacles (things to take note off)?

greetings,
driesel

---

### Post by aysiu on 2006-07-10
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by driesel on 2006-07-30
Could I also use a Windows tool like Acronis Disk Director to copy all partitions from my 40 GB ATA133 drive onto my new SATA 160 GB drive?

The partitions are:
*/dev/hda1 => ntfs
*/dev/hda2 => ext3 => boot
*/dev/hda3 => extended
     */dev/hda5 => linux-swap
     */dev/hda6 => ext3

If I do this, will I still be able to boot Ubuntu properly from the SATA disk?

greetings,
driesel

---

