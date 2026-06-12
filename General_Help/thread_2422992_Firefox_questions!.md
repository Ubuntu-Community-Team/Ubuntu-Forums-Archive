---
title: "Firefox questions!"
date: 2019-07-16
forum: General Help
---

### Post by cellsite60 on 2019-07-16
Hello all!

I'm a little curious to why Firefox not working OOTB on certain video sites in Ubuntu but it does work when installed in Elementary OS?

I've done some checks to find out why, for example: 
[html5test.com]("http://www.html5test.com") shows some differences, mainly under Video it shows **H.264 support** is marked as "yes" in Elementary but not in Ubuntu.
[youtube.com/html5]("http://www.youtube.com/html5") shows **H.264** and **MSE & H.264** marked in Elementary but not in Ubuntu. (youtube works fine on Ubuntu though)
In both instances i've tested with a fresh install and no Add-On's and both had the **OpenH264 Video Codec** installed as it comes originally.

If i install the **ffmpeg plugin for gstreamer **from Ubuntu Software Center it all works fine and shows the same test results as Elementary.

Isn't Ubuntu and Elementary pulling Firefox from the same repository if i re-install Firefox in Ubuntu?

---

### Post by Impavidus on 2019-07-16
I don't know all specifics, but there are many different video codecs, many of which have restrictive licenses. Different Linux distros make different choices on what codecs to install by default.

---

### Post by uRock on 2019-07-16
What you're seeing has nothing to do with Firefox itself. I am not very sure about Elementary OS, but checking the box in this screenshot installs the packaging to support those formats.

---

### Post by cellsite60 on 2019-07-16
Alright, cheers guys for the answers :-)

---

