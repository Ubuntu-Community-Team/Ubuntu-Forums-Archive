---
title: "Can I use a USB drive for system memory or swap space?"
date: 2007-05-12
forum: General Help
---

### Post by Tom Chaudoir on 2007-05-12
1. My system only has 256 megs of memory and I think it's limiting me.
2. I have a spare 1 gig thumb drive.

Can I plug the stick into a USB port for good and use it to fortify my system somehow?

Sorry if this is a dumb question but I'm a recent convert from, you know, that other OS.

Thanks!
Tom

---

### Post by tgalati4 on 2007-05-12
This is where Vista really kicks butt.  If you don't have enough memory to run it, it will find space on USB drives to consume.

I suppose it is possible.  Flash memory chips to have a limited life.  Perhaps 10,000 read/write cycles.  The memory controller has some housekeeping to do to mark bad bits.  Although the memory is faster than harddisks for reading, sometimes writing can be slower because of the controller and the bit verification routines.

By assigning it as swap, it may get thrashed quickly.  But as the USB sticks are cheap these days, it can be better than trying to track down memory for an oddball machine.

Since USB is controlled by the hotplug kernel poller, I'm not sure how performance will be effected.  Of course pulling the stick on a running system would be interesting.

Perhaps you can tell us.

---

### Post by taurus on 2007-05-12
Yes, you can use your USB thumbdrive as a swap partition for your Ubuntu BUT the only problem is that there is a limited times that you can write to your thumbdrive.  After that amount of times, it's dead.  So, using thumbdrive as a swap space is not a good idea.

What's wrong of creating a swap partition on your harddrive?

---

### Post by Tom Chaudoir on 2007-05-13
> **taurus said:**
> 

What's wrong of creating a swap partition on your harddrive?

I do have a swap partition. When I run vmstat 2 it shows that the partition is being used pretty heavily. That seems to be what's degrading performance. I was hoping to prove or disprove that with the thumb drive before buying more memory.

Thanks for the answers. I didn't know that flash drives wear out. Guess I'll just bite the bullet.

Best,
Tom

---

### Post by taurus on 2007-05-13
If you have space on your harddrive, you can also create a swap file.  Or resize your / partition and create another swap partition.

---

