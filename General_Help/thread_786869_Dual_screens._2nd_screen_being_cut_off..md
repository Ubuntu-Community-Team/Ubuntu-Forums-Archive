---
title: "Dual screens. 2nd screen being cut off."
date: 2008-05-08
forum: General Help
---

### Post by VII on 2008-05-08
Hello all,

I'm having trouble getting my dual screen setup working correctly in 8.04. I don't think it's 8.04's fault though.

For some reason there's a black border around my screen that seems to be about 20px wide. I can move my mouse through these black areas. Any idea what it might be?

The setup is a monitor connected to by VGA and a projector connected to by DVI. Screen wise the projector screen is to the left of the monitor screen.

For some reason this black border is transparent in the screenshot below. Can't see it.

Also, the monitor is acting like the main screen, hosting the panels and such. But, new files on the desktop, like when taking a screenshot for example, ends up on the projector screen, at its top left corner. Speaking of the main screen issue, when I change the volume from my keyboard the volume display is being shown at the projector screen.

[Screenshot]("http://imageupload.com/~imageupl/show.php/114946_screenshot.jpg.html") <-link

xorg.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "type1"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Epson"
    ModelName      "TW700"
    HorizSync       15.0 - 60.0
    VertRefresh     50.0 - 85.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT, DFP"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, CRT: 1280x1024_75 +1280+0"
#nvidia-auto-select
EndSection

Section "Extensions"
    Option         "DAMAGE" "Enable"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection

```

---

### Post by yaknowwat on 2008-05-09
I don't have too much experience with multimonitors i have setup dual monitors in Puppy linux on some legacy age Nvidia graphics cards did it for fun a temporary thing.

It seems your missing the second monitor setup in the xorg.conf

try redoing xorg while the second monitor is in backup your original.

---

### Post by ryanhaigh on 2008-05-09
I haven't had any of the issues you are experiencing, to configure my dual displays using my nvidia card I use the nvidia-settings app that comes with the driver. If you want to make changes permanent run it (alt-f2) using gksudo nvidia-settings and save to X configuration when your happy with what you have. Also I recommend using twinview for dual display.

---

### Post by RebateFX on 2008-11-11
> **ryanhaigh said:**
> I haven't had any of the issues you are experiencing, to configure my dual displays using my nvidia card I use the nvidia-settings app that comes with the driver. If you want to make changes permanent run it (alt-f2) using gksudo nvidia-settings and save to X configuration when your happy with what you have. Also I recommend using twinview for dual display.

Thanks for the twinview suggestion. 

I have a laptop (hp pavillion dv6000) with 1280x800 widescreen and second monitor which is 1280x1024. Using separate X sessions, the second screen had the bottom cut off like it was displaying the desktop in 1280x800 mode. Using twinview, the second monitor now has a full desktop view and as a plus, the compiz/emerald effects are running just fine. nice work!

---

