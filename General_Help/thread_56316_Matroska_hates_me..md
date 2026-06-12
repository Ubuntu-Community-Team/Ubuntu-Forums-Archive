---
title: "Matroska hates me."
date: 2005-08-12
forum: General Help
---

### Post by bored2k on 2005-08-12
How in the world do I make my mkv's to run correctly on linux ? I have already installed everything that remotely smelled like MKV to me and I still can't get them to work  (some work but the majority does _not_). I've tried Xine-ui, totem-xine, mplayer, vlc. After installing mkvtoolnix from its Ubuntu repositories VLC now shows a _little_ video and audio --they didn't run correctly, but at least I was able to see something for a glimpse.

Help ?
 
I wished I had VLC .8.2 :( (· Massive Matroska improvements).

---

### Post by maan84 on 2005-08-24
Found this by searching, I also have problems with *.mkv. When I open it with xine, sound is fine but video freezes like ever 2 seconds and the plays on freezes etc, and in totem I only have sound but no video, and I asked in the irc channel for advice, and they told me to try VLC, and I got it from universe and it won't play mkv at all =/

Also need help :)

---

### Post by bored2k on 2005-08-24
Try installing libmatroska-dev and w32codecs

---

### Post by maan84 on 2005-08-24
[QUOTE=bored2k]Try installing libmatroska-dev and w32codecs[/QUOTE]
 Thank you for your reply, 

I already had w32codecs installed, and I searched for the matroska in synaptic and found them and installed, but still same problems with the applications previously listed =/ Though I tried open Mplayer and chose video codec: Win32/VfWex video codecs, and it plays perfectly video without lag like in xine, but here it's no sound :P And then I noticed it was on OSS so I changed it to ESD and it worked :D And with Mplayer of all that hasn't been able to play the *.avi files without freezing, but which xine played perfectly. 

Mystery :)

---

