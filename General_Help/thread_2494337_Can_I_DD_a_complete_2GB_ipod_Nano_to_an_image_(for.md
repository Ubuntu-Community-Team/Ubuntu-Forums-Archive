---
title: "Can I DD a complete 2GB ipod Nano to an image (for later use)?"
date: 2024-01-12
forum: General Help
---

### Post by 777funk on 2024-01-12
I've had a few cases where I've bricked or corrupted one of these (using ubuntu and rockbox) and DD has saved the device.

I usually just use another "known good" ipod nano with the same storage size (i.e. 2GB or 4GB ipod Nano).

Part of the problem is that my family members (children usually) do not always eject the device from Ubuntu before unplugging and it corrupts the unit. 

So my question should be... how do I uncorrupt the unit. But after trying fsck.hfsplus and regular fsck to no avail (still read only in Ubuntu), my solution is to just use DD.

With that said, my question is, rather than plugging in two ipods and DD ing from say:
sudo dd if=/dev/sdX of=/dev/sdY

Is it possible to make a backup image on my computer in some directory to dd from in the future?

---

### Post by TheFu on 2024-01-12
yes, if the source device is truly available.  I'd use ddrescue, not dd for this, so any bad blocks are ignored and the copy continues.  Just make the OF a filename.
I'd use something with ipod-nano-yyyy-mm-dd.img ... or run it though gzip to get ipod-nano-yyyy-mm-dd.img.gz

Beware that dd and similar image tools will copy all the empty space too, so if you plan to compress it, you might want to fill the storage with files containing lots of zeros.  Those compress REALLY well compared to random data.

---

