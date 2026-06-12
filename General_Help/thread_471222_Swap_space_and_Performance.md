---
title: "Swap space and Performance"
date: 2007-06-11
forum: General Help
---

### Post by fragos on 2007-06-11
I've seen some assertions on swap space that seemed a bit off.  Hardly claiming to be the definitive expert on OS performance I have some good practical experience that has served me well with Linux.  I thought I'd share and perhaps gain a deeper understanding from other members of the Ubuntu community.

Swap space makes it possible for your machine to run as if it had more memory than it actually does -- the good part.  The act of swapping memory and disk slows down performance -- the bad part.  You can learn about your use of swap space with the "free" command which amongst other things tells you how much swap is being used.  You can use it to determine how much memory you need for optimal performance.  Going from 256MB to 512MB reduced my use of swap space and upgrading to 1GB rarely required the use of swap.  The more applications you keep open and the more open tabs you have in Firefox the more memory you'll use.

Once you've found an optimal memory size for performance there's still more you can do.  The kernel tries to keep a balance between available cache space and swap memory.  There is a "swappiness" parameter that it uses to weight that decision.  It's value can range between 0 and 100 with the default being 60.  100 keeps cache memory free by swapping often even if everything will fit in memory.  0 causes applications to shrink cache size to avoid swapping.  If you're running on a laptop and want to give your drives a chance to spin down and save battery power, use 20 or less.  The information I've found is more trend than scientific but it does give you basis of understanding and the ability to experiment a bit.  Believing that 100% is never an answer I chose a value of 10 and with 1GB of memory, I rarely find anything in swap space.  IMHO the total elimination of swap space may be risky.

You can change swappiness by doing the following:

sudo gedit /etc/sysctl.conf

Find the line containing "vm.swappiness=" and change the number to the one you'd like to try.  In my case "vm.swappiness=10".

---

### Post by dfreer on 2007-06-11
> **fragos said:**
> Swap space makes it possible for your machine to run as if it had more memory than it actually does -- the good part.  

Thanks for the info, I'm going to check out changing the "swappiness" parameter on my laptop now.

One thing though, although the above statement is well enough for a beginner, it isn't quite accurate. Swap doesn't "give" you more memory, it doesn't really make the machine run faster at all. Any time you use swap you lose speed as RAM is far faster than accessing the hard drive. It is also used for dumping the contents of your RAM when you hibernate your machine, which is why it needs to be at least 1.0 X the amount of RAM (preferably 1.5 x or even 2.0 x the amount, depending on who you ask), from what I understand of things.

Otherwise very good post!

---

### Post by timzak on 2007-06-11
fragos,

Your point about swap size only matters if one uses hibernate.  What advantage does hibernate hold over just turning your computer off?  I've never used it, so I'm curious.  I always shut my computer down when I go to work or bed, and let it go into suspend after 30 mins when it is on.  It comes out of suspend in about 5-10 seconds.

Another tip is location of swap file.  In a single drive system, the swap should be the first thing created on the hard drive (even before your OS partition).  Not only will it be on the fastest portion of your hard drive, but it will be physically close to your OS partition, so anytime it accesses the swap the hard drive head has less distance to travel (as opposed to putting the swap at the end of the drive, where it can't get any farther away from your OS files).  This equals faster performance (and as a byproduct, less wear and tear on the hard drive).

For multiple drive systems, place the swap as the first thing on the next-fastest hard drive that is on its own IDE channel (doesn't matter with SATA or SCSI as they can be accessed concurrently).  This will allow the swap to be accessed simultaneous to the OS with no delay for the read head to travel.

But as fragos said, swap is actually worst case scenario as even the fastest hard drive is slower than the slowest ram, so these tips are only to maximize performance when the swap can't help but be accessed.

---

### Post by fragos on 2007-06-11
> **timzak said:**
> fragos,

Your point about swap size only matters if one uses hibernate.  What advantage does hibernate hold over just turning your computer off?  I've never used it, so I'm curious.  I always shut my computer down when I go to work or bed, and let it go into suspend after 30 mins when it is on.  It comes out of suspend in about 5-10 seconds.

Another tip is location of swap file.  In a single drive system, the swap should be the first thing created on the hard drive (even before your OS partition).  Not only will it be on the fastest portion of your hard drive, but it will be physically close to your OS partition, so anytime it accesses the swap the hard drive head has less distance to travel (as opposed to putting the swap at the end of the drive, where it can't get any farther away from your OS files).  This equals faster performance (and as a byproduct, less wear and tear on the hard drive).

For multiple drive systems, place the swap as the first thing on the next-fastest hard drive that is on its own IDE channel (doesn't matter with SATA or SCSI as they can be accessed concurrently).  This will allow the swap to be accessed simultaneous to the OS with no delay for the read head to travel.

But as fragos said, swap is actually worst case scenario as even the fastest hard drive is slower than the slowest ram, so these tips are only to maximize performance when the swap can't help but be accessed.

It's true that swap space is used to hibernate but, that's not it's primary purpose.  Utilizing swap space while running definitely can effect performance.  This will occur as the applications you're running come closer to utilizing all of physical RAM.  You make some good points about the location of the swap partition.  Disk head seek time can have a major impact on performance.

---

