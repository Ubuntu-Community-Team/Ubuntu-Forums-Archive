---
title: "Change LUKS partitions that were made with alternate-install cd"
date: 2008-01-16
forum: General Help
---

### Post by Meson on 2008-01-16
I'm not sure if "LUKS partitions" is the right term, but I installed 7.10 from the alternate install CD and chose to use LUKS to setup an encrypted volume.  I have what should be a default configuration.

I want to shrink my current root partition (located at /dev/mapper/computer-root) and make two roots for separate installations.  How can I do this?

Also, if I wanted, could I resize the entire encrypted partition, and just create another ext3 and swap partition.  So I'd have one installation behind and one in front of the encryption.  Or will resizing the encrypted partition screw it up?

---

### Post by shanepardue on 2008-02-28
I'm looking for this solution as well. I want to resize an encrypted ext3 partition to fill up an 
entire hard drive, but it seems to be more tricky than I thought. Is this possible?

---

