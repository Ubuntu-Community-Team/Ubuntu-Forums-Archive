---
title: "Can't specify charset for mounting USB HDD partitions"
date: 2004-11-04
forum: General Help
---

### Post by timothyha on 2004-11-04
I was so happy when at last Ubuntu with kernel 2.6 and a fixed hotplug recognized my Sarotech USB 2.0 HDD drive. Latest Fedora 2/3 has some broken hotplug with kernel 2.6 and it could not see my drives.

But my filenames are in Russian, so when the disk is automounted, I see that the charset goes wrong. How do I specify something like iocharset=utf8 ? I don't have /etc/fstab entries for the USB HDD partitions, since they are supermounted.

Also, one partition is NTFS (others are FAT32) and it didn't appear on desktop even though Ubuntu has NTFS support. I even added libntfs and libntfs-gnomevfs from Synaptic.

---

