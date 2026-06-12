---
title: "Making use of apparent second hard drive"
date: 2012-10-24
forum: General Help
---

### Post by lesliek on 2012-10-24
I have an Asus Eee PC 900. The specifications say: "12GB S.S.D. (4GB built-in + 8GB flash)".

fdisk reports that there are sda (4GB) and sdb (8GB), so that although there seems to be one SSD, it's recognized as two separate hard drives.

I've got Ubuntu 12.04 on three partitions on sdb.

I had Windows XP on sda, but removed all partitions on sda, so that it's all unallocated space.

How do I now make use of the space on sda for Ubuntu?

---

### Post by sienile on 2012-10-24
Fire up Gparted and format it to a ext filesystem. That's it.

---

### Post by lesliek on 2012-10-24
Thanks for your reply, sienile.

I've done as you suggest.

I've created one partition on sda, with filesystem ext 4.

However, I'm not sure what to do next.

I haven't tried yet to see whether it'll be mounted automatically on bootup, but I suppose that, if it doesn't, I can mount it manually.

Can I now transfer to it things like my home folder and then make a link between that folder and its former location? If i can, should I?

I guess I'm really asking what's the best way to make use of this extra 50% of hard drive space I 've just obtained, given that I only had 8GB before and it's pretty much full.

Thanks again.

---

### Post by sienile on 2012-10-24
You can mount it in any file manager and use it now.

To do what you were saying about moving your home directory, here's a guide. [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by lesliek on 2012-10-24
Thank you for the reference to the guide.

I'll now try to absorb that.

---

