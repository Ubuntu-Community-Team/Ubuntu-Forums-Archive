---
title: "SIGBART in () raise"
date: 2013-08-02
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-08-02
After a clean install of Ubuntu ver. 12.04 LTS (Precise Pangolin) in June of 2013, I installed Brother printer drivers for my MFC-240c (inkjet, fax, copy scan) printer.

Shortly after that, every time I run a print job, an apport error wants to send an error report to Launchpad. This in and of itself is not a problem, as the printer does: print, copy, scan without error. The fax doesn't work and has been reported to Brother. I have uninstalled and re-installed the drivers to no change in the problem. Launchpad thinks this is the [bug]("https://bugs.launchpad.net/ubuntu/+source/brother-cups-wrapper-common/+bug/863450").

I post about this as I am now receiving SIGBART in raise() errors from two more applications:

MythTV

Network Manager

and reiterating: the Brother fax - that is called from the terminal with BRFAX. A dialpad appears on the screen, a number can be "dialed" by clicking the numbered radio buttons, but when FAX is clicked, nothing happens. Came onscreen for a while, but calling it as I type this post, nothing comes up. Nor another apport, either.

Further afield, memcoder is giving some users a SIGBART in raise() message, too. So to for Nautilus. So to for colord. So to for Totem.

How serious is a SIGBART in raise()? Should I un-install the Brother drivers and wait for a fix?

---

