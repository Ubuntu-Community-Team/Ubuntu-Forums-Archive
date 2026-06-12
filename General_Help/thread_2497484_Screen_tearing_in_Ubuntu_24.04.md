---
title: "Screen tearing in Ubuntu 24.04"
date: 2024-05-07
forum: General Help
---

### Post by laserburn2 on 2024-05-07
GeForce 1060 graphic card with 535.171.04 drivers. First I noticed some screen tearing in Stremio watching a movie in full screen mode. Then today I try a video game and again I notice screen tearing, mostly around the middle and upper half of the screen. I try another game, the same happens. I try playing VLC in full screen, there is tearing. There is no tearing on the desktop, windows are not tearing when moving them. There is no tearing when I play game or video in a window, tearing is only in full screen mode. I tried turning off 'sync to vblanc' in OpenGL settings, doesn't make a difference if it's on or off. 

This is frustrating to no end. Just last week this same card with the same 535 drivers was working flawlessly on Ubuntu 22.04, but now with the new LTS this happens. Do you know what could be the problem? If you have an Nvidia card with the new Ubuntu 24.04, could you please try to replicate the problem?

---

### Post by laserburn2 on 2024-05-07
I found a solution. Install this extension:
[https://extensions.gnome.org/extension/1873/disable-unredirect-fullscreen-windows/](https://extensions.gnome.org/extension/1873/disable-unredirect-fullscreen-windows/)

---

### Post by #&amp;thj^% on 2024-05-07
You don't mention your DE used, mine is XFCE4 with X11, my specs:
```
inxi -G 
Graphics:
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] [COLOR="#FF0000"]driver: nvidia
    v: 550.78[/COLOR]
  Device-2: AMD Cezanne [Radeon Vega Series / Radeon Mobile Series]
    driver: amdgpu v: kernel
  Device-3: Bison Integrated Camera driver: uvcvideo type: USB
  Display: x11 server: X.Org v: 21.1.11 driver: X: loaded: amdgpu,nvidia
    unloaded: fbdev,modesetting,nouveau,vesa dri: radeonsi
    gpu: amdgpu,nvidia,nvidia-nvswitch resolution: 1: N/A 2: 1920x1080~120Hz
  API: EGL v: 1.5 drivers: nvidia,radeonsi,swrast
    platforms: gbm,x11,surfaceless,device
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: amd mesa v: 24.0.5-1ubuntu1
    renderer: AMD Radeon Graphics (radeonsi renoir LLVM 17.0.6 DRM 3.57
    6.8.0-31-generic)

```
No tearing in any of the mentioned apps your showing, outside of  Stremio I don't use it so I can't report on that.

Are you in a Wayland session?

EDIT: You found a fix now i see. :)

---

### Post by laserburn2 on 2024-05-13
On closer inspection, no, it's actually not solved completely, though the situation is much better with the extension than without it. How the extension works is it disables undirected fullscreen windows, because desktop vsync gets turned off for them, releasing the vsync control to the application (usually a game). Without the extension the tearing was all over the place, with it it just pops here and there, from time to time, not terrible, but still annoying. I play video in full screen window and it works fine, I run it full screen borderless and there is tearing.

I wish I could remove the [solved] tag. I'm using Gnome and X11. If you're using Nvidia proprietary drivers, please pay attention for screen tearing in fullscreen apps.

---

### Post by #&amp;thj^% on 2024-05-13
> **laserburn2 said:**
>  I'm using Gnome and X11. If you're using Nvidia proprietary drivers, please pay attention for screen tearing in fullscreen apps.

I'm on Xubuntu all applications in full screen or not>>>No Tearing seen on my end.
```
 inxi -G | grep -e Display -e Device-1
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] driver: nvidia
  Display: x11 server: X.Org v: 21.1.13 driver: X:

```
Driver in use:
```
 nvidia-smi | grep NVIDIA-SMI
| NVIDIA-SMI 550.78                 Driver Version: 550.78         CUDA Version: 12.4     |

```

---

### Post by laserburn2 on 2024-05-14
Ok, I believe I got it this time. I had to check "Force Full Composition Pipeline" in Nvidia drivers. Seems that in Ubuntu 24.04 you can't let composer lose control over a window at any time, otherwise you can get tearing.

---

### Post by him610 on 2024-05-14
A couple of thoughts come to mind: (1) Try reducing the resolution of your screen. (2) Is your power supply adequate for the load? Sometimes they go flaky.

---

### Post by laserburn2 on 2024-05-15
> **him610 said:**
> A couple of thoughts come to mind: (1) Try reducing the resolution of your screen. (2) Is your power supply adequate for the load? Sometimes they go flaky.

Nope, it's not a hardware problem, the solution above works. The only problem is that in order to permanently save changes, you have to click on the button that says save changes to files. But nvidia-settings would than complain that it can't write to /etc/X11/xorg.conf even when I ran it with sudo. Fortunately, it shows preview of the changes it makes, so I just created xorg.conf manually and copied the text into it.

---

### Post by #&amp;thj^% on 2024-05-15
Might I give a good suggestion here; write that file .conf to "/etc/X11/xorg.conf.d/" as this example name "20-nvidia-xorg.conf" 
Less chance of it getting overwrote.

---

### Post by hoppingturtles on 2024-05-16
I have the same issue for many weeks now, but I'm on Ubuntu 23.10. This only happens on my secondary external display. Installing the extension does fix it for me, and a reboot also, but only temporarily. Also, after using wayland for many months and then switching back to X11, I was surprised by how smooth the cursor and animations felt. Something is really up nvidia/wayland integration :/

> **laserburn2 said:**
> Ok, I believe I got it this time. I had to check "Force Full Composition Pipeline" in Nvidia drivers. Seems that in Ubuntu 24.04 you can't let composer lose control over a window at any time, otherwise you can get tearing.

Where did you enable that setting? `nvidia-settings` does not have it?

Btw [https://forums.developer.nvidia.com/t/545-29-02-ghosting-artifacting-stuttering-on-fullscreen-when-below-monitor-framerate/271853/28](https://forums.developer.nvidia.com/t/545-29-02-ghosting-artifacting-stuttering-on-fullscreen-when-below-monitor-framerate/271853/28) seems related to our issue. Don't remember this happening with an older driver like 535, though I'm not going to downgrade to check that.

---

### Post by #&amp;thj^% on 2024-05-16
> **hoppingturtles said:**
> 


Where did you enable that setting? `nvidia-settings` does not have it?

Yes it dose, see my screenshot with a Note.
And my file reads like:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 550.78

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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AU Optronics Corporation"
    HorizSync       138.0 - 138.0
    VertRefresh     60.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVIDIA GeForce RTX 3050 Ti Laptop GPU"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DP-4"
    Option         "metamodes" "DP-4: nvidia-auto-select +0+0 {ForceCompositionPipeline=On, ForceFullCompositionPipeline=On}"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by lauramv on 2024-09-19
> **laserburn2 said:**
> The only problem is that in order to permanently save changes, you have to click on the button that says save changes to files. But nvidia-settings would than complain that it can't write to /etc/X11/xorg.conf even when I ran it with sudo.

To permanently save changes in nvidia-settings app, try:

```
$ [COLOR=#131313][FONT=&amp]sudo chmod +x /usr/share/screen-resolution-extra/nvidia-polkit[/FONT][/COLOR]
```

It worked for me.

---

