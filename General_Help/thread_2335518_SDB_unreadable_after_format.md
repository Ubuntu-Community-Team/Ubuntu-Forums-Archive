---
title: "SDB unreadable after format"
date: 2016-08-29
forum: General Help
---

### Post by jacksontheguy192 on 2016-08-29
Recently I have gotten an SD card to use for a few of my electronic projects, I put it in, and I was told to format it, while formatting... I didn't notice it was still formatting so I took it out. When it said there was an error I put it back in... and the icon didn't show up, I then tried ```
sudo fdisk -l
``` and it didn't show any /dev/sdb. I think I corrupted it. What do I do?

---

### Post by ajgreeny on 2016-08-29
You may have killed the card completely by interrupting a format operation, but if this were mine I would either install gparted in my *ubuntu OS, or use a live *ubuntu OS which has gparted by de4fault, and try to start again.

Insert the card, start gparted and look for it in the drop-down box at top right. If found, for example as /dev/sdb, go to **Device ->Create new partition table** and make a new msdos partition table then a new partition formatted to whatever filesystem you want, probably fat32 for a card.

---

