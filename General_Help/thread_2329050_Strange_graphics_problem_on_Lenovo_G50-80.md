---
title: "Strange graphics problem on Lenovo G50-80"
date: 2016-06-27
forum: General Help
---

### Post by amhndu on 2016-06-27
Sometimes the following graphics glitch is triggered where the screen starts moving/rotating rapidly: [https://i.imgur.com/u6j5auo.gif](https://i.imgur.com/u6j5auo.gif) (gedit on LXDE).
This is triggered semi-randomly while using specific apps like Kate, gEdit, gVim, leafpad, embedded console inside Dolphin, KDevelop and rarely with Konsole.
Also triggered for a few split-seconds when I move the mouse when in fullscreen mode in VLC but stabilises quickly. However, everything is stable when I just use Chrome or Firefox, LXTerminal, Clementine and Code::Blocks, even for hours.

Whenever this is triggered, it can mostly be fixed when I switch to desktop or Chrome or a different app while closing the trigger-er app. Sometimes (rarely) the screen becomes completely black after a while, with key-presses and mouse movements revealing the screen for split-seconds which allows me to properly shutdown/restart the laptop.
I've tried to Google the problem with no results, I'm not even sure what to search for.

Some more details:
OS: Lubuntu 16.04 (Kernel 4.4.0-22-generic)
Current DE: KDE 5.5.5 installed with kubuntu-desktop package (with no install recommends to save bandwidth). This problem also occurred with LXDE (thus openbox), so nothing to do with the DE.
Laptop: Lenovo G50-80 with integrated graphics chip (Broadwell-U Integrated Graphics)

Please tell me what more information I can provide.

I don't have Windows either to test the graphics stability there.
This is extremely inconvenient deterring me from using specific apps, I'd really like this solved.

---

### Post by amhndu on 2016-06-27
Bump. (Sorry, it's been 10 hours, had to do this)

---

### Post by amhndu on 2016-06-29
Update: I did an apt upgrade which included kernel updates, graphics seem more stable, however when the glitch is triggered is becomes impossible to clear it without a reboot

---

### Post by amhndu on 2016-07-13
Installing 'xserver-xorg-video-intel' fixes the problem.

---

