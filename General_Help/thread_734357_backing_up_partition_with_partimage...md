---
title: "backing up partition with partimage.."
date: 2008-03-24
forum: General Help
---

### Post by Mia_tech on 2008-03-24
I want to backup my ubuntu and windows machine with partimage, and so far I have not been able to...this is what I do, backup the partition table with```
dd if=/dev/sdo of=/file/mbr bs=512 count=1
```
then I proceed to backup the partition, all goes well ecxept when I restore the partition table  and reboot, I get "error can't fiend the operating system"
does anybody know what are the correct steps to backup and restore with partimage?

thanks

---

### Post by cmnorton on 2008-03-25
But this does not look like partimage; it just looks like you are using dd, not a bad thing, but you've not told us how you have set things up to perform this operation.

---

### Post by mlapaglia on 2008-03-25
I use partimage to backup my computer every week, because I am constantly breaking ubuntu ;).

I simply boot from a livecd, mount my network drive, install partimage, run it, and tell it to backup to the mounted server. if you select the most compressed option, my 100 gb hard drive is shrunk down to about 8 gb (it only backs up actualy used hard drive areas, not the free parts.

Partimage (at least in my usage) backs ups the partition table and MBR, so all i have to do is the same procedure again and click "restore" instead of "save."
Let me know if you need anymore help on getting it to work.

---

### Post by Mia_tech on 2008-03-25
> **cmnorton said:**
> But this does not look like partimage; it just looks like you are using dd, not a bad thing, but you've not told us how you have set things up to perform this operation.

what I was doing is backing up the partition table manually, which is unnecessary, I finally got it to work, one thing I don't understand about the way partimage works, is that when you are restoring you have to restore the partition table and mbr before restoring your image, and that info is in the same file as your image, but if you restore your image without restoring the partition table, your computer leave you with a blank screen when you reboot...go figure!..but any ways I finally got it working, great substitute for ghost, which I've allways used... and the best thing is free ;0)

thanks

---

