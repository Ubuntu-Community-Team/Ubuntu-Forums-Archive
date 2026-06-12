---
title: "Xorg using 100% cpu when typing (and more) in a browser"
date: 2014-09-08
forum: General Help
---

### Post by andy92 on 2014-09-08
**Description of the problem:**


I've been stuck on this for months now (I'm not an expert), but my browser is almost unusable for typing or doing anything else with visuals. If I reboot, graphics are great for a few hours. When I do anything causing ridiculous visual slowdown, Xorg is at 100% CPU. All other visuals seem ok. Typing in any other application (Terminal, pidgin, etc.) works perfectly, vlc runs great.


I'm currently using chrome, but I've tried chromium and firefox and they also show this behavior after a few hours.


**Some specifics:**


I'm running Ubuntu 14.04.1 on 3.13.0-35-generic. I'm currently using the fglrx-updates driver from aptitude for my Radeon HD 7770 card, but I've tried fglrx, the amd-catalyst-13.12 driver from their website, and an older amd 12-6 driver from their website, but I get the same behavior.


Here is my Xorg.0.log, showing that there are no errors and that I'm loading the proprietary driver. [http://paste.ubuntu.com/8290901/](http://paste.ubuntu.com/8290901/) I have no errors in syslog or dmesg.


Any help is greatly appreciated, as it took quite a while just to type this message due to the Xorg slowness. Let me know if there are more specifics I can give which will be helpful.

---

### Post by andy92 on 2014-09-08
I should add that the chrome task manager does not show high cpu or memory usage anywhere, so the problem is related to Xorg.

---

### Post by alain-meirhaeghe on 2014-11-01
J got same problem:
amd radeon  hd7770/8760/ R7 250X
processor amd fx8320 8 cores.
I tri all driver: amd, open source...

---

### Post by scottstensland on 2015-02-04
The default super quick troubleshooting technique to many such graphics related issues is to reboot ubuntu from its Live CD install DVD - once booted up where its all stock then see if the issue continues to appear - too often its just fine  ;-)   .... so problem is unstable combination of subsequent installs ... knowing this my solution is to perform ALL file edits of stuff I wish to keep (code/documents/...) where its parent directory lives on Dropbox so I am free to reformat then reinstall ubuntu to start fresh ... knowing I have accessible notes on any hard to install steps for necessary libraries/applications/etc ...

---

