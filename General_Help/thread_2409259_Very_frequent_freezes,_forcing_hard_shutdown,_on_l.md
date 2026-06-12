---
title: "Very frequent freezes, forcing hard shutdown, on laptop"
date: 2018-12-30
forum: General Help
---

### Post by gotchstyle on 2018-12-30
I have a Thinkpad T480 with a single SSD, Intel i5-8250U, 8 GB of RAM and the GeForce MX150 graphics card alongside the onboard Intel UHD Graphics 620. As far as I can tell, the issues below occur regardless of whether the Nvidia card is using Nouveau or nvidia-driver-390. Whether the computer is running on battery power or plugged in doesn't seem to make a difference, either.

I had Xubuntu 18.04.1 running like a dream on my Thinkpad for months. Still, I installed Solus (not in a separate partition, just a fresh install) to try that out and that's when the trouble described below started. I figured, no problem, I'll just go back to Ubuntu - no such luck; I now have Xubuntu 18.04.1 installed and the issues persist. I have also tried Ubuntu Budgie and Windows 10 on the Thinkpad; the freezing persisted with Ubuntu Budgie, and not with Windows.

My entire desktop freezes very frequently, seemingly at random. I might get 18 hours uptime before it happens, I might get 20 minutes. I usually get about an hour and a half. There are no performance issues before the freeze hits. The freezes usually, but not always, begin with my browser (Firefox or Chromium doesn't seem to make a difference) and then spread to the rest of the computer. Attempting to kill the browser process or do anything else in a terminal window just makes that freeze, too.

Sometimes I'll step away from the computer while it's working fine and come back to find it frozen with all the icons in my panel and whiskermenu replaced with blank rectangles.

Occasionally, but not often, the panel and everything else I have open will disappear entirely a few moments after everything freezes. Either way, the only way to recover is a hard shutdown and restart - IF whiskermenu opens properly, trying to logout, reboot or shut down only gives an error message like "Failed to execute child process 'xfce4-session-logout' (Input/output error)."

Please let me know if there's anything I should try, or what other information might be helpful in solving the problem - I'd really, really rather not have to use Windows just to avoid having to reboot six times a day. Thank you in advance for any help or advice!

---

### Post by clementc on 2018-12-31
Hi [**[COLOR=#000000]gotchstyle[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115159"),

First of all, can you please try to run a memory test on your computer to make sure that your 8Gb (I assume 2 sticks of 4Gb of RAM) are not faulty?

This page will guide you through the steps of running the memtest: [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

Please report back once the test has been completed.

---

### Post by gotchstyle on 2019-01-05
Thank you! I wasn't able to run the test as described there because I'm using UEFI, but I ran a test with MemTest86 from PassMark's website and the results turned up zero errors.

---

### Post by wildmanne39 on 2019-01-05
Until your issue is resolved, you can safely restart your computer if it freezes by holding down Alt+PrintScreen, and then press R-E-I-S-U-B slowly, one after the other. On some keyboards/systems, you need to use the AltGr key. 

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

REISUO will do a shutdown rather than a restart.

---

### Post by clementc on 2019-01-05
Hi [**[COLOR=#000000]gotchstyle[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115159"),

Thank you for running the test. Next time the issue occurs, can you please provide the last relevant entries from file /var/log/syslog

Also, pressing the following keys on your keyboard might let you access other tty interfaces when the main desktop one has crashed: Ctrl + Alt + F3 to F6

---

### Post by gotchstyle on 2019-01-06
Thanks to both of you!

REISUO had no effect when I tried it.

It just happened again, but checking /var/log/syslog, there are no entries within ten minutes of the time the freeze itself actually occurred.

---

### Post by clementc on 2019-01-06
Hi [**[COLOR=#000000]gotchstyle[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115159"),

Can you please check in the BIOS of your laptop what graphics card has been set as default (either dedicated, i.e. NVIDIA, or discrete, i.e. Intel) and swap them around just to see if this changes anything?

---

### Post by gotchstyle on 2019-01-06
That setting doesn't appear to be available in my BIOS (N24ET44W (1.19)).

---

### Post by clementc on 2019-01-06
Hi [**[COLOR=#000000]gotchstyle[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115159"),

This was worth a shot. What's odd with your issue is that you already tried different Ubuntu flavors and all of them seem to be affected. However, Windows is not.

One more thing I can think of would be to try upgrading/downgrading the kernel (preferably upgrading of course). You can use Ukuu to do so easily. [This page]("http://ubuntuhandbook.org/index.php/2017/02/ukuu-install-latest-kernels-ubuntu-linux-mint/") will help you do it.

However, please only attempt this if you feel comfortable doing so and after backing up all your files (just in case something goes wrong).

---

### Post by gotchstyle on 2019-01-06
Alright! I'll give that a try later. Thank you for all your help!

---

### Post by Impavidus on 2019-01-06
> **wildmanne39 said:**
> ... by holding down Alt+PrintScreen, and then ...

The actual key you have to hold is SysRq, which is on most keyboards accessed with alt+PrintScreen, but there are exceptions. On my laptop I have to use fn+delete.

---

### Post by pending... on 2019-01-06
Just as a test, you could try a more recent kernel. I'm actually running the 4.19.13 because I've had some freezing issues as well with the one released with Ubuntu 18.04.

---

