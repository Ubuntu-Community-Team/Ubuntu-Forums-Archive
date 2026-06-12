---
title: "Playing video from command line and sending to other X server"
date: 2008-06-02
forum: General Help
---

### Post by GammaPoint on 2008-06-02
Hi, I have my monitor and my TV set up as two different X servers (labeled 0 and 1). How do I (from the desktop command line) start a movie whose output is to be seen on the TV's X server?

I think the command has something to do with a colon and the number of the server, but it's not working for me and I can't find it through google. Could you help me?

---

### Post by RAOF on 2008-06-02
You need to be setting the 'DISPLAY' environment variable to the appropriate value; this is likely to be either :0 or :1.  An example at the console would be:
```

DISPLAY=:1 *do-stuff*

```

---

### Post by GammaPoint on 2008-06-03
Hmm, I tried that in mplayer and got the following:

> DISPLAY=:1 mplayer Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street\[Dvdrip\].avi 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Sweeney.Todd-The.Demon.Barber.Of.Fleet.Street[Dvdrip].avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  24bpp  23.976 fps  820.9 kbps (100.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
vo: couldn't open the X11 display (:1)!
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
**E: client-conf-x11.c: XOpenDisplay() failed**
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   4.7 (04.7) of 52021.6 (14:27:01.5)  0.8% 
Exiting... (Quit)



I could hear the movie, but it wasn't showing up on X server #1.  I've made bold the error message that showed up in red on my terminal. 

Any ideas? :confused:

---

### Post by NT4usB on 2008-06-03
> **RAOF said:**
> You need to be setting the 'DISPLAY' environment variable to the appropriate value; this is likely to be either :0 or :1.  An example at the console would be:
```

DISPLAY=:1 *do-stuff*

```

I understood it to be, and have used:```
DISPLAY=":0.1" *do-stuff*
```on my dual x setups... LCD/LCD and LCD/TV.```
ct@wimp:~$ DISPLAY=":1" mplayer /data/download/pan/movie/Bitter\ Moon\ CD1.avi
```doesn't work for me but:```
ct@wimp:~$ DISPLAY=":0.1" mplayer /data/download/pan/movie/Bitter\ Moon\ CD1.avi
```does.
More reading here:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens)

---

### Post by jocko on 2008-06-03
If you want to make it always output to the tv, try this:
```
gedit ~/.mplayer/config
```
and add these lines:
```
DISPLAY=:0.1
fs=1
```
That way you can simply double click a video file and have it open up on your tv (as long as you have mplayer as default movie player).

---

### Post by GammaPoint on 2008-06-03
> **NT4usB said:**
> I understood it to be, and have used:```
DISPLAY=":0.1" *do-stuff*
```on my dual x setups... LCD/LCD and LCD/TV.```
ct@wimp:~$ DISPLAY=":1" mplayer /data/download/pan/movie/Bitter\ Moon\ CD1.avi
```doesn't work for me but:```
ct@wimp:~$ DISPLAY=":0.1" mplayer /data/download/pan/movie/Bitter\ Moon\ CD1.avi
```does.
More reading here:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens)


Yes, that definitely works for me.  Thanks for the help, I appreciate it! :)

---

