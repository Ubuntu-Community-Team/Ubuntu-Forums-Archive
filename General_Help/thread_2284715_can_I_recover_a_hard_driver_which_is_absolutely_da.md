---
title: "can I recover a hard driver which is absolutely damaged?"
date: 2015-07-01
forum: General Help
---

### Post by Jonatan Formentera on 2015-07-01
Hi, the hard driver of my computer broke down absolutely. I took it out and put it in an enclosure in order to use it from an usb, but the system doesn't even detect it. Can anyone tell me if there is some way to recover it?
Thanks

---

### Post by TheFu on 2015-07-01
Maybe. Is this a spinning HDD or SSD or M2?

There are 10,000 things that could be wrong with it so it may not be possible to recover at all or it could be a trivial error. If you want more help, you'll need to be much more descriptive about how the disk failed, any sounds heard, was the drive performing well before it stopped working?  Anything else that might be important - did you just reinstall an OS or touch the partitions in any way? Did the drive get dropped?

It would be easier if connected through SATA or eSATA, not USB. USB doesn't have the full instruction set needed for complex data recovery.  eSATA is 100% like SATA, just external. USB can access data, but it isn't ideal.

If the data is worth $3000+ and you don't have a good backup - take it to a professional data recovery company - they have the right hardware to do this and the expertise to replace the parts of the disk that aren't working.  Assuming the heads didn't crash into the platter. Most of the things we can try will make any existing physical damage worse, so if there is physical damage to the platters - STOP, unplug ASAP.


Having a good backup would make all of this a non-issue, right?

---

### Post by Jonatan Formentera on 2015-07-01
It was suddenly. The screen froze and I had the suspicion it was the hard driver. The computer is OK. I replaced the hard driver and it works perfectly. I don't need to recover the files. I did a back up. I was just wondering about the possibility to recover it just to learn a little.
Thanks

---

### Post by TheFu on 2015-07-01
> **Jonatan Formentera said:**
> It was suddenly. The screen froze and I had the suspicion it was the hard driver. The computer is OK. I replaced the hard driver and it works perfectly. I don't need to recover the files. I did a back up. I was just wondering about the possibility to recover it just to learn a little.
Thanks

Excellent! I don't have to worry about "do no harm" ... 

If it still spins, then I'd use a few tools in this order:
* fsck - see if it is a trivial issue.
* ddrescue to mirror the data bit-for-bit off to another disk. 
* badblocks scan it for ... bad blocks.. 

The last 2 items help a HDD fix itself by exercising the bit reading for every byte on the media. If it cannot retrieve data from a block, it will use a spare block and relocate all the data it can there.

IF you have SMART data enabled for the drive, it would be good to look at that using hdparm.  IME, SMART is only useful if graphed over time. Values for now, without some history aren't useful since there aren't any standards for what this data actually means.

If the partition table is corrupted, there are tools to scan and rebuild it.
If the built-in controller HW is dead, there isn't much to be done - but find an exact copy of the HW and swap the controller boards - good for bad. This is what the pros do.

Do this stuff even over a USB3 connection will be relatively slow compared to SATA.

---

