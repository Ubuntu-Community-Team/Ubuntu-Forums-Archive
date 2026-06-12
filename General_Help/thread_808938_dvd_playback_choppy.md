---
title: "dvd playback choppy"
date: 2008-05-27
forum: General Help
---

### Post by Pomo on 2008-05-27
My dvd playback in Ubuntu Hardy 64bit is choppy at random. Even if I try to play it from .iso image it makes no difference. All of my searches on this subject end up on "how to enable dma" back from 2005, and so I confirmed that my devices use dma. Here is the hdparm output form my hdd and my dvd-rw:

```
 Model=SAMSUNG HD501LJ                         , FwRev=CR100-11, SerialNo=S0MUJ1NP907222      
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

 Model=TSSTcorp CDDVDW SH-S203D                , FwRev=SB01    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode


```
Does anybody have any idea how to resolve this issue? It appears to affect only dvd playback, my avi-s, mkv-s and simmilar seem to be fine.
I use VLC and Totem movie player that comes with Ubuntu.
Thanks

---

### Post by Pomo on 2008-05-28
BUMP???
Anybody?
Did I post in the wrong section?

---

### Post by prshah on 2008-05-29
> **Pomo said:**
> My dvd playback in Ubuntu Hardy 64bit is choppy at random. 
I use VLC and Totem movie player that comes with Ubuntu.
Thanks

The fact that you get the same problem even when playing back from an ISO obviously indicates it's not related to DMA.

Can you run either vlc or totem from the command line, and post any messages back here? Try```
mplayer dvd:///dev/cdrom0
```; obviously, replace /dev/cdrom0 with your actual dvd drive device.

---

### Post by Pomo on 2008-05-29
Thanks for your advice.
Here is the output:
```
pomo@pomo-desktop:~$ mplayer dvd:///dev/scd0
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd:///dev/scd0.
Option stream url: This URL doesn't have a hostname part.
There are 1 titles on this DVD.
There are 21 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: it
subtitle ( sid ): 2 language: hr
subtitle ( sid ): 3 language: iw
subtitle ( sid ): 4 language: sl
number of subtitles on disk: 5
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
```
There seems to be no such problem with mplayer though?

---

### Post by prshah on 2008-05-29
> **Pomo said:**
> 
```
pomo@pomo-desktop:~$ mplayer dvd:///dev/scd0
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(

```
There seems to be no such problem with mplayer though?

As suggested, maybe ```
 mplayer -vf spp,scale dvd:///dev/scd0
``` Any improvement?

---

### Post by Pomo on 2008-05-29
Sorry, you must have misunderstood me. Mplayer works just fine.
Other players don't.
I must point out that I did not have mplayer installed, just the default Movie player that comes with Ubuntu and VLC. Problem with those two players is still here.
I installed Mplayer upon your request to see terminal output.
Above command has no effect on my problem with other players.
If I go t terminal and type:
"vlc -vf spp,scale dvd:///dev/scd0" I get an error message:
"Unable to open 'spp,scale'"
Hope this helps...

---

### Post by prshah on 2008-05-30
> **Pomo said:**
> Sorry, you must have misunderstood me. Mplayer works just fine.
Movie player that comes with Ubuntu and VLC. Problem with those two players is still here.

Err.. Mplayer _is_ the default ubuntu player, only it's controlled through a front end called Totem.

---

### Post by Pomo on 2008-05-30
> **prshah said:**
> Err.. Mplayer _is_ the default ubuntu player, only it's controlled through a front end called Totem.
I know that, but the syntax that you gave me to start mplayer thru terminal did not work. I went "sudo apt-get mplayer". Only after that it worked.

---

