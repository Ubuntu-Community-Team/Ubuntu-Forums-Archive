---
title: "Beryl, Nvidia, and kiba-dock issues"
date: 2006-10-30
forum: General Help
---

### Post by JedTheHead on 2006-10-30
I have this all working on my laptop with a crappy ATI 9200 Radeon Mobility card and it is smooth as silk and really pleases me ;)

However: on my desktop machine I have Edgy, beryl, Nvidia, etc. install.  I followed this thread to get it up and running:  

[http://ubuntuforums.org/showthread.php?t=263851&highlight=bind]("http://ubuntuforums.org/showthread.php?t=263851&highlight=bind")

I have tried BOTH drivers for the NVIDIA card, and have gone through all the references to my problem(s) and none have seemed to work yet. 

When I launch beryl, all is well and good - as long as open only "regular windows".  If I drag an icon, move a message in Evolution, launch kiba-dock, or do anything that doesn't involve a "traditional window", I get the output below until I kill beryl, and evrrything on the desktop slows down.  

> 
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 to texture
beryl: pixmap 0x32001be can't be bound to texture
beryl: Couldn't bind redirected window 0xa00006 


My xorg.conf:

> 

Section "Device"
    Identifier     "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Driver         "nvidia"
EndSection

Section "Screen"

  # If you are using an older version of compiz that
  # does not support rendering into the Composite
  # Overlay Window, you will need to disable clipping
  # of GLX rendering to the X Root window with this
  # option, or you will get a blank screen after
  # starting compiz:
  #    Option "DisableGLXRootClipping" "True"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Monitor        "E90f+-3"
    DefaultDepth    24
    Option         "TripleBuffer" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection




I have tried this too, with the exact same result:

> 
Section "Device"
    Identifier     "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Driver         "nvidia"
    Option          "TripleBuffer" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

  # If you are using an older version of compiz that
  # does not support rendering into the Composite
  # Overlay Window, you will need to disable clipping
  # of GLX rendering to the X Root window with this
  # option, or you will get a blank screen after
  # starting compiz:
  #    Option "DisableGLXRootClipping" "True"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Monitor        "E90f+-3"
    DefaultDepth    24
#    Option         "TripleBuffer" "true"
#    Option         "RenderAccel" "true"
#    Option         "AllowGLXWithComposite" "true"
#    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection



Any help would be greatly appreciated!!!

Thanks!

---

### Post by theshaw on 2006-11-07
Any luck with this?  I'm looking into the same issue you've described.

---

### Post by ubs on 2006-11-09
Same problem here :(

---

### Post by JedTheHead on 2006-11-09
No progress here either.  I need to spend some time really digging into this but haven't been able to as of yet.  I was hoping others had run into it and had a solution.  It appears to be Nvidia related.  I have a GF 6500 chipset, btw.

Thanks!

---

