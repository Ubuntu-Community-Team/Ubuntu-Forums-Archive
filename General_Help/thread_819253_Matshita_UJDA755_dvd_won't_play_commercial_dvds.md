---
title: "Matshita UJDA755 dvd won't play commercial dvds"
date: 2008-06-05
forum: General Help
---

### Post by Crusty Juggler on 2008-06-05
I'm trying to get Ubuntu working on a friend's reclaimed old Toshiba Portege, but I can't get the DVD player working.  Burnt DVDs will work fine, but commercial DVDs, from both region 1 and 4, won't mount or play, as they go totally unrecognised. The drive is set at region 4.

My efforts to get the drive working are as follows: First, I tried installing totem-xine libxine1-ffmpeg libdvdread3, no joy.  Then I installed libdvdcss2 and w32codecs.  Nothing still.  I then went through synaptic package manager and added gstreamer good bad and ugly.  Still no go.  Added elisa good bad and ugly.  Not sure what else to try at this point.  

Also: this is the output I get when I run vlc cdrom0:
```
VLC media player 0.8.6e Janus
libdvdnav: using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat cdrom0
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[000000293] main input error: no suitable access module for `cdrom0'
[000000284] main playlist: nothing to play
[000000284] main playlist: stopping playback
```

Any help?

---

### Post by mrMango on 2008-06-05
Obviously vlc is saying it can't find cdrom0.

Perhaps running ```
vlc /dev/dvd
``` would help.

---

### Post by Crusty Juggler on 2008-06-05
Works for burnt DVD, not for commercial.

---

