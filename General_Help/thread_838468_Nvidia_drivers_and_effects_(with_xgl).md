---
title: "Nvidia drivers and effects (with xgl)"
date: 2008-06-23
forum: General Help
---

### Post by benthegreat on 2008-06-23
Im running hardy and iv got a nvidia 7600GT.

After installing the nvidia drivers, my compiz effect no longer worked, ok a bit annoying. Then I realized I hadn't actually got xgl installed, so I did that and I get the nice compiz effect back, but it disables my nvidia drivers, which wouldn't be a problem, except I need xinrama enabled to utilize my dual monitor setup properly, something that only an nvidia driver can do.

Any help?

---

### Post by benthegreat on 2008-06-24
anyone, Id rather not let this die...

---

### Post by Zorael on 2008-06-24
Er, I'm confused. Nvidia drivers support TwinView which seems to me to be able to do everything Xinerama does, better.

We'd need to know details; how does Compiz "not work" without XGL? What are the error messages output when started manually in a terminal?
```
$ compiz --loose-binding --replace &
```

---

### Post by Forlong on 2008-06-24
Compiz doesn't work on Xinerama without Xgl because it kills the composite extension.

Like Zorael mentioned, if you switch to TwinView, you will be able to run Compiz without Xgl.

---

### Post by benthegreat on 2008-06-24
having 2 monitors act as one huge wide screen desktop is fairly useless to me, also having 2 separate screens I can't move windows between is a waste of time as well. If twinveiw can do what xinerama can do then thats fine.

I get this: 
```
ben@bens:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option --loose-binding

```
 When I start compiz

compiz is installed

---

### Post by psyopper on 2008-06-24
Which nvidia drivers did you install - the ones from the Ubuntu Repositories, or the ones from the Nvidia website?

Can you post a copy of your /etc/X11/xorg.conf, preferrably between code tags?

---

### Post by benthegreat on 2008-06-24
I'm using the "new" nvidia drivers from the repositories.

xorg:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107E"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
EndSection

```

I have tried adding:
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

to no avail


Is it possible to get twinview to give me a setup similar to that of xinerama, rather than a large split up wide-screen desktop?

---

### Post by psyopper on 2008-06-25
So do you actually have 2 nvidia 7600 GT's installed in the system? 

The next step is to try runing Forlongs Compiz Check. Click the link in his signature to get a copy of compiz-check. Again please post the results here.

I've never used TinView or Xinerama so I am starting to get out of my league here. Have you tried setting up X to work on a single monitor and leaving out all of the dual screen Twinview and Xinerama stuff?

---

### Post by Zorael on 2008-06-25
```
Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection
```
Xinerama MUST be **disabled** for Nvidia to play ball without xserver-xgl installed. Installing it will make things very, very slow.

I strongly suggest you disable it (Xinerama 0 or just comment the whole line) and rely on TwinView instead. This entails removing all the TwinView 0 lines you seem to have.

---

### Post by benthegreat on 2008-06-25
> So do you actually have 2 nvidia 7600 GT's installed in the system? 
Nope just one!! but it has two ouputs, which im guessing ubuntu treats as two seperates.

Also before we go any further, having dual monitors is infinitely more useful to me than flashy compiz, as god as it looks.


> I strongly suggest you disable it (Xinerama 0 or just comment the whole line) and rely on TwinView instead. This entails removing all the TwinView 0 lines you seem to have.
ok, but can I get a similar setup with twinview, either one huge desktop or 2 separate ones would be pointless for me.

I imagine compiz will work painlessly with only one screen, it always has done before, but isnt useful for me.


Update:
Yes getting rid of xinerama works, but like I said, I dont mind how its done, but I need two desktops that allow me to drag windows in between, yet support two maximized windows.

---

### Post by benthegreat on 2008-06-25
I ran the compiz check, first time it failed due to "more than one X server running", so I disabled one of my screens, and ran again:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 The default window manager of GNOME has its own compositing manager to
 provide basic desktop effects.
 If this one is in use, Compiz will not be able to run. 

```

---

### Post by Forlong on 2008-06-25
Didn't it give you the option to disable GNOME's compositor?

---

### Post by benthegreat on 2008-06-26
Yes it did, I went through with that, and I get a different error in the next run:
```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by Forlong on 2008-06-26
Are you using Xinerama?

---

### Post by benthegreat on 2008-06-26
well yes, because I can get compiz working with twinview and as 2 separate screen easily, but thats not the problem. Unless theres another way to get to the same outcome, I need xinerama enabled, could someone please explain why xinerama causes so many problems compared to twinview?

---

### Post by Forlong on 2008-06-27
All I can tell you is this:
- if you want to use Xinerama , you have to use Xgl
- if you don't want to use Xgl, you have to use TwinView

Other than that, I have no experience with such a setup, because I have neither a dual-head nor a nvidia card.

You should consider starting a separate thread where you ask for advice how to get TwinView behave like Xinerama (don't know whether it's possible or not, though).

---

### Post by benthegreat on 2008-06-27
So I need xgl until a better solution is found? How do I go about making xgl and my nvidia driver work in harmony?

---

### Post by Forlong on 2008-06-27
To be honest, Xgl is not a good solution at all with Nvidia cards, not even temporary.

I'd recommend making your peace with TwinView somehow.

---

### Post by benthegreat on 2008-06-27
OK. Whats exactly is wrong with xgl? Iv even heard reports of it improving performance...

---

### Post by Forlong on 2008-06-27
> **benthegreat said:**
> Whats exactly is wrong with xgl?
Well, nothing in general. Using it just has side-effects on many setups.

---

### Post by benthegreat on 2008-06-27
oh ok, well after some research, it would seem that twinview can only do the combined desktop thing, on Linux at least. So it comes down to a buggy xgl and compiz mix or no compiz unfortunately. I still can't find out how to get xgl to use xinerama instead of twinview though, is there an xorg.conf equivalent for xgl?

---

