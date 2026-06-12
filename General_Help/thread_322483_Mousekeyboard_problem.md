---
title: "Mouse/keyboard problem"
date: 2006-12-20
forum: General Help
---

### Post by pwbrawner on 2006-12-20
I am new to Ubuntu, but have been running RedHat/Fedora previously for several years and never run into anything like this. I am running 6.10. This is a fresh install on a new pc. I am running dual screens with the latest nvidia driver. What happens is when I hold down a key on the keyboard then the mouse pointer will not move until I release the button. I discovered this when holding the ctrl key down trying to select multiple things. I am plugged into a Raritan SwitchMan KVM, but I have bypassed that and gone directly to the pc. Both the keyboard and mouse are Microsoft and connected vis ps/2. I have also tried a Logitech mouse with the same Microsoft keyboard, the Logitech mouse with a HP keyboard, and the HP keyboard with the original Microsoft mouse. They all produce the same results and were all plugged directly into the pc. I have also tried adding psmouse to /etc/modules to no avail.

Here is a copy of the keyboard and mouse sections from my xorg.conf file

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "6 7"
Option "Emulate3Buttons" "true"
EndSection

Just a little more info, this is a work pc and my boss has the same setup pc wise except for the video card has 128 MB of memory instead of the 256 MB that mine has and he has a 3 button + wheel Microsoft mouse and mine is a 5 button + wheel Microsoft mouse and he has no trouble with his.

I also copied my .evolution folder over from my old pc to keep all my mail, if anyone thinks that for any reason that would have anything to do with this.

I have searched all over and have not been able to find anything like this so if anyone has any suggestions I would grealty appreciate it.

Thanks in advance for any and all help.

---

