---
title: "how to play .rmvb files?"
date: 2008-05-30
forum: General Help
---

### Post by Th3Professor on 2008-05-30
How do I play .rmvb files?

I've tried totem, mplayer, vlc... only get audio, no video.

EDIT:

I tried this:
[http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/](http://www.simplehelp.net/2007/07/27/how-to-play-rmvb-files-in-ubuntu/)

But to no avail...
(added /usr/lib/win32 codecs, updated mplayer preferences (video from xv to x11, and video/audio codec families from "none" to RealVideo decoder and FFmpeg/libavcodec audio decoders), and restarted the application to try to implement the changes.)

I currently have libstdc++6 installed, should I use libstdc++5 instead? (My guess is no; that 6 is just the newer version and has no negative effect on apps that required 5.)

EDIT 2:
I tried putting the /usr/lib/win32 files into /usr/lib/codecs and still no luck.
Files are still in /usr/lib/win32 just in case.
Also tried putting video preferences in mplayer back to xv, still nothing.

EDIT 3:
I added this:[FONT=monospace]
[/FONT]sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
and tried:[FONT=monospace]
[/FONT]sudo apt-get install w32codecs
and:[FONT=monospace]
[/FONT]wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
and:[FONT=monospace]
[/FONT]sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
(it required libstdc++5 so I went ahead and installed it)
...and finally, put video preferences in mplayer back from xv to x11.

AND NOW IT WORKS! ...wow, so many steps just to get video working on .rmvb files!
(Probably would've been easier to just install realplayer!)

---

