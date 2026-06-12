---
title: "How to play vp9 Videos"
date: 2013-11-11
forum: General Help
---

### Post by Chelidze on 2013-11-11
Does any one knows how to enable Vp9 Video playback

I can not play the video audio works but as you might guessed it is vorbis

Thank you in advanced

---

### Post by mc4man on 2013-11-11
The only player I have that currently supports is mpv, an mplayer/mplayer2 fork or ffplay
Otherwise play in google-chrome or chromium  till some other player(s) catch up,

> doug@doug-Lenovo-IdeaPad-Y580:~$ mpv   '/home/doug/Videos/out9.webm' 
Playing: /home/doug/Videos/out9.webm
Detected file format: Matroska
[stream] Video (+) --vid=1 (vp9)
Selected video codec: Google VP9 [lavc:vp9]
Audio: no audio
VO: [xv] 512x288 => 512x288 420p 
V: 00:00:00 / 00:00:09 (0%)


---

### Post by mc4man on 2013-11-12
Put up some packages of mpv for 13.10, 14.04 
Haven't used that much, seems ok.

In addition to cli it comes with a .desktop so available in the context menu, from there opens in a window, window fullscreens here with d. click..
( command for cli  is mpv
There is a frontend  called cmplayer that uses mpv [in a ppa]("https://launchpad.net/~darklin20/+archive/cmplayer-ppa"), though it needs newer versions of qt5 from yet another ppa so haven't tried.
(worth a look at  for 14.04

mpv also uses a config file like mplayer, in home > .mpv/config

[https://launchpad.net/~mc3man/+archive/mpv-tests](https://launchpad.net/~mc3man/+archive/mpv-tests)

---

### Post by Chelidze on 2013-11-12
> **mc4man said:**
> Put up some packages of mpv for 13.10, 14.04 
Haven't used that much, seems ok.

In addition to cli it comes with a .desktop so available in the context menu, from there opens in a window, window fullscreens here with d. click..
( command for cli  is mpv
There is a frontend  called cmplayer that uses mpv [in a ppa]("https://launchpad.net/~darklin20/+archive/cmplayer-ppa"), though it needs newer versions of qt5 from yet another ppa so haven't tried.
(worth a look at  for 14.04

mpv also uses a config file like mplayer, in home > .mpv/config

[https://launchpad.net/~mc3man/+archive/mpv-tests](https://launchpad.net/~mc3man/+archive/mpv-tests)

Thank you the MPV player works

---

### Post by shantiq on 2013-11-12
cool   plays everything really well   including 1080p and shorten  ...    will definitely use

---

### Post by shantiq on 2013-11-19
and mpv plays [4k]("http://www.hqshare.net/redirector.php?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2F4K_resolution") **when nothing else does** on my system


[http://www.youtube.com/watch?v=k_okcNVZqqI](http://www.youtube.com/watch?v=k_okcNVZqqI)

[https://en.wikipedia.org/wiki/4K_resolution](https://en.wikipedia.org/wiki/4K_resolution)


> 

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L5.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 2 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 3mn 4s
Bit rate                                 : 17.1 Mbps
[B]Width                                    : 3 840 pixels
Height                                   : 2 160 pixels[/B]
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.086
Stream size                              : 376 MiB (99%)

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 3mn 4s
Bit rate mode                            : Constant
Bit rate                                 : 254 Kbps
Channel count                            : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Delay relative to video                  : 42ms
Stream size                              : 5.58 MiB (1%)



---

### Post by mc4man on 2013-11-27
put up a new saucy using git master of the other day. (available in a few hrs. or so.
shorten had been broken in master but dev's responded quickly & should be ok
if any issue let me know as I no longer use saucy

---

### Post by VMC on 2013-11-27
VLC just stepped into the [VP9]("http://news.cnet.com/8301-11386_3-57612525-76/vlc-steps-into-next-gen-video-wars-with-vp9-hevc-support/") arena also.

---

### Post by mc4man on 2013-12-20
Added some encoding support though one could just as well use FFmpeg. Anyway info in man mpv & thru here
mpv --oac=help
mpv --oacopts=help
mpv --ovc=help
mpv --ovcopts=help

---

### Post by shantiq on 2014-02-08
found this on the net   ;   very handy


> [COLOR=#3F4549][FONT=Helvetica Neue]you can also stream youtube videos and listen to music without video too via libquvi script:
[/FONT][/COLOR]
```
[COLOR=#3F4549][FONT=Helvetica Neue] mpv --no-video --quvi-format=best [youtube url][/FONT][/COLOR]
```


arrows to move back and forth

---

### Post by andrew.46 on 2014-02-08
Times have moved on of course and now MPlayer is quite capable of vp9 playback:

```

andrew@ilium~$ **[COLOR="#FF0000"]mplayer -vc help | grep -i vp9[/COLOR]**

ffvp9       ffmpeg    working   FFmpeg VP9  [vp9]
fflibvpxvp9 ffmpeg    working   FFmpeg wrapper for libvpx/VP9  [libvpx-vp9]

```

And 'hi' shan :)

---

### Post by shantiq on 2014-02-08
hi Andrew :smile:


and of course


```
mpv  --quvi-format=best youtubevideoURL

```

if you want to see the vid as well as the audio



```
mpv  --quvi-format=best http://www.youtube.com/watch?v=iNJdPyoqt8U
```

---

