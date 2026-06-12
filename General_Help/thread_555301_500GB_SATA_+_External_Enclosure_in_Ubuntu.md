---
title: "500GB SATA + External Enclosure in Ubuntu"
date: 2007-09-20
forum: General Help
---

### Post by kockroach on 2007-09-20
Hi, I'm a newbie in Ubuntu. Recently I bought this WD500gb together with a Cooler Master enclosure, formatted the disc in to two partition, both NTFS since I dual boot it with Vista. My question is whenever I restart the Ubuntu, the desktop will show my 2 partition in the 500gb but when I click on it. It said the partition is not mounted, then I need to restart my 500gb, but then now I've another 2 drive coming out with the same partition. e.g. Drive A Drive B another Drive A Drive B. One of them when I right click it shows unmount partition, another one shows reject volume, how can I fix it? Thanks

---

### Post by dcstar on 2007-09-20
> **kockroach said:**
> Hi, I'm a newbie in Ubuntu. Recently I bought this WD500gb together with a Cooler Master enclosure, formatted the disc in to two partition, both NTFS since I dual boot it with Vista. My question is whenever I restart the Ubuntu, the desktop will show my 2 partition in the 500gb but when I click on it. It said the partition is not mounted, then I need to restart my 500gb, but then now I've another 2 drive coming out with the same partition. e.g. Drive A Drive B another Drive A Drive B. One of them when I right click it shows unmount partition, another one shows reject volume, how can I fix it? Thanks

I assume it connects via USB, if so make sure your /etc/fstab file does** not** have any entries for them - they will be mounted automagically because it is USB.

If you want the two filesystems to be on your desktop with individual names, just label them in Windows and that is how you will see them in Linux.

Also, you will need to install the ntfs-3g package if your want to write to them from Linux (do a forum search for specific instructions).

---

