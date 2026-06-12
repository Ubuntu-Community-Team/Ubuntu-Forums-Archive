---
title: ".3gp"
date: 2005-05-24
forum: General Help
---

### Post by Oblivious Hazard on 2005-05-24
I was wondering if there is a way i can watch my .3gp files?

---

### Post by pdk001 on 2005-05-24
put ctrl+H at the same time in the your home folder
or type "ls -a" on the console

---

### Post by jcooper on 2005-05-25
I think the problem is watching video files recorded on latest mobile handsets, rather than watching hidden files.

I have a nokia 6630 and would also like to know if anyone has successfully watched a sgp video clip in linux?

I doubt the codec is freely available from nokia; would it be possible to add it to gstreamer as a w32codec?

---

### Post by TheCondor on 2005-05-25
Hello, I successfully transfered the videos i took from my cell phone ( nokia 7610 ) and they all worked with xine, but had no sound. You can try it out

---

### Post by nbcthreat on 2005-07-05
I'm working on the same issue. Saw this blog post today, but I also had no sound when playing in Xine or VLC. Any idea how to get the audio working?

[http://blog.chris.de/archives/22_Nokias_3gp_Files.html](http://blog.chris.de/archives/22_Nokias_3gp_Files.html)

(blog excerpt below)

 I noticed that Nokia's .3gp files are simpy ffh263 encoded :-) Therefore, it's easy to get MPlayer playing those videos. Follow me...

First of all, download MPlayer and install it. (Note that mplayer should have support for ffmpeg, so ffmpeg development libraries have to be installed). If you try to watch a video from your Nokia with mplayer right now, it will most likely fail with an error message like this one:

Cannot find codec matching selected -vo and video format 0x33363273.

This is easily fixed though:

1. Copy the codecs.conf file from the etc/ directory in your mplayer sources to ~/.mplayer/
2. Add the following line under the videocodec ffh263 (just search for it) section in this file:

format 0x33363273

Watching videos should work now. Also converting is possible :-)

This command converts the .3gp to a DivX4:
# mencoder -ovc divx4 -nosound "Video.3gp" -o Video.avi

I'm still profiling a bit. I will update this entry, as soon as I found an appropriate bitrate and got sound conversion working.

Good luck! :-)

---

### Post by laxmanbalu on 2008-05-12
> **jcooper said:**
> I think the problem is watching video files recorded on latest mobile handsets, rather than watching hidden files.

I have a nokia 6630 and would also like to know if anyone has successfully watched a sgp video clip in linux?

I doubt the codec is freely available from nokia; would it be possible to add it to gstreamer as a w32codec?

Hello
What are the codecs for 3gp file with gst-launch tool. Because I am not getting audio and video in 3gp file. So please explain it to me . How to get audio and video in gstreamer.

my mail id [email]laxmanbalu@gmail.com[/email]

---

