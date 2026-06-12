---
title: "Issue with mouse-over text, and dragging text/images (Please help)"
date: 2020-01-19
forum: General Help
---

### Post by aelshako on 2020-01-19
Whenever I try to mouse over text, right click, or drag text and images: it shows up garbled as shown in the attached image. I am new to Ubuntu, so any advice on how to fix this would be great.[IMG]https://ibb.co/bKVNXW1[/IMG]

---

### Post by CelticWarrior on 2020-01-19
Graphics card and drivers?

---

### Post by aelshako on 2020-01-19
I have an AMD Radeon 6950. How should I check the drivers?

---

### Post by CelticWarrior on 2020-01-19
AMD graphics should work with open-source drivers, already installed, no need for user actions.

Now, that graphics chip/card is very old and is probably failing, the artifacts are likely a symptom.

---

### Post by aelshako on 2020-01-19
Thanks for the info. I was planning an upgrade soon anyways. So perhaps now is the time.

---

### Post by Impavidus on 2020-01-19
Which release of Ubuntu? Which kernel? You can check with```
uname -r
```

---

### Post by dora5 on 2020-01-27
> **Impavidus said:**
> Which release of Ubuntu? Which kernel? You can check with```
uname -r
```

I am running 18.04, have been since last summer, and have just started noticing the exact same thing.  Don't believe it's suddenly my video or my driver, especially since I'm using both onboard video (Intel) and an AMD card with their drivers.   Same problem all three monitors.   Think something went flaky with Ubuntu.

Is there a way to check my driver update history and roll back?

---

### Post by paydaydaddy on 2020-01-27
I had a similar issue that I resolved by going to >system settings>Display and Monitor>Compositor>Rendering Backend>choose XRender. This worked for me and for at least a few others. I am running Kubuntu 18.04.03. I am guessing that this is something that broke due to an update. I have a second computer running the same OS that has not had the same problem. The main difference is that one is AMD graphics and  the other is Nvidia. The AMD machine was the problem for me.

---

### Post by Impavidus on 2020-01-28
Something significant happened during a recent upgrade. Systems originally installed as Ubuntu 18.04.2 or 18.04.3 upgraded their kernel from 5.0 to 5.3. Systems originally installed as 18.04 or 18.04.1 or upgraded from an earlier release to 18.04 stay on the 4.15 kernel. This new kernel means that the amd graphics drivers are no longer the proprietary drivers, but the open source drivers built into the kernel. If they don't work properly, you could try downgrading to the 4.15 kernel. Just install the package **linux-generic**, reboot and use the grub menu to boot the 4.15 kernel.

---

### Post by dora5 on 2020-01-29
Thanks paydaydaddy and impavidus.   While googling the incomprehensible if roughly on target explanation I got on a different Ubuntu forum, I learned that there is indeed a bug - in xserver-xorg-video-ati-hwe-18.04 and xserver-xorg-video-amdgpu-hwe-18.04.  This is all several days old.  They are evidently pushing fixes down the distro chain, way to go to reach Ubuntu, and in the meantime one can do something but I'm totally confused about what.

Inxi tells me I'm running

Graphics:  Card-1: Intel 2nd Generation Core Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: Advanced Micro Devices [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.5 ) drivers: i915,radeon
           Resolution: 1280x1024@60.02hz, 1280x1024@60.02hz, 1280x1024@60.02hz
           OpenGL: renderer: AMD CEDAR (DRM 2.50.0 / 5.3.0-26-generic, LLVM 9.0.0)
           version: 3.3 Mesa 19.2.1 Direct Render: Yes

Inxi tells me the kernel version.  CPU~Quad core Intel Core i5-2400 (-MCP-) speed/max~1599/3400 MHz     Kernel~5.3.0-26-generic x86_64 Up~2 days Mem~7427.2/32024.9MB HDD~1878.4GB(41.2% used) Procs~366 Client~Shell inxi~2.3.56  


I have an older AMD card that won't even run the current proprietary driver and must run Radeon.  I've ALWAYS used the open source driver and am still using the open source driver, though if Kernel 5.3 isn't what I installed it is what I am now using.  So using the open source driver did not change.   And, again, the same thing happens on the monitor connected to onboard video and using Intel i915.   Not making sense it would have much to do with RAdeon, must be X.



[COLOR=#000000]
[/COLOR]
Do I need to change anything or just wait for the fixes to appear when I run system upgrade and update?


Really,  simple logic said that the bug must be in a recent update to the software that actually displays video, eg, X.   How could people just auto-advise people to change to more up to date hardware, not something I will ever understand!

---

### Post by dora5 on 2020-01-29
Nothing like this appears in system tools in Ubuntu, how would I make this change?  

The only option I get is display arrangement.

---

### Post by paydaydaddy on 2020-01-31
video driver updates for Kubuntu came in today. That seems to have fixed the rendering problems for the mouseovers, dropdowns, and etc. I was able to go back to openGL (default) rendering. Hopefully it fixed things for the Gnome desktops as well.

---

### Post by guiverc on 2020-01-31
It's possible this relates to [https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718](https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718) and this what you were referring to (was the other forum ask ubuntu?; a link may have been handy)

If that's it, you don't need to do anything, the fix was available some time ago (if you used proposed) but the [COLOR=#242729][FONT=Arial]verification of the SRU for xserver-xorg-video-ati-hwe-18.04 has completed successfully (days ago) and the package was released to -updates  

Sorry I only scanned the prior links and may have missed bits..[/FONT][/COLOR]

---

