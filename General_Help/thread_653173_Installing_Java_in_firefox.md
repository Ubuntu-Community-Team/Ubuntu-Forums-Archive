---
title: "Installing Java in firefox"
date: 2007-12-29
forum: General Help
---

### Post by UK-Wobbie on 2007-12-29
How do you install java in firefox? I installed "sun-java6-plugin" But it still asking me to install java all the time :confused:

Thanks

---

### Post by Hallvor on 2007-12-29
This should do it.

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by UK-Wobbie on 2007-12-29
> **Hallvor said:**
> This should do it.

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Thanks mate :)

---

### Post by UK-Wobbie on 2007-12-29
Installed it and it's still telling me to install Java on a java site :(

---

### Post by Hallvor on 2007-12-29
Might be a stupid question, but did you close and restart Firefox?

---

### Post by UK-Wobbie on 2007-12-29
> **Hallvor said:**
> Might be a stupid question, but did you close and restart Firefox?

Yes i did and i had a go rebooting my computer! Still asking me to install java on a java site :(

---

### Post by Hallvor on 2007-12-29
OK. Try to enter ```
about:plugins
``` in the Firefox address bar and press enter. What is the output?

---

### Post by UK-Wobbie on 2007-12-29
> **Hallvor said:**
> OK. Try to enter ```
about:plugins
``` in the Firefox address bar and press enter. What is the output?

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r115

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
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



I can not see anything about Java! It's installed as when i go to Synaptic Package Manager it says it's installed :confused:

I had a go restalling firefox and java and still getting asked to install java on any java chat site :confused: It as got me FOXED :lolflag:

---

### Post by erfahren on 2007-12-29
try this, in terminal enter:
```

sudo update-alternatives --config java

```
you may see something like
```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```
select the "sun" one if it isn't selected

if it already is post the output of
```

ls /usr/lib/firefox/plugins

```

note: there seems to be a lot of people having similar problems with Java lately, might be a bug of some kind. see:
[http://ubuntuforums.org/showthread.php?t=652574](http://ubuntuforums.org/showthread.php?t=652574)
[http://ubuntuforums.org/showthread.php?t=648117](http://ubuntuforums.org/showthread.php?t=648117)

---

