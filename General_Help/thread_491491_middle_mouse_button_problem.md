---
title: "middle mouse button problem"
date: 2007-07-03
forum: General Help
---

### Post by ryankent on 2007-07-03
my middle mouse button doesn't want to seem to work. it doesn't paste copied text or anything. i ran cat /dev/input/mice and nothing happens when i press the middle click... so i don't even think the computer recognizes that the button is being pressed. i need to get it to work so i can work in blender faster and easier. the mousewheel works but just the middle click doesnt. here is my xorg.conf:

> Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "false"
    Option         "ZAxisMapping" "4 5"
EndSection

im using ubuntu feisty with all the latest updates, if that matters. 

thanks for taking the time to try and help. :)

---

### Post by Juan_VCS on 2007-07-03
Do you have a USB mouse? I read that it's a 2.6.20 kernel issue

---

### Post by ryankent on 2007-07-03
yeah its a usb mouse

---

### Post by RedSquirrel on 2007-07-03
> **ryankent said:**
> yeah its a usb mouse
Which mouse do you have? You may have to make some changes to xorg.conf and/or use xmodmap to setup your middle-click.

If it's a well-known mouse, there might even be a guide here on ubuntuforums to help you set it up (try a search).

---

