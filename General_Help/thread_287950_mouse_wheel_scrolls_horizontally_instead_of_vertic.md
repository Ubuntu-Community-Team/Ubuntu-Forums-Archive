---
title: "mouse wheel scrolls horizontally instead of vertically"
date: 2006-10-29
forum: General Help
---

### Post by The Doc on 2006-10-29
I just upgraded to edgy and now my mouse (MX1000) scrolls horizontally instead of vertically.

In dapper everything worked fine, all of those buttons (using xbindkeys, imwheel and evdev). The MX1000 offers a horizontal scrolling wheel but I remapped those buttons to be middle clicks.

Here are the important configuration files:

**xorg.conf**
```
Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "evdev"
    Option         "Name" "Logitech USB RECEIVER"
    Option         "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

I tried "ZAxisMapping" "7 6" instead of HWHEEL... but that didn't work either.

**~/.imhweelrc**
```
".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
```

**~/.xbindkeysrc**
```

# back forward
"xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
# up down
"xvkbd -xsendevent -text "\[Page_Up]""
  b:11
"xvkbd -xsendevent -text "\[Page_Down]""
  b:12
# horiz scrolling = middle mouse button click
"echo ButtonPress 2 ButtonRelease 2 | xmacroplay -d 0 :0.0"
  Release + b:13
"echo ButtonPress 2 ButtonRelease 2 | xmacroplay -d 0 :0.0"
  Release + b:14
# Application-Switch button
# mapped on kompose
"dcop kompose KomposeDcopIface createDefaultView"
  b:10
```

I really need my scrolling wheel back!

---

### Post by Choad on 2006-10-29
could try a sudo dpkg-reconfigure xserver-xorg

---

### Post by The Doc on 2006-10-29
I don't think this will help, as it doesn't offer me to use evdev as a mouse driver.

---

### Post by Choad on 2006-10-29
oh silly me... didnt realise u were using a funky mouse

---

### Post by The Doc on 2006-10-30
ok, I got a step further!

configuration imwheel in the following way worked for me:

**~/.imwheelrc**
```
".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
, Up, Button6
, Down, Button7
, Left, Button4
, Right, Button5
```

That basically swaps these buttons, just what I was looking for! Now my only problem is, that xbindkeys doesn't listen to the b:13 and b:14 events anymore - I want these to be middle clicks as well... (using m:0x10 doesn't work either). But well, that's ok for me, at least I got my scrolling wheel back!

---

### Post by The Doc on 2006-10-31
alright, now I completely fixed my problem *and* made imwheel obsolete!

first of all, don't let imwheel start automatically (usually you have made an entry in ~/.kde/Autostart or your /etc/X11/imwheel/startup.conf works correctly with `IMWHEEL_START=1` - set it to `0`)

secondly don't use `HWHEELRelativeAxisButtons` or `ZAxisMapping` in your /etc/X11/xorg.conf.

now create an automatically called script with the following contents (I use KDE thus I moved it to ~/.kde/Autostart and put chmod +x on it):

```
#!/bin/bash
xmodmap -e "pointer = 1 2 3 4 5 7 6 8 9 10 11 12 13 14 15 16 17 18 19 20" && xmodmap -pp
```

To put b:13 and b:14 on middle clicks use the .xbindkeysrc above for b:13 and b:14 and disable "cruise control" with [lmctl](http://www.bedroomlan.org/~alexios/coding_lmctl.html) . Download and compile it than run the following command and add it to your just created bash script.

```
lmctl --no-sms
```

whoa, it's always a bit of a pain if you update / upgrade and something like this happens out of nowhere but it makes me happy nonetheless if I can fix the problem :cool:

---

