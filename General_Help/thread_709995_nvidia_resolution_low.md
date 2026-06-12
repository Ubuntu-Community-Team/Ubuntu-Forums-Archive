---
title: "nvidia resolution low"
date: 2008-02-28
forum: General Help
---

### Post by creznedmick on 2008-02-28
Greetings
 Running Gutsy with a change of video cards. Now installed  nVidia Corporation NV31 [GeForce FX 5600]. With the open source drivers I get a resolution of 800x600 max. With proprietry drivers 640x480 only.
Below is a copy of xorg.conf, I only change "nvidia" to "nv" to change drivers . Yes I have tried; sudo dpkg-reconfigure -phigh xserver-xorg  & sudo dpkg-reconfigure  xserver.xorg. Both end up with the same .conf file


Section "Device"
        Identifier      "nVidia Corporation NV31 [GeForce FX 5600]"
        Driver          "nv"   #"nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "IBM G96"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV31 [GeForce FX 5600]"
        Monitor         "IBM G96"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Thanks for any help 
Michael

---

### Post by erginemr on 2008-02-28
Hi Michael,

Can you inform us about your monitor too, please?

---

### Post by creznedmick on 2008-02-29
Greetings
monitor ibm G96 
refresh:  H: 30-95, V; 50-160
anything else please ask
Thanks Michael

---

### Post by creznedmick on 2008-02-29
what seems to me to be the relavent section of Xorg.O.log


(II) NVIDIA(0): NVIDIA GPU GeForce FX 5600 (NV31) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.31.20.38.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5600 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

MIchael

---

### Post by brabo on 2008-02-29
hi,

i had the same issue, also with nv driver

i modified /etc/X11/xorg.conf so that 1280-1024 was the ONLY mode in it,
and added horizontal and vertical as :
Section "Monitor"
	Identifier	"CB773F-NJ"
	HorizSync	30.0 - 69.9
	VertRefresh	48.0 - 100.0
	Option		"DPMS"
to the monitor section.
after that, it did perfectly 1280*1024. if you try this, first copy xorg.conf to xorg.conf.good, so that if it fails and gdm won't start, you can change back through a shell login ;)

brabo.

---

### Post by erginemr on 2008-02-29
If this is your monitor:
[http://www.superwarehouse.com/IBM_G96_White_19_CRT_Monitor/65490AN/p/142696](http://www.superwarehouse.com/IBM_G96_White_19_CRT_Monitor/65490AN/p/142696)
[http://www.etech4sale.com/IBM_6549_4AN_G96_19-Inch_White/WD15/partinfo-id-119721.html](http://www.etech4sale.com/IBM_6549_4AN_G96_19-Inch_White/WD15/partinfo-id-119721.html)

then it is a real mystery why Ubuntu cannot recognize your monitor's capacity, since my mouth started drooling looking at that 19" rig.

I second to brabo's suggestion, which looks like the most reasonable way to follow.

---

### Post by erginemr on 2008-02-29
I have one question: What is the resolution of the desktop when you boot your computer with the Ubuntu Live CD?

---

### Post by creznedmick on 2008-02-29
Greetings
seems to have worked a treat 
Thanks again Michael

---

### Post by erginemr on 2008-02-29
> **creznedmick said:**
> Greetings
seems to have worked a treat 
Thanks again Michael

Great news! :guitar:

But can you report exactly what you did to guide any one visiting this thread later on? You should also make sure that the fix is permanent by restarting your system.

And it is up to you, but I think you should thank brabo for his help.

**To close a thread **-> Select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

**To thank someone **-> Click on the blue ribbon/badge on the bottom right part of the post(s), whose author(s), you believe, has helped you fix your problem.

Take Care and Have Fun! :popcorn:

---

### Post by creznedmick on 2008-02-29
Greetings
I went back into the .conf file and left the part about vert and horz refresh in and reput in the various possible screen resolutions. Now I have the choices again (1280x1240 plenty small enough formy eyes). It seems it was somehow mucking up the refresh rates until specified in the .conf file?
As to the live CD I can`t remember exactly but I know it was a better than 800x600
Thanks again  Michael

---

### Post by creznedmick on 2008-02-29
Greetings
OK to fix the problem with resolution stuck on 640x480 or at least inmy case

open /etc/X11/xorg.conf in text editor as root
find "Monitor" section
Add your Vertical (VertRefresh) and Horizontal (HorizSync) refresh rates. In my case it looked like this

Section "Monitor"
    Identifier     "IBM G96"
    HorizSync      30.0 - 95.0
    VertRefresh    50.0 - 160.0
    Option         "DPMS"
EndSection

use keys Alt + Ctrl + Backspace to restart display
And that is what worked for me

Thanks again to barbo and those who helped 
Michael

---

