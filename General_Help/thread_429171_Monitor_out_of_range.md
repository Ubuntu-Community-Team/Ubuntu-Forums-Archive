---
title: "Monitor out of range?"
date: 2007-05-01
forum: General Help
---

### Post by Jack the R on 2007-05-01
At startup I get the error message "monitor out of range, set to 1280 X 1024."  The machine seems to hang up during this period and the screen is distorted.

I have an LCD and the native resolution is indeed 1280 X 1024.  Buuuuut - xdpyinfo shows the screen* is* at 1280 X 1024 :confused: 

xorg.conf has 'Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"'

What is going on here?  It appears the rez is set correctly, and yet I get an annoying error screen.

---

### Post by phiphedog on 2007-05-01
Sounds like a refresh rate error. Have you tried changing this?

See this post for more info
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Jack the R on 2007-05-01
I have now :)

Still not working :(

The error does also say @ 60 hz.  

I went to [here](http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1280+1024&FREQ=60) and got my modeline.  I typed in modeline and the commented out section above it.  That didn't work.  Then I added the four lines above the comment.  Then X wouldn't start at all.  

Maybe the problem is here - 

> Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1024x768_75.00"
    EndSubSection
EndSection

Is the 75 in "1024x768_75.00" the refresh rate?  I don't have the refresh rate there.  Maybe there's a whole lot of stuff I don't need in my xorg.conf -

[img]http://www.extinctionlevelevent.com/misc/linux/monitor01.png[/img]

Do I really need multiple display subsections, with multiple resolutions each?  I think 1280X1024 with 24 bit color would be fine.

---

### Post by phiphedog on 2007-05-01
Here's my xorg.conf (or part of it) it just uses the generic monitor although I have an LG-T910B

Maybe you could try adding in the lines for my monitor and commenting out yours and see if the generic monitor settings work.

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
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
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by phiphedog on 2007-05-01
This may also help
[http://ubuntuforums.org/showpost.php?p=253944&postcount=3](http://ubuntuforums.org/showpost.php?p=253944&postcount=3)

---

### Post by Jack the R on 2007-05-01
> **phiphedog said:**
> This may also help
[http://ubuntuforums.org/showpost.php?p=253944&postcount=3](http://ubuntuforums.org/showpost.php?p=253944&postcount=3)

Any idea what I would enter for HorizSync?

I tried the first two values alone, but that didn't do it.

Is it possible this is normal?  Once Ubuntu starts, the picture is fine and stable.  It only has the out-of-sync screens at startup and shutdown.

---

### Post by phiphedog on 2007-05-01
Do you have the manual for your monitor? You may need it.

[http://ubuntuforums.org/showthread.php?t=422782&highlight=refresh+rates](http://ubuntuforums.org/showthread.php?t=422782&highlight=refresh+rates)

---

### Post by dcstar on 2007-05-01
> **Jack the R said:**
> Any idea what I would enter for HorizSync?

I tried the first two values alone, but that didn't do it.

Is it possible this is normal?  Once Ubuntu starts, the picture is fine and stable.  It only has the out-of-sync screens at startup and shutdown.

AFAIK the startup and shutdown screens have nothing to do with the X server, they are using a basic VESA mode which you may be able to adjust with a Grub boot option.

---

### Post by Jack the R on 2007-05-01
> **dcstar said:**
> AFAIK the startup and shutdown screens have nothing to do with the X server, they are using a basic VESA mode which you may be able to adjust with a Grub boot option.

I think you may have it - once X starts, everything is fine.  So how does one edit Grub?

---

### Post by Jack the R on 2007-05-02
I've looked through menu.lst, but I don't see anything graphical in it, other than the "pretty colors" line.

Any ideas?

---

