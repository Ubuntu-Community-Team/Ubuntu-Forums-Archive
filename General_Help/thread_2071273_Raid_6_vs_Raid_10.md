---
title: "Raid 6 vs Raid 10"
date: 2012-10-15
forum: General Help
---

### Post by rob0214 on 2012-10-15
Hi all,

I'm setting up a backup server (yes, I know raid isn't a backup).

I purchased 4 3TB drives, and I was thinking, is there any point to the performance boost Raid 10 gives over Raid 6?  All the accesses will be remote, so even with Gigabit ethernet, I'll max out at 125 MB/s (theoretical).  

With USB drives running at 480 MB/s (theoretical), it seems like it shouldn't be an issue running Raid 6 (and getting guaranteed recovery from 2 drives failing), since the network will be the bottleneck anyway.

Or, is the write performance of Raid 6 that horrible?

Actually, I think I figured out the answer, but IIRC you can't add disks to RAID 10 (which I might need down the line).

---

### Post by Lars Noodén on 2012-10-15
It's hard to find concrete data on the RAID levels.  If you have time to experiment you could set up both and test the throughput with a direct write using dd, seeing how long it take to write or read a few hundred MB.

---

### Post by swright300 on 2012-10-15
You might listen to a TechSNAP episode 24 over at Jupiter Broadcasting.  They go over several of the RAID options and you might get some of the information you are needing from that episode.


[http://www.jupiterbroadcasting.com/12307/ultimate-raid-techsnap-24/]("http://www.jupiterbroadcasting.com/12307/ultimate-raid-techsnap-24/")

---

### Post by lukeiamyourfather on 2012-10-15
In theory RAID 10 (or 01) will be substantially faster than RAID 6, especially if relying on software instead of a dedicated hardware RAID controller. Whether this matters for your application is up to you to decide. The advantage of RAID 6 is you can lose **any** two drives. With RAID 10 you can lose two drives **if** they are not part of the same stripe. So you get a little more robustness but you sacrifice performance.

---

### Post by dcstar on 2012-10-16
> **rob0214 said:**
> 
..........
With USB drives running at 480 MB/s (theoretical), it seems like it shouldn't be an issue running Raid 6 (and getting guaranteed recovery from 2 drives failing), since the network will be the bottleneck anyway.
..........

Why on earth do you think that the wire speed connecting storage devices is the bottleneck?

Mechanical hard drive limitations will always be the limiting factor in storage performance in virtually every circumstance, the wire speed of any interface only comes into play for transient traffic that can be served by a storage device's cache.

---

### Post by rob0214 on 2012-10-16
> **dcstar said:**
> Why on earth do you think that the wire speed connecting storage devices is the bottleneck?

Mechanical hard drive limitations will always be the limiting factor in storage performance in virtually every circumstance, the wire speed of any interface only comes into play for transient traffic that can be served by a storage device's cache.

Assuming 1 NIC to the server, how is it not a bottleneck?  Even with 3 NICs at Gigabit ethernet, it seems like it would still be a bottleneck.

---

### Post by lukeiamyourfather on 2012-10-16
> **dcstar said:**
> Why on earth do you think that the wire speed connecting storage devices is the bottleneck?

Mechanical hard drive limitations will always be the limiting factor in storage performance in virtually every circumstance, the wire speed of any interface only comes into play for transient traffic that can be served by a storage device's cache.

Modern hard disk are way faster than USB 2.0, that bandwidth number is megabits not megabytes. If you convert 480 megabits to megabytes you get 60 megabytes per second. Since that's the theoretical maximum you'll get even less in practice. Most modern drives are capable of 100+ megabytes per second.  So the interface makes a **huge** difference.

---

### Post by rob0214 on 2012-10-17
> **lukeiamyourfather said:**
> Modern hard disk are way faster than USB 2.0, that bandwidth number is megabits not megabytes. If you convert 480 megabits to megabytes you get 60 megabytes per second. Since that's the theoretical maximum you'll get even less in practice. Most modern drives are capable of 100+ megabytes per second.  So the interface makes a **huge** difference.

D'oh.

---

