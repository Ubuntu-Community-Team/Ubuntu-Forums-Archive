---
title: "Hotkeys in kubuntu"
date: 2014-10-30
forum: General Help
---

### Post by Tom_Carr on 2014-10-30
I can't find a list of keyboard shortcuts for Kubuntu.  I can't find info on how to set up my own hotkeys.  I would like shortcuts to open dolphin, chromium, gedit and a few more apps.

---

### Post by deadflowr on 2014-10-30
System settings >> Shortcuts and gestures.
Click on custom shortcuts.
Now go down to the option Edit , then click on new >> (I use global shortcut, but you can try either of the others)
Then you want to set the shortcut bindings with trigger, and the action the bindings will execute with actions >> command/url.

Try it by making a trigger and then simply use dolphin as the action/command.

The click on Apply in the corner, and try it out.

Of note, sometimes commands are not as easy to figure out like dolphin is.
In this case a simple way to find what a command is is to look in the folder /usr/bin(these are where the executables typically are.
Sometimes though they are in different places, another place to look is in the applications desktop file.
These are typically in the folder /usr/share/applications.
Since these are basically launchers and clicking on them normally makes them launch, you are best to open them directly in the text editor to view the contents.
Hope that helps.

---

### Post by Tom_Carr on 2014-10-31
Thanks deadflower.  That works great.  Very helpful.

---

