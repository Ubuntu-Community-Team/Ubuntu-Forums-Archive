---
title: "Screen tearing Xubuntu 16.04"
date: 2016-07-02
forum: General Help
---

### Post by adytza232 on 2016-07-02
Hello i'm new to this forum and i have installed Xubuntu 16.04 (my favorite distro)  to my HP Pavilion ab002nq with Core i5 and nvidia 940m and my problem is that i have screen tearing and i searched everywhere for a fix and tried different methods but nothing seems to work so i figured to try here for help, so if anybody knows a good solution it would be much appreciated, thanks in advance!

---

### Post by T.J. on 2016-07-02
> **adytza232 said:**
> Hello i'm new to this forum and i have installed Xubuntu 16.04 (my favorite distro)  to my HP Pavilion ab002nq with Core i5 and nvidia 940m and my problem is that i have screen tearing and i searched everywhere for a fix and tried different methods but nothing seems to work so i figured to try here for help, so if anybody knows a good solution it would be much appreciated, thanks in advance!


No problem!  The issue is that the current version of XFCE uses XRender instead of OpenGL for vertical synchronization.  The next version of XFCE plans to replace it so it will no longer be a problem.  In the meantime, you can:
[LIST=1]
[*]Turn off the XFCE compositor under Window manager tweaks.
[*]Install compton.
[*]Configure compton the way you want it using compton-conf
[*]Add compton to "Session and Startup" so it will always be started with XFCE.
[*]Log out and then back in.
[/LIST]

That should fix your problem.  I've used it myself (with the Nvidia proprietary driver), so I know it works, although I switched to Mate.

---

### Post by adytza232 on 2016-07-11
> **T.J. said:**
> No problem!  The issue is that the current version of XFCE uses XRender instead of OpenGL for vertical synchronization.  The next version of XFCE plans to replace it so it will no longer be a problem.  In the meantime, you can:
[LIST=1]
[*]Turn off the XFCE compositor under Window manager tweaks.
[*]Install compton.
[*]Configure compton the way you want it using compton-conf
[*]Add compton to "Session and Startup" so it will always be started with XFCE.
[*]Log out and then back in.
[/LIST]

That should fix your problem.  I've used it myself (with the Nvidia proprietary driver), so I know it works, although I switched to Mate.

i tried installing compton but it does not work anymore on Xubuntu 16.04, any other solution?

---

### Post by T.J. on 2016-07-11
> **adytza232 said:**
> i tried installing compton but it does not work anymore on Xubuntu 16.04, any other solution?


That's disappointing. I'm using it right now on Xubuntu 16.04.  I'm not doubting you - quite the reverse.  Compositors are known to be quirky with certain drivers.  

Well, let's see - the problem is that once we move past Compton, we are actually replacing the Window Manager, and that means you lose the ability to manage it on the XFCE panel, along with possibly the sticky button. When you do that, you could get some really weird issues.  We can solve them. but I think it best we start at the beginning.  

Hmm let me check into your Nvidia. I use Nvidia also.  Are you using the proprietary driver?

---

### Post by adytza232 on 2016-07-11
> **T.J. said:**
> That's disappointing. I'm using it right now on Xubuntu 16.04.  I'm not doubting you - quite the reverse.  Compositors are known to be quirky with certain drivers.  

Well, let's see - the problem is that once we move past Compton, we are actually replacing the Window Manager, and that means you lose the ability to manage it on the XFCE panel, along with possibly the sticky button. When you do that, you could get some really weird issues.  We can solve them. but I think it best we start at the beginning.  

Hmm let me check into your Nvidia. I use Nvidia also.  Are you using the proprietary driver?

Yes i use 3.61 proprietary driver

---

### Post by T.J. on 2016-07-11
For the moment, we will assume that your driver is installed correctly.  (Sometimes they don't.)  Before you do this, make sure the XFCE compositor is off or it won't work at all.

Here is my personal Compton config file.  Save it as ".compton.conf" in your home directory. Don't forget the first period in the name, it's important.
```

# Shadow
shadow = true;
no-dnd-shadow = true;
no-dock-shadow = true;
clear-shadow = true;
shadow-radius = 7;
shadow-offset-x = -7;
shadow-offset-y = -7;
# shadow-opacity = 0.7;
# shadow-red = 0.0;
# shadow-green = 0.0;
# shadow-blue = 0.0;
shadow-exclude = [
    "name = 'Notification'",
    "class_g = 'Conky'",
    "class_g ?= 'Notify-osd'",
    "class_g = 'Cairo-clock'",
    "_GTK_FRAME_EXTENTS@:c"
];
# shadow-exclude = "n:e:Notification";
# shadow-exclude-reg = "x10+0+0";
# xinerama-shadow-crop = true;


# Opacity
menu-opacity = 1;
inactive-opacity = 1;
# active-opacity = 1;
frame-opacity = 1;
inactive-opacity-override = false;
alpha-step = 0.06;
# inactive-dim = 0.2;
# inactive-dim-fixed = true;
# blur-background = true;
# blur-background-frame = true;
blur-kern = "3x3box"
# blur-kern = "5,5,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1"
# blur-background-fixed = true;
blur-background-exclude = [
    "window_type = 'dock'",
    "window_type = 'desktop'",
    "_GTK_FRAME_EXTENTS@:c"
];
# opacity-rule = [ "80:class_g = 'URxvt'" ];


# Fading
fading = false;
# fade-delta = 30;
fade-in-step = 0.03;
fade-out-step = 0.03;
# no-fading-openclose = true;
# no-fading-destroyed-argb = true;
fade-exclude = [ ];


# Other
backend = "glx"
mark-wmwin-focused = true;
mark-ovredir-focused = true;
# use-ewmh-active-win = true;
detect-rounded-corners = true;
detect-client-opacity = true;
refresh-rate = 0;
vsync = "none";
dbe = false;
paint-on-overlay = true;
# sw-opti = true;
# unredir-if-possible = true;
# unredir-if-possible-delay = 5000;
# unredir-if-possible-exclude = [ ];
focus-exclude = [ "class_g = 'Cairo-clock'" ];
detect-transient = true;
detect-client-leader = true;
invert-color-include = [ ];
# resize-damage = 1;


# GLX backend
# glx-no-stencil = true;
glx-copy-from-front = false;
# glx-use-copysubbuffermesa = true;
# glx-no-rebind-pixmap = true;
glx-swap-method = "undefined";
# glx-use-gpushader4 = true;
# xrender-sync = true;
# xrender-sync-fence = true;


# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = true; opacity = 0.75; focus = true; };
};

```

Then using the Verve applet on your panel enter:  *compton --backend glx  --vsync opengl-swc*

That should fix your vsync problem, at least temporarily.  Test moving a few windows around.  To make it permanent, you have to add that command to your startup.

---

### Post by zer010 on 2016-09-10
I would also like to know if there's a fix for this. My situation is a little different as I have the infamous optimus setup.  I haven't installed any proprietary drivers or any of the switching programs like Prime/Bumblebee.

---

### Post by T.J. on 2016-09-13
Try enabling the composition pipeline, if you are planning to use the commercial driver. It should eliminate the tearing on Nvidia cards.   I do not use Nouveau, it has extremely poor performance on my hardware.


```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2250 SERIES"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 960"
EndSection


Section "Screen"


# Removed Option "metamodes" "DVI-I-1: nvidia-auto-select +0+0, DP-5: nvidia-auto-select +1920+0"
# Removed Option "nvidiaXineramaInfoOrder" "DFP-0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-7"
    Option         "metamodes" "DVI-I-1: 1920x1080_60 +0+0 { ForceFullCompositionPipeline = On }, DP-5: 1920x1080_60 +1920+0 { ForceFullCompositionPipeline = On }"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by antti-savo on 2016-12-07
Found this fix from /g/. It'll work if you're using nvidia drivers.

```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"

```
Put the command into your startup applications

---

### Post by renanrischiotto1 on 2017-05-05
> **antti-savo said:**
> Found this fix from /g/. It'll work if you're using nvidia drivers.

```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"

```
Put the command into your startup applications

Amazing man, thanks!

---

### Post by MetCom45 on 2018-01-12
> **antti-savo said:**
> Found this fix from /g/. It'll work if you're using nvidia drivers.

```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"

```
Put the command into your startup applications

Fixed my problem, thank you! Such an easy fix.

---

