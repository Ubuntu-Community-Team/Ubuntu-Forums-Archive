---
title: "Xorg- growing in memory - from 3% to 13% in 24hours !"
date: 2007-03-12
forum: General Help
---

### Post by brucenico on 2007-03-12
Hi all,
I've noticed that Xorg si always growing in memory, and I don't understand why... So, here are the traces on 24h to see this evolution. The only actions on the PC with ubuntu Edgy were a few web search and mails checks. I didn't work with this computer during those 24h.

************************
1- before the test. My computer was too slow after a few days of use: Xorg was consuming 80% of my memory (RAM 1Go / Swap 2Go). That was the result with "top". I used "xrestop" and I saw that swiftfox (I'm using an AMD64) was consuming 70%. So I closed all the swiftfox windows. Xrestop said that Xorg was now at 20%. But... with top, Xorg was still at 70% !!! ====> X reboot

************************
2- begin of the test

19:24
==> Xorg 3% of memory
==> swiftfox 4.9%
==> For whole ubuntu : 243Mo

20:46
==> Xorg: 4.1%
==> swiftfox 5.6%
==> For whole ubuntu : 262Mo

23:15
==> Xorg: 10.3%
==> swiftfox 6.3%
==> For whole ubuntu : 363Mo

The day after, 9:50 (AM) (so: one night without action on the PC)
==> Xorg: 9.8%
==> swiftfox 6.3%
==> For whole ubuntu : 397Mo

20:15
==> Xorg: 13%
==> swiftfox 6.7%
==> 448Mo au total en charge mémoire

(just before this last test, I've check my mails with a webmail in swiftfox, here the traces with xrestop :
With the active webmail
2c00000   323   67    1  264  136    62893K     13K  62906K  5008 Webmail
After closing the webmail and another swiftfox window:
2c00000   259   66    1  211  128    11063K     11K  11075K  5008 Forum
)

**********************************************************************************
**********************************************************************************
**********************************************************************************
Conclusion:
Swiftfox seems to ask ressources to X, and after closing its windows those ressources seem to be free (xrestop, the last test). BUT, with "top", X stay at the same level in memory ?!?!

[B]==> In 24hours, Xorg goes from 3% to 13% in memory, without working on the pc, just with a small use of swiftfox (and this last: from 4% to 6.7%) ! For the whole Ubuntu system, it goes from 243Mo to 448Mo !
[/B]

==> Why ?????? :confused:

---

### Post by brucenico on 2007-03-13
No idea for this memory leak ? :(

---

### Post by rcoconnell on 2007-03-30
I may have a similar problem.  I'm running xubuntu on an old Ramline touchscreen computer, with 128 MB of RAM and 128 MB of swap.  Most of the time it just acts as a picture frame, running xscreensaver (with the opengl slideshow plugin that comes with xscreensaver).  For several weeks I've been finding the computer unresponsive if I leave it running for several hours -- no programs running besides xscreensaver, mind you.  The screen would go blank, but not turn off.  I caught it in the act recently, and heard the hard drive grinding.  I was able to ssh in, though it took several minutes for the computer to repsond.  Running top revealed that my physical memory and swap were full, with xorg responsible for about 80% of that.

Poking around, I found this bug report: [https://launchpad.net/ubuntu/+source/xorg-server/+bug/92882](https://launchpad.net/ubuntu/+source/xorg-server/+bug/92882)

Can somebody who knows what they're talking about tell me if my diagnosis sounds reasonable?

-ross

---

