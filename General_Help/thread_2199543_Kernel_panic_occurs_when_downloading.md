---
title: "Kernel panic occurs when downloading"
date: 2014-01-14
forum: General Help
---

### Post by gyepesmernok on 2014-01-14
So the story in short: I bought a brand new PC, then successfully  installed 13.10. I was happy at the first 10 minutes then suddenly black  screen, and a kernel panic... then I tryed a 12.04 64bit LTS but it's the  same...
I can recreate the panic, by simply starting a download from a browser,  or trying to download updates. The first thing I notice that the wi-fi  turns off, and then bam.
  I've ran a memtest, but it didn't find any problems.
Tried to check  the kernel and system log, but all i see is 00/00/00/00-s with a red  background in the log files. 

  I've tried to search for a solution, but those problems didn't had these symptoms.

  You see, I use ubuntu for 5 years, and never ever had any problems, so I don't really know what is going under the hood...

  My PC's specs: 
Asrock B85M-HDS main board
Intel Core i5-4570 cpu 
Kingston HyperX PnP 2x4GB DDR3 1600MHz KHX1600C9D3P1K2/8G RAM 
Western Digital 1TB 64MB WD10EZEX HDD
and also, to connect to the internet I use a TP-Link TL-WN722N wi-fi stick.

  ohh and some part of the kernel panic: 

BUG: unable to handle kernel NULL pointer dereference at 00000000000005b8
IP:  [<ffffffff8153f73a>] handle_stopped_endpoint.isra.38+0x7/a0x280
Kernel panic - not syncing: Fatal exception in interrupt
drm_kms_helper: panic occured, switching back to text console

Any idea what can cause this, and how can I fix it? 
Every comment is appreciated!

---

### Post by newbie-user on 2014-01-15
Have you tried installing a newer kernel? The latest is 3.12.7 from kernel.org. Newer hardware isn't always supported in the default kernels used by various distributions.

---

### Post by gyepesmernok on 2014-01-16
Great idea! I will definitely try it out, as soon as I can get a wired connection! After that I'll write down what happened!
Thank you!

---

