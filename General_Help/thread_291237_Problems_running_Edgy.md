---
title: "Problems running Edgy"
date: 2006-11-02
forum: General Help
---

### Post by s26c.sayan on 2006-11-02
I have clean-intsalled Ubuntu Edgy on my system using the alternate install Cd. My video card is an integrated Intel 82845G, so i chose the i810 video driver while configuring X. Later, I gave the appropriate sync. ranges for my monitor (Horiz : 30-54 KHz & Vert. : 50-160 Hz). however, when I tried to start x, nothing came up except a black screen. so I decided to do a 'sudo dpkg-reconfigure xserver-xorg' again, where I chose VESA as my driver. Now I can start X, but it is restricted to a poor display of 640 X 480. Is this the maximum I can get with VESA and my card? Or can I somehow get a better resolution of 1024 X 768.

Further, I had also installed Mepis 6.0 and Debian sarge on the same machine (just for testing) . I chose i810 as my driver in both cases. Debian (which uses xfree86 instead of xorg as xserver) worked absolutely fine.I could get the desired 1024 X 768 resoultion after a little reconfiguration.
As for Mepis,while booting, I had to give a boot option of 'xdrvr=vesa' and that too worked fine with desired resolution.

So what's wrong with Ubuntu? and what is the solution?
[B][U]
EDIT[/U][/B]
I seem to have found a 'strange' solution to my problem. If I switch off my monitor right after I choose Ubuntu Edgy from GRUB menu, and switch it on after 2-3 min when the gdm login screen is ready, everything works just fine!!
This is a solution allright, but does not satisfy my curiosity as to why I have to do that!!!

---

