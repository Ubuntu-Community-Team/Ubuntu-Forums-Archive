---
title: "I can't view videos in any of my players"
date: 2007-05-20
forum: General Help
---

### Post by squeezy on 2007-05-20
At first Movie Player couldn't play any of my .avis, so I downloaded the codecs I needed through the Synaptic. After that, everytime I try to view a file, the player immediately closes itself. I downloaded VLC and Mplayer, and they both do the same thing too. Any suggestions?

---

### Post by nerdman978 on 2007-05-20
Do you have the restricted extras package and the gstreamer plugins?

---

### Post by squeezy on 2007-05-20
I just installed all that. Now MPlayer gives me an error, and both VLC and Movie Player still close immediately. Movie Player looks as though it's about to open the video, the it's gone.

---

### Post by squeezy on 2007-05-20
I just had VLC play some sounds and video for like a nano second and then closed. So it can play it, it just doesn't want to.

---

### Post by nerdman978 on 2007-05-20
your using feisty right?

---

### Post by nerdman978 on 2007-05-20
try this 
> sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
and then
 > sudo aptitude install w32codecs

If that doesn't work consult the Feisty Wiki here [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs")

---

### Post by squeezy on 2007-05-20
Feisty is correct. Thanks for the help, I think that fixed it. That, or Beryl was causing the trouble. I tried loading a video without Beryl and worked fine, loaded it, and the same thing before happened.

---

### Post by nerdman978 on 2007-05-20
No problem. There is a section on the Feisty Wiki about problems with beryl and video playback and how to fix them. Good luck :p

---

### Post by Dougie187 on 2007-05-25
I am having the same problem. Except i am not using Beryl. I used all the commands that you gave. I guess my problem is a bit different, Some of my movies play correctly, however not all of them do. 

The ones that don't play correctly just open movie player and close it right when it appears to be playing the movie. Does anyone know how to fix this?

---

### Post by Limitlesschannels on 2007-05-26
I have the exact same problem as Dougie.  It is rather annoying.  Most of my videos play fine, but others will just open and close.  I don't use Beryl and I tried the above commands.  And I am running Fiesty and Gnome.

Here is the error codes when i attempted it from the command line.  Hopefully someone can help us out.

```

limitlesschannels@Compy:~/Desktop$ mplayer Film.avi
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.86GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Film.avi.
AVI file format detected.
VIDEO:  [XVID]  640x480  24bpp  23.972 fps  1120.0 kbps (136.7 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by Limitlesschannels on 2007-05-26
wow, and after looking through various other threads this problem looks to have been around for a while, here are some other posts that seem to have the same issues.  The first is leftover from dapper, so maybe it is some bug that never got fixed.

[http://ubuntuforums.org/showthread.php?t=407894&highlight=videos+open+close](http://ubuntuforums.org/showthread.php?t=407894&highlight=videos+open+close)
[http://ubuntuforums.org/showthread.php?t=404120&highlight=videos+open+close](http://ubuntuforums.org/showthread.php?t=404120&highlight=videos+open+close)

The FP seemed to think that it was the .mkv files, but like he said, some others of the same format would play.  I wonder exactly how many are plagued by this problem... Well, maybe we could start a poll, but the title would have to be rather long to showcase the true nature of the problem.  Unless we give it some catchy title like "Another Random Ubuntu Bug #32398239832742."


UPDATE EDIT:  A rather annoying and long way of getting around this problem has been to restart your system, or at least for me it works.  Still a massive hassle, though.

---

### Post by Limitlesschannels on 2007-05-31
bump.  anyone have any ideas?

---

### Post by GabrielDunn on 2007-05-31
I'm going to try the same thing tonight.  When i use Beryl as my desktop manager my videos either dont show or have a grainy line overlay.  but no issue in metacity.  

I'm going to try your fix tonight.  Thanks.

---

### Post by marsm on 2007-06-02
I have absolutely _no_ idea why this worked, but my 'Not a single media player can play any media file for any user on this computer'-problem was solved by doing this:

sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

---

### Post by Dougie187 on 2007-06-04
I got my problem fixed.. here is a link just so you know.

[http://ubuntuforums.org/showthread.php?t=454026](http://ubuntuforums.org/showthread.php?t=454026)

It was a very easy fix but i dont know why it works.

---

### Post by Limitlesschannels on 2007-06-08
blast, that fixed didn't work for me, thanks anyway Dougie.

UPDATE: whoa, and for anyone who doesn't know what their doing, stay well away from xorg.conf.  This is the last time I am messing with that.

---

### Post by Dougie187 on 2007-06-10
you can mess with it all you want. Just make sure you keep a backup so you can copy it back over if you do totally mess something up.

---

### Post by ivesjd on 2007-06-10
If your using beryl, compiz, or the standard desktop effects youll probably have video play back problems.

---

