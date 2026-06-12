---
title: "Shrinking Volume"
date: 2008-06-08
forum: General Help
---

### Post by fredster001 on 2008-06-08
Hi,

I want to install Ubuntu so i can dual boot with windows Vista. I have vista installed and am attempting to "shrink" the hard drive volume using the disk manager. Then will install ubuntu on the other partition.

However, it says i can only shrink it 10 Gigs. Even though i have 50Gigs free. I've defragged, disk cleanuped but cant think of anything else. Anyone have any ideas to increase this, i think i want about 25 gigs for ubuntu.

Thanks,

Fredster001

---

### Post by Matthew Wiebelhaus on 2008-06-08
I've used vista for awhile but need xp for games. Depending on the size of your hard drive it will only let you shrink so much even if you have 50 gbs free. You can try shrinking and then shrinking again if it will let you but I don't know how much progress you will get. I'm not sure but I think during the installation progress in Ubuntu 8.04 it can shrink the Vista partition.

---

### Post by Monicker on 2008-06-08
When I got my new laptop, I noticed the same issue of Vista only letting me shrink the partition by a relatively small amount.  I just booted the live cd and used gparted to shrink it down to the size I wanted.

---

### Post by fredster001 on 2008-06-09
Hi,

I have tried shrinking it using the disk management on Vista, after that it wouldn't let me shrink it again.

So i downloaded, burned and booted GParted. I selected the disk, clicked resize, but it wouldn't let me drag the size smaller. All the boxes where you can type in how much to resize were faded and i couldn't enter anything into them.

Any help/other ideas?

Thanks

---

### Post by quill3033 on 2008-09-12
ok i'm really rusty on the terminology but the reason windows doesn't let you shrink any further is that it does its own version of a backup which i think is called system restore and needs that space in theory to do that. i couldn't shrink mine either beyond what it would let me do and ended up installing ubuntu (6.06) on only 17Gig partition which was fine. 
I've recently installed Hardy on my dad's computer - he has Windows XP- and again, we are restricted to 17 Gig on an 80Gig disk. You could turn off system restore and it might give you more space (I don't know I honestly haven't tried it) ... but it's not really a good idea because the system restore is useful in Windows if you install a program that stuffs up the system, you can go back in time and restore system to how it was working then. 
What I've done with my dad is buy him a Seagate drive of 120 Gib and installed Ubuntu there and we boot to external usb drive when he wants Ubuntu.

---

