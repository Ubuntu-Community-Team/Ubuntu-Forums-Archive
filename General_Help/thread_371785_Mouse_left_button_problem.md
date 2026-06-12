---
title: "Mouse left button problem"
date: 2007-02-27
forum: General Help
---

### Post by wehrmanweb on 2007-02-27
I'm having some problems with my mouse click speed. when I select anything with the left click I have to hold the button down for a good .5 - .75 seconds for it to select what I'm clicking. This makes double clicking this a pain. As it stands now it is faster for me to right click a folder and right click on open then it is to open the folder the normal way. The right button works as it should with a tap and I get the appropriate menu.

I'm at work on a XP box at work so the settings are coming from memory.

Ubuntu Edgy
Beryl is running.
MS IntelliMouse Explorer - edited settings so extra buttons work.

Double click speed 400 I've adjusted this to just about every speed and same results. 

I don't know if it's the mouse that is causing the problem or Ubuntu.

Thanks for any help.

---

### Post by clint1010 on 2007-02-27
> MS IntelliMouse Explorer - edited settings so extra buttons work.


I wasn't aware that this has been ported to Linux ???

If you adjust the click speed and nothing changes, I suspect your mouse is faulty.

Do you have another mouse to try out on your system?

---

### Post by wehrmanweb on 2007-02-27
> **clint1010 said:**
> I wasn't aware that this has been ported to Linux ???

If you adjust the click speed and nothing changes, I suspect your mouse is faulty.

Do you have another mouse to try out on your system?

I'm going to try a mouse from work and see if that is the problem. I hope that's the problem because I need a good reason to get a new mouse. 

It really wasn't ported to Linux you just need to edit the xorg.conf so it can see the extra buttons.

kind of like this (This isn't my xorg.conf)
...
Section "InputDevice"
   Identifier  "Mouse0"
   Driver      "mouse"
   Option      "Protocol"     "ExplorerPS/2"
   Option      "Device"       "/dev/input/mice"
   Option      "Buttons"      "7"
   Option      "ZAxisMapping" "6 7"
EndSection
...

---

