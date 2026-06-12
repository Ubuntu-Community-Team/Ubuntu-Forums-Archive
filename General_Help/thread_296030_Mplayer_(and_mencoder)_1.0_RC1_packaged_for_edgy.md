---
title: "Mplayer (and mencoder) 1.0 RC1 packaged for edgy"
date: 2006-11-09
forum: General Help
---

### Post by Treviño on 2006-11-09
New Mplayer version with new great features (like internal decoding support of WMV 3 = wmplayer 9) and fixes (for example for mac-intel ;))

Simply download it from [here]("http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/") (I don't give direct links becouse when upgrading they whould change...)

Anyway if you want add the repo to your source.list
```
[FONT=courier new,courier]# Treviño&#8217;s Ubuntu edgy Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" softwares: aMule, amsn, mplayer, moto4lin, flashplugin & flashplayer (9.x)&#8230;
# Further informations: http://3v1n0.tuxfamily.org
deb http://3v1n0.tuxfamily.org edgy 3v1n0
[/FONT][FONT=courier new,courier]deb-src http://3v1n0.tuxfamily.org edgy 3v1n0[/FONT]
```Bye ;)

---

### Post by Synikk on 2006-11-09
> **Treviño said:**
> Simply download it from [here](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/) (I don't give direct links becouse when upgrading they whould change...)

Anyway if you want add the repo to your source.list
```
[FONT=courier new,courier]# Treviño’s Ubuntu edgy Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" softwares: aMule, amsn, mplayer, moto4lin, flashplugin & flashplayer (9.x)…
# Further informations: http://3v1n0.tuxfamily.org
deb http://3v1n0.tuxfamily.org edgy 3v1n0
[/FONT][FONT=courier new,courier]deb-src http://3v1n0.tuxfamily.org edgy 3v1n0[/FONT]
```

Bye ;)

Excellent, thanks! :D

---

### Post by Rob2687 on 2006-11-11
Hi...Can you tell me what build options you used for mplayer? Like the ./configure --prefix=/usr --enable... 
Thanks.

---

### Post by Treviño on 2006-11-12
Sure, Sorry... 
```
CFLAGS="" ./configure --prefix=/usr --mandir=\${prefix}/share/man --confdir=/etc/mplayer --datadir=/usr/share/mplayer --language=all --enable-largefiles --with-extraincdir=/usr/include/ffmpeg --enable-fbdev --enable-directfb --enable-joystick --enable-lirc --with-xanimlibdir=/usr/lib/codecs --enable-runtime-cpudetection --enable-gui --enable-xmga --enable-mga --enable-tdfxfb --enable-joystick --enable-faad-external --disable-tremor-internal --enable-amr_nb --enable-amr_wb --disable-mpdvdkit --enable-lirc --enable-xvmc --with-xvmclib=XvMCW --enable-win32 --with-reallibdir=/usr/lib/codecs --with-xanimlibdir=/usr/lib/codecs
```

So, this is the result:
> Install prefix: /usr
  Data directory: /usr/share/mplayer
  Config direct.: /etc/mplayer

  Byte order: little-endian
  Optimizing for: Runtime CPU-Detection enabled

  Languages:
    Messages/GUI: en
    Manual pages:  cs de en es fr hu it pl sv

  Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l tv live555 cdda dvdread dvdnav vcd dvb smb
    Codecs: qtx x264 xvid libdv amr_wb amr_nb libavcodec real xanim win32 faad2 faac musepack libmpeg2 libdts liba52 mp3lib libtheora speex libvorbis twolame libmad liblzo gif
    Audio output: alsa jack esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix md5sum dxr3 sdl gif89a pnm jpeg png mpegpes(dvb) fbdev svga caca aa ggi xmga mga opengl dga xvmc xv x11 xover dfbmga directfb tga tdfxfb
    Audio filters: ladspa
  Disabled optional drivers:
    Input: vstream pvr radio mpdvdkit2
    Codecs: toolame
    Audio output: sun openal polyp ivtv dxr2
    Video output: winvidix bl zr zr2 ivtv dxr2 vesa tdfx_vid s3fb 3dfx
    Audio filters:


---

### Post by abu_nawas on 2006-11-17
i got audio glitches. how do i fix the problem?

---

### Post by Treviño on 2006-11-27
Please post a log here...

---

### Post by dragon76 on 2006-11-28
Hey Trevino,

I have had audio problems as well with the build of mplayer from your repo. Bellow is my last email to you so that others can benefit or help.

  The following is a log of the output before I stoped the player.  What I get is the correct track plays in the background if you listen closely but there is static/screeching over top of the track that is loud and you can't hear the track unless you listen very closely.  This happens with mp3, avi, mpeg, rawdv, even audio cd's.   Basically everything I try to play.  If you do an audio dump the resulting file has the same audio problems when played back in a working player such as vlc.  All of these files were working with mplayer under dapper and play fine using vlc or other players.  Thanks for the help as I use mplayer scripts along with cron for recording streams of shortwave and medium wave radio shows at night so I can listen to them durring the day and for now am forced to use dapper.  I will also try to sign up for the ubuntu forums and post this problem and correspondence in case it could help others.  If nothing else I will simply have to compile mplayer myself, though it is nice to have a package to use due to dependencies and updates and I have not learned how to build packages yet.

Thanks,
******** 

*******@x2-3800:~$ mplayer /media/sda4/mp3/Coast-to-Coast/Bumper\ music/John\ Lennon\ -\ Imagine.mp3
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
98 audio & 216 video codecs
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/sda4/mp3/Coast-to-Coast/Bumper music/John Lennon - Imagine.mp3.
Audio file file format detected.
Clip info:
 Title: Imagine
 Artist: Jon Lennon
 Album: 1981 - Top 100
 Year: 1981
 Comment: [http://canna.c4.to](http://canna.c4.to)
 Track: 50
 Genre: Folk
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
mpg123: Can't rewind stream by 62 bits!%
mpg123: Can't rewind stream by 19 bits!%
mpg123: Can't rewind stream by 19 bits!%
mpg123: Can't rewind stream by 51 bits!%
mpg123: Can't rewind stream by 79 bits!%
mpg123: Can't rewind stream by 31 bits!%
mpg123: Can't rewind stream by 8 bits!0%
mpg123: Can't rewind stream by 32 bits!%
mpg123: Can't rewind stream by 8 bits!0%
mpg123: Can't rewind stream by 28 bits!%
mpg123: Can't rewind stream by 47 bits!%
mpg123: Can't rewind stream by 74 bits!%
mpg123: Can't rewind stream by 44 bits!%
mpg123: Can't rewind stream by 9 bits!0%
mpg123: Can't rewind stream by 58 bits!%
mpg123: Can't rewind stream by 30 bits!%
mpg123: Can't rewind stream by 16 bits!%
mpg123: Can't rewind stream by 20 bits!%
mpg123: Can't rewind stream by 35 bits!%
mpg123: Can't rewind stream by 38 bits!%
mpg123: Can't rewind stream by 40 bits!%
mpg123: Can't rewind stream by 43 bits!%
mpg123: Can't rewind stream by 27 bits!%
mpg123: Can't rewind stream by 48 bits!%
mpg123: Can't rewind stream by 40 bits!%
mpg123: Can't rewind stream by 28 bits!%
mpg123: Can't rewind stream by 135 bits!
mpg123: Can't rewind stream by 14 bits!%
mpg123: Can't rewind stream by 3 bits!0%
mpg123: Can't rewind stream by 11 bits!%
mpg123: Can't rewind stream by 24 bits!%
mpg123: Can't rewind stream by 11 bits!%
mpg123: Can't rewind stream by 14 bits!%
mpg123: Can't rewind stream by 19 bits!%
mpg123: Can't rewind stream by 35 bits!%
mpg123: Can't rewind stream by 85 bits!%
mpg123: Can't rewind stream by 62 bits!%
mpg123: Can't rewind stream by 8 bits!0%
A:  24.5 (24.4) of 185.0 (03:05.0)  2.0%

MPlayer interrupted by signal 2 in module: play_audio
********@x2-3800:~$

P.S. Hello to ubuntu comunity.

---

### Post by kriloter on 2006-11-30
same problem ...

---

### Post by getaceres on 2006-12-19
I have a problem with your packages as well. I cannot play any video using gmplayer. I get:

jose@Ubuntu:~$ gmplayer copy_music_to_mp3_device.ogg
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2200+ (Family: 6, Model: 8, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
xscreensaver_disable: Could not find XScreenSaver window.
98 audio & 216 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
[GUI] Adding video filter: pp

Playing /home/jose/copy_music_to_mp3_device.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  860x592  24bpp  9,000 fps    0,0 kbps ( 0,0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
Opening video filter: [pp]
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x89ccef8]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 860 x 592 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1,45:1 - prescaling to correct movie aspect.
VO: [xv] 860x592 => 860x592 Planar YV12
[ws] Error in display.
[ws]  Error code: 2 ( BadValue (integer parameter out of range for operation) )
[ws]  Request code: 12
[ws]  Minor code: 0
[ws]  Modules: init_video_codec

But when I try with plain mplayer I can play it so maybe it's a problem with gtk?

Using default fglrx drivers in edgy with Xgl+Beryl svn (from your repositories too).

---

### Post by dragon76 on 2007-01-05
My above problem was solved by completely removing this mplayer package and using the one that has since shown up in the regular repositories. I now have a new problem with some codecs but that is minor, and I probably just need to set something different in a config.

---

### Post by ftmichael on 2007-10-02
This is a known bug in mplayer/mencoder.  See [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751) for further discussion.

Apparently the mplayer part, if not the mencoder part, is fixed in Gutsy.

See [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) for a note for Feisty users; apparently you can downgrade your mplayer and mencoder to the Edgy versions with a simple download from their site (scroll to the bottom of that page) and it'll work.

Michael

---

