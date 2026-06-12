---
title: "Can't Change Partition on 2nd Drive"
date: 2007-09-17
forum: General Help
---

### Post by fishmorg909 on 2007-09-17
Got a problem with resizing partitons on my second drive. I have Ubuntu on the primary drive, and Mepis on the second drive (chainloaded select from Grub). I'm running out of room on HDB3 (where "my" stuff is), so I want to expand it by taking space from HDB1.

After trying QTParted on the Mepis drive (Won't do it), the Mepis live CD (Won't do it either), I boot up the primary Ubuntu drive and try GParted to shrink HDB1 by 2 GB. Worked fine, Mepis booted with no trouble. But I still can't get GParted or QTParted to expand HDB3. I've tried logging in as root on Mepis live and Knoppix, but no go. I can't seem to find the solution on the forum -- any advice?

Here's what it looked like on Mepis live CD:

[IMG]http://i33.photobucket.com/albums/d56/mntcorr57/gpart.png[/IMG]

---

### Post by yabbadabbadont on 2007-09-17
hdb3 appears to be mounted.  umount it and try again.

---

### Post by fishmorg909 on 2007-09-17
> **yabbadabbadont said:**
> hdb3 appears to be mounted.  umount it and try again.

Hmm, no -- it was already unmounted. I checked a couple of times, it didn't make any difference.

---

### Post by yabbadabbadont on 2007-09-18
Download the gparted livecd.  Boot with it and try from there.

---

### Post by fishmorg909 on 2007-09-20
Eh, I found out on MepisLovers Forum that the hdb3 sector is in the wrong place -- it's last, so that means it can't be extended. I'd have to futz around with everything to rearrange it. I'd be better off with a new (larger) drive... thanks anyway!

---

