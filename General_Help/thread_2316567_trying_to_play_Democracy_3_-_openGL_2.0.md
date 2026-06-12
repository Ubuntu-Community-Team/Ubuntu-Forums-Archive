---
title: "trying to play Democracy 3 - openGL 2.0"
date: 2016-03-09
forum: General Help
---

### Post by ssmith2 on 2016-03-09
I'm trying to run a game through steam called democracy 3.

when I try to launch it I get the following error message

"Missing Open GL Extensions
required open GL extensions are not supported by your hardware
Open GL 2.0 or greater is required"


Any advice?
 
My pc is a U310 running a Intel® Pineview chipset and an Intel® Atom&#8482; CPU D525 

Processor Information:
    Vendor:  GenuineIntel
    CPU Family:  0x6
    CPU Model:  0x1c
    CPU Stepping:  0xa
    CPU Type:  0x0
    Speed:  1795 Mhz
    4 logical processors
    2 physical processors
    HyperThreading:  Supported
    FCMOV:  Supported
    SSE2:  Supported
    SSE3:  Supported
    SSSE3:  Supported
    SSE4a:  Unsupported
    SSE41:  Unsupported
    SSE42:  Unsupported
    
Network Information:
    Network Speed:  
    
Operating System Version:
    Ubuntu 15.10 (64 bit)
    Kernel Name:  Linux
    Kernel Version:  4.2.0-30-generic
    X Server Vendor:  The X.Org Foundation
    X Server Release:  11702000
    X Window Manager:  Compiz
    Steam Runtime Version:  steam-runtime-release_2015-06-12
    
Video Card:
    Driver:  Intel Open Source Technology Center Mesa DRI Intel(R) Pineview x86/MMX/SSE2


    Driver Version:  1.4 Mesa 11.0.2
    OpenGL Version: 1.4
    Desktop Color Depth: 24 bits per pixel
    Monitor Refresh Rate: 60 Hz
    VendorID:  0x8086
    DeviceID:  0xa001
    Number of Monitors:  1
    Number of Logical Video Cards:  1
    Primary Display Resolution:  1280 x 1024
    Desktop Resolution: 1280 x 1024
    Primary Display Size: 14.80" x 11.85"  (18.94" diag)
                                            37.6cm x 30.1cm  (48.1cm diag)
    Primary VRAM Not Detected
    
Sound card:
    Audio device: Realtek ALC662 rev1
    
Memory:
    RAM:  1990 Mb
    
Miscellaneous:
    UI Language:  English
    LANG:  en_AU.UTF-8
    Microphone:  Not set
    Total Hard Disk Space Available:  598765 Mb
    Largest Free Hard Disk Block:  556212 Mb
    
    



[ATTACH=CONFIG]267715[/ATTACH]

---

### Post by mastablasta on 2016-03-09
a bit of hacking.... you could try this:

[http://askubuntu.com/questions/19607/how-to-enable-opengl-2-0-and-webgl-on-gma-3150](http://askubuntu.com/questions/19607/how-to-enable-opengl-2-0-and-webgl-on-gma-3150)

2.0 seems tobe supported on Linux but not on windows.&#382;

your GPU is Intel GMA 3150

---

### Post by ssmith2 on 2016-03-11
Got it sorted :)

Found the intel driver suite for ubuntu and installed it. OpenGL is now working :)

Next  thing to find is why its made the ubuntu search so slow (about a 60 second delay per click) and fade in/outs terrible, but one thing at a time

---

### Post by Yellow Pasque on 2016-03-12
> **ssmith2 said:**
> Next  thing to find is why its made the ubuntu search so slow (about a 60 second delay per click) and fade in/outs terrible, but one thing at a time

If you read the bug report, you'll see that enabling the fragment shader extension causes issues like that which is why it's not enabled by default: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/696190/comments/3](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/696190/comments/3)

---

