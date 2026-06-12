---
title: "Ati Radeon HD 4670 Driver Problem"
date: 2012-10-19
forum: General Help
---

### Post by garginis on 2012-10-19
So, today i've got a fresh install of 12.10 x64 on my pc.Everything was fine except video driver.I've downloaded video driver from ati's website.Installation was successfully too.Then i did reboot, and after reboot compiz won't work.

I did  compiz --replace but that doesn't help.So, only way to get back unity was to uninstall ati driver through terminal.After that, i did reboot and everything was fine but i don't have video driver. So, does anybody know why compiz isn't working when video driver is installed?And also, are there some unofficial video drivers for ati radeon  hd 4670 because i can't use official ones.

Cheers, Dragan

---

### Post by BicyclerBoy on 2012-10-19
You might like to read thru' this thread
[http://ubuntuforums.org/showthread.php?t=2073193](http://ubuntuforums.org/showthread.php?t=2073193)

AFAIK There is no "official" driver distinction just free open source (radeon) & closed proprietary (AMD catalyst).

Could argue the community open source is more "official" than the blob..

---

### Post by QIII on 2012-10-19
Because HD 4000 series cards and prior are no longer supported by the current ATI driver and previous drivers do not work with X Server 1.13.

You will have to use the open source Radeon driver while we all hope ATI will reconsider its Linux support model.

Believe me, I will be in touch with them.  I've supported them for years, including on this forum.

---

### Post by garginis on 2012-10-20
Thank you guys.
Radeon driver works fine.In glxgears i got result about 22000 frames in 5 seconds.It's pretty good.On ubuntu 12.04  i used to get about 25000 frames in 5 seconds, but it is ok.It's always better to have graphic driver than not to have it.

Cheers, Dragan

---

### Post by scitizen17 on 2012-12-22
Hi,

Probably my first post here. Hi everyone.

I recently purchased the: HIS IceQ H467QS1GHA Radeon HD 4670 1GB 128-bit DDR3 AGP 4X/8X HDCP Ready Video Card

Trying to get the most life out of what I have.

My system is:
Asus P4P800e Deluxe MB
Pentium 4 Prescott 3.2GHz 1MB L2 Cache
4GB Ram
AGP bus (obviously)
Samsung P2770 Monitor

I have been running Ubuntu 10.04 for a couple of years and had an Nvidia card, OK, but VLC for hi-res video was right on the edge of not working. Usually had to skip H.264 processing to make it watchable.

When I installed the HD 4760 card, nothing but problems getting the ATI fglrx drivers to work. No go. Tried everything, believe me.

Upgraded to Ubuntu 12.04LTS, tried the ATI fglrx again, no go.

Now using the open-source "radeon" driver. 3D and GPU decoding works great, VLC is now v2.0.3, I get 60 FPS.

30 - 40% CPU usage during video playback, and avi, mkv, mp4 video works flawlessly with VLC 2.0.3.

Don't bother with the ATI fglrx driver, just use "radeon" open source.

Works great for me.

Hope this helps.

---

