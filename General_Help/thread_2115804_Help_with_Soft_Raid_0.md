---
title: "Help with Soft Raid 0"
date: 2013-02-14
forum: General Help
---

### Post by rosefox911 on 2013-02-14
Hey guys,

I currently have 3x 3TB drives in my Ubuntu home server. One of t hose is used exclusively for  Ubuntu. Currently, the other 2x 3TBs are not used. I wanted to do a soft raid 0 with them. I did some googling but couldn't find much on it. Is there an easy way to create this soft raid through the disk utility or something of the sort? Thank you!

---

### Post by papibe on 2013-02-14
Hi rosefox911.

I haven't find any 'ultimate' documentation, so you would need to research and read several tutorials to get the most of it

Here are some references:
[LIST]
[*][Ubuntu official documentation: Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID").
[*][Ubuntu Wiki: Raid]("https://wiki.ubuntu.com/Raid").
[*][How to Geek: How to Setup Software RAID for a Simple File Server on Ubuntu]("http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/").
[/LIST]This couple of youtube tutorials are good too:
[LIST]
[*][Ubuntu mdadm lesson 1]("http://www.youtube.com/watch?v=mee9l1aNZdc").
[*][Ubuntu mdadm lesson 2]("http://www.youtube.com/watch?v=HryJvlOtEVU").
[/LIST]Hope it helps. Let us know how it goes.
Regards.

---

### Post by ali abry on 2013-02-14
get "[The Debian Administrator's Handbook]("http://debian-handbook.info/")" from this link :
[http://debian-handbook.info/get/now/](http://debian-handbook.info/get/now/)
in chapter 12 it describe setting up raid perfectly.
i suggest to test it once on virtual Ubuntu and then run it on real word.

---

### Post by oldfred on 2013-02-14
I do not use RAID, but I think RAID 0 is not often suggested. If you really need speed then use a SSD.
      

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by papibe on 2013-02-14
> **rosefox911 said:**
> **2x 3TBs**
I missed this.

If you want to use the whole space on those 3TB disks, don't use 'fdisk' as described on the tutorials. Use '**gdisk**' instead.

fdisk, at this moment, only supports MBR partition tables, which are up to around 2TB.

Regards.

---

