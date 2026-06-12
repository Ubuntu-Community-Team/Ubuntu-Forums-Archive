---
title: "recommendation for RAID-type backups?"
date: 2013-09-23
forum: General Help
---

### Post by rebeltaz on 2013-09-23
This weekend (at the same time my internet went down for 4+ days (still on-going)) my media drive refused to mount. I figured out that the main superblock bad damaged, so I ran fsck using an alternative superblock and was luckily able to recover the drive. This is a 1.5 TB external desktop USB drive, by the way.

First thing I did was to go purchase a second 2 TB external desktop USB drive. What I would like to do is to have the system keep a running mirror image of my media drive on the second drive. I know about rsync and a couple of it's GUI frontends, including grsync, but is that the only (best) option for what I would like to do, or is there a better mousetrap? 

Thanks...

---

### Post by XBNCPRk on 2013-09-23
You can make a partition of the same size on your new 2tb drive, and use it and the partition on the old 1.5tb drive to make a mirrored RAID1 array using mdadm. It will keep a real time mirror, and you can use the remaining space on the new drive for whatever else youd like (though it will not be protected by redundancy).

---

### Post by rebeltaz on 2013-09-23
As soon as get a stable connection, I'll install that and give it a try. Does it REQUIRE postfix or can that be removed once mdadm is installed? I was able to get that far before I lost connection again...


Thank you for the advice.

---

### Post by SaturnusDJ on 2013-09-24
I really suggest not doing that. RAID and backup don't go in the same sentence.
It's most likely that a damaged filesystem superblock is being synced by the RAID. RAID typically isn't smart. It just syncs the ones and zeroes in the layer beneath. RAID is for speed and uptime.

Go for the rsync or other backup software.

---

