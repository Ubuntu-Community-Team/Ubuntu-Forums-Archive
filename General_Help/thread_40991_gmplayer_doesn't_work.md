---
title: "gmplayer doesn't work"
date: 2005-06-11
forum: General Help
---

### Post by fedesuarez on 2005-06-11
Hi,

I wrote because I can't make gmplayer working on my laptop (Dell Latitude C800).

I already followed the Howto written on this section, but it didn't work for me.  I was also "googling" a lot, but without major success.

What really makes me wonder is the fact that I have no troubles running mplayer, but I can't run gmplayer.  (Of course, I did ./configure --enable-gui)

The output I get after I install it is this:

fede@fede:~$ gmplayer
MPlayer 1.0pre7-3.3.5 (C) 2000-2005 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE


vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":0.0" => local display)
85 audio & 196 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.


After googling a lot, I found the solution to avoid the RTC error message by typing this:

sudo sysctl -w dev.rtc.max-user-freq=1024

But I still wonder how to add it in my start up files.  Maybe you can help me.  Anyhow, after I run that command, I get this output:

fede@fede:~$ gmplayer
MPlayer 1.0pre7-3.3.5 (C) 2000-2005 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE


vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":0.0" => local display)
85 audio & 196 video codecs


But nothing happens after that.  Of course, I just need to type ctrl-c to get back the terminal, getting a "Fatal error" in a graphical window saying "MPlayer interrupted by signal 2 in module: Unknown".


That's all I did, and I'm totally stuck  ](*,)  at this point, so I need expert help.

Thanks.

fede.

---

### Post by poofyhairguy on 2005-06-11
Two things:

1. You are new so I wont lecture, but that wasn't the forum for questions so I moved it.

2. Gmplayer seems to dislike Ubuntu. I have had sme problems. Either use mplayer or try Gxine -the best (I think) Gnome natural media player.

---

