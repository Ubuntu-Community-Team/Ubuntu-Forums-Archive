---
title: "[SOLVED] WMV9: mplayer32 sound works, gmplayer sound doesn't work"
date: 2007-02-26
forum: General Help
---

### Post by unebaguettesvp on 2007-02-26
Hey-

I'm still having problems playing Windows Media Files with Ubuntu 6.10 using AMD 64 archtitecture. I do have some progress.

I compiled the latest version of MPlayer (1.0rc1). I can now play WMV files perfectly ... from the command line!!!

This works:

mplayer32 movie.wmv

This doesn't:

gmplayer movie.wmv

Using gmplayer, from the command line or selecting it from the menu plays WMV files just fine but there is no sound!!! Any ideas why this would happen? I would much rather use gmplayer.

Also, has anyone gotten the MPlayer plugin for Firefox to play WMV files on Ubuntu 6.10 AMD64?!?!?!?!

Any help would be appreciated!

---

### Post by unebaguettesvp on 2007-02-26
Also.....

Ideally I would much rather use totem-xine to play wmv files. I found this: [http://xinehq.de/index.php/faq#WMV](http://xinehq.de/index.php/faq#WMV)

Since, I don't have xine installed, I don't have a ~./xine/config file. So, I installed xine. Put all of the codecs in /usr/lib/win32. Opened up the config file. There was no decoder.external.win32_codecs_path, so I added this at the end of the file:

decoder.external.win32_codecs_path:/usr/lib/win32

Still, no luck. Then I tried using totem-xine. Again, no luck.

Am I missing something here?!

---

### Post by zvacet on 2007-02-26
From mplayer GUI choose preferences>codecs&demuxer,and in audio family select type you want.

---

