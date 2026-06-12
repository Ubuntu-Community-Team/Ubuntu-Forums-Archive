---
title: "Mouse button confusion"
date: 2007-09-15
forum: General Help
---

### Post by yang on 2007-09-15
The back button on my mouse (a Dexxa Optical) is being treated as a middle click, and the forward button is being treated as a right click. (If I switch to left-handed mouse, the forward button is still a right-click, so instead of bringing up context menus, it acts as a "normal" click.)

Tried searching but found nothing. Any hints?

---

### Post by rivalarrival on 2007-09-15
This should help!
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by yang on 2007-09-15
My mouse is just a standard 5-button mouse with which I've never had issues at other sites (including Ubuntu sites). The page you pointed out just says:

> If you have installed the GNOME (default for Ubuntu) environment you ALREADY have the software needed to get the "4th" and "5th" mice buttons working (forward/backward on most mice)!

Anyway, I tried playing around with Emulate3Button, Buttons, ButtonMapping, and ZAxisMapping (using ctrl-alt-bkspc at the Logon screen to restart X), but nothing seemed to work.

I don't know if this is relevant, but the mouse is a USB mouse (though I assume that isn't the cause of these problems).

Here is the section from my xorg.conf, if it matters (it's just the default):

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

---

### Post by yang on 2007-10-19
This is still a problem, in Gutsy. Please help.

---

