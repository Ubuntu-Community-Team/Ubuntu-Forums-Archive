---
title: "nVidia dual screen display port daisy-chain MST troubles"
date: 2015-11-02
forum: General Help
---

### Post by mave-m on 2015-11-02
I will start with a short explanation of the trouble in ran into. I have a dual screen setup, the primary monitor is connected to my graphics card using displayport, the secondary monitor is daisy-chained from the first monitor. The primary monitor works as expected without any problems, the secondary monitor stays in power saving mode. That said i will give you some specs, logs, numbers and how i can reproduce the problem.

My graphics card is a nVidia Geforce GTX 970 with two Dell Ultrasharp U2515H monitors connected. Both monitors are set to displayport 1.2 mode to make daisy-chaining possible through MST. Therein lies the problem i guess, MST support in the Linux kernel is added not that long ago. As far as i know and found in the forums Ubuntu 15.04 was the first version using a kernel that has MST support. So i tried my luck with the latest Ubuntu 15.10, after installation i updated Ubuntu and installed the latest nVidia graphics (nvidia-355) driver using the [Proprietary GPU Drivers PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"). On reboot my primary monitor was enabled and the secondary still in power saving mode. I opened the display settings and saw that both monitors were detected. After that i checked the output of xrandr and saw that the resolution included both monitors 5120x1440, when i move my mouse cursor to the secondary monitor it disappears off my primary screen telling me that my desktop is spanned over both monitors. It&#347; just that my secondary monitor won´t come out of power saving mode...

Then my phone rang and i left the computer, when i came back the screensaver kicked in. So i went to unlock my computer when all of a sudden both monitors came out of power saving mode. Yes, my dual screen setup is working! That lasted until the next reboot and the secondary monitor stayed in power save mode again. The first thing i thought was to lower the inactivity timer to 1 minute and wait for the screensaver to kick in again, when it did i moved my mouse and again both monitors came out of power save mode. So yes i can reproduce it and only in Ubuntu 15.10, the trick didn´t work in other flavors like Ubuntu MATE or previous versions of Ubuntu. The problem is that i don´t know if this is a Linux kernel, Ubuntu or nVidia driver bug. I didn´t create a xorg.conf file as i was told that it should run out of the box on auto-detect these days, and it does (sort of). Ofcourse i tried if it makes a difference creating one using nividia-xconfig but it didn´t. Anyone have an idea on this?

Xrandr output: [http://pastebin.com/GPj5Jb51](http://pastebin.com/GPj5Jb51)
Xorg.0.log: [http://pastebin.com/mzyBTPVD](http://pastebin.com/mzyBTPVD)

If i need to provide more information please tell me.

---

### Post by fabbari on 2015-11-17
Hi there --

  having the same problem with my setup (Two dell monitors daisy chained out of a NVidia 980M). If I setup the monitors as separate screens all the monitors work fine, when I use them on the same screen one or more of the daisy chained ones will not switch on, even if they ware detected.

  I noticed that the monitors would all turn on when the screens came back out of the sleep mode, so for the moment I came up with this: I have a desktop shortcut to the following command: ```
xset dpms force off
``` - the command will switch off all the monitors - as if they were going to sleep, then - when you move the  mouse - all the monitors will come back up at the same time --- better than waiting one minute, but still an issue.

  I'm opening a thread on the NVidia Linux developers forum to see if there are any suggestions on how to permanently solve the issue.

  cheers,

 Fabio

---

### Post by mave-m on 2015-12-28
> **fabbari said:**
> Hi there --

  having the same problem with my setup (Two dell monitors daisy chained out of a NVidia 980M). If I setup the monitors as separate screens all the monitors work fine, when I use them on the same screen one or more of the daisy chained ones will not switch on, even if they ware detected.

  I noticed that the monitors would all turn on when the screens came back out of the sleep mode, so for the moment I came up with this: I have a desktop shortcut to the following command: ```
xset dpms force off
``` - the command will switch off all the monitors - as if they were going to sleep, then - when you move the  mouse - all the monitors will come back up at the same time --- better than waiting one minute, but still an issue.

  I'm opening a thread on the NVidia Linux developers forum to see if there are any suggestions on how to permanently solve the issue.

  cheers,

 Fabio
Thanks for this tip Fabio, it's a workaround. Did you get any answers at the nVidia developer forums yet?

---

### Post by alex494 on 2016-01-09
> **mave-m said:**
> Thanks for this tip Fabio, it's a workaround. Did you get any answers at the nVidia developer forums yet?

Thanks [COLOR=#000000][I]Fabio & mave-m
[/I][/COLOR]do you have further update to fix the issue?

---

### Post by alex494 on 2016-01-09
i have similar setup as yours:
- two Dell Unltrsharp U2515H, first and second monitors are connected with MST daisy chain
- 1 desktop running ubuntu and windows dual boot, connect to first monitor via the DisplayPort input
- 1 laptop running ubuntu and windows dual boot, connect to first monitor via the mini DisplayPort input

ubuntu for both PC are 15.10, kernel is 4.3.3. windows for both PC are windows 10.

when both PC boot from linux, i have the same problem as mave-m (first monitor is enabled but second monitor is in power-saving mode). This is resolved by Fabio's solution.

But my headache come when switching the input source of the first monitor (so that I can toggle between the desktop and laptop).
When both are running windows, I can switch the input source in the first monitor between desktop and laptop. and both monitors can display correctly.
However, when one or both PC are running ubuntu, both monitors will be blanked if I change the input source of first monitor.

I guess the issue is the same (both monitors are in power saving mode). This is even worse as both are switch off and I can not run any command.

is there any way to automatically run command when new monitors are detected / connected? Thanks!

---

### Post by commerce-s on 2016-08-27
I was skeptical that `xset dpms force off` would work in my case, but it did.

I'm running a Dell U2715H as my main display, with a displayport chained to an ASUS branded Ancor VG248.  My card is a GTX670.

Prior to enabling DisplayPort 1.2 on the U2715H, both monitors came up fine in mirrored mode, though neither NVIDIA X Server Settings nor Displays detected the VG248. After enabling DisplayPort 1.2 features on the U2715H, The VG248 was detected, but blank.  Now everything is OK (until the system sleeps or reboots, presumably).

---

### Post by acuenat on 2016-11-22
> **fabbari said:**
> Hi there --

  having the same problem with my setup (Two dell monitors daisy chained out of a NVidia 980M). If I setup the monitors as separate screens all the monitors work fine, when I use them on the same screen one or more of the daisy chained ones will not switch on, even if they ware detected.

  I noticed that the monitors would all turn on when the screens came back out of the sleep mode, so for the moment I came up with this: I have a desktop shortcut to the following command: ```
xset dpms force off
``` - the command will switch off all the monitors - as if they were going to sleep, then - when you move the  mouse - all the monitors will come back up at the same time --- better than waiting one minute, but still an issue.

  I'm opening a thread on the NVidia Linux developers forum to see if there are any suggestions on how to permanently solve the issue.

  cheers,

 Fabio

Hi Fabio,

many thanks for the workaround it works for me as well. Did you happen to get more information from Nvidia or find a more permanent solution?

Best regards,
Alex

---

### Post by totymedli on 2016-11-28
Great solution! The **perfect solution** is to **[run the command on startup]("http://askubuntu.com/q/814/323990")**. Search for "startup" in the dash, click add and paste the command: ```
xset dpms force off
```. I had the same problem with a GeForce GTX 1080 with two daisy chained Dell U2715H monitors under Ubuntu 16.04. After the startup hack you doesn't even notice the problem. It is virtually solved.

---

### Post by oldos2er on 2016-11-28
Since this thread originally concerned a version of Ubuntu that is no longer supported (15.10), I'm closing it. Anyone experiencing similar problems on a supported version of Ubuntu, please start a new thread. Thanks!

---

