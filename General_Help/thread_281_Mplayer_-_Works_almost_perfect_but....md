---
title: "Mplayer - Works almost perfect but..."
date: 2004-10-12
forum: General Help
---

### Post by Perfect Storm on 2004-10-12
I can see there some things it can't get

> orion@Universe:~/Downloads/Software/Mplayer $ gmplayer
MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Intel Pentium 4/Xeon/Celeron Foster 2387 MHz (Family: 8, Stepping: 4)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Reading config file /usr/local/etc/mplayer/mplayer.conf: No such file or directory
Reading config file /home/orion/.mplayer/config
[cfg] read config file: /home/orion/.mplayer/gui.conf
Reading config file /home/orion/.mplayer/gui.conf
vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":0.0" =&gt; local display)
Reading /home/orion/.mplayer/codecs.conf: Can't open '/home/orion/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: 73 audio &amp; 180 video codecs
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 &gt; /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using usleep() timing
Can't open input config file /home/orion/.mplayer/input.conf: No such file or directory
Input config file /usr/local/etc/mplayer/input.conf parsed: 53 binds
SKIN dir 1: '/home/orion/.mplayer/Skin'
SKIN dir 2: '/usr/local/share/mplayer/Skin'
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)



Anyway to fix it?

---

### Post by ubuntu-geek on 2004-10-12
It looks like some configuration files might be missing.. Take a browse at this howto it might help to re-install a few things..

[http://ubuntuforums.org/viewtopic.php?t=112](http://ubuntuforums.org/viewtopic.php?t=112)

---

### Post by Perfect Storm on 2004-10-12
Thanks, gonna check it out....I might forgot something when installing from the source.


.:=The AI Dude=:.

---

