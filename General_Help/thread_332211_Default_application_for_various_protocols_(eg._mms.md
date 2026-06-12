---
title: "Default application for various protocols (eg. mms)"
date: 2007-01-05
forum: General Help
---

### Post by detyabozhye on 2007-01-05
How do I change the system default application for opening a url with a non-http protocol from my browsers? Such as when I click on an mms://blablabla.wmv link in Firefox, it wants to open in Totem because that is the default app (running Xfce, not Gnome btw, I don't know why it is default). I want to change the default application, so that when I tell Opera, Firefox, etc to open an mms or other protocol, it will open in MPlayer or VLC without me configuring every single application to open it in that app. Where are the defaults for these protocols stored? Thanks.

---

### Post by pinguinus on 2007-01-06
You could try the following how-to to be able to play, for example, online mms multimedia streaming files with Firefox:
[http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html](http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html)

Or if that doesn't work well enough, you could read this thread and try to follow that advice:
[http://www.ubuntuforums.org/showthread.php?t=325692&highlight=totem+gstreamer+wmv](http://www.ubuntuforums.org/showthread.php?t=325692&highlight=totem+gstreamer+wmv)

---

### Post by pinguinus on 2007-01-06
As a Firefox user only I dunno about enabling mms and rtsp streaming media support in Opera but the following thread seems to indicate that it might work in the newest Opera:

[http://ubuntuforums.org/showthread.php?t=228710&highlight=mms+rtsp](http://ubuntuforums.org/showthread.php?t=228710&highlight=mms+rtsp)

Anybody else know about Opera's support for streaming media?

---

### Post by Seq on 2007-01-07
This may end up being gnome-specific, but considering how firefox tends to take settings from gnome, it may be worth a shot.

Fire up `gconf-editor` and browse to "/desktop/gnome/url-handlers/mms" and change the "command" value. I found this when trying to figure out how to have nautilus handle ftp:// urls.

---

### Post by detyabozhye on 2007-01-07
Thanks guys. Seq's thing did the trick. Seems that Firefox gets the "system" default not from the system settings, but from Gnome settings whether or not you have Gnome installed.

---

