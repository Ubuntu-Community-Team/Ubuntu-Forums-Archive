---
title: "looking for a little mplayer help"
date: 2008-02-28
forum: General Help
---

### Post by bum000 on 2008-02-28
Im new to linux,,,  & still trying to figure it all out,,,,

I've been using mplayer exclusively because it starts up so fast, open up a video & its playing withing 0.2 seconds.   

 but it got messed up somehow, now its taking 7-8 seconds every time I open up a video.
Anyone knows how to fix this?

---

### Post by kellemes on 2008-02-28
> **bum000 said:**
> Im new to linux,,,  & still trying to figure it all out,,,,

I've been using mplayer exclusively because it starts up so fast, open up a video & its playing withing 0.2 seconds.   

 but it got messed up somehow, now its taking 7-8 seconds every time I open up a video.
Anyone knows how to fix this?

No, but you can startup mplayer from the commandline and see if it gives some terminal output that may be informative.

---

### Post by bum000 on 2008-02-28
yes I tried that, & what it says might be very informative, but unfortunately not to me  :)


AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  512x384  12bpp  29.970 fps  1262.2 kbps (154.1 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled


             !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!   THIS IS WHERE IT PAUSES    !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 512 x 384 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 512x384 => 512x384 Planar YV12 
A:   2.8 V:   2.8 A-V:  0.000 ct:  0.000  85/ 85 11%  0%  2.3% 0 0

---

### Post by seventyeights on 2008-02-28
I tried that on mine and found a delay too. However, I never use the mplayer command.

Try it again but this time use gmplayer. It's just mplayer with a gui. This loads right away. I don't know why mplayer would be slow and gmplayer fast, but thats what I'm seeing.

---

### Post by kellemes on 2008-02-29
Well, it seems you have mplayer configured to prevent XScreensaver from running during play. Try unchecking the following..
mplayer -> preferences -> misc -> Stop XScreensaver

---

### Post by Man Eating Duck on 2008-03-03
> **kellemes said:**
> Well, it seems you have mplayer configured to prevent XScreensaver from running during play. Try unchecking the following..
mplayer -> preferences -> misc -> Stop XScreensaver

Thanks! I had similar woes, and this solved it. Now startup is close to instant (actual playback starts in <1 sec). The screensaver doesn't appear anyway, so no loss there.

It's a bit strange, because I'm positive I didn't change this setting prior to the problem appearing a few days ago. When viewing the console output while launching mplayer, the pause occured some lines after the screensaver message as well.

---

### Post by bum000 on 2008-03-04
youre the man kellemes!   that took care of it!  now its back to start up in <1 second again !

---

