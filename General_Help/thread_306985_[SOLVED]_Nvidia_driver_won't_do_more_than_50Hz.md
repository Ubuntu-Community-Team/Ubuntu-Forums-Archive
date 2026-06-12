---
title: "[SOLVED] Nvidia driver won't do more than 50Hz"
date: 2006-11-25
forum: General Help
---

### Post by reclusivemonkey on 2006-11-25
I have a clean install of Edgy. I have a NVIDIA FX5200. I have followed all the instructions on the Ubuntu Wiki here;

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

on installing nvidia. I've added the repos;

```

deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://amaranth.selfip.com edgy lrm

```

and followed all the instructions to install the nvidia drivers. Whatever I do I cannot get anything except 800x600 at 50Hz. Previously, I ran at 1152x864 at 75Hz. I am using exactly the same xorg.conf that worked this morning before I reinstalled;

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    # Option         "DPMS"
EndSection

```

with
```

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

```

and

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection  
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection  
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection  
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection  
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

I've also tried downloading envy to compile the very latest nvidia driver but I get exactly the same result. Please someone help!!!

---

### Post by twstokes on 2006-11-25
After reading your problem over again my post might not be all that informative. I was thinking you had the correct resolution but wrong refresh rate. For my NVIDIA I've used the 9629 drivers with Beryl without a problem. 

Here's my original post:

I had to change xorg.conf to make it run at 60Hz for my LCD. Take a look at an excerpt of my file below that might help.

```
Section "Monitor"
    Identifier     "DELL 1907FP"
    VendorName     "Dell"
    ModelName      "Dell 1907FP (Digital)"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "DELL 1907FP"
    DefaultDepth    24
    Option         "NoLogo" "1"
    Option         "dpms"
    Option         "Coolbits" "1"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024@60"
    EndSubSection
EndSection

```

---

### Post by reclusivemonkey on 2006-11-26
> **twstokes said:**
> After reading your problem over again my post might not be all that informative. I was thinking you had the correct resolution but wrong refresh rate. For my NVIDIA I've used the 9629 drivers with Beryl without a problem. 

Thanks for the post anyway. Yeah, I had the NVIDIA drivers and Beryl running fine yesterday morning. The only thing different is that I had some other repos in the list. I am going to try changing the repos today, see if that changes anything.

---

### Post by halfvolle melk on 2006-11-26
Under Dapper adding **Option         "UseEDID" "FALSE"** to the **Device** section solved it. Under Edgy with the 9629 driver I also only had a 50Hz option. After the above UseEDID -> false I have an additional 55Hz option. Not really what I'd hoped for, but maybe you'll get better results out of it.

---

### Post by reclusivemonkey on 2006-11-26
> **halfvolle melk said:**
> Under Dapper adding **Option         "UseEDID" "FALSE"** to the **Device** section solved it. Under Edgy with the 9629 driver I also only had a 50Hz option. After the above UseEDID -> false I have an additional 55Hz option. Not really what I'd hoped for, but maybe you'll get better results out of it.

DUDE I COULD KISS YOU :-D

That fixed my problem. Screen resolution claims the refresh rate is 50Hz but I know its not that as it would make my eyes bleed (I have a CRT BTW). More importantly, I now have 1152X864!!!

Many, many, many thanks for the post.

---

