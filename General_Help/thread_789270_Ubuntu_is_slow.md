---
title: "Ubuntu is slow"
date: 2008-05-10
forum: General Help
---

### Post by kevinstonge on 2008-05-10
I'm posting this in hopes of getting some good advice on FIXING the general and pervasive problem of slowness in ubuntu. I realize that Linux is not Windows (lnw), but if Ubuntu wants to compete with Windows, there has to be a way to speed things up significantly.

Bootup: Ubuntu boots up much slower than my XP install (I'm running dualboot w/2 partitions on one HDD, so I think its a fair comparison)

Firefox: This is the most unbearable aspect, firefox startup time is MUCH MUCH MUCH slower under Ubuntu (Firefox 3, Beta 5), and navigating from web page to web page is MUCH MUCH slower in firefox (differences of over five seconds per page usually).

My final complaint is not about speed, but about support for my printer over the network. I can install my Canon MX700 if it is connected to my PC via the USB wire, but I cannot get Ubuntu to see my MX700 on the network when it is connected to my router (without the USB wire connected). It is important for me to have the printer connected to the network rather than the workstation, this is unacceptable.

---

### Post by sekinto on 2008-05-10
Are you using Compiz as your window manager? It can take up quite a bit of resources. You may want to try a lighter WM if that is what you are using.

---

### Post by vanadium on 2008-05-10
This might be hardware issues. I find Hardy to be the speediest edition, both on my Dell laptop and an older 256 Mb Pentium desktop.

---

### Post by kevinstonge on 2008-05-10
I am using Compiz. However with 2GB of system RAM, is it really possible for compiz to slow down Firefox page load/rendering times?

---

### Post by daimaru on 2008-05-10
> **kevinstonge said:**
> I am using Compiz. However with 2GB of system RAM, is it really possible for compiz to slow down Firefox page load/rendering times?

I agree with kevinstonge. Since 8.04 my ubuntu seems way slower too. Maybe its a problem with having used update distribution instead of clean fresh install. I normally used clean install, but I must say that the 6 month distribution upgrade cycle is working to ubuntus disadvantage, if they can not figure out smooth updating without problems from previous versions. I really don't want to keep adjusting my whole ubuntu appearance programs etc every 6 month.
Firefox takes ages to load and it seems to hang alot too. Greyed out firefox window. It seems that my whole system has somehow slowed down.

---

### Post by kevinstonge on 2008-05-10
Just a side note - I did a clean install of 8.04 on my system.

---

### Post by someonestolemyname on 2008-05-10
I have found that the biggest thing to slow down Firefox is flash. After installing flash + compiz, Firefox is considerably slower. Bootup-wise, Ubuntu (for me at least) takes longer to get to login, but faster to a working desktop, a worthwhile tradeoff. For real speed, turn off compiz, remove panel applets, and turn of startup programs.

Works for me. Besides, anything that really stresses the comp tends to go a lot faster.

Daniel

---

### Post by inportb on 2008-05-10
> **kevinstonge said:**
> I am using Compiz. However with 2GB of system RAM, is it really possible for compiz to slow down Firefox page load/rendering times?

Absolutely. And only Firefox. At least the last time I tried compiz, I could not use Firefox at all. Does it work better in fullscreen mode?

---

### Post by keykero on 2008-05-10
I've found it very slow overall as well.  I thought it might just be the implementation of Gnome, but KDE was also slow.  It's the loading times of apps, screen re-draw, and things like opening folders in my case.  On WinXP on the same box, the difference is staggering (instantaneous loading & opening of pretty much everything).  While Hardy Heron certainly is quite usable, this definitely needs to be addressed in future versions.

---

### Post by yaknowwat on 2008-05-10
May i suggest Preload it helps a lot with startup times for applications.

Linux in general is extremely good at handling RAM and Processing usage but bad applications tend to screw up an experience such as Flash, Graphics drivers that don't have nearly as much support as their windows counterparts.

If firefox is greying out then chances are your window manager is compiz.

Xubuntu has really improved with the newest release its very fast and design nicely only taking 100 MiB of RAM on a normal boot unfortunately there is no Xfce Compiz (that is stable and well supported)

As far as printers go companies need to make drivers for linux so that they can be packaged with the OS.  Linux uses a different Printing style as compared to windows so using windows drivers isn't a stable option.

---

### Post by keykero on 2008-05-10
> **yaknowwat said:**
> May i suggest Preload it helps a lot with startup times for applications.

I was under the impression Preload was on by default in Hardy - it's running on mine (though it's possible I might have done that myself and don't remember).  Still even with it running, it's not as snappy as I feel it should be.

---

### Post by ThomasNovin on 2008-05-12
> **keykero said:**
> I was under the impression Preload was on by default in Hardy - it's running on mine (though it's possible I might have done that myself and don't remember).  Still even with it running, it's not as snappy as I feel it should be.

No, preload isn't even installed by default. I just installed it today on my fresh Hardy install.

---

### Post by keykero on 2008-05-12
> **ThomasNovin said:**
> No, preload isn't even installed by default. I just installed it today on my fresh Hardy install.

Thanks.  Have you noticed a difference?  I guess it takes time, though.  As a sort of bizarro experiment I just uninstalled it to see how the system feels.  I don't think it's any different.

---

