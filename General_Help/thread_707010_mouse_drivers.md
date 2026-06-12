---
title: "mouse drivers"
date: 2008-02-25
forum: General Help
---

### Post by foosed on 2008-02-25
I have a dell bluetooth mouse, Its basic functions all work but the extra buttons apparently need drivers. I looked around dell's website for them but they didn't seem to be there. Is there anywhere to find these for linux or is there a way to use the windows drivers?

---

### Post by belda on 2008-02-25
it differs from mouse to mouse, but definitely dont try to use the win drivers, they probably wont even do anything. You might try changing the xorg.conf file.
```
sudo nano /etc/X11/xorg.conf
```
there locate the mouse section, and change it to something like
```
Section "InputDevice"
        Identifier  "Mouse1"
        Driver      "mouse"
        Option      "Protocol" 		"ExplorerPS/2"
        Option      "Device" 		"/dev/input/mice"
        Option      "ZAxisMapping" 	"4 5"
        Option      "Buttons" 		"9"
EndSection
```
save and restart X (ctrl+alt+backspace) or the whole system
if this doesnt help, you can look in other threads
[http://ubuntuforums.org/showthread.php?t=556812](http://ubuntuforums.org/showthread.php?t=556812)

---

