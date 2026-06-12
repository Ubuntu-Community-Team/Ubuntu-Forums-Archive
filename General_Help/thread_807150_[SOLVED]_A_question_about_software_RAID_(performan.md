---
title: "[SOLVED] A question about software RAID (performance)"
date: 2008-05-25
forum: General Help
---

### Post by panayk on 2008-05-25
Hi!

From what I've read, I understand that RAID level 1 on two identical disks offers not only disk failure protection, but also better performance compared to using one of disks alone.

I want to use mdadm to create a RAID 1 array, in which to store a large volume of valuable documents.
I have only two disks with enough free space.
The first one is an 80GiB PATA Western Digital, and the other one is a 250GiB external USB drive.
So I am thinking of using the ATA disk as a single partition and creating an equally sized partition on the USB disk.
I also have a third ATA disk, containing the root and /home partitions.

My question is: will the resulting RAID partition be slower or faster that an ATA disk?
Should I transfer /home there or leave it on the internal disk, since I want to get good performance from it and it does not contain very important data?

Thanks in advance for any insight!

---

### Post by shifty_powers on 2008-05-25
right, well firstly, to use raid, you new two disks of identical sizes.

so using an 80gig and a 250 gig is out of the question ;)

sorry...

---

### Post by srt4play on 2008-05-25
> **shifty_powers said:**
> right, well firstly, to use raid, you new two disks of identical sizes.

so using an 80gig and a 250 gig is out of the question ;)

sorry...

Not true, although it is more common to use two full disks of identical sizes, two partitions of identical sizes will work just fine.

---

### Post by panayk on 2008-05-25
Wait, can't I use two partitions of (roughly) the same size?
Like the first disk plus 80Gib from the second, leaving the rest for something else?

EDIT:Sorry, slow posting. Anyway, I found this:
> C.7.3. RAID-1

Characteristics:

    * Consists of two or more disks to provide a two-way or N-way mirrored MD device.
    * Writes result in writing identical data to all active disks in the array.
    * Reads can be performed on any active disk of the array.
    * Data is intact as long as there is at least one "good" active disk in the array.
    * **The disks should be the same size. If they are different sizes, the size of the RAID-1 array is determined by the smallest disk.** 

Advantages:

    * 100% redundancy of data.
    * Under certain circumstances, a RAID-1 array can sustain multiple simultaneous disk failures.
    * **Kernel MD code provides good read-balancing algorithm.**
    * No parity calculation overhead is involved. 

Disadvantages:

    * **Write performance is often worse than on a single device.**

So that answers my question, read performance may be better, but write performance isn't.

---

