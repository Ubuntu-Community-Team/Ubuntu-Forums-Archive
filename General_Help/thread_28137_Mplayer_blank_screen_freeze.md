---
title: "Mplayer blank screen freeze"
date: 2005-04-18
forum: General Help
---

### Post by Dkinc on 2005-04-18
i have recently began my climb to the freedom from windows and have chosen mplayer and vlc to do my vidz.. i got vlc to work but not play .wmv files.. well it played em i got sound but no video.. and it did work with all my other vidz just not .wmv.

then i thought i would try mplayer as it was highly suggested to me.. i used synaptic to install the core and fonts.  It said all installed just fine.   here is the problem

i start it up.. click on open file and imediately the video screen goes blank and mplayer is frozen.  to stop it i have to go to system monitor and end process.. i went to shell and did gmplayer and here is what i got after repeating the same steps... [-X  [-X  [-X  [-X  [-X 

MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for Debian.



vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/jeremy/ArkAngelsDIVX.avi.
AVI file format detected.
VIDEO:  [DX50]  640x480  24bpp  25.000 fps  972.4 kbps (118.7 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 24000 Hz, 2 ch, 16 bit (0x10), ratio: 7000->96000 (56.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 24000Hz/2ch/16bit -> 24000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 24000 hz, little endian signed int
AF_pre: 24000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default

---

### Post by kb00heda on 2005-04-19
Do you have the appropriate codecs installed as well (e.g. w32codes)?

Also, I had some problem running mplayer/gmplayer, where I couldn't use the xv or x11 video drivers; the former caused (at least) gmplayer to freeze at startup, while the former couldn't handle full screen mode (only got an enlarged black frame). My solution to this was changing the video driver from x11 to gl or gl2. This can be done either via gmplayer like

Preferences --> Video --> [select your preferred driver]

or from the command line

gmplayer -vo gl2 (or mplayer -vo gl2)

The -vo option allows to choose the wanted video driver from those available.

This was a kind of a "trial-and-error" process for me. Others seem to manage just fine using the xv drivers. 

Don't know if this does the trick for you (I honestly don't understand your terminal output that good) --- one can only try (until someone who knows better comes along!)? The codecs ought to be required anyhow.

Good luck!

/David

---

### Post by Dkinc on 2005-04-19
okie... i have reinstall mplayer adn have gotten a mpeg to work on mplayer but..

here is the deal i followed most of the forums on how to get the source list for w32codecs add howerver when i do the apt-get install w32codecs there are none available or i get the messege that the comman is obselete or some kind of stuff.

---

### Post by kb00heda on 2005-04-20
OK. If you want to install w32codecs using apt, the best howto probably is located at

[Unofficial Ubuntu Starter Guide](http://www.ubuntuguide.org)

Have a look under the section "Repositories" to complete your sources list, i.e., the file "/etc/apt/sources.list". Have it changed from (3) ---> (4) according to "Q: How to add extra repositories?". I believe the important repositories in this case would be the Marillat ones.

Afterwards, having added a couple of repositories, it should be as easy as typing

```
sudo apt-get update
sudo apt-get install w32codecs
```
in a terminal (this could be done via synaptic as well). See "Q: How to install Multimedia Codecs?" in the guide.

However, I installed w32codecs in a different way, downloading it from the Ubuntu backports

[Ubuntu Backports](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/)

and then, once again in a terminal, typing

```
sudo dpkg -i w32codecs_20050216-0.0_i386.deb
```
This assumes you have an i386 architecture, i.e., a Pentium-like processor. There are separate packages for AMD64-computers.

Do it the way you find easiest. Also, the Ubuntu guide is a marvelous starting-point, that answers many questions, and is well worth reading. It helped me quite a lot to get going.

If this wasn't your problem, you did indeed have Marillat added already, please provide the output you get from "apt-get install w32codecs", to specify exactly what is going wrong.

---

