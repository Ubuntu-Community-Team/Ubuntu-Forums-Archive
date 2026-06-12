---
title: "HDMI issue on HTPC"
date: 2015-06-27
forum: General Help
---

### Post by Dan_Adams on 2015-06-27
Hello,

I'm a new to Ubuntu user, but not new to Linux. I actually work with Linux servers as an admin for a webhost. I have extensive experience with RHEL6 and 7, CentOS and Mint among other distros but haven't used Ubuntu in years. I recently built a brand new HTPC to primarily be used for torrents, streaming and video and audio playback. I got it all slapped together, booted up and installed Ubuntu while connected to a monitor over DVI. At this point everything was working flawlessly and I was ready to move the PC to hook it up to the TV. I did that and after getting it set up, the girlfriend and I sat down to enjoy our first movie on it. 

Video playback started and ran flawlessly as well as audio, however about 10-15 minutes in there was a problem. The screen turned green (while still playing the movie, the green was more of a tint than solid color) and began flashing. This lasted about a minute, maybe two then things went back to normal. At first I thought it may have been a fluke, but it kept oiccurring. I tried different movies, thinking the file was the problem, however it persisted and continued even after exiting out of video playback. It also ocurred again shortly, but this time there was no video playing at the time, in fact nothing was running at all. 

Things I have tried to resolve this:

* Every available driver for my APU
* Different HDMI cables
* Reinstalling Ubuntu
* Checking CPU temps
* Checking memory usage/ load when it occurs
* Reinstalling Ubuntu
* Checked every possible displaysetting in Ubuntu
* Tried different HDMI inputs on my TV
* Verified that other devices connected over HDMI do not experience thisissue as well
* Reseated and thermal compounded the APU and heatsing
* Checked every cable connection several times
* Ran every repair utility available in Ubuntu

I'm nearly about to give up and try Mint on this PC even though I really wnted to run Ubuntu for a change of pace and I like Unity for the HTPC a lot. I've searched extensively over the last few days and have not found even one other instance of another person having this same issue. I'm sure that it has happened but if they've fixed it I can't find it. I appreciate absolutely any help anyone can offer towards resolving this or even just sympathy.

For reference, my PC is made up of the following:

APU: AMD A6-7400K
Mobo: Gigabyte F2A78M-D3H
RAM: 4GB G.Skill
Display: 50" Panasonic Viera Plasma
OS Ubuntu 14.04 LTS w/ Unity

I truly do appreciate any help or insight anyone can provide. I'm absolutely at a loss for how this can work flawlessly over DVI but not over HDMI. And if I've posted in the wrong place or if ther is a more appropriate place for this post please feel free to move the thread/let me know.

---

### Post by QIII on 2015-06-27
Hello!

Do you currently have the proprietary AMD fglrx video driver installed?

If you don't, it may be that the default open source Radeon driver is causing some overheating.  The open source developers have done an absolutely outstanding job of improving the Radeon driver over the last few years and the AMD engineers have helped them.  But if there is one thing that is still far inferior to the proprietary driver, it is power management.

This is typically more of a problem with laptops, since ventilation is an issue.  But the same may hold true with the sorts of small cases used with HTPCs.

If the problem is identical with either driver, it works with DVI and only happens with HDMI I am disposed to wonder if there isn't a hardware issue -- except that the HDMI works with other things as you say.

---

### Post by Dan_Adams on 2015-06-27
Okay, I'm kind of feeling like a jackass. I just changed the driver to the flgrx-updates instead of the flgrx or X.Org X server drivers and things have been stable for nearly 30 minutes after a reboot, when typically this was occurring within 5 minutes of bootup before. I can't say it's fixed yet, but I'm holding my breath. Will be trying some HD video playback in a moment to see what happens during that. Will report back with results as well.

If there's one thing I have learned from years of working with/on computers it's that there's always a reason for everything and it's usually because I'm dumb.

---

### Post by Dan_Adams on 2015-06-27
Alright, Iam in fact an idiot. Problem is solved, and it only took me 4 days. Sigh, thanks for the help. This thread can be closed.

---

### Post by cariboo on 2015-06-27
I've marked the thread solved for you.

---

