---
title: "Better resolution(Ubuntu 6.10)"
date: 2006-11-05
forum: General Help
---

### Post by dc12volthippy on 2006-11-05
Is there any way to get a resolution of 1280X1024 on Ubuntu 6.10?

---

### Post by Synikk on 2006-11-05
If the resolution dialogue doesn't offer you the option of a 1280x1024 resolution, you may need to edit xorg.conf by hand to insert the option.

---

### Post by deeble on 2006-11-05
As Synikk says... 
You need to sudo your text editor /etc/X11/xorg.conf.Else the file is read only!
I enter the horizontal and vertical rates for my monitor to look like this:
Section "Monitor"
    Identifier     "NEC FE1250"
    HorizSync       31.0 - 110.0
    VertRefresh     55.0 - 160.0
    Option         "DPMS"
EndSection

Then add 1280 x 1024 just for the high colour depths:
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17GL [Quadro4 200/400 NVS]"
    Monitor        "NEC FE1250"
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
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
Gives me 1280 with 85Hz refresh rate. Which is how I like it.
My HorizSync and VertRefresh are high as it's a 22" monitor. Find your values in the monitor manual or online.

---

### Post by dc12volthippy on 2006-11-06
How do you sudo it?

---

### Post by John.Michael.Kane on 2006-11-06
dc12volthippy Type **sudo gedit /etc/X11/xorg.conf**

Heres a thread which may help as well. [http://ubuntuforums.org/showthread.php?t=289269&highlight=modeline](http://ubuntuforums.org/showthread.php?t=289269&highlight=modeline)

---

### Post by fragos on 2006-11-06
The ability to run higher resolutions requires a driver specific for your video card or chip set.  The "vesa" generic driver will default to lower resolutions regardless of whats in xorg.conf.

---

### Post by strabes on 2006-11-06
I agree with fragos. I would recommend installing the latest driver for your video card. This process would differ depending on whether you have an ATI or Nvidia card. For ATI, look here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I'm not sure about an nvidia site as I have never used an nvidia card for reasons that I will not mention in order to not start an argument :) sorry nvidia users

---

### Post by fragos on 2006-11-06
Compiling proprietary drivers can have its challenges.  Ubuntu has simplified the process.  Make sure the universe and multiverse repositories are enabled and in Synaptic install nvidia-glx.

---

