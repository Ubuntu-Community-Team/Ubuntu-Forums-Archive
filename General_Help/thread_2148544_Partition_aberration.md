---
title: "Partition aberration"
date: 2013-05-25
forum: General Help
---

### Post by tyela on 2013-05-25
I have a Toshiba Satellite with a 32 GB SSD on which Ubuntu 13.04 is installed, and a regular 500GB HDD (which contains some remnants of the factory Windows 7 installation - wish I had formatted this before). In any case, the big HDD presents itself as "Windows" under "Devices" in nautilus, situation which I obviously found revolting and proceeded to attempt to change. Moreover, I was looking for a way to mount this HDD automatically upon startup. 

I thus went to "Disks", selected the 500 GB HDD (which was at /dev/sda1), and clicked on More actions -> Edit mount options. I turned on automatic mount options, and, while I was at it, entered "HDD" in the "Display name" field. I am 99.9% sure that I did not do anything else, just clicked OK and closed "Drives". The first suspicious thing came about when I opened nautilus. Now I had both "Windows" and "HDD" under devices. I opened Drives again and, indeed, there were 3 drives, a random 13 GB (!?) one called HDD, now at /dev/sda1, what was now left of the 500GB Windows at /dev/sda2, and the SSD at /dev/sdb1. I got annoyed and deleted the HDD partition. Naturally, I now have 13GB of unallocated space. What's worse, when I boot, the computer remains in the ubuntu screen indefinitely. I tried advanced options boot and I think it has to do with the fact that it's still trying to mount /dev/sda1, which doesn't exist anymore. It gets out of the screen if and only if i press 'S' (skip mounting?).

How do I make it automatically get out of the purple boot screen? Also, is there a way to reallocate the lost 13GB to the big partition (without reinstalling ubuntu or wrecking any more havoc)? I'm ok with losing 13GB as long as the computer will just boot.. And can anyone explain to me why this might have happened with the renaming?

---

### Post by ohnonot on 2013-05-26
i'm not qite sure what you're talking about, but if what you experience now happens before login, you should probably do some reading about fstab and grub and mount (all documented on ubuntu interwebs).
plus taking a look at your hd and its partitions (maybe with sth like gparted).
you are moving into sudo territory now, beware.

---

### Post by fantab on 2013-05-27
Boot with Ubuntu Live DVD/USB and:

Post the screenshot of your partiions.
post the output of:

```
sudo parted -l
```

---

