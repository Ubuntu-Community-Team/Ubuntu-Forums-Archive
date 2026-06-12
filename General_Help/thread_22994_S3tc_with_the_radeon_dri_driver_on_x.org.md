---
title: "S3tc with the radeon dri driver on x.org"
date: 2005-03-30
forum: General Help
---

### Post by zep24 on 2005-03-30
Hi, 

I'm trying to get s3tc compression working on my radeon 9200 using the radeon driver from x.org 6.8.2 and the instructions on [this](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html)  
site. For now without success.
I get a libtxc_dxtn.so libray installed in my /usr/lib directory but the radeon driver doesn't seem  to use it: glxinfo doesn't report it and doom3 log says it's missing. 
I tried to tweak my system with driconf or set the force_s3tc_enable option to true in my .drirc file but it doesn't change anything. Has anyone managed to get s3tc working with these drivers?

---

### Post by Seth Quarrier on 2007-03-18
This worked fine on my Mac Mini running Feisty. I just did a make and make install and it worked. Out of curiosity if you run eg. Saurbraten, do you get the error 

implementation error: external dxt library not available

That is the error I got before I installed the external dxt library which worked with no further configuration. I would guess that if you are not getting this error then s3tc is disabled. If you are then s3tc is enabled and you are having issues with the driver. I enabled s3tc with driconf.

Hope this helps

---

