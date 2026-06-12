---
title: "Mouse buttons switched after Edgy upgrade"
date: 2006-11-17
forum: General Help
---

### Post by zergberg on 2006-11-17
After I upgraded to Edgy, I discovered that my right and middle mouse buttons were switched under both the standard mouse driver and evdev. How do I switch them back?

---

### Post by bayvista on 2006-11-18
System - Preferences - Mouse

---

### Post by mgmiller on 2006-11-18
I have had the same problem,  I have gotten all my buttons working again in firefox 2.0 by editing /etc/X11/org.conf

first back it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then edit the file:
```
sudo gedit /etc/X11/xorg.conf

```
This is what my mouse section looks like:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" 		"/dev/input/mice"
        Option      "Protocol" 		"ExplorerPS/2"
        Option      "ZAxisMapping" 	"6 7"
        Option      "ButtonMapping" 	"1 2 3 4 5"
EndSection
```

You will see the zaxis and buttonmapping lines have changed their numbers around since Dapper.

Save your changes and log off and restart x for the changes to take effect. (ctrl+alt+backspace)

The buttons should work normally in firefox.  
I used the imwheel method to get the side buttons working in nautilus with Dapper, but I can't get the side buttons to work yet in Edgy.

At least this is a start for you.

---

