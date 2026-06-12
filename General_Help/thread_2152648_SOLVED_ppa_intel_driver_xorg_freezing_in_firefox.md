---
title: "SOLVED: ppa intel driver xorg freezing in firefox"
date: 2013-06-08
forum: General Help
---

### Post by ajgreeny on 2013-06-08
Yesterday I did a normal upgrade of my system and a newer version of the xserver-xorg-video-intel driver package arrived (xserver-xorg-video-intel_2%3a2.21.9~precise~ppa1_amd64.deb) from the ppa that I've been using without any problems to date.  I carried on using the computer withouit logging out to get the new xsession and driver running.

This morning I have been having continual freezes of firefox, or that is all I have seen problems with.  The only new package on the machine or change made was to that xorg driver, so today I have downgraded to the previous driver version, also from the ppa (xserver-xorg-video-intel_2%3a2.21.8~precise~ppa1_amd64.deb) and it seems that all is well again.

Has anyone else seen a similar problem with this ppa xorg driver?  Any thoughts anyone?

I know that using the ppa is perhaps asking for trouble in Xubuntu 12.04, but this is the first sign of anything not working brilliantly using the ppa.  Certainly the sna acceleration it gives me makes things about 30 -40% faster using gtkperf to get figures, which go from 1.9 to 1.4, very fast for my system (spec below), I think.

EDIT:
After a few reboots and messing about with compton and the standard xfce4 compositor, the problem seems to have gone away, and I am now using the updated intel driver from the ppa with no sign of any freezing in FF.

EDIT 2:
I have just noticed that there was yet another update to the driver between my problem appearing and the solution then appearing almost straight away with xserver-xorg-video-intel_2%3a2.21.8~precise~[COLOR=#ff0000]ppa1[/COLOR]_amd64.deb being updated to [COLOR=#ff0000]ppa2[/COLOR], so perhaps it was tis second immediate upgrade that got rid of the problem.  I have not been able to find any changelog on the ppa site, but either way, the problem is gone.

So perhaps not one of those insoluble and strange problems that appeared and then suddenly disappeared again, as I originally thought.

Spec.  Xubuntu 12.04 64bit, ASUS P8H61-MX USB3 m/b with i5-3570K cpu, 8GB ram

---

