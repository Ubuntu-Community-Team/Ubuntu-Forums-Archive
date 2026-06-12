---
title: "How to: logitech mx400 mouse"
date: 2007-02-18
forum: General Help
---

### Post by m_bridge on 2007-02-18
I'm currently using a logitech mx400 mouse, not all of its buttons works out of the box.
messing up gave some positive results so far so i post them. they involve_ just minimal changes to xorg.conf_

[COLOR="SeaGreen"]Working buttons[/COLOR]
[LIST]
[*]Button1    (left click)
[*]Button2    (wheel click)                 
[*]Button3    (right click)                   
[*]Wheel-scrolling up and down     
[*]Button8    (thumb button down) 
[/LIST]

1. Make a backup
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```
2. edit the file
```
sudo gedit /etc/X11/xorg.conf
```
3. one of the "input device" contains configurations of your mouse,
mine at the moment looks like that
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
EndSection
``` Save the changes
4. Restart gdm
if you are not sure about how to do that, just _save your work_ and type
```
sudo shutdown -r now
```
Panic! if anything goes wrong (ex. the windows manager does not start) 
restore your old xorg config (you can always get a terminal with <ctrl><alt>F1)
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 
sudo shutdown -r now
```

[COLOR="Red"]
i will update with rest of the buttons fixies soon hopefully[/COLOR]

_Not working yet_
[LIST]
[*]Button?    (thumb button up)
[*]Button?    (wheel-left)
[*]Button?    (wheel-right)
[/LIST]
Those does not even show up as events in **xev** 

:)[COLOR="Red"] [SIZE="4"]WTF Corner[/SIZE][/COLOR]:)
By applying a wrong configuration to the Zaxis option, (buttons 6 an7) i got that the wheel scroll was assigned to forward/backward buttons of firefox...
so that rule that associates mouse events with <alt>leftarrow/rightarrow is defined somewhere in gnome(?) further investigation required.. [SIZE="4"][COLOR="DarkOrange"]any hint is welcome[/COLOR][/SIZE]

---

### Post by markitect on 2007-02-27
some generic stuff that may be helpful

try the driver evdev, it might allow all the buttons to work


xmodmap -r "pointer = [numbers]" from a terminal will allow you change the order of the buttons

"pointer = 1 3 2" would switch buttons 2 and 3 around.

---

### Post by traemccombs on 2008-05-09
I set mine up as you've described above... and things seem ok.  The only problem is... I got REALLY used to my left side "down button" (I'm guessing this is for scrolling in windows or something) to be my middle click button.  I didn't set this up this way it just started working in Ubuntu 7.04 that way by default!

Anyway I did your suggestion, but in addition, I did the following:

xmodmap -e "pointer = 1 8 3 4 5 6 7 2 9"

(I set that up as a session entry to run when X starts) and things seem to work as I'd like now.  I'll reply back if I start to see any funkiness. ;)

Thanks and goodluck to all that read this!

---

