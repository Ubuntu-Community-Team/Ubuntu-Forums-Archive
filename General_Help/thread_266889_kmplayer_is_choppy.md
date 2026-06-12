---
title: "kmplayer is choppy"
date: 2006-09-27
forum: General Help
---

### Post by TheRingmaster on 2006-09-27
Whenever I play a video that requires the use of Kmplayer (I am using Konqueror by the way) the video is choppy and it lags. When I play a video with the xine backend, there is no video at all. When I use the mplayer backend, the video is choppy (as I said before). I haven't used the other option, but I predict that it won't either. Is there any solution for this?

EDIT: no the gstreamer backend doesn't play the video at all.

---

### Post by TheRingmaster on 2006-09-28
no one has any idea of what the problem is. 

Mplayer for firefox is perfect. I think that the problem is that Kmplayer doesn't buffer before it plays.

---

### Post by kerry_s on 2006-09-28
You have to play with the settings.

(General Options)->(Output tab)
General Options= X11Shm
Audio driver= Advanced Linux Sound Architecture
(Mplayer tab)
Cache size=512
Build new index when possiable=x


(Output Plugins)
Enable use of postprocessing filters=x
(Output Plugins)->(General)
fast   <I selected
(Output Plugins)->(Deinterlacing)
X   <I selected all of them


These are the changes i made to get mine to play apple trailers in konqueror.

---

### Post by TheRingmaster on 2006-09-29
OMFG!!!!

It actually worked. Firefox flicks were horrible before and now They are like videos from heaven.

Thanks

---

### Post by TheRingmaster on 2006-09-29
I can't play video from wwe.com though and that is sad. here is what the console said.

> MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Terminal type `unknown' is not defined.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
STREAM_HTTP(1), URL: [http://wmsvod.wwe.com/ecw/200606/cenasabuwweecw56.wmv](http://wmsvod.wwe.com/ecw/200606/cenasabuwweecw56.wmv)
Resolving wmsvod.wwe.com for AF_INET6...
Couldn't resolve name for AF_INET6: wmsvod.wwe.com
Resolving wmsvod.wwe.com for AF_INET...
Connecting to server wmsvod.wwe.com[64.152.4.95]: 80...
Resolving livewms.wwe.com for AF_INET6...
Resolving livewms.wwe.com for AF_INET...
Couldn't resolve name for AF_INET6: livewms.wwe.com
Connecting to server livewms.wwe.com[64.152.4.93]: 80...
STREAM_ASF, URL: [http://wmsvod.wwe.com/ecw/200606/cenasabuwweecw56.wmv](http://wmsvod.wwe.com/ecw/200606/cenasabuwweecw56.wmv)
Resolving wmsvod.wwe.com for AF_INET6...
Couldn't resolve name for AF_INET6: wmsvod.wwe.com
Resolving wmsvod.wwe.com for AF_INET...
Connecting to server wmsvod.wwe.com[64.152.4.95]: 80...
Server return 301:Moved Permanently
Failed to parse header
Failed, exiting
STREAM_HTTP(2), URL: [http://wmsvod.wwe.com/ecw/200606/cenasabuwweecw56.wmv](http://wmsvod.wwe.com/ecw/200606/cenasabuwweecw56.wmv)
Resolving wmsvod.wwe.com for AF_INET6...
Couldn't resolve name for AF_INET6: wmsvod.wwe.com
Resolving wmsvod.wwe.com for AF_INET...
Connecting to server wmsvod.wwe.com[64.152.4.95]: 80...
Resolving livewms.wwe.com for AF_INET6...
Couldn't resolve name for AF_INET6: livewms.wwe.com
Resolving livewms.wwe.com for AF_INET...
Connecting to server livewms.wwe.com[64.152.4.93]: 80...
Cache size set to 512 KBytes
Cache fill:  0.03% (161 bytes)   


Exiting... (End of file)

---

### Post by kerry_s on 2006-09-29
Yep, same here. It looks like that site-vids is for M$ only. It even requires flash 9. :evil:

---

### Post by TheRingmaster on 2006-09-29
I swear that I used to play them when I used firefox.

Flash 9 is coming soon!...I hope

---

