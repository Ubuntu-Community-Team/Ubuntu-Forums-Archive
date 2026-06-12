---
title: "Streaming video &quot;demuxer&quot; problem: mplayer can't open wmv file"
date: 2005-08-23
forum: General Help
---

### Post by clehel on 2005-08-23
Hi,
I ran into a problem with streaming video. I tried a few players (Kaffeine, vlc, gmplayer), I reached furthest with mplayer. I tried mplayer as Mozilla plugin, upon clicking on the video link in Firefox the Mplayer window did open, but the video did not start to play. I figured out the name of the file, it has a wpl extension. I tried gmplayer with the wpl file from the command line, it crashed (you can see the output below.) wpl is a redirector that points to the actual video file, in my case a wmv file. I was able to locate the wmv file, and when I tried gmplayer with this wmv file from the command line, it started playing the video automatically, perfectly. So the problem seems to be that gmplayer can't interpret what is in the wpl file. Why is that happening, and what can I do? It seems that Kaffeine and vlc also have similar problems. Kaffeine does not crash, gives no obvious error message, just does not open the wmv file, vlc gives a short error message, as you can see below.

Thank you very much for your help in advance!

> Error message by gmplayer:

clehel@apagepe:~$ gmplayer [http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl](http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl)
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX

vo: X11 running at 800x600 with depth 24 and 32 bpp (":0.0" => local display)
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
Playing [http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl](http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl).
Resolving [www.godsdirectcontact.eu.com](www.godsdirectcontact.eu.com) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.godsdirectcontact.eu.com](www.godsdirectcontact.eu.com)
Resolving [www.godsdirectcontact.eu.com](www.godsdirectcontact.eu.com) for AF_INET...
Connecting to server [www.godsdirectcontact.eu.com](www.godsdirectcontact.eu.com)[8.3.8.107]:80 ...
Cache size set to 1024 KBytes
Connected to server: [www.godsdirectcontact.eu.com](www.godsdirectcontact.eu.com)
Cache fill:  0.03% (291 bytes)    XMMS: found plugin: libmpg123.so (MPEG Layer 1/2/3 Player 1.2.10)
XMMS: found plugin: libwav.so (Wave Player 1.2.10)
XMMS: found plugin: libmikmod.so (MikMod Player 1.2.10)
XMMS: found plugin: libcdaudio.so (CD Audio Player 1.2.10)
XMMS: found plugin: libtonegen.so (Tone Generator 1.2.10)
XMMS: found plugin: libvorbis.so (Ogg Vorbis Player 1.2.10)

MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

> vlc error message:

clehel@apagepe:~$ wxvlc [http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl](http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl)
VLC media player 0.8.1 Janus
[00000253] ts demuxer error: cannot peek

> Content of .wpl file:

<?wpl version="1.0"?>
<smil>
    <head>
        <meta name="Generator" content="Microsoft Windows Media Player -- 10.0.0.3646"/>
        <title>1999hun01</title>
    </head>
    <body>
        <seq>
            <media src="1999hun01-LAN.wmv"/>
        </seq>
    </body>
</smil>

---

