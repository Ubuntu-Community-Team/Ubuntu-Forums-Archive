---
title: "Xorg sometimes maxes out CPU or crashes"
date: 2012-10-27
forum: General Help
---

### Post by Stonecold1995 on 2012-10-27
A few times a week, I'll get up in the morning and go on my computer, just to find the frame rate reduced to 5-10 FPS with a huge input lag.  Logging out and back in fixes this.  It turns out that when this happens, Xorg begins using 12.5% CPU constantly (way more than it should), and I assume that's because it's using 100% of one of my eight cores (four physical).  Also, this isn't a sudden thing.  Xorg will start slowing down slightly, maybe using about 3-5% CPU, and my frame rate drops to about 30 FPS.  As time goes on in that state, the FPS gets lower and lower and Xorg begins using more CPU, until finally it hits a low of about 5 FPS (and the lag is to the point where I have to wait maybe 10 seconds for the "auto-hidden" task bar to appear when I hover over it, and sometimes after that it'll crash.

Is there any way I can catch this before it begins to happen, or better yet, prevent it altogether?

I put the Xorg logs in an attachment.

---

### Post by MutantJohn on 2012-10-27
The ability of a processor to handle two threads at once does not make it another core but a logical equivalence to one.

Anyway, I have the same issue you do only it's not causing me to crash. I have my computer on all day and even though Xorg, Nautilus and the gnome-shell have my cpu idling around 50% usage combined, the system is still stable and not overheating.

I think this a new issue with the 12.10 release.

And it's across different brands of cpu's as well. Mine is AMD while yours must obviously be Intel.

---

### Post by Stonecold1995 on 2012-10-27
> **MutantJohn said:**
> The ability of a processor to handle two threads at once does not make it another core but a logical equivalence to one.
Yeah I know.  I meant four logical and four physical cores.

> **MutantJohn said:**
> Anyway, I have the same issue you do only it's not causing me to crash. I have my computer on all day and even though Xorg, Nautilus and the gnome-shell have my cpu idling around 50% usage combined, the system is still stable and not overheating.

I think this a new issue with the 12.10 release.

And it's across different brands of cpu's as well. Mine is AMD while yours must obviously be Intel.
OK, I was thinking it might have been that I've enabled experimental SNA support (I forgot to mention that) which is slightly unstable, but if you have AMD then it can't be SNA's fault.

Sadly I don't think there's a way to restart the X server without logging out, otherwise I'd just create a bash script to restart Xorg if its CPU usage went too high and for too long.

---

### Post by MutantJohn on 2012-10-27
It just occurred to me that you're using Kubuntu and not Ubuntu. Do you know what the main difference between our distros is?

I'm only wondering because Xorg handles proprietary drivers, right? I'm using nVidia and I used the nVidia control panel to enchance application's antialiasing and to also enhance image quality to max. My driver version is 304.43 also.

And I have a roommate who might be wrong but he told me that one of Ubuntu's main design philosophies was based around aesthetic beauty, that this OS would have the potential to look very, very pretty.

So I'm just curious if 12.10 is an attempt at increasing, what was it called, the post-processing and anti-aliasing? Because I think it is not a coincidence that the gnome-shell, Xorg and nautilus eat my CPU like never before.

---

### Post by Stonecold1995 on 2012-10-28
> **MutantJohn said:**
> It just occurred to me that you're using Kubuntu and not Ubuntu. Do you know what the main difference between our distros is?
The main difference is that Ubuntu uses Unity by default and Kubuntu uses KDE by default.  They also come with a different set of applications (Kate instead of Gedit, etc).  Other than that they're essentially the same.

> **MutantJohn said:**
> I'm only wondering because Xorg handles proprietary drivers, right? I'm using nVidia and I used the nVidia control panel to enchance application's antialiasing and to also enhance image quality to max. My driver version is 304.43 also.
I also have Nvidia, but I'm currently using Intel's integrated GPU (the Intel HD 3000) because I'm on a laptop.  Bumblebee does allow me to use my discrete GPU but only with individual applications.  So I guess that means it's happening on both Intel graphics and Nvidia.

> **MutantJohn said:**
> And I have a roommate who might be wrong but he told me that one of Ubuntu's main design philosophies was based around aesthetic beauty, that this OS would have the potential to look very, very pretty.
I think Ubuntu's philosophy is to be easier to use for people who are new to Linux.  That's why I use Kubuntu, because I feel that Unity and its set of default applications "hold you hand" through things too much (I would use Fedora or another distro but I love the *buntu's support).  And Kubuntu's KDE is made to be both very aesthetically appealing, and also very customizable.

> **MutantJohn said:**
> So I'm just curious if 12.10 is an attempt at increasing, what was it called, the post-processing and anti-aliasing? Because I think it is not a coincidence that the gnome-shell, Xorg and nautilus eat my CPU like never before.
I don't know about that.  I don't think that's it but I have no definitive proof one way or the other.

So I guess now we know it's occuring on both Intel and AMD CPUs, and on both Nvidia and Intel GPUs, so I guess it's more-or-less hardware-independant.

---

### Post by Stonecold1995 on 2012-11-07
Just a few minutes ago, this happened again (it happens about once a day), but this time the graphics went all wonky.  Here's the screenshot I managed to take before it became too glitchy to navigate around (I had to restart Xorg).

[[IMG]http://www.pictureshack.us/thumbs/1490_Xorg_crash_glitch.png[/IMG]](http://www.pictureshack.us/images/1490_Xorg_crash_glitch.png)

Does anyone know of any (even temporary) work-arounds for this?

---

### Post by Stonecold1995 on 2012-11-15
bump

---

### Post by Stonecold1995 on 2012-12-01
bump?

This is still causing a lot of problems for me.  Just a few minutes ago I had to reset Xorg again because my computer bottomed out to 6 fps.

---

### Post by Stonecold1995 on 2012-12-06
Anyone?

---

### Post by Stonecold1995 on 2012-12-11
b-bump?

---

### Post by MutantJohn on 2012-12-11
Isn't Xorg what handles your proprietary drivers? Have you tried disabling those or just straight-up killing the Xorg process? Then again, a direct kill will probably just make your crash so I wouldn't do that.

Also, what frequency are your cores running at? % usage is, I'm pretty sure, amount of actual things done over the number of CPU-cycles in a period. Or some unit of time. Either way, I'm fairly confident frequency affects CPU % usage.

---

### Post by Stonecold1995 on 2012-12-11
> **MutantJohn said:**
> Isn't Xorg what handles your proprietary drivers? Have you tried disabling those or just straight-up killing the Xorg process? Then again, a direct kill will probably just make your crash so I wouldn't do that.
Usually I just log out and back in, because that restarts Xorg.  If my display is lagging too much to get to the logout button I just go to tty1 and either do "sudo killall Xorg" or "sudo service kdm restart".  Both restart the Xorg process.

> **MutantJohn said:**
> Also, what frequency are your cores running at? % usage is, I'm pretty sure, amount of actual things done over the number of CPU-cycles in a period. Or some unit of time. Either way, I'm fairly confident frequency affects CPU % usage.
I don't exactly get what you're saying.  My CPU frequency is 2.4 GHz, and my CPU usage is usually around 100% (I run Folding@home 24/7).  When Xorg goes wonky, it uses about 12% total CPU usage (that's 100% of a single core, Xorg is single-threaded).

And I don't think clock frequency affects % CPU usage.  Increased clock frequency *increases* the maximum performance of the CPU, and % CPU usage is what percent *of* that maximum is actually being put to work.  CPU frequency doesn't affect % CPU usage, but if the CPU usage is high enough, most will increase their frequency to handle a higher load.

---

### Post by Stonecold1995 on 2012-12-19
bump

---

### Post by diskmaster23 on 2012-12-20
I wish someone would help find a solution for this. I've been having this problem for several months now and haven't been able to really find a solution. Some people blame the drivers, some people blame outdated xorg, and some people blame an outdated kernel. However, I've changed all three variables and haven't found a solution yet.

The only thing I can think of this problem to reoccur regardless of what kernel, xorg, nvidia driver version, is the video card is bad. Except, I don't know how to test the video card on linux.

If you dig far enough, you'll see a ton of bug reports on this Xorg 100% cpu crashing bug, but thus far, I haven't found a solution. However, I ordered a new nvidia video card. I am going to install that and see if it cures my problem.

---

### Post by Stonecold1995 on 2012-12-20
> **diskmaster23 said:**
> The only thing I can think of this problem to reoccur regardless of what kernel, xorg, nvidia driver version, is the video card is bad. Except, I don't know how to test the video card on linux.
I don't think it's a bad video card.  I have both Intel HD 3000 (integrated) and a GTX 675M (discrete), and both of them have this problem, which is now occurring more than once daily.  I've tried turning desktop effects on or off, but to no effect, so I don't think it's being overworked.

Strangely, I don't think my brother's or mother's laptop, which both run 12.10, have this problem, but Kubuntu 12.10 was cleanly installed for them, whereas I upgraded directly from 12.04.

How common is this issue for 12.10?

---

### Post by diskmaster23 on 2012-12-21
> **Stonecold1995 said:**
> I don't think it's a bad video card.  I have both Intel HD 3000 (integrated) and a GTX 675M (discrete), and both of them have this problem, which is now occurring more than once daily.  I've tried turning desktop effects on or off, but to no effect, so I don't think it's being overworked.

Strangely, I don't think my brother's or mother's laptop, which both run 12.10, have this problem, but Kubuntu 12.10 was cleanly installed for them, whereas I upgraded directly from 12.04.

How common is this issue for 12.10?

This problem actually seems to affect several different versions from 10.04 through 12.10. I was orginally on Mythbuntu 10.04 then upgraded to a XBMCBuntu 12.10, but I experience the same problem no matter what I do. Like I said, there are bug reports on this, but no real solution.

---

### Post by diskmaster23 on 2012-12-21
I've been doing more digging and I think I found something that probably accurately describes the problem, but the solution doesn't work.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/733374/comments/72](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/733374/comments/72)
I've been trying various 'solutions' with no success yet. If I ever find the solution, I'll send it back here.

---

### Post by chandra on 2012-12-29
I am really glad I stumbled upon this thread. I have the same problem. It started after a few weeks of updates for 12.10. So, I think it is a bug that has been introduced by the update of some package or another.

I am on a system with an AMD Athlon II X2 260 processor and Radeon HD 3000 card.

The applications running are `kile`, `okular`, `thunderbird` and `firefox`.There are no graphic-intensive applications.

The mouse becomes unresponsive and then the screen goes white and the system becomes unuseable.

My workaround has been to dual boot into Kubuntu 12.04, which is, true to its name, more robust :-)

If anyone finds a solution, I would be keen to know.

Thanks.

---

### Post by Zirts on 2013-02-17
Having the same problem. Dual Core CPU 2.20 GHz and every 7 minutes Xorg puts Core 1 under 100% pressure which causes stuttering in everything for a couple of seconds. No idea how to troubleshoot further from here.

---

### Post by diskmaster23 on 2013-02-17
> **Zirts said:**
> Having the same problem. Dual Core CPU 2.20 GHz and every 7 minutes Xorg puts Core 1 under 100% pressure which causes stuttering in everything for a couple of seconds. No idea how to troubleshoot further from here.

The best solution I found was to get a video card that has VDPAU or similar capability. Stability has never been better.

---

### Post by slowpoison on 2013-02-22
I have a similar problem and this has been causing a significant disruption in my daily work. Vim just freezes on me for a second or two and that's enough to distract me from coding. Really sucks.

---

### Post by ildefonso on 2013-03-01
Hi all!

I have had this issue for quite some time, I'm using fglrx driver downloaded from AMD (built packages, version 13.1 - fglrx_9.012).  

Anyway, I have a two-fold issue here: 

1. X taking 100% CPU, but this seem to be related to "gnotime", I just stop it and things works just fine.
2. Sometimes, while switching from one window to another, X crashes, and I can see this backtrace in /var/log/Xorg.0.log.old (because X restarts itself, I have to look at the .old):

[ 30230.002] (EE) Backtrace:
[ 30230.003] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f1e36ccab76]
[ 30230.003] (EE) 1: /usr/bin/X (0x7f1e36b22000+0x1ac9a9) [0x7f1e36cce9a9]
[ 30230.003] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f1e35e48000+0xfcb0) [0x7f1e35e57cb0]
[ 30230.003] (EE) 3: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7f1e359b6000+0x71e90) [0x7f1e35a27e90]
[ 30230.003] (EE) 4: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7f1e359b6000+0x7220f) [0x7f1e35a2820f]
[ 30230.003] (EE) 5: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (pixman_blt+0x52) [0x7f1e359c0472]
[ 30230.003] (EE) 6: /usr/lib/xorg/modules/libfb.so (fbCopyNtoN+0x343) [0x7f1e32534b63]
[ 30230.003] (EE) 7: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so (0x7f1e30672000+0x8d491) [0x7f1e306ff491]
[ 30230.003] (EE) 8: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so (0x7f1e30672000+0x8f62b) [0x7f1e3070162b]
(.....)

And glesx is actually part of fglrx driver.... I added debug packages for libpixman right now, next time it crashes I should have more info, I don't get why X is not giving more details, just "xorg_backtrace" (I have many -dbg packages for xorg), anyway.... I thought that maybe this was because of AMD driver (so much that I even considered getting an nVidia card just to get rid of this issues), but I read that someone has an Intel, and nVidia..... so, maybe it is not AMD.....

---

