---
title: "Mplayer broken - Xlib: connection to &quot;:0.0&quot; refused by server"
date: 2005-10-20
forum: General Help
---

### Post by SadaraX on 2005-10-20
Hello. I just downloaded via apt-get mplayer. I tried to open a video with it, but I had an error. My System specs:
> 
Motherboard: EPOX EP-9NPA+Ultra NF4 ULTRA RT

Video Card: Geforce 6800GT 256MB DDR PCI Express x16 Video Card - ASUS EN6800/TD/256
	Type VGA XFX|
	Model PVT45GUDF3

CPU: AMD Athlon 64 X2 4200+ Manchester 2000MHz FSB Socket 939 Dual Core
	Processor Model ADA4200BVBOX

RAM: CORSAIR XMS 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) Unbuffered System
	Memory Model CMX1024-3200C2PT
	Model #:CMX1024-3200C2PT

 
I tried using mplayer-586, mplayer-386, mplayer-k7, and mplayer-nogui. They all had the same error. Here is a copy of what the error looks like for mplayer-nogui:

> 
root@[XviD]# mplayer video.ogm
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for Debian.


86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing ../Television/Cartoons/My Life as a Teenage Robot/encodes/MLaaTR - Opening (Album Track).ogm.
Cache fill:  0.00% (0 bytes)    [Ogg] stream 0: audio (Vorbis), -aid 0
[Ogg] stream 1: video (FOURCC XVID), -vid 0
Ogg file format detected.
VIDEO:  [XVID]  704x460  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libvorbis] Ogg/Vorbis audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 499.8 kbit/35.42% (ratio: 62477->176400)
Selected audio codec: [vorbis] afm:libvorbis (OggVorbis Audio Decoder)
==========================================================================
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

vo: couldn't open the X11 display (:0.0)!
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
alsa-init: 1 soundcard found, using: default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO ARTS] can't connect to aRts soundserver
[AO ESD] esd_open_sound failed: No such file or directory
AO: [polyp] -(null)-(null)-
util.c: WARNING: SIGPIPE is not trapped. This might cause malfunction!
client-conf.c: WARNING: failed to open configuration file '(null)': No such file or directory
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

client-conf-x11.c: XOpenDisplay() failed
AO: [polyp] Failed to connect to server: Connection refused
JACK compiled with System V SHM support
[JACK] cannot open server
ao_nas: init(): Can't open nas audio server -> nosound
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
[AO SDL] Unable to open audio: No available audio device
AO: [null] 44100Hz 2ch s16le (2 bps)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 704 x 460 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.53:1 - prescaling to correct movie aspect.
VO: [3dfx] 704x460 => 704x460 Planar YV12
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified



MPlayer interrupted by signal 11 in module: decode_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


I tested this with a few videos and the results are all the same. My video drivers are working just fine. I can player World of Warcraft (in Kubuntu) at maximum graphics and quality settings with no less than 24fps in the most populated areas. Basically, my video runs just awesome (thank you Ubuntu). 

When I try to run glxgears, I get this error:
> 
root@[XviD]# glxgears
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: couldn't open display :0.0


So, I have no idea what the problem is, but help would be greatly appreciated.

---

### Post by SadaraX on 2005-10-20
Hmm, wonder of wonders. When I try to play files as a regular user, everything is just fine. Very strange... Never mind I guess. The problem looks like its not important.

---

### Post by mpettitt on 2005-10-20
You don't have a root x session running, so if you try to play vidoes as root, it is effectively trying to play them on a console. Since you shouldn't play videos as root anyway (not system critical, hence shouldn't be done in a root login!) the problem is, as you have discovered, not important.

Incidentally, the same will happen with any other X based programs...

---

### Post by thomax on 2005-10-20
Try with sudo, because with su you can't run any X apps ;)

---

### Post by Nathaniel on 2005-10-20
Took me a while to figure this out too. It wasn't until my teacher told me about this fact, that I understood why I wasn't allowed to open a file for editing in kate or scite. Instead, I have to 'exit' and 'sudo scite <file>', and then 'su' again, anytime I'm working inside root. Sure, sudo is fine at times, but I tend to execute more than one or two commands at a time as root...

---

### Post by webappz on 2005-12-08
[QUOTE=SadaraX]Hello. I just downloaded via apt-get mplayer. I tried to open a video with it, but I had an error. My System specs:

 
I tried using mplayer-586, mplayer-386, mplayer-k7, and mplayer-nogui. They all had the same error. Here is a copy of what the error looks like for mplayer-nogui:



I tested this with a few videos and the results are all the same. My video drivers are working just fine. I can player World of Warcraft (in Kubuntu) at maximum graphics and quality settings with no less than 24fps in the most populated areas. Basically, my video runs just awesome (thank you Ubuntu). 

When I try to run glxgears, I get this error:


So, I have no idea what the problem is, but help would be greatly appreciated.[/QUOTE]

You probably have to configure your xhost permissions.

For troubleshooting you can just enable all access to the xhost:
su
xhost +

Then do a 'man xhost' to learn how to configure it properly.  or google xhost howto.  I just put xhost + in my .bashrc in my /home/user1 directory to disable the xhost security (probably not a good idea.)

---

### Post by teslarage on 2006-02-06
ahahah... thank you. had this problem too. after using normal user, can easily run mplayer..

cheers :)

---

### Post by newuser111 on 2006-02-06
dont see much reason to run mplayer or glxgears as root

---

