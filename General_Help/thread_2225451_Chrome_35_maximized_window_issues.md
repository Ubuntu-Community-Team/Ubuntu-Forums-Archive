---
title: "Chrome 35 maximized window issues"
date: 2014-05-21
forum: General Help
---

### Post by pnarciso on 2014-05-21
I'm running Ubuntu 14.04 and with the latest Chrome 35, when I enable system limits and borders, maximized window gets offset to the right as it is shown on the pic below. When I untick system limits and borders everything works as it should. Chrome 34 doesn't show this behaviour which could tell that aura toolkit is clashing with ubuntu theme.

[[IMG]http://s18.postimg.org/shbp3e7g5/Captura_de_ecr_de_2014_05_21_17_42_38.jpg[/IMG]]("http://postimg.org/image/shbp3e7g5/")

---

### Post by pnarciso on 2014-05-23
No one experienced this?

---

### Post by slickymaster on 2014-05-23
I'm running Chrome 35.0.1916.114-1 on both Trusty and Utopic without that issue.

---

### Post by pnarciso on 2014-05-23
I've reinstalled Ubuntu 14.04 and with the default llvmpipe driver (r9 290x doesn have 3d acceleration enabled yet) chrome behaves as it should with ubuntu native decorations and window maximize allright. But after installing amd fglrx version 14.10.1006 (catalyst 14.4) the problem arises. So it's safe to conclude that the problem is related to fglrx.

Curiously it worked fine with Chrome 34.

Also, Chromium 34 from Ubuntu repos have the same problem.

---

### Post by danep on 2014-11-12
I'm having the same problem on a fresh 14.10 install with the latest stable versions of Chrome and fglrx.

This doesn't seem to be specific to Chrome: [http://ubuntuforums.org/showthread.php?t=2241392](http://ubuntuforums.org/showthread.php?t=2241392)

---

### Post by acerspyro2 on 2014-11-16
Damn, it took me forever to find this thread again!

The OP forgot to mention that they are using the **FGLRX DRIVERS **found in the repos for their ATI card/chip. Affects both fglrx and fglrx-updates.

But anyways, this is not a Chromium-only bug. It seems to affect more than one program.
As said on the thread linked previously by danep ([http://ubuntuforums.org/showthread.php?t=2241392](http://ubuntuforums.org/showthread.php?t=2241392)), it also seems to affect **Minecraft**, **Blender**, **Cube 2-based games** and **probably more**.
You can clearly see the relation between those programs: **OpenGL**.
You can clearly see it if you run **glxdemo** and maximize the window. Altho much harder to see, **glxgears **is also affected by this.

I tried disabling hardware acceleration in Chromium, and the bug was gone, which means it has nothing to do with the Aura toolkit Chrome / Chromium is using.

Before updating to 14.10, I was using the bundle provided on the ATI website (Which no longer works with 14.10, for some reason) and it didn't have the issue, so it is a Ubuntu-Unity bug, not an ATI bug.

It is truly annoying and I would love to see a fix for this.

---

### Post by acerspyro2 on 2014-11-16
I will file a bug on this.

---

### Post by acerspyro2 on 2014-11-19
[Bug here]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1390234"). Should be complete, I'd love if someone took care of it.

---

### Post by VinodkumarKN on 2015-03-27
I am also experiencing this bug on my 14.10.

After a fresh install of 14.10, I tried the proprietary driver fglrx-updates from repos. After that I uninstalled, and tried the one from AMD website.
This bug is still showing.

As far as I know, this occurs for Chrome browser, Chromium browser, Adobe brackets(which is also a node-webkit), Opera browser.
I tried disabling HW acceleration in Opera which fixed for Opera. But I don't want to do that.

When maximizing the application is offset to right slightly. At this condition, I opened Compiz and Toggle 'Snapping Windows'.
A toggling will make the app display correctly at once. So is this a Unity/Compiz problem? Completely disabling/enabling snapping won't work, you need to toggle when an application is offsetted.

---

