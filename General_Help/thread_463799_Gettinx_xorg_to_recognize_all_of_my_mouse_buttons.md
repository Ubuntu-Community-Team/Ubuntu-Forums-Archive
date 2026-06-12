---
title: "Gettinx xorg to recognize all of my mouse buttons"
date: 2007-06-04
forum: General Help
---

### Post by Sockerdrickan on 2007-06-04
Hi how can I get xorg to recognize all of my mouse buttons.
1 2 3 usual buttons and 2 more on each side. 7 buttons (9 with scroll up and down)

You have to type something in xorg.conf I saw someone do it :P

Thanks;)

---

### Post by mills on 2007-06-04
[https://help.ubuntu.com/community/ManyButtonsMouseHowto?highlight=%28mouse%29](https://help.ubuntu.com/community/ManyButtonsMouseHowto?highlight=%28mouse%29)

that should do it.

---

### Post by Sockerdrickan on 2007-06-04
It now looks like

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "9"
EndSection

I have a "5" button mouse according to walkthrough

I have 4 extra buttons

In DOOM 3 it says

1st  mouse2
2nd mouse3
3rd  scroll up
4th  scroll down

---

### Post by Sockerdrickan on 2007-06-04
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Resolution" "1600"
    Option "Buttons" "9"
    Option "Device" "/dev/psaux"
    Option "Name" "Razer Diamondback Optical Mouse"
    Option "Protocol" "auto"
    Option "ZAxisMapping" "4 5"
    Option "ButtonMapping" "1 2 3 6 7 8 9"
    Option "Emulate3Buttons" "true"
EndSection

This makes the following with the extra buttons:

1st mouse5
2nd mouse4
3rd scroll up       <--
4th scroll down  <--
Can I get the last to work as mouse6 and mouse7 or something? :)

---

