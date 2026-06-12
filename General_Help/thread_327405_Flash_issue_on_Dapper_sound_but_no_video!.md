---
title: "Flash issue on Dapper: sound but no video!"
date: 2006-12-29
forum: General Help
---

### Post by gabriello on 2006-12-29
Hi everyone,

I'm a very happy user of Ubuntu since last year, I succesfully upgraded from Hoary to Breezy and then to Dapper in the last few days.
Here's my problem:
after the upgrade I can't make flash plugin for firefox work.

I tried almost everything:
-installing flashplugin-nonfree package using Synaptic;
-installing flashplugin using firefox assisted procedure (the procedure that shows up when you jump to a page that needs plugins that are not found by firefox)
-installing "by hand" flashplugin v9 following the instructions I found in many posts on this forum.

In all the cases the problem is the following: when I try to access a flash content (for example a video on google video) I can hear the sound correctly, but I don't see any video, nor any "box" containing the flash player. Even using tha right mouse button over the area that should contain the video doesn't show the usual flash menu.
This happens an all web pages containing flash, not only on google video, I'm using Firefox 1.5.0.8 (with italian translation, but I don't think this matters...) and Ubuntu Dapper 6.06 LTS after an upgrade done step by step from Hoary.

Any idea on how to solve this issue??

Thanks a lot,
...and Happy New Year to all of You!

---

### Post by Ashrael on 2006-12-29
You might try to upgrade firefox to V2. I've had long issues with flash, but got it to work eventualy......it all resolved when i installed firefox 2 and on top of that the v9 beta plugin, and it worked......

---

### Post by gabriello on 2006-12-29
Thanks Ashrael for your reply.

Just an update: I tried to use mozilla-mplayerplugin, it seems to work fine, but again no video and only sound on all pages with embedded video.

I'm pretty sure this is a firefox related issue, but I dont' know how to solve it.
Maybe it is just a configuration problem, in my case firefox doesn't handle plugins properly.

G.

---

### Post by l.tambiah on 2006-12-29
In regards to flash, you are better off installing the flash-plugin 9 beta plugin. Go to the link below and look for the two debs and install.

[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)

As for mozilla-mplayerplugin, I don't use it so cant advise, however instead you may want to try the media connectivity plug-in for Firefox.

Media Connectivity
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

---

### Post by gabriello on 2006-12-29
> **l.tambiah said:**
> In regards to flash, you are better off installing the flash-plugin 9 beta plugin. Go to the link below and look for the two debs and install.

[http://www.ubuntuforums.org/showthread.php?t=279990](http://www.ubuntuforums.org/showthread.php?t=279990)

Already did it by hand (installing from tar.gz) and it didn't solve the problem.

> **l.tambiah said:**
> 
As for mozilla-mplayerplugin, I don't use it so cant advise, however instead you may want to try the media connectivity plug-in for Firefox.

Media Connectivity
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
I tried this program, it works fine, but it doesn't solve my issue with flash :-(

The problem is still that plugins that have to show video under firefox do not work, nor flash plugin, nor mplayer plugin.

G.

---

### Post by Ashrael on 2006-12-29
tell us what this says: in firefox addressbar type "about:plugins"

i'm curious....

---

### Post by Ashrael on 2006-12-29
That should be plugins....about : plugins

without the spaces.....

---

### Post by gabriello on 2006-12-29
Here's the about:plugins page: (in italian but should be very easy to read...)

```
Shockwave Flash

    Nome file: libflashplayer.so
    Shockwave Flash 7.0 r68

Tipo MIME 	Descrizione 	Estensione 	Attivo
application/x-shockwave-flash 	Shockwave Flash 	swf 	Sì
application/futuresplash 	FutureSplash Player 	spl 	Sì
Google VLC multimedia plugin 1.0

    Nome file: mplayerplug-in-gmp.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Tipo MIME 	Descrizione 	Estensione 	Attivo
application/x-google-vlc-plugin 	Google Video 		Sì
QuickTime Plug-in 6.0

    Nome file: mplayerplug-in-qt.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Tipo MIME 	Descrizione 	Estensione 	Attivo
video/quicktime 	Quicktime 	mov 	Sì
video/x-quicktime 	Quicktime 	mov 	Sì
image/x-quicktime 	Quicktime 	mov 	Sì
video/quicktime 	Quicktime 	mp4 	Sì
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Sì
application/x-quicktimeplayer 	Quicktime 	mov 	Sì
application/smil 	SMIL 	smil 	Sì
RealPlayer 9

    Nome file: mplayerplug-in-rm.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Tipo MIME 	Descrizione 	Estensione 	Attivo
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Sì
application/vnd.rn-realmedia 	RealMedia 	rm 	Sì
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Sì
video/vnd.rn-realvideo 	RealVideo 	rv 	Sì
audio/x-realaudio 	RealAudio 	ra 	Sì
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Sì
application/smil 	SMIL 	smil 	Sì
Windows Media Player Plugin

    Nome file: mplayerplug-in-wmp.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Tipo MIME 	Descrizione 	Estensione 	Attivo
application/asx 	Media Files 	* 	Sì
video/x-ms-asf-plugin 	Media Files 	* 	Sì
video/x-msvideo 	AVI 	avi,* 	Sì
video/msvideo 	AVI 	avi,* 	Sì
application/x-mplayer2 	Media Files 	* 	Sì
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Sì
video/x-ms-asf 	Media Files 	asf,asx,* 	Sì
video/x-ms-wm 	Media Files 	wm,* 	Sì
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Sì
audio/x-ms-wmv 	Windows Media 	wmv,* 	Sì
video/x-ms-wmp 	Windows Media 	wmp,* 	Sì
video/x-ms-wvx 	Windows Media 	wvx,* 	Sì
audio/x-ms-wax 	Windows Media 	wax,* 	Sì
audio/x-ms-wma 	Windows Media 	wma,* 	Sì
application/x-drm-v2 	Windows Media 	asx,* 	Sì
audio/wav 	Microsoft wave file 	wav,* 	Sì
audio/x-wav 	Microsoft wave file 	wav,* 	Sì
mplayerplug-in 3.17

    Nome file: mplayerplug-in.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Tipo MIME 	Descrizione 	Estensione 	Attivo
video/mpeg 	MPEG 	mpg,mpeg 	Sì
audio/mpeg 	MPEG 	mpg,mpeg 	Sì
video/x-mpeg 	MPEG 	mpg,mpeg 	Sì
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Sì
audio/mpeg 	MPEG 	mpg,mpeg 	Sì
audio/x-mpeg 	MPEG 	mpg,mpeg 	Sì
audio/mpeg2 	MPEG audio 	mp2 	Sì
audio/x-mpeg2 	MPEG audio 	mp2 	Sì
video/mp4 	MPEG 4 Video 	mp4 	Sì
audio/mpeg3 	MPEG audio 	mp3 	Sì
audio/x-mpeg3 	MPEG audio 	mp3 	Sì
audio/mp3 	MPEG audio 	mp3 	Sì
application/x-ogg 	Ogg Vorbis Media 	ogg 	Sì
audio/ogg 	Ogg Vorbis Audio 	ogg 	Sì
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Sì
video/fli 	FLI animation 	fli,flc 	Sì
video/x-fli 	FLI animation 	fli,flc 	Sì
video/vnd.vivo 	VivoActive 	viv,vivo 	Sì
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Sì
video/vnd.divx 	DivX Media Format 	divx 	Sì
audio/basic 	Basic Audio File 	au,snd 	Sì
audio/x-basic 	Basic Audio File 	au,snd 	Sì
```

...as you can see for what's about flash I have:
file: libflashplayer.so
Shockwave Flash 7.0 r68

...just another update:
If I try to open a .swf file using firefox, it is handled and displayed correctly.
So, in my opinion, there's something wrong in the way firefox handles embedded flash objects or embedded movies.

Still no luck in trying to find a solution... :-(

G.

---

### Post by gabriello on 2006-12-29
Hi everyone!

I finally found the solution!
Unfortunately I forgot to mention that I'm using the Adblock extension... (it's more than a year that I use it without problems, this is the first one!)

Once I disabled OBJ-TABS from AdBlock configuration, everything started to work as expected.

Sorry if I bothered you, hope this can help other users with similar problems.

Cheers, and thank you for helping!

G.

---

