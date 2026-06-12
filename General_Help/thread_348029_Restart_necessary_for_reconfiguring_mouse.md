---
title: "Restart necessary for reconfiguring mouse?"
date: 2007-01-28
forum: General Help
---

### Post by _jj on 2007-01-28
Decided to take the plunge and move from windows, now running ubuntu and kubuntu (edgy eft).  Generally everything fine but am having problems configuring my 5 button mouse (currently my scroll wheel moves forward and back and the side(thumb?) buttons do nothing)

I have read ways to fix this and am trying them, but was wondering, after changing the configuration files (ie xorg.conf and imwheelrc) do i need to do a full restart to see the effect of the changes?  Is there anyway I can see the effect of the changes without a full restart (both for this and any other types of changes I make)?

If anyone has any ideas relating to my current mouse situation here is the relevant section of my xorg.conf file

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" 		"/dev/input/mice"
        Option      "Protocol" 		"ExplorerPS/2"
        Option      "ZAxisMapping" 	"6 7"
        Option      "ButtonMapping" 	"1 2 3 4 5"
EndSection

Thanks a lot!

---

### Post by Ramses de Norre on 2007-01-28
A golden rule: you never have to restart linux except for kernel upgrades.

For changes you make to your xorg.conf you only have to restart your X server, to do so: close all programs (or you might loose changes you've made) and press ctrl+alt+backspace. 
You'll then see the login screen again and your xserver is restarted.
Make sure you're xorg.conf has no syntax errors and always make backups, otherwise your X server might not start.

---

