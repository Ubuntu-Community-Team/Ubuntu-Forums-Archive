---
title: "Remove dual boot, 2 hd's"
date: 2006-11-17
forum: General Help
---

### Post by clsnyder on 2006-11-17
Hi

I have limited linux experience.
I have 2 internal hds, and have used dual boot system (ubuntu and win xp) for  1 - 2 yrs. On hd is ubuntu, and the other is win xp. I got a virus / trojan on the xp hard drive, and can't get rid of it (big suprise). Windows is nfts format on /dev/hda (200 gig). ubuntu is on /dev/hdb (250 gig). 

I want to reformat the windows hard drive and format it as FAT - I may eventually put win vista on it. Failing that, I would like to just run ubuntu only from the 250 gig hd, and take out the other hd.

I used sudo gedit grub menu.lst to make ubuntu the default boot (but left win xp on the list). However, even when I physically unplug the windows drive, and use the ubuntu as the master (no slave) I get a boot error. (grub 21). 

Any suggestions?

TIA

CLSnyder

---

### Post by louieb on 2006-11-17
I can't figure out what is worong. But if it were mine I would follow the link in my Signature and reinstall grub. BTW Error 21 is grub can't find the hard drive.

---

