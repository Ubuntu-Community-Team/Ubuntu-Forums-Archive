---
title: "Interesting info re: Swap File vs. Swap Partition"
date: 2007-12-21
forum: General Help
---

### Post by sd_smoker on 2007-12-21
I'm new here and have been spending the last few days researching various topics relating to setting up Ubuntu to dual-boot with Windows. Not sure why, but I've always felt that it was best to have the fewest number of partitions one can get away with. I was thinking (1) Windows (2) /home (which would also act as the shared data repository for both OS'es) and (3) everything else. What I'm getting to is that I think I'm going to go against the flow and set up a swap file instead of a swap partition. The interesting info I referred to in the title is this from the Paging entry in Wikipedia:

> However, with the 2.6 Linux kernel, **swap files are just as fast[6] as swap partitions. The administrative flexibility of swap files outweighs that of partitions; since modern high capacity hard drives can remap physical sectors, no partition is guaranteed to be contiguous**.

Edit: [Link]("http://en.wikipedia.org/wiki/Paging#Swapping_in_Linux")

I haven't seen this specific tidbit discussed in the forums so I thought I would share. Any thoughts?

---

### Post by dcstar on 2007-12-22
> **sd_smoker said:**
> I'm new here and have been spending the last few days researching various topics relating to setting up Ubuntu to dual-boot with Windows. Not sure why, but I've always felt that it was best to have the fewest number of partitions one can get away with. I was thinking (1) Windows (2) /home (which would also act as the shared data repository for both OS'es) and (3) everything else. What I'm getting to is that I think I'm going to go against the flow and set up a swap file instead of a swap partition. The interesting info I referred to in the title is this from the Paging entry in Wikipedia:



Edit: [Link]("http://en.wikipedia.org/wiki/Paging#Swapping_in_Linux")

I haven't seen this specific tidbit discussed in the forums so I thought I would share. Any thoughts?

If you have enough RAM then you may not even need swap space.

Anyway, speed is less of an issue than filesystem reliability, if swap is on a separate partition then any writes to it will have no effect on your data partitions, if your swap was in a data partition then there is more potential for corruption in the event of power failure etc.

---

### Post by LaRoza on 2007-12-22
I don't see a reason to use a file, and several for a partition. If you dualboot (or multiboot) with another Linux, you can use the same partition for swap, for one.

---

