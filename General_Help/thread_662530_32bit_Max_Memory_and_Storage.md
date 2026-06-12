---
title: "32bit Max Memory and Storage"
date: 2008-01-09
forum: General Help
---

### Post by Saicho on 2008-01-09
Hi all,

I have a few questions about my Dell XPS 600
[http://support.dell.com/support/edocs/systems/xps600/en/SM/index.htm](http://support.dell.com/support/edocs/systems/xps600/en/SM/index.htm)

I apologize in advance if something that I mention is completely off base =)

I want to turn the xps600 into a server, most importantly for running Samba so Windows clients can connect (along with Apache, mySQL, mail, etc).

I have an Intel P4 3.4 , I believe this limits my choice to a 32 bit kernel.

I have 4 memory slots, but I believe I can only put in a max of 3GB of RAM if I use a 1GB swap. Should I use this, or can I just have 4GB of RAM without any swap? Is that even possible? If so, which is better and why? If the 4GB w/no swap is better, how would I go about installing Ubuntu like that?

The mobo has an NVIDIA nForce4 SATA RAID controller. I'd like to put a few hard drives in there in a RAID0 for the other computers to use for storage with Samba. I remember reading somewhere that a 32bit kernel is limited to 2TB stripes? Is that correct, or is that only for windows? I'd like to maximize the size of the RAID0 array.

Any answers, insight, or help is appreciated. Also, if you think I'm going about this all wrong and have a better idea or some suggestions please let me know. I'm not really looking to buy any hardware (like an expensive external PCIe raid card, or a new proc/mobo) short of a few more SATA hard drives.

Thanks in advance!

-Saicho

---

### Post by -grubby on 2008-01-09
about your memory question:
the actual physical amount of RAM you can use for 32-bit is 4GB. But some of that is taken up by various things so your system can function. I wouldn't even recommend a swapfile at all unless you're running some REALLY hardware (RAM) intensive programs or want to edit 5 GIMP images that are 3000x3000

---

