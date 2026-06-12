---
title: "Totem: Video codec 'FMP4' is not handled."
date: 2005-05-20
forum: General Help
---

### Post by spiraloid on 2005-05-20
I received this error when trying to play an AVI I encoded with mencoder:

Totem could not play 'file:///home/mike/render/rotation.avi'.

Video codec 'FMP4' is not handled. You might need to install additional plugins to be able to play some types of movies.

I am using totem-xine. No I am not going to change to totem-gstreamer because it has nothing but problems for me. I already tried that anyway, and it also did not work. The command line I used for encoding the video was:

mencoder "mf://*.tga" -fps 30000/1001 -ofps 30000/1001 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2400:v4mv:mbd=2:trell:cmp=3:subcmp=3:mbcmp=3:autoaspect:vpass=1 -o rotation.avi

Any ideas? I'm probably missing a lib, but I can't figure out which one it would be. :-/ It's not ffmpeg, I can say that much.

Mike

---

### Post by spiraloid on 2005-05-20
Turns out I'm not missing a library, and this I guess is a problem with xine (the video did play fine in mplayer, I forgot to mention that). The way to "fix" it is to use avifix (part of the transcode package, which is available from the marillat repositories) to set the header to DX50:

avifix -i rotation.avi -F DX50

All that really needs to happen I guess is for xine or whatever library it's using to recognise FMP4 tag as an mpeg4 video since it appears that is what newer versions of libavcodec are doing. The video was encoded using libavcodeccvs from marillat.

---

