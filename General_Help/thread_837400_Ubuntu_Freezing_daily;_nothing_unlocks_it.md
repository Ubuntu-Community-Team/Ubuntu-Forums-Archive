---
title: "Ubuntu Freezing daily; nothing unlocks it"
date: 2008-06-22
forum: General Help
---

### Post by kevin1780 on 2008-06-22
I'm running 8.04 on a Dell desktop with 2.0 GiB of RAM and a 2.8 GHz Pentium Dual-Core processor. I've been elated with the switch to Linux, but I am plagued by these (seemingly) random system crashes where the screen is frozen (including mouse pointer).

Everything I've tried has failed, to include the _Alt+Printscreen_+R+E+I+S+U+B technique, CTRL+ALT+BACKSPACE, even _Alt+Printscreen_+O doesn't work. I inevitably have to hit the power switch.

All I can say is that I'm somewhat certain that Firefox (v.3.0) is usually running when this happens - not sure if this has anything to do with it.

I checked the log, and the last line before the restart said:
[INDENT]npviewer.bin[9181]: segfault at f5aea030 rip f78de540 rsp 55b8681c error 4[/INDENT]

Any advice? My wife is threatening to put Windows back on this machine unless I figure this out!  Thanks.

---

### Post by fsmithred on 2008-06-22
There may be more elegant solutions, but 'sudo apt-get remove powernowd' would probably fix it. You'll lose cpu frequency scaling, which shouldn't make any difference unless you're worried about laptop battery life.

---

### Post by danwood76 on 2008-06-22
npviewer is used when you are running 64-bit firefox and allows you to run the 32 bit flash plugin.
It shouldnt crash your whole system though, just firefox.

Have you got all the latest updates etc installed?
I know npviewer used to crash regularly on my initial hardy install but it seems fine now with the latest version of firefox and npviewer.

What graphics card and drivers are you using?
Random lockups have been reported with certain nvidia cards and the proprietry drivers, I think the fix is to update to the latest nvidia drivers from their site.

---

### Post by kevin1780 on 2008-06-22
I do have a nvidia driver. What's the easiest way to update?

From nvidia's site: "We're sorry, the NVIDIA Smart Scan does not support your system at this time."

---

