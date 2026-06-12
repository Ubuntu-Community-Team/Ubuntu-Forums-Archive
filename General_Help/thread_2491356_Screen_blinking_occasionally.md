---
title: "Screen blinking occasionally"
date: 2023-10-05
forum: General Help
---

### Post by contra-point on 2023-10-05
Ever since I have installed Ubuntu 22.04 (around a month ago) the screen blinks every few minutes: it goes completely black for a second, seemingly without specific triggers. That's pretty much it, but it's really annoying. Has anyone faced the same issue?

---

### Post by TheFu on 2023-10-05
DRM or bad video cable is where I'd start.

---

### Post by contra-point on 2023-10-05
I'm afraid I really don't know what I should do about those. I'm not using any cables since it's a laptop.. Can you please explain further?

---

### Post by TheFu on 2023-10-05
> **contra-point said:**
> I'm afraid I really don't know what I should do about those. I'm not using any cables since it's a laptop.. Can you please explain further?

I'm not an expert.  [https://www.kernel.org/doc/html/latest/gpu/introduction.html?highlight=drm](https://www.kernel.org/doc/html/latest/gpu/introduction.html?highlight=drm)
[https://www.kernel.org/doc/html/v4.11/gpu/drm-internals.html](https://www.kernel.org/doc/html/v4.11/gpu/drm-internals.html)
Though I doubt those are the answer you seek.  Start by looking at log files and trying a few different kernel versions if the GPU drivers are part of the kernel for you system.  If you have nvidia, it gets harder, since they require adding THEIR code after the fact.

But I only posted leads, not an answer.

Have you looked at your exact hardware+drivers and searched for answers already?  Without posting that information, it is highly unlikely anyone can make good suggestions.

**inxi -Gxx** is a nice overview of the graphics system being used.

For example, here's mine:
```
$ inxi -Gxx
Graphics:
  Device-1: AMD vendor: ASUSTeK driver: amdgpu v: kernel bus ID: 09:00.0 
  chip ID: 1002:1638 
  Display: x11 server: X.Org 1.20.13 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1200~60Hz 
  OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-84-generic LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6 direct render: Yes 
```

When I had display issues, a new cable fixed it nicely.

But the real issue might not be related to the GPU or cables at all. Can't tell from the vast amount of information provided.

---

### Post by #&amp;thj^% on 2023-10-05
> **TheFu said:**
> Can't tell from the vast amount of information provided.
:lolflag: Right? 
@ contra-point due to the fact that not enough info provided, and I'm also guessing here, but try this:
This is a default setting compiled into Xorg.

To disable it for the current session, run:
```

xset s off

```
If that helped I'll show you how to make last on every boot.

---

### Post by contra-point on 2023-10-05
Well, thanks! while it might sound funny to you guys, I'm new to all of this. This is my first time ever using Linux and I didn't know what sort of information I had to provide. Here's the output of $ [FONT=courier new]inxi -Gxx:
[/FONT]
```
Use of uninitialized value $data{"current_link_speed"} in substitution (s///) at /usr/bin/inxi line 28449.
Graphics:
  Device-1: AMD Topaz XT [Radeon R7 M260/M265 / M340/M360 M440/M445 530/535
    620/625 Mobile]
    vendor: Hewlett-Packard driver: amdgpu v: kernel bus-ID: 01:00.0
    chip-ID: 1002:6900
  Device-2: AMD Picasso/Raven 2 [Radeon Vega Series / Radeon Mobile Series]
    vendor: Hewlett-Packard driver: amdgpu v: kernel pcie: speed: 8 GT/s
    lanes: 16 ports: active: eDP-1 empty: HDMI-A-1 bus-ID: 04:00.0
    chip-ID: 1002:15d8
  Device-3: Cheng Uei Precision Industry (Foxlink) HP TrueVision HD Camera
    type: USB driver: uvcvideo bus-ID: 1-4:3 chip-ID: 05c8:03d2
  Display: wayland server: X.org v: 1.21.1.4 with: Xwayland v: 22.1.1
    compositor: gnome-shell v: 42.9 driver: gpu: amdgpu display-ID: 0
  Monitor-1: eDP-1 model: BOE Display res: 1366x768 dpi: 112
    diag: 355mm (14")
  OpenGL: renderer: AMD Radeon Vega 3 Graphics (raven2 LLVM 15.0.7 DRM 3.49
  6.2.0-33-generic)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes


```

Does this tell you anything?

I also ran the command [FONT=courier new]xset s off[/FONT] though I'm not sure what to do afterwards..

---

### Post by #&amp;thj^% on 2023-10-05
> **contra-point said:**
> 
I also ran the command [FONT=courier new]xset s off[/FONT] though I'm not sure what to do afterwards..

Us old timers have a tough time with a lack of provided info thus leaves us guessing or to assume, and if you were offended
My apologies, it's a coping mechanism.
And on the setting you just ran, just let us know if it's working after a period of time. (It won't hold on your next reboot)

**EDIT**: You also have a thread found here that you have not yet replied back: [https://ubuntuforums.org/showthread.php?t=2491343](https://ubuntuforums.org/showthread.php?t=2491343)
It's just a learning curve try not to take it personal.

---

### Post by TheFu on 2023-10-05
Looks like he's using Wayland, so **xset** won't do anything, right?
Try using Xorg, not Wayland.  In theory, it shouldn't matter, but ....

---

### Post by #&amp;thj^% on 2023-10-05
> **TheFu said:**
> Looks like he's using Wayland, so **xset** won't do anything, right?
I honestly don't know, have to wait for proof.
EDIT: It seems to work:
```
&#9492;&#9472;> xset s off
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
no errors.
EDIT2: No it won't work with wayland, x11 just fine.
```
DE: GNOME 44.5 (Wayland)
```
> **TheFu said:**
> 
Try using Xorg, not Wayland.  In theory, it shouldn't matter, but ....
+1
That's the best for this case.
But there is:
```
caffeine/mantic,mantic 2.9.12-1 all
  prevent the desktop becoming idle in full-screen mode
``` 
naming will differ ",mantic"

---

