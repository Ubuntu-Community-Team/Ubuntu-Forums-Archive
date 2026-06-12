---
title: "firefox crashes flash/video"
date: 2007-06-11
forum: General Help
---

### Post by rickdog on 2007-06-11
Okay, I've been wondering about this for a long time. Every time I open a page with some video or flash for the first time Firefox simply "core dumps", then when I restore the browser everything works fine. This happens on both of my computers and I would like to finally solve this. Here's the output of when I started Firefox out of the terminal and go to my igoogle page that has a game and some news video:

[COLOR="Blue"]rick@rick-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0x8e72058]
** Message: Init mimetype 'application/x-mplayer2' mode 1
** Message: Base URI is 'http://32.gmodules.com/ig/ifr?url=http://www.cammap.net/tvlive/livetvint.xml&nocache=0&up_kanaal=ABC+News+Now&up_autoplay=Yes&up_none=-+Fill+in+below+-&up_statn=&up_urls=&up_urlw=http://&lang=en&country=us&.lang=en&.country=us&synd=ig&mid=32&parent=http://www.google.com'
** Message: Real mimetype for 'application/x-mplayer2' is 'video/x-msvideo'
argv[0] type application/x-mplayer2
argv[1] pluginspage [http://www.microsoft.com/windows/windowsmedia/download/AllDownloads.aspx/](http://www.microsoft.com/windows/windowsmedia/download/AllDownloads.aspx/)
argv[2] filename [http://a1729.l2168647534.c21686.g.lm.akamaistream.net/D/1729/21686/v0001/reflector:36819](http://a1729.l2168647534.c21686.g.lm.akamaistream.net/D/1729/21686/v0001/reflector:36819)
argv[3] src [http://a1729.l2168647534.c21686.g.lm.akamaistream.net/D/1729/21686/v0001/reflector:36819](http://a1729.l2168647534.c21686.g.lm.akamaistream.net/D/1729/21686/v0001/reflector:36819)
argv[4] name MediaPlayer6
argv[5] showcontrols 0
argv[6] showdisplay 0
argv[7] showstatusbar 1
argv[8] height 200
argv[9] width 270
** Message: mSrc: [http://a1729.l2168647534.c21686.g.lm.akamaistream.net/D/1729/21686/v0001/reflector:36819](http://a1729.l2168647534.c21686.g.lm.akamaistream.net/D/1729/21686/v0001/reflector:36819)
** Message: mCache: 0
** Message: mControllerHidden: 1
** Message: mShowStatusbar: 1
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty) --mimetype video/x-msvideo --no-controls --statusbar 
Segmentation fault (core dumped)
rick@rick-laptop:~$ 
[/COLOR]

Can anyone help me with this? How do I get past that segmentation fault?
Thanks.

---

