---
title: "Regular System Freezes with Gutsy"
date: 2008-04-30
forum: General Help
---

### Post by psoplayer on 2008-04-30
I have liked everything I've seen in Gutsy so far, with no outstanding problems except for this.

Within minutes or hours of logging in, the entire system will freeze. For a moment the cursor will continue to move (extremely laggy though), but it quickly the entire system will become unresponsive to any input whatsoever. I can't 'Ctrl + Alt + Bksp' to restart the xserver, and I can't 'Ctrl + Alt + F1' to switch to a terminal. Sometimes the monitor will report 'No Input' shortly thereafter, and sometimes the screen will stay exactly as it froze indefinitely. I have left it overnight in that state and it remained as frozen as a popsicle. My only option is a hard reset.

I've had this happen to me in both the final release and in the release candidate before that. I haven't been able to figure out how to recreate it. Sometimes it will happen while I'm using VirtualBox, sometimes when I'm browsing with Firefox. I've even had it crash when all I was doing was writing in gedit and listening to rhythmbox. I haven't yet had it happen when I wasn't using the computer, so logging in and letting it sit in screen saver for 12 hours is fine. But, reliably, within several hours of use it *will* freeze up.

I read somewhere on the forum that it might be related to wireless support, so in the network manager I told it to disable wireless, but that hasn't changed a thing. This bug has forced me to remain in my Windows partition when I'd much rather be completing my C++ and Ruby programming assignments in a friendly environment.

I've got plenty of system specs (the whole system has run Ubuntu fine since 6.06, so I hope no problems here):
[LIST]
[*]Ubuntu 8.04 Desktop 64 bit
[*]AMD 4200+ (Overclocked a bit, but windows and Feisty are/were 100% stable with it, so I can't imagine this being a problem)
[*]1G Ram
[*]nVidia GeForce 8800 GT 256M (using nvidia-glx-new thanks to the automatic restricted drivers tool)
[*]Onboard Gbit Ethernet (nForce 4 MoBo)
[*]Gigabit 802.11g PCI wireless card (RT2500 chipset)
[*]160GB SATA HDD (Dual Booting w/Windows x64 Edition)
[*]IDE DVD+RW Drive
[*](any other relevant specs I might add?)
[/LIST]

My questions are:
[LIST]
[*]What's wrong?
[*]What log files need I be checking/posting?
[*]Where else should this have been posted instead?
[*]What can I do to help get this bug squashed so I (and others) can get back to using what should have been the best Ubuntu release yet?
[/LIST]

---

