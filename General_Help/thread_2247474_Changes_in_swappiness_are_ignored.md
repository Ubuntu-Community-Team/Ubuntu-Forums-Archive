---
title: "Changes in swappiness are ignored?"
date: 2014-10-08
forum: General Help
---

### Post by john294 on 2014-10-08
Hi, 
I have a workstation with about 80 GB Ram, but only a small portion of SWAP-space on my SSD disk. 
I am currently using Ubuntu 14.04.
To further minimize the usage of the SSD as SWAP, i have changed the swappiness setting as per the instructions [here]("http://askubuntu.com/questions/103915/how-do-i-configure-swappiness").

Ihave changed the swappiness value to 5, meaning that basically the swap space should only be used if 95% of the physical memory is full (Or isn't his correct?).

However, when i check the memory consumption using the gnome-system-monitor, I see that, even though only 2% of my RAM is currently in use, 309 Mb of SWAP space is also being used. How can that be? Is my system currently ignoring my swappiness settings?

---

### Post by ibjsb4 on 2014-10-08
There are certain files (of fixed size) that use swap as storage.  You have options:

1)  Set swap to zero.
     swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible 
     [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

2)  Turn swap off or change priorities.
     [https://help.ubuntu.com/community/SwapFaq#What_is_the_priority_of_swap_containers.3F](https://help.ubuntu.com/community/SwapFaq#What_is_the_priority_of_swap_containers.3F)

On my laptop with 4G of ram, I use #1.  On my desktop (24G ram), I do not use swap at all (no swap partition).

I believe you have a typo.  80G should of been 8G of ram.  I would be tempted to turn swap off and run it like that for a while.

---

