---
title: "compile a driver"
date: 2007-05-13
forum: General Help
---

### Post by tomlj on 2007-05-13
Please can someone tell me how to compile and install this a driver? 

[http://cvsweb.xfree86.org/cvsweb/xc/programs/Xserver/hw/xfree86/drivers/trident/trident_video.c](http://cvsweb.xfree86.org/cvsweb/xc/programs/Xserver/hw/xfree86/drivers/trident/trident_video.c)

I need to know the commands and procedure I need to follow, as I'm new to this,

Thanks
Tom

---

### Post by heimo on 2007-05-13
Is there some special reason for needing to compile it? I think Ubuntu comes with trident driver for Xorg.

---

### Post by tomlj on 2007-05-13
Hi

Yes, I'm having a serious video overlay problem (left offset wrong, video wraps round screen).
In the notes it says that this driver has been update to address this, 

Thanks
Tom

---

### Post by heimo on 2007-05-13
> **tomlj said:**
> 
Yes, I'm having a serious video overlay problem (left offset wrong, video wraps round screen).
In the notes it says that this driver has been update to address this, 


Ok. Did you try xvidtune to correct it?

Sorry, I can't help with compiling that driver - other than point to some generic instructions. (./configure; make; make install)

---

### Post by tomlj on 2007-05-13
I haven't tried xvidtune. Is it in the settings somewhere? 

Is compiling a driver problematic then? Should I ask in a different forum, or give up?

Tom

---

### Post by heimo on 2007-05-13
> **tomlj said:**
> I haven't tried xvidtune. Is it in the settings somewhere? 


I think xvidtune is installed by default. Open a terminal (Applications->Accessories->Terminal) and type xvidtune [enter]. Then you should be able to tweak your screen left/right etc, and click show to see modeline (a bunch of numbers) on the terminal window. If you can get your screen fixed this way, you could put that modeline into xorg.conf, so that it gets loaded automatically.

I don't know how hard it is to compile Xorg drivers. I think your link is to another version of X server than what Ubuntu uses, so that'd be a problem.

---

### Post by tomlj on 2007-05-13
No luck, I'm afraid...

---

### Post by heimo on 2007-05-13
What resolution do you use? Is it very old card? Have you tried changing to vesa driver, does that remove the problem?

---

### Post by tomlj on 2007-05-13
Hi 

1024*768. The vesa driver works, however the video plays back very badly. at least it's in the right place though. The video with the trident driver plays back very smoothly, although it overlaps itself.

Here is a relevant posting (I think):  [http://bellet.info/XVideo/trident.html](http://bellet.info/XVideo/trident.html)

Yes, it's an old card, but because of my lcd panel I'm stuck with it :(

All video is messed up dvd xvid etc... everything else is great..

Tom

---

### Post by heimo on 2007-05-13
Oh, ok. I didn't understand the problem correctly at first.

It's possible that trident driver is old in Ubuntu. What I suggest is that you file a bug report in Launchpad for this.  [http://www.launchpad.net/](http://www.launchpad.net/) So that it'll hopefully get included in future versions and possibly even fed upstream (included in Xorg) if this patch hasn't been included yet. Dates on both links you provided are really old, so it may be quite difficult to adapt it for Xorg - I don't know. But I'm sure it's not as simple as taking that .c file, and compiling it.

---

### Post by tomlj on 2007-05-13
I see,

I just found someone who has updated the driver in a different ubuntu version (I'm using 7.04) > After i installed  a new version of ubuntu (the Edgy Eft) on my tarantula, i found that my video card wasnt work properly especially when im doing fast scrolling, after i searching it through many search engine just to find some "typical problems" (noted: ive already configure my xserver for many times but wont work), i found a link that make my video card works perfect on Edgy

just do this steps

    #apt-get install xorg-dev
    #apt-get build-dep xorg-server
    #wget -c [http://xorg.freedesktop.org/releases/individual/\](http://xorg.freedesktop.org/releases/individual/\)
    driver/xf86-video-trident-1.2.3.tar.bz2
    #tar xjf xf86-video-trident-1.2.3.tar.bz2
    #cd video-trident-1.2.3
    #./configure
    #make
    #make DESTDIR=/tmp/xorg_ install
    --- Backup old driver
    #sudo mv /usr/lib/xorg/modules/drivers/trident_drv.so /usr/lib/xorg/modules/drivers/trident_drv.so.bak
    --- Install new one
    #cd /tmp/xorg_/usr/local/lib/xorg/modules/drivers/
    #sudo mv * /usr/lib/xorg/modules/drivers/

    Restart X and your're set.


references : [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-trident/+bug/67620](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-trident/+bug/67620)
thx to Stefan Sonnenberg-Carstens for the steps, and Alan Hourihane for the trident drivers patch

But again I don't really know what to do..

Cheers
Tom

---

### Post by heimo on 2007-05-13
Well. Those same instructions may work in Feisty too. Quite detailed step-by-step instructions actually. Those commands go to a terminal and at least some of those you need to run as root (prefix with "sudo" or run "sudo -i" before the commands)

---

### Post by tomlj on 2007-05-13
I'll try it then, and let you know if it works.
Thanks for all your time Heimo

---

