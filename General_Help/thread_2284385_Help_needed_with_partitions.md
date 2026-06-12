---
title: "Help needed with partitions"
date: 2015-06-29
forum: General Help
---

### Post by k0tt0n on 2015-06-29
I have recently removed the windows OS I had with my dual boot with Ubuntu on my laptop. It has a 500GB hard drive and now I seem to have partitions all over the place as you can see by the image. Essentially what I would like to have is one partition with Ubuntu of say 100GB and one empty one with the remaining 400BG or so to use for storage/back-up etc. (I know there needs to be small partitions for boot and linux-swap)

Help appreciated as I am relatively new to Ubuntu and Linux

Thanks


[[img]http://s6.postimg.org/a03o02d31/Screenshot_from_2015_06_29_15_39_48.jpg[/img]](http://postimg.org/image/a03o02d31/)

---

### Post by Bucky Ball on 2015-06-29
There needs to be no partition partition for boot. Purely voluntary and in most situations, best not having one. / and /swap is all you need, and some don't bother with /swap either (although best stick with it, 2Gb).

sda3 and sda4 can go by the looks of it. They appear to have nothing on them. Check. sda2? No idea what you have on that, but there's 31Gb of it. Check, backup if required. 

Best plan I'd say:

Boot from the live media> Try Ubuntu> launch Gparted;
Delete sda3, 4 and 2 (where required);

The rest depends on what you are going to do with sda2. Get back to us with a plan and let's see how we can make it work. Use Gparted for this, not Win software.

PS: If you are going to have your personal data stored on a partition other than the / partition, you don't need the / partition to be anywhere near 100Gb. 25b would be fine. If you set up right, you can expand later in the very unlikely situation you need to. You'd probably get away with 20Gb.

---

