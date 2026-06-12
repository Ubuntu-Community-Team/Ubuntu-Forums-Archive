---
title: "logging out gives black screen and maybe a system freeze"
date: 2007-11-14
forum: General Help
---

### Post by Zerol on 2007-11-14
When I log out, or come back from Hibernate/Suspend mode I wont be able to do anything with my laptop since I just get a black screen and it responds to nothing.

I am running Feisty Fawn 7.04 and I've got an AMD Turion64 MT processor. My graphics card is a ATI Radeon Xpress 200M.

Now I' ve found 2 or 3 topics also consulting this problem but they didnt solve mine.
[https://bugs.launchpad.net/ubuntu/+s....1/+bug/107115](https://bugs.launchpad.net/ubuntu/+s....1/+bug/107115)
This Launchpad report his fix still gives me a black screen.

Now I also found this post;

have had a similar problem, which is now fixed, but I didn't find the solution anywhere on this forum so I'll post it here. It's pretty simple, but being a complete linux newb it took me ages to discover it.

My onboard graphics:
Code:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I don't use any special effects or graphics acceleration, but still I was getting a blank screen when I logged out and when I ctrl+alt+f7, although I could move to a ctrl+alt+f1, then ctrl+alt+backspace and tty1 would appear. I would also get no splash screen when shutting down, even though I would when booting up.

I fixed it using "dpkg-reconfigure xserver-xorg", the key being to change the video driver from vesa to "i810". Here are the specific /etc/X11/xorg.conf settings:

Code:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection



But I have no idea how to get detailed information about my on-board Graphic card and I also dont know how to proceed with the steps he just recalls since I am still a newbie. I also dont know if that solution will help me.

Hope somebody can help me with this because it really sucks.

---

