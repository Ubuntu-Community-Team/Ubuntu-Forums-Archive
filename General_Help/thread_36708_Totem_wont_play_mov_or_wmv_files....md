---
title: "Totem wont play mov or wmv files..."
date: 2005-05-24
forum: General Help
---

### Post by reformedgeek on 2005-05-24
i cannot get totem to play quicktime .mov(s) or wmv files.

I've apt-get(ted)/(got?) gstreamer0.8 and the gstreamer-plugins as well as the ffmeg and faad plugins.

As soon as i click on a .mov file, totem says it's unable to decode it.
I've check the addons folder and the qt and win codecs are all there. gst-register shows the ffmpeg is there too.

any ideas?
it works ok with mplayer...
 ](*,) 

help please!!

---

### Post by jkndrkn on 2005-05-24
Try this:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by reformedgeek on 2005-05-24
thanks,
but i tried that first.  it's worked before, but i reinstalled ubuntu a few days ago, and now it's not working...

it's very strange.
Totem plays music fine, even AAC files. just not movs

si
 ](*,)

---

### Post by lorap on 2005-05-27
hi friend!
try to install this codec - gstreamer0.8-ffmpeg
hope it'll solve your problem.
have a nice day.
pavel

---

### Post by ttp on 2005-05-27
IMO totem+gstreamer just doesn't work with all files. Try to install totem-xine.

---

### Post by twoseids on 2005-06-09
[QUOTE=ttp]IMO totem+gstreamer just doesn't work with all files. Try to install totem-xine.[/QUOTE]
 lorap, your fix worked for me - I was having the same problems but am now up and running with totem.  Thanks!

---

