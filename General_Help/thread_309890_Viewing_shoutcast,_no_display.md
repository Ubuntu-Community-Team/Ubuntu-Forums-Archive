---
title: "Viewing shoutcast, no display ??"
date: 2006-11-30
forum: General Help
---

### Post by Green_Star on 2006-11-30
I am in Edgy, I am trying to watch shoutcast video, i am getting audio but no video !! in my console it is giving following message...

> $ vlc
VLC media player 0.8.6 Janus
[00000326] access_http access: Raw-audio server found, nsv demuxer selected
[00000330] main decoder error: no suitable decoder module for fourcc `VP62'.
VLC probably does not support this sound or video format.


Any other way to watch this video? I do not mind installing other media players or codecs.

---

### Post by princemackenzie on 2006-11-30
A quick googling points to this: [http://wiki.multimedia.cx/index.php?title=VP62](http://wiki.multimedia.cx/index.php?title=VP62)

Apparently FFmpeg handles this.  Searching synaptic for "ffmpeg" should point you in the direction of this codec...

---

