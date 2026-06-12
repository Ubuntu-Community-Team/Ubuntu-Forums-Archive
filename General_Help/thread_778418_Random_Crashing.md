---
title: "Random Crashing"
date: 2008-05-02
forum: General Help
---

### Post by Wish4Me on 2008-05-02
Im having problems. I installed Ubuntu 8.04 but I get random Crashing. The screen goes white and im unable to identify the problem. I tried both x84_64 and the x86 versions. Its perplexing. I also tried Fedora 8 KDE(3.5) LIVE and there was no crashing but in the Fedora 9 GNOME there was crashing(blue screen)on the live. I bring up Fedora because I wasnt sure if it was Ubuntu or linux. There wasnt any problems with the KDE so maybe it is a problem with Gnome. I will try a live of Kubuntu KDE(4.0) tomorrow. Any ideas?

Specs:
AMD Athlon 64
Radeon Xpress 200 Chipset

That is pretty much it.

---

### Post by czechman86 on 2008-05-02
> **Wish4Me said:**
> Im having problems. I installed Ubuntu 8.04 but I get random Crashing. The screen goes white and im unable to identify the problem. I tried both x84_64 and the x86 versions. Its perplexing. I also tried Fedora 8 KDE(3.5) LIVE and there was no crashing but in the Fedora 9 GNOME there was crashing(blue screen)on the live. I bring up Fedora because I wasnt sure if it was Ubuntu or linux. There wasnt any problems with the KDE so maybe it is a problem with Gnome. I will try a live of Kubuntu KDE(4.0) tomorrow. Any ideas?

Specs:
AMD Athlon 64
Radeon Xpress 200 Chipset

That is pretty much it.

i had similar problems on a different computer and it was related to my memory. i would recommend running a memtest. if you have some fails, then you know what the problem is. good luck!

---

### Post by Wish4Me on 2008-05-02
I ran the memtest overnight. In ten tests no errors. ALso, I ran windows and no crashes. It has to do with linux.

---

### Post by czechman86 on 2008-05-03
> **Wish4Me said:**
> I ran the memtest overnight. In ten tests no errors. ALso, I ran windows and no crashes. It has to do with linux.

i am really sorry to say, but this is above my level now. i have heard of some people having problems with gnome. i read a forum a while back where a guy was having just horrible problems and he switched to xfce and everything was fine. good luck! sorry i cant really help out anymore.

---

### Post by hardyn on 2008-05-03
there are a growing number of reports of this... a LOOOONG bug report has been started, you can find the link on this forum somewhere i don't have it handy starts with bug number 2*******.

They (community) cannot find a pattern of the crashing just yet, but may be related to disk or network or acpi activity.  read the launch pad notes on filing kernel bugs, include your logs, and be very specific about hardware, network chips, motherboard chips, etc.  the better the reports are the fast a pattern can be determined

---

### Post by Wish4Me on 2008-05-03
Its very strange because the Fedora 8 Live Disc KDE3.5 is completely stable for me. Ive ran it randomly for awhile with no issues. I installed kubuntu with KDE4 and complete system crash (white screen with a small black bar this time) within the first 10 minutes. Same for Ubuntu and the Fedora 9 Gnome beta I tried. Its unlrelated to any program but apears to be graphical. Maybe Compiz.

---

### Post by hardyn on 2008-05-03
There has been some suspician that is may be related to the 2.6.24/25 kernels from the trunk, not related to ubuntu patches; or compiz, or the sata drivers, etc... they don't know at this point.  but depending on the kernel verions of the other distros you have tried, this may still be consistant with that error.

---

### Post by Wish4Me on 2008-05-03
I cant find the bug post. I looked for it but it apears to be missing.

---

### Post by Wish4Me on 2008-05-05
:/ Ah trying to figure this out is quite annoying. On I go!

---

