---
title: "Specifc window or widget focus toggle"
date: 2008-04-29
forum: General Help
---

### Post by Zxaos on 2008-04-29
I've got a little bit of an annoyance I'd like some help with.

Is there any way using gnome/compiz to toggle focus to one specific window?

For example, I've currently got screenlets set up and toggling with the f9 key through compiz.  What I'd like to do is match that up with a focus hotkey so that when I press f9, it activates the widget layer and gives a specific widget keyboard focus. I press f9 again and the widgets disappear and focus returns to the windows that previously had it.

My first guess would be some sort of bash script that targets with window names, but I wouldn't know how to write that, and I wouldn't know where to bind it to f9 either.

Any help or suggestions would be appreciated.

---

### Post by Zxaos on 2008-05-03
Anyone?

---

### Post by Zxaos on 2008-05-23
Ok, so I've got this *nearly* solved. I've installed wmctrl, and set up a simple shell script to call it to set the focus after a delay - 
```
#!/bin/bash
sleep 1 && wmctrl -R TerminalScreenlet.py
```

The issue now is that I don't seem to be able to have the hotkey both activate the widget layer *AND* run the script. The script works correctly, I've tested it by activating the widget layer and then running the script in another terminal window - the terminal widget takes focus as expected, and when the widget layer is hidden the script doesn't do anything since there aren't any active windows named TerminalScreenlet.py.

So the question turns into - can anyone help me find a way to bind more than one action to a hotkey in compiz or metacity?

---

### Post by ripps818 on 2008-08-09
In order to call the Widget Layer and focus on a terminal widget I use this script.
```
#!/bin/bash
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/widget/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
wmctrl -R TerminalScreenlet.py
```

Then just bind the script to whatever command and key in General Options that you want.
Unfortunately, you can't use this with the hot corners.

---

