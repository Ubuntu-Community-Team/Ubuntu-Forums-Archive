---
title: "I would like to get Ogg Theora working in MPlayer"
date: 2007-01-15
forum: General Help
---

### Post by darweth on 2007-01-15
Ogg Theora vids play beautifully on my computer within Totem and VLC, but I get a "Ogg Stream 0 is of an unknown type" error for the video in MPlayer.  The audio plays fine.  Since I use MPlayer for streaming internet video, it is very important that I get Theora to actualy play inside of it.  Has anyone else had success with this?  What do I need to do here?  I use Edgy which comes with the latest libtheora built in so there shouldn't be a problem.  I compiled MPlayer obviously after the libtheora was in the system.  How can I get this to run?  Does anyone have any ideas?

---

### Post by pay on 2007-01-15
If you're compilling mplayer with theora support, then you would need the libtheora-dev package.

---

### Post by darweth on 2007-01-15
Thank you!~  That worked... kinda.  The video plays fine :)  but MPlayer loads up with a "could not open codec" message.  Anyway to get rid of that?

---

### Post by darweth on 2007-01-15
Nevermind.  I guess that depends on the inputs you have in codecs and demuxers or whatever. :)

---

