---
title: "Problems playing streamed content with MPlayer"
date: 2007-02-24
forum: General Help
---

### Post by chriswyatt on 2007-02-24
When I play this clip: 'http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram' in Firefox, it plays fine via the MPlayer plugin, but if I try to run the clip from within MPlayer it won't play :confused: .  Here are the results I got when trying to play the stream from the command line:

```

mplayer [http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram](http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram)

MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing [http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram](http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram).
STREAM_HTTP(1), URL: [http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram](http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram)
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.bbc.co.uk](www.bbc.co.uk)
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET...
Connecting to server [www.bbc.co.uk](www.bbc.co.uk)[212.58.224.89]: 80...
Cache size set to 320 KBytes
Cache fill:  0.02% (76 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll

```

The clip plays in Realplayer, but there are gaps and crackles and it doesn't sound too great, also it comes from my laptop speakers even though I've set my SB Audigy 2 NX USB as the default.

---

### Post by yabbadabbadont on 2007-02-25
I get the same error in mplayer, but xine will play it.  However, the sound is messed up just as you described.  Since RealPlayer produces the same output as xine, I would guess that the original source may be messed up.  Can you, or have you, tried playing it from a different operating system to verify that the source is good?

---

### Post by chriswyatt on 2007-02-25
Yes, it's a good source, and it sounds fine through Firefox.

---

### Post by benblout on 2007-04-03
Hi,

Two things that might help.
1) I read somewhere that the real problem isn't with the avisynth.dll - that is a default that should only be tried by mplayer when something else goes wrong (I don't know about that, but thought it worth mentioning).

2) Try downloading that file:

```
$ wget http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram
```
Then look at the contents:
```
$ cat r1live.ram
rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio1/live/r1_dsat_g2.ra
```

Then feed that file to mplayer:
```
gmplayer "rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio1/live/r1_dsat_g2.ra"
```

The quotes aren't needed in this example, but there are often ? characters in these URLs, and you then do need the quotes.

Does this work for you?

-Ben

---

