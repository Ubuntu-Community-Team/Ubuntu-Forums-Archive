---
title: "Wacom tip/eraser reversed in Photoshop 7 (Crossover Office)"
date: 2007-01-28
forum: General Help
---

### Post by Kaladar on 2007-01-28
I have Crossover Office 5 installed. Installed Photoshop 7 with no problem.

Now, after a bit of tweaking in Xorg.conf [ HOWTO: Enable your Wacom Intous/Graphire Tablet with Pressure Sensitivity]("http://ubuntuforums.org/showthread.php?t=25151") , I was able to get GIMP to recognize my Wacom's pressure settings (Graphire 3). 

At first, it appeared that Photoshop 7 had stopped recognizing input. I could still move cursor and click on menus. After a few minutes of poking around, I discovered that the 'tip' of my pen was acting like the ERASER! If I turned the eraser-side down, I got input with pressure.

GIMP sorta has it right too, even though it treats both ends like the tip (never swaps to the eraser).

Any ideas?

---

### Post by gottferdamnt on 2007-05-24
Up! Same issue with photoshop 7 and a Wacom Graphire 3!

---

### Post by Malachi Wolfe on 2007-05-26
Bump! Intuos 3, and the pen is reversed in photoshop 7. Works fine under GIMP (Dealing with the reversed eraser of course) but this is the only thing that's keeping me from getting my girlfriend happy with photoshop in ubuntu. =P

---

### Post by fragos on 2007-05-26
Perhaps xsewacom can help you.  What does your xorg.conf Wacom statements look like?  I haven't heard anyone with your particular problem.  The scrool wheel on the Wacom mouse and on the Graphire 4 tablet work in the opposite direction from regular mice.  I believe that can also be delt with but I haven't bothered to try.

---

### Post by Malachi Wolfe on 2007-05-27
There's a fix for the mouse wheel being backwards that I found here: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Pressure sensitivty is only being recognized when the button on the pen is held down in Photoshop 7. 

It doesn't treat the eraser on the pen as a seperate tool in P7 either. Works in Gimp if I -tell- it to behave like an eraser, but not in P7.

Sections from xorg: 

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "pad" 
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
 

        Identifier  "pad"
        Driver      "wacom"
        Option      "Device"        "/dev/input/wacom"   #USB ONLY
        Option      "Type"          "pad"
        Option      "USB"           "on"                  #USB ONLY
EndSection

---

### Post by Malachi Wolfe on 2007-05-31
Okay, I think I've figured it out. Should the tablet read the pen when it's not even touching the pad?

---

### Post by fragos on 2007-05-31
The tablet can sens the stylus when its close to but not touching the pad.  Although not measured I think .25 inch is close enough to be to be senses and respond with cursor movement.

---

