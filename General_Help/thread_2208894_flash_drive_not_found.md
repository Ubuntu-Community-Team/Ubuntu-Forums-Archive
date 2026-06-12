---
title: "flash drive not found"
date: 2014-03-02
forum: General Help
---

### Post by frog3764 on 2014-03-02
Greetings to the Group - My system is a dual boot with W7 and U 12.4.  I have a 8 GB flash which works just fine in W7 but U won't find it.  I just formatted the flash in W7 again.  So why doesn't U find it?  Do I have to mount it, and if so, how do I do that?  I want this flash to be recongnized and usable by both systems.  My other flaash, 1 GB woks fine with both systems.  I am constantly copying files from U to W7 or to my other pc, XP Pro.  All input is appreciated.

Jim

---

### Post by Impavidus on 2014-03-03
I think the small usb drives are automatically mounted, whereas the large ones are only detected, but not mounted. I don't have a small drive at hand to test it. Not sure whether it's based on size, file system, something else – it's all correlated. Still, the usb drive should show up in the side pane of the file manager or on the desktop, depending on which desktop environment you use. Then you can right click&#8594;mount.

---

### Post by frog3764 on 2014-03-03
Hey Impavidus, I don't know what happened earlier, but the flash shows up now, so everything seems OK.  

Jim

---

### Post by varunendra on 2014-03-03
Please mark the thread as [Solved] then. :)

@ Impavidus,

I have two Kingston 8 GB pen drives, one is partitioned into 3 partitions (2 FAT32, 1 EXT3) and one is whole 8 GB FAT32 partition. All of them automount as soon as plugged in. I have also tested a Sony 32 GB once, and that one automounted as well. So that's definitely not size or filesystem dependent. Probably some bug or permission issues in umount or something, I'm not sure either. But one thing that I'm sure is that it can be 'Forced' to automount by adding fstab entries, not the best option, but works.

---

### Post by Impavidus on 2014-03-03
It could be a little bug somewhere. My old 1GB Sandisk drive, single FAT16 partition, automounts always, but my 16GB Kingston (FAT32) doesn't, and neither does my 8GB Sandisk SD card (FAT32), directly plugged in or left in my camera and connected by usb, or my external usb hard drive. Strange, but I don't really care.

---

