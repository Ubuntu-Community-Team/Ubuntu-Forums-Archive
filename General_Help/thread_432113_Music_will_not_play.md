---
title: "Music will not play"
date: 2007-05-03
forum: General Help
---

### Post by tc101 on 2007-05-03
This is not a problem with feisty but something that has never worked. I don't use the computer for music so I have never bothered to fix it.

If I go to amazon.com and look at music it has an option to listen to sample songs. You can select to listen using windows media player or realone player.
If I select windows media player a blank screen with a black box comes up and nothing happens. If I select realone player a box comes up saying "You have chosen to open hurl.exe which is a real audio player, what should firefox do with this file". The only option in the drop down box is Movie Player (default), which doesn't doesn't work and tells me

"An Error Occured
The playback of this movie requires a text/uri-list decoder plugin which is not installed.."

So how do I get music to work on this computer?

By the way, youtube videos with music work just fine since I installed the component they told me to.  I don't remember what that was.  I did it months ago.

---

### Post by benanzo on 2007-05-03
I just tried it at amazon.com and the Windows Media files plays fine for me in Totem.  the Real Player does not.  i got the same error you did.

In order to got Windows media (wma) to play you need to acquire the necessary codecs.


Open Add/Remove and search for "gstreamer plugin"
In the top-right corner change the Show menu to "All available applications"

make sure that these are installed:

GStreamer extra plugins
GStreamer ffmpeg video plugin
GStreamer plugin for aac, xvid, mpeg2, faad
GStreamer plugin for mms, wavepack, quicktime, musepack


that will install basically every popular codec including wma.  then try the amazon Windows Media files again.

---

### Post by tc101 on 2007-05-03
That worked.  Thanks.

---

