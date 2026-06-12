---
title: "mimimize writes with compact flash"
date: 2007-12-06
forum: General Help
---

### Post by markp1989 on 2007-12-06
am planning on installing ubuntu server edition, plus xorg, and tunar, xfce4,xdm, amsn and Ktorrent to a CF card,i have heard that CF cards only have a limited amount of writes, is there any way to reduce the number of writes to the CF card?


its for the Media Pc mentioned in my sig, and is going to be used for file management, on the 2 hard drives, internet surfing, and torrent downloads

i have already created a swap partition on one of the IDE drives that is 1gb in size, and i cannot think of any other ways to reduce writes, even thou i know there must be a way.

---

### Post by viciouslime on 2007-12-22
Use ext2 for all the partitions on the CF card instead of ext3. Ext2 isn't journaled which significantly reduces the number of writes.

---

