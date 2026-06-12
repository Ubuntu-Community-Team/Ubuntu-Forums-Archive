---
title: "Help configure Logitech G5 mouse"
date: 2006-12-04
forum: General Help
---

### Post by leonlauncher on 2006-12-04
so yea i've been looking around and could'nt find any help to configure my g5 mouse

well what im trying to do is making the thumb button for back and the tilt buttons into mousebutton3 so i can open up new tabs in fire fox

this is what i've done so far 

in xorg.conf
```
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "evdev"
    Option "CorePointer"
    Option "Name" "Logitech USB Gaming Mouse"
    Option "ZAxisMapping" "4 5 6 7"
    Option "Emulate3Buttons" "false"
EndSection
```

and i've also install xbindkeys
```
sudo apt-get install xbindkeys
```
```
gedit ~/.xbindkeysrc
```

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "[Control_L]\[Enter]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Enter]""
  m:0x0 + b:8
```

mostly taken from [HTML]http://www.ubuntuforums.org/showthread.php?t=125752&highlight=mouse+pointer[/HTML]
so yeah any help would be  great

---

### Post by humina on 2007-12-13
I've been trying to get this to work too.  All I can figure out is how to get my tilt wheels to go back and forth in the history.  I hate my logitech g5 mouse.

---

### Post by humina on 2007-12-19
you also need to install xvkbd for this to work.  I'm still debugging but I got 1 of my buttons to work properly now.

---

### Post by Keith Hedger on 2008-01-09
Thanks this worked great for me as i had just switched machine and upgraded to gutsy and couldn't get imwheel to work that i had been using on feisty:):):)

---

