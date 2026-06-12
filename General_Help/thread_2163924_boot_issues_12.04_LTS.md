---
title: "boot issues 12.04 LTS"
date: 2013-07-20
forum: General Help
---

### Post by matamoscas on 2013-07-20
Hi,

I have a multi-OS (Win7, OS X, Ubuntu 12) system, setup on my Macbook Pro.

I have had it setup like this for years, and had various (often self-inflicted) issues=) But, for the most part, everything works seamlessly =)

But, lately, I have been having problems booting into Ubuntu. 

It usually shows a purple screen, then a mostly black/purple, few color bars, screen and doesn't move. It doesn't matter what keys I pushed, it hangs here.

About 20-25% of the time, it boots into Ubuntu normally, as expected.

The rest of the time, I just have to restart, and hope I can log in.

Any one able to offer any tips? Suggestions? Where can I find the boot log, or show what is hanging me? 

Thanks,
matt

---

### Post by DeathByDenim on 2013-07-20
Boot logs are stored in /var/log. The ones of interest would be dmesg.0, which should the boot process for the previous boot and syslog, which is a log of almost everything that went on. Hopefully you should be able to get some clues from that.

---

### Post by matamoscas on 2013-07-20
thanks for the tip. I was able to see a few errors, and perhaps it was related to my network manager. Strangely, still can't pin down why it boots sometimes (sometimes back to back!) and then other times it doesn't boot at all. Will have to keep an eye on it =) (as if I have a choice). Will just boot into the older working version for now.

---

