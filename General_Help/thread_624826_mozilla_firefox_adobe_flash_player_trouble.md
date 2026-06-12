---
title: "mozilla firefox adobe flash player trouble"
date: 2007-11-27
forum: General Help
---

### Post by prow on 2007-11-27
hi, 

when i visit certain pages that require flash it doesn't load right and i cant see the whole page properly.  I can attach an example.

[picture link]("http://i7.tinypic.com/7347ua9.png")

for reference to what the page should look like please visit [here]("http://remix.nin.com")

---

### Post by FuturePilot on 2007-11-27
Looks like it possibly has something to do with WMODE Transparency which Adobe claims is not supported on Linux browsers:confused:

---

### Post by prow on 2007-11-27
so im eff'd?

cause i tried using other browsers too like konqueror

---

### Post by andybleaden on 2007-11-27
Not necessarily effed but first can you say which of the flash software you were trying to download?

Also I assume your firefox version is the most recent?

I have found firefox can be crashy and problematic but usually the flash stuff works ok

I find that konqueror can be even more problematic sometimes

So I would check on all your java runtime stuff as well as firefox upgrades and extensions and then on the web page check what the software requirements are. 

Sorry to be of more immediate use but if you stick some more info on here more people with expertise may help you more ( well more than me!) 

Good luck

---

### Post by prow on 2007-11-27
i honestly have no idea what flash version im using....how can i figure that out?

---

### Post by FuturePilot on 2007-11-27
> **prow said:**
> i honestly have no idea what flash version im using....how can i figure that out?

You can check by putting 
```
about:plugins
```
in the address bar.

---

### Post by andybleaden on 2007-11-27
That can help

Post it on here for advice  like this...

Installed plugins
Find more information about browser plugins at mozilla.org. 
Help for installing plugins is available from plugindoc.mozdev.org. 
Shockwave Flash
File name: libflashplayer.so
 Shockwave Flash 9.0 r31
MIME Type
Description
Suffixes
Enabled
application/x-shockwave-flash  Shockwave Flash  swf  Yes
  application/futuresplash  FutureSplash Player  spl  Yes
  Shockwave Flash
File name: libflashplayer.so
 Shockwave Flash 9.0 r48
MIME Type
Description
Suffixes
Enabled
application/x-shockwave-flash  Shockwave Flash  swf  Yes
  application/futuresplash  FutureSplash Player  spl  Yes
  Java(TM) Plug-in 1.6.0_03-b05
File name: libjavaplugin_oji.so
 Java(TM) Plug-in 1.6.0_03
MIME Type
Description
Suffixes
Enabled
application/x-java-vm  Java  Yes
  application/x-java-applet  Java  Yes
  application/x-java-applet;version=1.1  Java  Yes
  application/x-java-applet;version=1.1.1  Java  Yes
  application/x-java-applet;version=1.1.2  Java  Yes
  application/x-java-applet;version=1.1.3  Java  Yes
  application/x-java-applet;version=1.2  Java  Yes
  application/x-java-applet;version=1.2.1  Java  Yes
  application/x-java-applet;version=1.2.2  Java  Yes
  application/x-java-applet;version=1.3  Java  Yes
  application/x-java-applet;version=1.3.1  Java  Yes
  application/x-java-applet;version=1.4  Java  Yes
  application/x-java-applet;version=1.4.1  Java  Yes
  application/x-java-applet;version=1.4.2  Java  Yes
  application/x-java-applet;version=1.5  Java  Yes
  application/x-java-applet;version=1.6  Java  Yes
  application/x-java-applet;jpi-version=1.6.0_03  Java  Yes
  application/x-java-bean  Java  Yes
  application/x-java-bean;version=1.1  Java  Yes
  application/x-java-bean;version=1.1.1  Java  Yes
  application/x-java-bean;version=1.1.2  Java  Yes
  application/x-java-bean;version=1.1.3  Java  Yes
  application/x-java-bean;version=1.2  Java  Yes
  application/x-java-bean;version=1.2.1  Java  Yes
  application/x-java-bean;version=1.2.2  Java  Yes
  application/x-java-bean;version=1.3  Java  Yes
  application/x-java-bean;version=1.3.1  Java  Yes
  application/x-java-bean;version=1.4  Java  Yes
  application/x-java-bean;version=1.4.1  Java  Yes
  application/x-java-bean;version=1.4.2  Java  Yes
  application/x-java-bean;version=1.5  Java  Yes
  application/x-java-bean;version=1.6  Java  Yes
  application/x-java-bean;jpi-version=1.6.0_03  Java  Yes
  DivX Browser Plug-In
File name: mplayerplug-in-dvx.so
mplayerplug-in 3.40

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer 
JavaScript Enabled and Using GTK2 Widgets
MIME Type
Description
Suffixes
Enabled
video/divx  DivX Media Format  divx  Yes
  video/vnd.divx  DivX Media Format  divx  Yes
  QuickTime Plug-in 6.0 / 7
File name: mplayerplug-in-qt.so
mplayerplug-in 3.40

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer 
JavaScript Enabled and Using GTK2 Widgets
MIME Type
Description
Suffixes
Enabled
video/quicktime  Quicktime  mov  Yes
  video/x-quicktime  Quicktime  mov  Yes
  image/x-quicktime  Quicktime  mov  Yes
  video/quicktime  Quicktime  mp4  Yes
  video/quicktime  Quicktime - Session Description Protocol  sdp  Yes
  application/x-quicktimeplayer  Quicktime  mov  Yes
  application/smil  SMIL  smil  Yes
  RealPlayer 9
File name: mplayerplug-in-rm.so
mplayerplug-in 3.40

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer 
JavaScript Enabled and Using GTK2 Widgets
MIME Type
Description
Suffixes
Enabled
audio/x-pn-realaudio  RealAudio  ram,rm  Yes
  application/vnd.rn-realmedia  RealMedia  rm  Yes
  application/vnd.rn-realaudio  RealAudio  ra,ram  Yes
  video/vnd.rn-realvideo  RealVideo  rv  Yes
  audio/x-realaudio  RealAudio  ra  Yes
  audio/x-pn-realaudio-plugin  RealAudio  rpm  Yes
  application/smil  SMIL  smil  Yes
  Windows Media Player Plugin
File name: mplayerplug-in-wmp.so
mplayerplug-in 3.40

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer 
JavaScript Enabled and Using GTK2 Widgets
MIME Type
Description
Suffixes
Enabled
application/asx  Media Files  *  Yes
  video/x-ms-asf-plugin  Media Files  *  Yes
  video/x-msvideo  AVI  avi,*  Yes
  video/msvideo  AVI  avi,*  Yes
  application/x-mplayer2  Media Files  *  Yes
  application/x-ms-wmv  Microsoft WMV video  wmv,*  Yes
  video/x-ms-asf  Media Files  asf,asx,*  Yes
  video/x-ms-wm  Media Files  wm,*  Yes
  video/x-ms-wmv  Microsoft WMV video  wmv,*  Yes
  audio/x-ms-wmv  Windows Media  wmv,*  Yes
  video/x-ms-wmp  Windows Media  wmp,*  Yes
  video/x-ms-wvx  Windows Media  wvx,*  Yes
  audio/x-ms-wax  Windows Media  wax,*  Yes
  audio/x-ms-wma  Windows Media  wma,*  Yes
  application/x-drm-v2  Windows Media  asx,*  Yes
  audio/wav  Microsoft wave file  wav,*  Yes
  audio/x-wav  Microsoft wave file  wav,*  Yes
  mplayerplug-in 3.40
File name: mplayerplug-in.so
mplayerplug-in 3.40

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer 
JavaScript Enabled and Using GTK2 Widgets
MIME Type
Description
Suffixes
Enabled
video/mpeg  MPEG  mpg,mpeg  Yes
  audio/mpeg  MPEG  mpg,mpeg  Yes
  video/x-mpeg  MPEG  mpg,mpeg  Yes
  video/x-mpeg2  MPEG2  mpv2,mp2ve  Yes
  audio/mpeg  MPEG  mpg,mpeg  Yes
  audio/x-mpeg  MPEG  mpg,mpeg  Yes
  audio/mpeg2  MPEG audio  mp2  Yes
  audio/x-mpeg2  MPEG audio  mp2  Yes
  video/mp4  MPEG 4 Video  mp4  Yes
  video/3gpp  MPEG 4 Video  mp4,3gp  Yes
  audio/mpeg3  MPEG audio  mp3  Yes
  audio/x-mpeg3  MPEG audio  mp3  Yes
  audio/x-mpegurl  MPEG url  m3u  Yes
  audio/mp3  MPEG audio  mp3  Yes
  application/x-ogg  Ogg Vorbis Media  ogg  Yes
  audio/ogg  Ogg Vorbis Audio  ogg  Yes
  audio/x-ogg  Ogg Vorbis Audio  ogg  Yes
  application/ogg  Ogg Vorbis / Ogg Theora  ogg  Yes
  audio/flac  FLAC Audio  flac  Yes
  audio/x-flac  FLAC Audio  flac  Yes
  video/fli  FLI animation  fli,flc  Yes
  video/x-fli  FLI animation  fli,flc  Yes
  video/x-flv  Flash Video  flv  Yes
  video/vnd.vivo  VivoActive  viv,vivo  Yes
  application/x-nsv-vp3-mp3  Nullsoft Streaming Video  nsv  Yes
  audio/x-mod  Soundtracker  mod  Yes
  audio/basic  Basic Audio File  au,snd  Yes
  audio/x-basic  Basic Audio File  au,snd  Yes
  audio/x-scpls  Shoutcast Playlist  pls  Yes

---

### Post by prow on 2007-11-27
welp here you go...

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Citrix Presentation Server Client for Linux

    File name: npica.so
    ICA Plugin (Linux) Version 10.6.115659 (/usr/lib/ICAClient/wfica)

MIME Type 	Description 	Suffixes 	Enabled
application/x-ica 	Handles ICA connections 	ica 	Yes
Totem Web Browser Plugin 2.20.0

    File name: libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	ogg 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogg 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NSV video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	WMV video 	wms 	Yes
application/asx 	Playlist 	asx 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
GCJ Web Browser Plugin 0.92

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	GCJ 	class,jar 	Yes
application/x-java-applet 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-applet;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
application/x-java-bean 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-bean;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes

---

