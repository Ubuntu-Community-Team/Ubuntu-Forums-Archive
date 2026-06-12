---
title: "some contents unreadable"
date: 2014-12-20
forum: General Help
---

### Post by mayagrafix on 2014-12-20
Why does the properties box for the / partition say "some content unreadable"? is it referring to data in the swap portion of the partition? why is the / partition a mix of ext3 and ext4? should it be ext3 100%? The home folder is in a separate partition from the Ubuntu OS partition.

[IMG]http://i.imgur.com/NBIyazW.png[/IMG]

---

### Post by mayagrafix on 2014-12-20
Here is a snapshot of my partition scheme. sda1 is Windows NTFS, sda3 is Ubuntu OS, sda2 extended is Home folder sda5 + SWAP sda6.

[IMG]http://i.imgur.com/DaoBASF.png[/IMG]

---

### Post by Dennis N on 2014-12-20
Contents would be unreadable if the user doesn't have permissions to read that content. An example would be /root/ folder with its 700 permissions, where you fall into other category (no permission).

---

### Post by Dennis N on 2014-12-20
Sorry, missed this part:

> is it referring to data in the swap portion of the partition?

There is no swap portion of the root partition. Swap is a separate partiton. Your gparted screen shot shows / as sda5, and swap as sda6.

---

