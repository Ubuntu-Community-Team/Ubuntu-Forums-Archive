---
title: "gst-monkeysaudio-0.8.2"
date: 2008-06-11
forum: General Help
---

### Post by jrincon87 on 2008-06-11
Hey, I just downloaded that package but haven't been able to compile it. The following message appears when I do ./configure:

> checking for   gstreamer-0.8 >= 0.8.0   gstreamer-plugins-0.8 >= 0.8.0... configure: error: you need gstreamer development packages installed !


I already installed libgstreamer0.10-dev and libgstreamer-plugins-base0.10-dev. What am I lacking of? 
Thanks.

---

### Post by zvacet on 2008-06-12
It looks  like you need gstreamer-0.8 which is not in repos.You can look [here]("http://aidanjm.wordpress.com/") and  see if it is of any help to you.Alternatively you can look [here]("http://morgoth.free.fr/ubports/?d=gutsy") and download libmac2,libmac2-dev and monkeys-audio ,but these are Gutsy packages so I don´t know if they work in Hardy.

---

