---
title: "Accidentally removed &quot;/dev/md/2&quot;"
date: 2013-01-02
forum: General Help
---

### Post by OklaMokla on 2013-01-02
Hello. I have two 3TB HHD on software raid 1, one ssd and one ramdisk on my Ubuntu Server. I wanted to test my main disk (/) write speed, so I typed "dd count=1k bs=1M if=/dev/zero of=/dev/md/2" and when I pressed enter I realized what I have done and quickly pressed control + c, the command ran for about 0.5 seconds. I had fstab open, but I was stupid and I closed that, anyway I can remember this

/dev/md/1 was boot
/dev/md/2 was the / with EXT4 filesystem
ssd was "/dev/sda" (maybe) and mounted on "/media/CraftSnow"
ramdisk was "/root/CraftSnow2

I cant remember the swap. I can boot the server from network to rescue system. Any idea how to fix this, whatever command I enter it just says segmentitation fault.

Thank you :)

- Oscar

EDIT:

I booted the server on virtual machine:
[IMG]http://i.imgur.com/QQi8g.jpg[/IMG]

EDIT2:


Hardware data:

   CPU1 Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz (Cores 12)
   RAM  63889 MB
   Disk /dev/sdc: 3000.6 GB  (=> 2861 GIB)
   Disk /dev/sda: 240.1 GB  (=> 228 GIB)
   Disk /dev/sdb: 3000.6 GB  (=> 2861 GIB)

the 3000 discs are in raid1

---

