---
title: "Can I resize my partition with a swap in the middle?"
date: 2012-11-22
forum: General Help
---

### Post by sdowney717 on 2012-11-22
I run off the sda6 partition which is inside the sda2 EXTENDED partition which includes the sda7 swap and sda5 (want to shrink) partition. SDA2 is what I would like to expand.

Will the SDA7 partition get in the way?
so what to do about this? I have lots of partitions on this drive.
I started getting messages saying I am running out of space.

Is SDA7 even needed?

here is gparted screen shot

---

### Post by sdowney717 on 2012-11-22
yes I suppose I can
I am shrinking and moving to the right about 300gb

For my boot partition I will have to run a live usb as you cant resize with it mounted.
I suppose I can just move the swap to the beginning of the other partion on the end

---

### Post by sdowney717 on 2012-11-22
Took very long time but the first part is done of shrinking and moving one partition.

---

### Post by dcstar on 2012-11-22
> **sdowney717 said:**
> 
.........
I suppose I can just move the swap to the beginning of the other partion on the end

You do not bother to move Swap partitions, there is **nothing** in them.

Record the UUID of the current Swap partition, delete it and then create a new Swap partition and assign the old UUID to it.

---

### Post by offgridguy on 2012-11-22
> **dcstar said:**
> You do not bother to move Swap partitions, there is **nothing** in them.

Record the UUID of the current Swap partition, delete it and then create a new Swap partition and assign the old UUID to it.

This is handy to know.  Thanks

---

### Post by sdowney717 on 2012-11-23
I did just move the swap as it was very easy. It took only about 15 seconds for gparted to do it. I kept it at 4gb in size. I have 8gb ram.
I thought that was easier than trying to edit something.

I then booted a live usb and expanded the root drive into the 
freed up 200gb. Which took about an hour. So about 5 hours to do this.

I also expanded my sda2 extended to use up the little extra space at the end and then expanded the sda5 into it.

---

