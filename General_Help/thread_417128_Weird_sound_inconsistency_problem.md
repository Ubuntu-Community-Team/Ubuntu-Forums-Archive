---
title: "Weird sound inconsistency problem"
date: 2007-04-21
forum: General Help
---

### Post by aysiu on 2007-04-21
Here's something a little weird.

I'm just starting to explore Jamendo, and I found an artist I like (Eva Garcia), so I downloaded her album via BitTorrent as MP3s. 

If I play the songs in Songbird or Rhythmbox, they sound great!

If I play them in VLC, however, they're all crackly.

Is this a setting in VLC I can fix? Is it a bug I should file (I'm using Feisty, by the way)? Any ideas? Any commands I can use to diagnose the problem?

---

### Post by heimo on 2007-04-21
Hi aysiu. See this thread:
[http://ubuntuforums.org/showthread.php?t=402321](http://ubuntuforums.org/showthread.php?t=402321)

Seems some kind of VLC <-> Alsa bug. Workaround is to setup VLC to use OSS, or to turn down VLC volume slider and up in volume manager. Or use another media player. I'm 99% this didn't exist before Feisty.

---

### Post by aysiu on 2007-04-21
Thanks for the link, heimo. I guess I should have searched first.

But since it seems to be pretty common, might it make sense to file a bug on it?

**Edit**: Never mind. I did a search this time. There are two bug reports on this:
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/95538](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/95538)
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025)

It's not a big deal. I don't use VLC for playing MP3s that often. Most of the time, I use Rhythmbox. I just pop open VLC if I want a quick preview. Maybe I'll use Songbird in the meantime until they fix this bug.

---

