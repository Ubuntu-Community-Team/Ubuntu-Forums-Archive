---
title: "Mouse cursor moves very choppy"
date: 2018-06-20
forum: General Help
---

### Post by sE7DNzA on 2018-06-20
Hello,

I just installed Ubuntu on my Lenovo Ideapad FLEX 4 1480, and my touchpad cursor is moving in a very choppy, grid-like manner. I'm using Ubuntu 18.04 LTS. I've seen several forum posts that talk about the same problem:

[https://askubuntu.com/questions/983419/touchpad-makes-mouse-go-in-a-grid-like-pattern-external-mouse-doesnt](https://askubuntu.com/questions/983419/touchpad-makes-mouse-go-in-a-grid-like-pattern-external-mouse-doesnt)

But the answer assumes that the latest version of Ubuntu solves the problem, and as I said, I have Ubuntu 18.04 installed. 

I assume the following might be helpful: xinput --list-props "SynPS/2 Synaptics TouchPad" gives the following: 

```

Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Tapping Enabled (283):    1
    libinput Tapping Enabled Default (284):    0
    libinput Tapping Drag Enabled (285):    1
    libinput Tapping Drag Enabled Default (286):    1
    libinput Tapping Drag Lock Enabled (287):    0
    libinput Tapping Drag Lock Enabled Default (288):    0
    libinput Tapping Button Mapping Enabled (289):    1, 0
    libinput Tapping Button Mapping Default (290):    1, 0
    libinput Natural Scrolling Enabled (291):    1
    libinput Natural Scrolling Enabled Default (292):    0
    libinput Disable While Typing Enabled (293):    1
    libinput Disable While Typing Enabled Default (294):    1
    libinput Scroll Methods Available (295):    1, 1, 0
    libinput Scroll Method Enabled (296):    1, 0, 0
    libinput Scroll Method Enabled Default (297):    1, 0, 0
    libinput Click Methods Available (298):    1, 1
    libinput Click Method Enabled (299):    0, 1
    libinput Click Method Enabled Default (300):    1, 0
    libinput Middle Emulation Enabled (301):    0
    libinput Middle Emulation Enabled Default (302):    0
    libinput Accel Speed (303):    0.000000
    libinput Accel Speed Default (304):    0.000000
    libinput Left Handed Enabled (305):    0
    libinput Left Handed Enabled Default (306):    0
    libinput Send Events Modes Available (264):    1, 1
    libinput Send Events Mode Enabled (265):    0, 0
    libinput Send Events Mode Enabled Default (266):    0, 0
    Device Node (267):    "/dev/input/event5"
    Device Product ID (268):    2, 7
    libinput Drag Lock Buttons (307):    <no items>
    libinput Horizontal Scroll Enabled (308):    1


```

---

