---
title: "Is my Geforce GTX 650 to weak to run 2 monitors?"
date: 2018-01-05
forum: General Help
---

### Post by marby188 on 2018-01-05
I'm having this screen setup:
1 x DELL U2713HM running on 2560x1440px
1 x DELL P2217H running on 1080X1920px

When resizing/moving windows they flicker on the edges. When scrolling webpages it flickers horizontally inside the windows.
Is this graphic card to weak? Is there anything I can do to make it run smoother?

System Ubuntu 16.04 LTS
Driver Nvidia binary driver 384.90

Thanks in advance for your answers.

---

### Post by pqwoerituytrueiwoq on 2018-01-05
Been a while since i used 2 displays with diff resolution (ubuntu 10.04 i think), but IIRC there was 2 ways you could do it in nvidia settings, one would allow out of bounds mouse if the screen were not the same height which option are you using?
i have used a GT 430 ad a GT 630 for dual displays in the past they both handled the job fine; i know the 630 ran compiz without issue with unity, so a 650 should have no problem

---

### Post by marby188 on 2018-01-06
I don't think I want out of bounds mouse, I want it to stay within the screen areas. Couldn't find the option in Nvidia x server settings either. I think it's frustrating that ubuntu isn't running smoother. Why can't it flow just like an macbook?

---

### Post by pqwoerituytrueiwoq on 2018-01-06
i think the out of bounds mouse thing was fixed a few years ago, but there are 2 features, one runs good the other is sluggish, i think there was some niche feature difference
i plugged in a second display 
If you are using Xinerama i think it will be slow or at lest it was back then, the option appears if you use separate x screens
[URL="http://i.imgur.com/XVoInqX.png"]
  [IMG]http://imgur.com/XVoInqXm.png[/IMG]
[/URL]
to answer the rhetorical question you are not using the nvidia official driver, the legacy nvidia driver still works better than the open source driver (Which has made leaps and bounds of improvements over the last few years) on my old crap Geforce 8200m laptop
you are better off trying to get that working

---

### Post by marby188 on 2018-01-07
I have now installed the official NVIDIA-Linux-x86_64-384.111 driver. Additional drivers looks like this:

[IMG]http://i63.tinypic.com/9sc8p2.jpg[/IMG]

Has it been installed correctly? There is still a little lag and Nvidia x server settings is not available anymore

---

### Post by pqwoerituytrueiwoq on 2018-01-07
i guess you downloaded the driver from nvidia's website
that will work until your kernel updates (should be seeing one in the next few days to patch specter/meltdown), but if you don't want the hassle remove it
[https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers](https://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers)
then select he 384.98 or 387.34 driver in thar window, the 388 driver should show up sooner or later

---

### Post by marby188 on 2018-01-08
Ok, thanks for your patience [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("https://ubuntuforums.org/member.php?u=865458") :-)

---

