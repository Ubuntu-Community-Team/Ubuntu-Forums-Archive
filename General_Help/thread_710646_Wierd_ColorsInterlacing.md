---
title: "Wierd Colors/Interlacing"
date: 2008-02-28
forum: General Help
---

### Post by TombstoneX on 2008-02-28
Im running 8.04 with all updates, with a GeForce 7300LE graphics card.

Img etting a problem with wierd colors, its really hard to explain, just see the screenshot.
I have tested the monitor, and also no issues outside of Xwindows.
Here is my xorg.conf file:

```

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Defaultdepth    24
EndSection
Section "Module"
    Load        "glx"
EndSection

```

---

### Post by solitaire on 2008-02-28
Only time i've seen something like that is when hte memory of the video card is faulty....

if you cange resolution do the colours change size and colour?

---

### Post by TombstoneX on 2008-02-28
Yes they change size. shouldnt it happen outside of x windows trhough if it the memory on the video card?

---

### Post by pointone on 2008-02-29
Not necessarily. Different video modes, and the fact the X uses more memory means it may only show up in X windows... And I agree that it looks faulty video RAM.

---

### Post by TombstoneX on 2008-02-29
what i will do is to try with a live CD and report the results.. it should show on a live stable version as well then if thats the theory.

Update: Same issue... so bad video card.. guess ill be replacing it now.. thanks boys.

---

