---
title: "GRUB problems: Sata, ata &amp; windows &amp; ntldr"
date: 2007-12-15
forum: General Help
---

### Post by Skerit on 2007-12-15
On a perfect day, I'll be able to run Adobe Premiere in Wine! Until this time, I'll have to do with bloody windows...

.. which really can't manage anything.

Here's the story, I have 2 SATA disks & 2 regular ATA disks, unfortunately, my mobo only has 1 IDE connector, so 1 regular ATA drive (the one with windows on it) is connected to the PC through a RAID card

This all used to work just fine until a while ago when I had to shuffle my hard drives around and now I can't get the original setup back.

So, when I first installed windows, it DEMANDED I made a boot partition for it on one of my SATA drives. I can get to this just fine in grub.

My RAID-drive, on the other hand, does not show up in the grub command line... 

When I boot to the SATA windows boot partition I'm always getting a "NTLDR missing" error, even though it's RIGHT THERE

---

