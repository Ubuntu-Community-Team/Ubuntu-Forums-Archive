---
title: "convert .ogg to mpg"
date: 2007-06-04
forum: General Help
---

### Post by hraposo on 2007-06-04
How I convert .ogg to mpg

---

### Post by Shazaam on 2007-06-04
.ogg is audio.
.mpg is video
If you want to strip audio from movies there are quite a few tools out there (too many to list).
.ogg to mp3- any converter should work. I use "sound converter" from synaptic.

---

### Post by php-trivandrum.org on 2008-02-24
some one said
[INDENT].ogg is audio.
.mpg is video[/INDENT]

OGG supports video too, infact the record-my-desktop records and saves in ogg format, but we need MPG or FLV such that this can be included into a cd based presentation.

---

### Post by banditxkr on 2008-02-24
perhaps he meant mp3 

if so all you have to do is download soundkonverter, great program that supports most types of audio.

---

### Post by HermanAB on 2008-02-24
The easiest way to transcode video is with avidemux.

Cheers,

Herman

---

### Post by keinea on 2008-06-07
I am currently running Ubuntu 8.04, Hardy Heron on my laptop.  I previously recorded some desktop activity using 'gtk-recordMyDesktop'.  This application works great for that sort of thing.  It saved the capture as a video/x-theora+ogg file. The dimensions of the video was 1280 x 1024, at 30 frames per second (FPS), with no audio recorded during the session.  

Using mencoder, I was able to convert the ogg files to MPEG-2 video, at 1280 x 1024, and 30 FPS, with very little loss to the video quality.  I don't remember which library it complained about not finding when I first ran it, but once I located and installed the missing library file using Synaptic, the process worked quite well and executed very quickly.  

Mencoder is a command line utility, and the command I used was:

  mencoder screencapture.ogg -o screencapture.mpg -ovc lavc -lavcopts vcodec=mpeg2video -oac copy -ofps 30 -of mpeg


I found some helpful information on mencoder at:

[http://gentoo-wiki.com/TIP_MEncoder_Tips_and_Tricks](http://gentoo-wiki.com/TIP_MEncoder_Tips_and_Tricks)
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

Cheers,
Keith
8)

---

