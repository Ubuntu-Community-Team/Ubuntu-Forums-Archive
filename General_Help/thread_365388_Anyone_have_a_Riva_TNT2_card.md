---
title: "Anyone have a Riva TNT2 card?"
date: 2007-02-19
forum: General Help
---

### Post by plb on 2007-02-19
If so, do the nvidia drivers work for you?

---

### Post by allwin on 2007-02-19
I think so.  I have a 64Meg, AGP 4x card in a 2002 model Dell desktop.  Use that package called ENVY to install the 9631 version driver and it works with Beryl, mostly, except for the BLACK WINDOW bug which is a fault of nVidia.  

I had an older nVidia card on an even older system which I could not get to work (16Meg) with anything but the legacy drivers which don't support Beryl.  So for $15 I ordered a newer ATI card on ebay...hard to find AGP 1x-2x antique, but it works with Beryl, too, and even better than nVidia for me.

---

### Post by MrFSL on 2007-02-19
Just put together a machine with a Nvidia TNT2 Riva Graphics AGP card. I installed the driver using [Automatix]("http://getautomatix.com") and have had no problems. Everything went off without a hitch.

---

### Post by robbr on 2007-03-08
Yes, I've had recent success with a Riva TNT2 card and the nvidia-glx-legacy driver.  I used the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=376481") and everything works really well.

In fact installing that driver is the only means by which I can use Firefox for more than $seemingly_random_duration without full system hard lockup.

---

### Post by dcstar on 2007-03-08
> **robbr said:**
> Yes, I've had recent success with a Riva TNT2 card and the nvidia-glx-legacy driver.  I used the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=376481") and everything works really well.
.........

I purchased a second-hand one at a swap meet a few weeks ago and it works fine with the legacy driver.

Just make sure that the highlighted line is in your xorg.conf:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV5 [RIVA TNT2/TNT2 Pro]"
    Monitor        "StudioWorks"
    DefaultDepth    24
**    Option         "AllowGLXWithComposite" "1"**
```

---

### Post by punong_bisyonaryo on 2007-03-28
Good day!

Everything seems fine, glxinfo looks fine, etc., but I get an GLX_EXT_texture_from pixmap fail when starting beryl. I've also tried following the steps here, [http://ubuntuforums.org/showthread.php?t=389872&highlight=beryl+tnt2](http://ubuntuforums.org/showthread.php?t=389872&highlight=beryl+tnt2), and also tried the sudo dpkg-reconfigure xserver-xorg as well. I resolved my earlier beryl "composite fail" problems, but I seem to be stuck on this one.

Help!

---

### Post by russell.h on 2007-03-28
I have a Riva TNT2 Model 64/ 64 Pro (or somesuch, note that this is actually a 32mb card with a deceptive name as far as I can tell) in one of my old computers running Dapper (it had Edgy until recently). 

I just installed nvidia-glx-legacy from the repositories and everything worked fine. 

Of course I never tried anything fancy with that (the computer has 256mb of SD RAM to go with its sweet video card).

---

### Post by medya on 2007-04-25
read this blog post[URL="http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html"] how to install TNT2 driver 
[/URL]

---

