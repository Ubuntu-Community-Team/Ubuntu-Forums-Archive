---
title: "Mplayer does not work"
date: 2005-09-20
forum: General Help
---

### Post by Zalbor on 2005-09-20
If I try to open any kind of video with mplayer, it freezes. If another window passes over it (or I change to another desktop) the controls go entirely black. Clicking on the X button does nothing, the "killall mplayer" command returns "No processes killed."
No way at all to make the window disappear until I log out, and no way to play a movie with it (I use xine). The plugin for firefox has a progress bar, which reaches near the end then freezes, but luckily I can just close the tab.

Any ideas? :confused:

---

### Post by karimw786 on 2005-09-20
Zalbor, this is exactly what is happening to me!!!  I have, however, found an easier way to kill mplayer:

Applications - System Tools - System Monitor - (select whichever process you wanna kill, in this case gmplayer) - End Process.

The fact still remains that mplayer, considered to be the best media player for Linux, ain't working for me.  Please help!   ](*,)

---

### Post by chris86wm on 2005-09-22
same problem here HELP?

---

### Post by providence on 2005-09-22
I'm having the same problem as the OP so I thought I'd give this a bump.

---

### Post by ow50 on 2005-09-22
[QUOTE=Zalbor]Clicking on the X button does nothing, the "killall mplayer" command returns "No processes killed."
No way at all to make the window disappear until I log out[/QUOTE]
If "killall mplayer" doesn't work, try "killall -9 mplayer". If X freezes, do the killing in a virtual console (hit Ctrl+Alt+F1 to get there and Ctrl+Alt+F7 to get back). And if you're using gmplayer you should probably be killing gmplayer, not mplayer.

[QUOTE=Zalbor]Any ideas? :confused:[/QUOTE]
Start mplayer from the terminal and attach the output. Then maybe someone might have some ideas.

---

### Post by Zalbor on 2005-09-24
[QUOTE=ow50]If "killall mplayer" doesn't work, try "killall -9 mplayer". If X freezes, do the killing in a virtual console (hit Ctrl+Alt+F1 to get there and Ctrl+Alt+F7 to get back). And if you're using gmplayer you should probably be killing gmplayer, not mplayer.[/quote]
Right about this, sorry. I thought mplayer was an X program. "killall gmplayer" worked.

> Start mplayer from the terminal and attach the output. Then maybe someone might have some ideas.
Alright... This is what it shows when the program starts:

```

user@ubuntu:~$ gmplayer
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Northwood (Family: 8, Stepping: 4)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.



vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
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

```

And this is when I try to open a file (any type):
```

Playing (the file's location, I didn't want to include it. it's on a FAT32 partition, if it helps)
Cache fill:  0.00% (0 bytes)    QuickTime/MOV file format detected.
Compressed header uses zlib algo!
Compressed header size: 8456 / 20541
--------------
MOV track #0: 1 chunks, 0 samples
Generic track - not completely understood! (id: 0)
--------------
MOV track #1: 240 chunks, 938 samples
Audio bits: 16  chans: 2  rate: 16000
Audio extra header: len=103  fcc=0x77617665
MOV: Found MPEG4 audio Elementary Stream Descriptor atom (51)!
Fourcc: mp4a
--------------
MOV track #2: 243 chunks, 1502 samples
MOV: Found unsupported Gamma-Correction movie atom (12)!
MOV: Found unknown movie atom SMI  (21)!
Image size: 320 x 180 (32 bpp)
Display size: 320 x 180
Fourcc: SVQ3  Codec: 'Sorenson Video 3'
--------------
MOV track #3: 1 chunks, 0 samples
Image size: 32 x 2 (32 bpp)
Display size: 320 x 180
Fourcc: rle   Codec: 'Animation'
--------------
MOV: longest streams: A: #1 (938 samples)  V: #2 (1502 samples)
VIDEO:  [SVQ3]  320x180  32bpp  25.014 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 encoder: Made with LiveStage Pro
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 32000 Hz, 2 ch, 16 bit (0x10), ratio: 4000->128000 (32.0 kbit)
Selected audio codec: [faad] afm:faad (FAAD AAC (MPEG2/MPEG4 Audio) decoder)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffsvq3] vfm:ffmpeg (FFmpeg Sorenson Video v3 (SVQ3))
==========================================================================
Checking audio filter chain for 32000Hz/2ch/16bit -> 32000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 32000 hz, little endian signed int
AF_pre: 32000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default

```

Then it freezes and I use killall.

---

### Post by ow50 on 2005-09-24
I don't see anything unusual in that output

Two things come to mind that you can test:
[list=1][*]Try playing without sound ("-ao null") or picture ("-vo null") and see if either would be the cause. Try first "mplayer -vo null -ao null <filename>".
[*]How did you install mplayer? You could try compiling the latest from source. I can give instructions if needed.[/list]

And just in case, it might be a good idea to test with something else than a QuickTime (.mov) file, since those don't always play that well whether or not mplayer works. At least make sure it's not a codec issue by testing the same file first with another player, e.g. Totem.

---

### Post by Zalbor on 2005-09-24
Thanks, something seems to have worked... I tried both a MOV and an AVI file, and both worked with no sound, while neither worked with no video. So it must be the sound...

I installed it with synaptic, following instructions from ubuntuguide.org. And I've tested files with gnome-xine, and they work fine except no sound in MOV files.

---

### Post by ow50 on 2005-09-24
[QUOTE=Zalbor]Thanks, something seems to have worked... I tried both a MOV and an AVI file, and both worked with no sound, while neither worked with no video. So it must be the sound...[/QUOTE]
Cool. Next, you can try different sound systems.

To get a list of options, use command
```
mplayer -ao help
```
Then try them individually. oss, alsa and esd are probably the most commonly used ones. For example, to play with esd sound, use command
```
mplayer -ao esd <filename>
```
If, for example, esd works for you, add "ao=esd" to ~/.mplayer/config and it will be used by default.

It seems alsa did not work for you. The other option would  be to try to fix that, but that I would not know how to do.

---

### Post by Zalbor on 2005-09-24
ESD worked! :D Many thanks!

---

