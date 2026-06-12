---
title: "Newbie needs a bit of help. Bios Flash on Asus M6000"
date: 2017-04-14
forum: General Help
---

### Post by sidewindersid on 2017-04-14
Hello all and thanks for looking.

I have installed 16.04 LTS on my old M6000 Asus

It has the F4 easy flash utility in bios, but that wants a Floppy drive !

So I thought maybe I could make a FAT32 partition on the HDD and name it for example U:/ etc.
So that the bios would be able to see it & use the new bios that I have from Asus website.

I have found GParted but after looking I was a bit worried about using this in case I killed the system.

Any clues or help would be really good.

Thanks
Sid

---

### Post by mikewhatever on 2017-04-14
What does BIOS flashing has to do with Ubuntu?

Floppy, CD or flash driver are all usual BIOS flashing tools, Ubuntu ...not so much.

---

### Post by sidewindersid on 2017-04-15
> **mikewhatever said:**
> What does BIOS flashing has to do with Ubuntu?

Floppy, CD or flash driver are all usual BIOS flashing tools, Ubuntu ...not so much.

Thanks

But what I was actually looking for is some help creating a fat32 partition within ubuntu, so that the bios could read it as it's flash drive.

Cheers

Sid

---

### Post by mörgæs on 2017-04-16
Have you tried creating a FAT32 partition on a USB stick and boot from that?

---

### Post by sp40140 on 2017-04-18
You can use Gparted to create FAT32. Just make sure you select correct drive / device to format. Also, it is a good sign that you are bit worried about messing up system with Gparted. It just makes you cautious. Any other tool you use will have same potential for mess-up.
Though it is advisable to use windows to create FAT/NTFS partitions, but if you don't have access to windows, you can use Gparted. It will work most of the time.

---

