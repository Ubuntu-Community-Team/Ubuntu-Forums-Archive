---
title: "Mouse fwd/back buttons malfunctioning"
date: 2007-02-08
forum: General Help
---

### Post by MeathooK427 on 2007-02-08
Recently, last night actually...after my Windows install on my other partition, when I got back into Ubuntu, my forward/back buttons on my Razer Diamondback no longer work correctly. The front button on the left pad goes back, and both of the buttons on the right pad go back, the rear button on the left pad does nothing. Here's my xorg.conf

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option 	   "Button Mapping" "1 2 3 6 7"
EndSection

```

Any help would be greatful, thanks

---

### Post by flammenwurfer on 2007-02-08
I'm not sure if this will help or not but..

I have an A4Tech mouse with a forward and a back button on the side.  All I had to do to get them to work was install the package imwheel with synaptic and then got to /etc/X11/imwheel/startup.conf and uncomment this line

IMWHEEL_PARAMS='-b "0 0 8 9"'

then Ctl-Alt-Backspace to restart x

---

### Post by MeathooK427 on 2007-02-08
Ah...I'll try that if I can't do it through Xorg. Thanks, though. I wanted to check to see if my code was correct. I didn't mess with it, then all of a sudden it stops working right. Did the source change or something? Thanks...

---

### Post by flammenwurfer on 2007-02-08
I'm not sure about that.  Somebody more knoweldgeable than myself will have to field that one.

---

### Post by MeathooK427 on 2007-09-03
Bump...need some help with this again. 

Update: I'm using Feisty Fawn now. Maybe it's still a bug, or maybe it has to do with Grub?

But anyways, the code is right, and it works...only if Ubuntu is the only OS installed on the system.

Whenever I add my Windows install to Grub, it freaks out and changes the configuration of the buttons. Does anybody know of a fix for this???

---

### Post by marttali on 2007-09-06
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "6 7"
Option "Emulate3Buttons" "true"
Option "Buttons" "9"
Option "ButtonMapping" "1 2 3 4 5 8 9"

try that instead what you have, hope it helps (helped me)

---

