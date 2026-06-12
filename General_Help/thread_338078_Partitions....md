---
title: "Partitions..."
date: 2007-01-13
forum: General Help
---

### Post by ryantmer on 2007-01-13
Hmm, I'm good at messing this stuff up >_>

Anyway, to the point. I have both Kubuntu and Ubuntu on this 10GB HDD (both 6.06LTS version). I originally installed Kubuntu, but something was wonky, so I made a new partition, and installed Ubuntu. The problem was that I sized the partitions wrong, and made the Ubuntu one far too small, ie after the initial updates, the partition was already 99% full. To attempt to fix this, I reduced the size of my Kubunut partition. However, I do not know how to add the unallocated space created by this downsize to my Ubuntu partition.

For those that don't want to read all that: How can I add unallocated space to a partition on my HDD?

Thanks in advance... in the meaning, LiveCD's ftw.

---

### Post by bodhi.zazen on 2007-01-13
You will have to move the partitions.

Right now you have 

Kbuntu
free Space
Ubuntu

You need to 

Kubuntu
Ubuntu
free space

Then resize Ubuntu.

Probably easier to delete Ubuntu partition and re-install ??

---

### Post by ryantmer on 2007-01-14
I would do that, but I have TBird emails to think about... Well, either that or transfer them to my external drive... Can't, though, but that's a separate problem.

A'ight, I'll try moving it... how do I move the Ubuntu partition? Using GParted?

---

### Post by bodhi.zazen on 2007-01-14
Yes, but you must boot to the live CD.

You can use Ubuntu or download the gparted CD

HTH

---

### Post by ryantmer on 2007-01-14
I booted to the LiveCD and ran gparted... but I have no idea how to move the partition over O_o

I can delete them, and I added a bit of space onto my Ubuntu one, but I still have 3.91GB Kubuntu, 2.12GB Unallocated and 2.29GB Ubuntu. How do I move the Ubuntu partition?

---

### Post by bodhi.zazen on 2007-01-14
I am not sure about the Ubuntu Linve CD

On the Gparted Live CD you can copy / paste / move partitions ....

---

### Post by ryantmer on 2007-01-16
Tried that, but I'm now in a bigger hole. I updated the kernel, which involved about 630MB of downloaded files. Of course, that filled up my Ubuntu partition to have only 70MB of free space, and it can no longer boot from it. Bad, bad, bad. Any other ideas?

---

