---
title: "Kiba-dock help autoconf2.13"
date: 2006-09-29
forum: General Help
---

### Post by jman2807 on 2006-09-29
Alright I was following the guide from [http://ubuntuforums.org/showthread.php?t=263810](http://ubuntuforums.org/showthread.php?t=263810) and I ran into some problems. The autogen gave me a truckload of errors so I followed the tip and installed automake 1.9 and removed automake1.4 and then the autogen worked perfectly, but now I am getting some more errors as follows:

kiba-render.c: In function ‘load_icon’:
kiba-render.c:82: error: ‘rsvg_resize_func’ undeclared (first use in this function)
kiba-render.c:82: error: (Each undeclared identifier is reported only once
kiba-render.c:82: error: for each function it appears in.)
make[2]: *** [kiba-render.o] Error 1
make[2]: Leaving directory `/home/jerrod/kiba-dock/dock'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jerrod/kiba-dock'
make: *** [all] Error 2

And I am sure that it is becuase of autoconf 2.59a-7 but whenever I use synaptic and try to remove it, it removes autoconf 2.13 and I cant get 2.13 installed without 2.59. Is there anyway to force it to use 2.13 or another method I can use to compile it. Thanks in advance.

---

