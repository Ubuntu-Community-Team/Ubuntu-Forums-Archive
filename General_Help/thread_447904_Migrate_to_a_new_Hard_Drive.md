---
title: "Migrate to a new Hard Drive?"
date: 2007-05-18
forum: General Help
---

### Post by aldenhg on 2007-05-18
I'm running out of space on my tiny 80GB drive. It being a dual-boot setup with games on both sides, space is at quite the premium right now. That's why I'm thinking of getting a 320-400GB monster to migrate my OSs on to. I know, I could just image the drive, plant the image on the new one and put it in the same location as the old one on the bus, right? Well, My current drive is an IDE and I'd like to switch over to SATA for the speed boost. This, of course, will change my /dev/sdaX numbering and I know how much that could screw things up. I know that I'll have to change my boot order in the BIOS and edit my grub menu.list, but what else would I have to do?

---

### Post by mvaniersel on 2007-05-18
Probably you also need to edit /etc/fstab

Nowadays partitions are recognized in fstab by an UUID. This makes it more robust for changes in the ordering of partitions. But I don't really know where the UUID comes from, if you can transfer it between partitions or regenerate it.

---

### Post by aldenhg on 2007-05-18
Is fstab the only file I have to worry about? If so I could just edit the new one to reflect the new drive layout.

---

### Post by mvaniersel on 2007-05-18
Probably. I've had a couple of times where I messed with my partitions, and I could fix everything easily by hand-editing /etc/fstab and /boot/grub/menu.lst

But do make sure you've backed up important stuff :) I don't want my advice to be responsible for data loss.

---

### Post by aldenhg on 2007-05-18
I don't think there's much risk of data loss, seeing as I'm not going to wipe the original drive until I know everything works. Thanks for the help.

---

