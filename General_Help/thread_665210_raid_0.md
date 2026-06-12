---
title: "raid 0"
date: 2008-01-12
forum: General Help
---

### Post by go_beep_yourself on 2008-01-12
I'm confused by what some people have said about raid 0. Does raid 0 cause a drive to physically damage sooner than it would normally would (decrease lifespan)?

---

### Post by dcstar on 2008-01-12
> **go_beep_yourself said:**
> I'm confused by what some people have said about raid 0. Does raid 0 cause a drive to physically damage sooner than it would normally would (decrease lifespan)?

All hard drives have a finite lifespan, by using two physical drives as one logical drive you effectively half the MTBF (Mean Time Between Failure) for your single logical drive, so for the sake of adding the drive capacities you will lose all of your data if either drive fails.

To me (in these days of massive drive capacity for low cost) RAID-0 is insanity, if you need more storage space then create a new partition on a separate drive so at least you won't lose everything if one of your drives fail.

I don't really know how RAID-0 qualifies to have the "Redundant" in RAID, there is no redundancy and in fact it is the opposite of redundancy (unlike all other RAID types).

---

### Post by fjgaude on 2008-01-12
The only valid reason someone uses raid0 is to increase the disk I/O throughput. The disk stripping results in parallel reading, writing which increase speed by about 95%. Relibality is cut in half. Some use raid10 using four or more drives to have redundancy and one-drive failure protection.

---

### Post by go_beep_yourself on 2008-01-12
> **fjgaude said:**
> The only valid reason someone uses raid0 is to increase the disk I/O throughput. The disk stripping results in parallel reading, writing which increase speed by about 95%. Relibality is cut in half. Some use raid10 using four or more drives to have redundancy and one-drive failure protection.

Do you mean raid1+0 or raid10? I really don't understand what raid1+0 is though I've seen it. I guess it is a combination of raid levels, but how does it work, and how is it different from raid0+1? Why would raid10 be used instead of raid5? From what you were telling me, they sound the same, but they must be different.

---

### Post by fjgaude on 2008-01-12
raid10 (same as raid1+0) is redundant strip. A good site for description:

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

raid5 is different, parity, and the like, better size for the number of drives used in the array.

---

