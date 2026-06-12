---
title: "Flash crashes when going full-screen in Firefox"
date: 2017-08-31
forum: General Help
---

### Post by SeijiSensei on 2017-08-31
This problem arose recently either via updating Firefox to 55.0.2 or updating Flash to 26.0.0.151.

Clicking the full-screen button on Flash videos like [this](http://www.crunchyroll.com/sakura-quest/episode-21-the-pixie-in-the-town-of-ice-741521) crashes the plugin. Right-clicking on the video (to turn off HW acceleration) also crashes the plugin.

 I've tried all the usual solutions, like preloading libGL.so.1 and creating an /etc/adobe/mms.cfg file with the line EnableLinuxHWVideoDecode=0.  None of them work.

The same plugin (from the adobe-flashplugin package) works fine with Chromium, just not Firefox.  I looked at the suggested solutions at both Mozilla and Adobe, but none seem to fix this problem.  Has anyone else encountered this bug?

Update:  The crash occurs on both my machine with an NVIDIA adapter, and one with an AMD/ATI adapter.

---

### Post by ajgreeny on 2017-08-31
No problems here with Xubuntu 16.04 running the 4.4.0-93 kernel on 64bit system.

What version of Ubuntu are you using; still Kubuntu-14.04 as shown in your info?
What hardware are you using?

---

### Post by SeijiSensei on 2017-08-31
Yes, still running Kubuntu 14.04.  As I said this happens on both systems I use, an HP notebook with AMD graphics and an Asus i5 desktop with an NVIDIA 750 GT.  Same result on both.  They both have 8 GB of memory and swap files.

The laptop is running 3.13.0-58-generic; the desktop runs 4.4.0-66-generic.

---

### Post by pasogo91 on 2017-10-17
Same problem Here. Ubuntu 14.04 with KDE desktop installed, Firefox 55  and 56 (54 and below does NOT have this problem). Intel HD graphic card.

---

### Post by pasogo91 on 2017-12-01
Seems to be fixed with Firefox 57.

---

