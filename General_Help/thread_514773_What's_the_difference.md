---
title: "What's the difference?"
date: 2007-08-01
forum: General Help
---

### Post by superbungalow on 2007-08-01
What's the difference installing ubuntu through wubi, and installing it on a separate disk partition?

---

### Post by ago on 2007-08-01
dedicated partition is 

1) more robust against file system corruption, 
2) you get hibernation/suspend
3) slightly faster disk I/O (normally not noticeable)

Of course you have to create a dedicated partition and burn the CD (or use shipit). If partitioning and CD burning are not a burden for you, go with a dedicated installation. 

Wubi is mostly for people that have no clue what a partition is and/or do not know what to do with an ISO file and/or for people that want to try Ubuntu  for a few days and weeks and do not know whether they will end up using it or not.

---

### Post by Odegard on 2007-08-01
hdparm -tT /dev/sda gives me around 42MB/s on my laptop harddrive... I'm really surprised it's this fast. Disk I/O should therefore not be a concern with wubi.

---

### Post by superbungalow on 2007-08-01
Well, I installed ubuntu on my home pc, running xp, using a live cd and that worked ok, but i uninstalled it because it is too slow, and I've reconsidered and I'm not too sure about installing it on my new laptop. But then I found wubi and I'm installing it on my laptop, will it work the same way as with the live cd? So it will show a list of operating systems to load when i boot up?

---

### Post by ago on 2007-08-01
Yep

---

### Post by tuxcantfly on 2007-08-02
> But then I found wubi and I'm installing it on my laptop, will it work the same way as with the live cd?

Also note that if you subsequently ever want to convert your Wubi install to a "real" install with dedicated partitions, you don't have to re-install Ubuntu, you can just use LVPM [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) and that way you'll have all the advantages of a full Ubuntu install.

---

