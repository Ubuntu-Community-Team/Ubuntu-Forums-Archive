---
title: "MPlayer won't play internet radio"
date: 2005-09-01
forum: General Help
---

### Post by zugvogel on 2005-09-01
Hello. I'm trying to play an internet radio station using mplayer from the command line:

mplayer -playlist [http://lsd.newmedia.tiscali-business.com/bb/redirect.lsc?adid=0\&stream=radiohamburg/livestream.wma\&content=live\&media=ms](http://lsd.newmedia.tiscali-business.com/bb/redirect.lsc?adid=0\&stream=radiohamburg/livestream.wma\&content=live\&media=ms)

I used to do this when I had Suse 9.1 last year and it worked well. I have to do it from the CL because I need to feed MPlayer the -playlist option. On Suse, it'd spend a few seconds building up the cache, then start playing. But now it takes a very long time to build up the cache (I might be on a slower network connection though) and then it just hangs and does nothing. The output is below:

```

james@ben:~$ mplayer -playlist http://lsd.newmedia.tiscali-business.com/bb/redirect.lsc?adid=0\&stream=radiohamburg/livestream.wma\&content=live\&media=ms
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Foster (Family: 8, Stepping: 7)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


Resolving lsd.newmedia.tiscali-business.com for AF_INET6...
Couldn't resolve name for AF_INET6: lsd.newmedia.tiscali-business.com
Resolving lsd.newmedia.tiscali-business.com for AF_INET...
Connecting to server lsd.newmedia.tiscali-business.com[213.200.64.155]:80 ...
Cache size set to 1024 KBytes
Connected to server: lsd.newmedia.tiscali-business.com
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing mms://213.200.64.231/radiohamburg$livestream2.wma.
Resolving 213.200.64.231 for AF_INET6...
Couldn't resolve name for AF_INET6: 213.200.64.231
Connecting to server 213.200.64.231[213.200.64.231]:1755 ...
connected
unknown object
unknown object
file object, packet length = 2261 (2261)
unknown object
stream object, stream id: 1
unknown object
unknown object
data object
mmst packet_length = 2261
Cache size set to 1024 KBytes
Connected to server: 213.200.64.231
Cache fill: 19.53% (204800 bytes)    ASF file format detected.
Clip info:
 name: Radio Hamburg
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, 16 bit (0x10), ratio: 6003->176400 (48.0 kbit)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (ffmpeg))
==========================================================================
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default

```

and nothing else happens. It just sits like that until Ctrl-C. Usually it'd start playing, and display time-elapsed.

So I was hoping someone might either know how to fix this, or could suggest a better way of playing internet radio? I tried using "Music Player" but it can't seem to handle streams that were designed for MS media player. Oh, and I have this problem with all radio stations, not just this one! And I installed all the codecs to play DVDs - maybe that's broken something with the codecs? I don't know much about that.

Many thanks.

---

### Post by zugvogel on 2005-09-01
Actually I've found it works using "totem http://pathToRadioStationStream" so it doesn't matter too much any more that mplayer doesn't work. There must be a better way than playing everything from the command line though. I have small c-shell one-liners set up so I can type in the name of the station instead of the whole address, but if I could get it to work with rythme box, that'd be much better of course.

Is there any way to get rythmebox to play microsoft .asx streams, or even .ram url's?

---

### Post by maril on 2005-09-01
did you compile mplayer with the latest codecs?  the ubuntu multimedia howto has instructions for that (unofficia howto)  

lol if you installed it from synaptic please tell me how to find it, i enabled universe but it still isnt there under mplayer

---

### Post by zugvogel on 2005-09-02
mplayer is listed under graphics multiverse, and I installed it from there. It may well be that it doesn't have the latest codecs. Totem seems to be able to play everything though, so it's not too much of a problem for me.

---

### Post by radiobuzzer on 2007-01-17
I think it is the incapability of the server to read properly the microsoft-formatted .asx playlist file.

---

