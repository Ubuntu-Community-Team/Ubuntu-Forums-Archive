---
title: "Please Explain..."
date: 2005-08-01
forum: General Help
---

### Post by grofaz on 2005-08-01
...the difference between Totem-gstreamer and Totem-xine? I can't playback DVDs with Totem-gstreamer but I can with Totem-xine, why? Appreciate some knowledge, thanks!

---

### Post by drummer on 2005-08-01
Xine and GSteamer are different backends and the 2 different versions of totem just utilise the different libraries of code for multimedia playback.

As for dvd playback in totem-gstreamer i think you'd need to "sudo apt-get install gstreamer0.8-dvd" then "gst-register-0.8" in a terminal. I'm not entirely sure as I don't use Totem, I use either VLC or MPlayer. There are also other plugins for gstreamer if you search for 'gstreamer' in Synaptic. 

I hope that is a little enlightening.

---

