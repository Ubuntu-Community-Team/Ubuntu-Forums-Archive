---
title: "MicroSD won't format"
date: 2020-09-29
forum: General Help
---

### Post by Geoff_Lane on 2020-09-29
Folks,

I have a suspect microSD card that is puzzling me.

It is formatted for a RaspberryPi with small fat32 partitions and a 7.5GB Ext4 partition.

I cannot seem to format this drive - that is not an issue except gparted says '**all operations successfully completed'** with green ticks by the various steps it takes when I try to delete both partitions.

dd gives the following;

```
sudo dd if=/dev/zero of=/dev/mmcblk0 bs=1M status=progress
7831814144 bytes (7.8 GB, 7.3 GiB) copied, 93 s, 84.2 MB/s
dd: error writing '/dev/mmcblk0': No space left on device

7528+0 records in
7527+0 records out
7892631552 bytes (7.9 GB, 7.4 GiB) copied, 118.328 s, 66.7 MB/s
```

Yet when mounted the disk still has its original RaspberryPi partitions.

There is no data I need to recover, quite happy to dispose of disk but why would gparted and dd both suggest the wiping operations were successful when they obviously are not?

Geoff

---

### Post by sudodus on 2020-09-29
It looks like your card is 'gridlocked'.

Maybe the card is *not* gridlocked, and there is a way around the problem. You can analyze the problem according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035), and if you are lucky, revive the card.

---

### Post by TheFu on 2020-09-29
I had a microSD go bad that was used in a r-pi the last 4 yrs, 24/7/365.  

On connection for that microSD to a few different systems here, it is usually not recognized at all.  It was cheap.  Flash storage wears out sometimes.

Spent $12 on a name-brand, high endurance, 32G microSD for replacement. All is well.  I didn't have a backup of that system, but I did have a nearly identical copy in another r-pi which was cloned, then just changed the hostname and IP. Both systems are kodi and mpd machines. Really the worst part if I had to start over would be to get the kodi addons back. I don't keep any content on the machines, so 8GB of storage is all they will ever need. Perhaps the extra 24G will be used to vastly increase the lifespan through wear leveling?

Think I got a package of 4 microSD storage devices for $30 years ago, so, to me, it isn't worth any real effort for recovery or attempts to fix. Useful life is over for that card.

---

### Post by tea for one on 2020-09-29
Try **gparted** > Device > Create Partition Table

Alternatively have a look at the options in **gnome-disk-utility **

Often, a combination of these two utilities will help format and/or re-format a troublesome SD/Micro card.

---

### Post by Geoff_Lane on 2020-09-30
> **sudodus said:**
> It looks like your card is 'gridlocked'.

Maybe the card is *not* gridlocked, and there is a way around the problem. You can analyze the problem according to [this link]("https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035"), and if you are lucky, revive the card.

Thank you for suggestion, I'll give that a try.

As mentioned, there is no data I need and even if I did manage to resurrect it doubt I'd trust it for anything so this is curiosity.  If the disk had been giving errors when trying to amend it using dd and gparted I'd have accepted that but they are saying adjustments are successful - hence the curiosity.

Geoff

---

