---
title: "Jpeg2yuv works but mplayer, vlc barf...ideas?"
date: 2005-08-17
forum: General Help
---

### Post by reuben on 2005-08-17
Hi, I'm trying to stop motion animate a bunch of JPGs I have, following the instructions on this page:

[https://sourceforge.net/docman/disp...p_id=5776#ss4.1](https://sourceforge.net/docman/disp...p_id=5776#ss4.1)

I am using the command:

jpeg2yuv -f 4 -b49 -n 161 -I p -j photo%04d.JPG | yuv2lav -o stream_without_sound.avi

Mplayer doesn't like the output *at all*. Vlc plays it, but drops frames part way in (claiming "computer too slow" -- don't think so! AMD64 3200 1GB RAM). The images were originally 1024x768, but I dropped their resolution to 640x480.

Is there another way I can do this? Or what should I do to prevent the framedropping from happening?

Thanks

---

