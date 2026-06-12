---
title: "Real player problem with stream .ram"
date: 2006-12-27
forum: General Help
---

### Post by aum11 on 2006-12-27
When I download a radio stream for real player, i initiate the download and get the following message:

Cannot open 702stream.ram

Real player 10 is installed.

The firefox2 plugin for real player looks ok.

What is the problem?

Thanks.

---

### Post by pay on 2006-12-27
Make sure the plugin is setup correctly by opening up firefox and typing ```
about:plugins
```into the address bar

---

### Post by aum11 on 2006-12-27
Here is the output from about:plugins.
Is the problem that it is looking for suffix rpm and not 
ram?


 Shockwave Flash

    File name: /usr/lib/firefox/plugins/libflashplayer.so
    Shockwave Flash 9.0 d55

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.16.2

    File name: /usr/lib/totem/libtotem-basic-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: /usr/lib/totem/libtotem-gmp-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
DivX® Web Player

    File name: /usr/lib/totem/libtotem-mully-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.0 (compatible; Totem)

    File name: /usr/lib/totem/libtotem-narrowspace-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: /usr/lib/firefox/plugins/nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.3.5 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile	rpm 	Yes

---

### Post by aum11 on 2006-12-27
Have solved the problem by installing the firefox extension "mediaplayer connectivity", and then adjusting the options for real player to be "/usr/X11R6/bin/X11/realplay".

Hope this helps You.

---

