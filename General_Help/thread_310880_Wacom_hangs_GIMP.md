---
title: "Wacom hangs GIMP"
date: 2006-12-01
forum: General Help
---

### Post by holycoww74 on 2006-12-01
Hi all, I know other people have had problems similar to this, but I've found no answers anywhere, so I'm asking again....

  I'm on xubuntu, have a wacom graphire 3, and the GIMP.  everything works allright as long as I don't try to click on anything outside the image window..... like .... changing colors, or brushes, or switch layers... I've set up my hotkeys so I don't need to do it much, but whenever I do, my whole system just hangs for up to two minutes!!!!  the mouse moves, but nothing is clickable.... very annoying, but not fatal.

  ```

#Wacom Section

Section "InputDevice"

    Identifier     "stylus"                                                 
    Driver         "wacom"                                              
    Option         "Device" "/dev/input/wacom"        
    Option         "Type" "stylus"
    Option         "USB" "on"
    Option	   "PressCurve" "50,0,100,50"
    Option         "Mode" "Absolute"
EndSection

Section "InputDevice"

    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"        
    Option         "Type" "eraser"
    Option         "USB" "on"
    Option         "Mode" "Absolute"               
EndSection

Section "InputDevice"

    Identifier     "cursor"                                                 
    Driver         "wacom"   
    Option         "Device" "/dev/input/wacom"             
    Option         "Type" "cursor"
    Option         "USB" "on"
    Option         "Mode" "Relative"
EndSection

```

I don't know if there is anything else you need to see... or if there are any error logs I can look at.... but this a problem I'd like to fix.

thanks all!

---

### Post by nolla on 2007-09-07
I have the same problem. Is this something that is only on xfce? Could someone GUESS what it is about... Its extremely annoying.

---

### Post by fragos on 2007-09-07
Gimp allow you to select maping the window or screen to the tablet.  I use screen and have no problems.  This would need to be set separately for cursor, eraser and stylus.

---

### Post by nolla on 2007-09-09
Actually i think i solved the problem...

It has something to do with xorg.conf. I removed anything to do with eraser and cursor and set "AlwaysCore" on. They didint really do anything, the wacom worked as usual, frequently hanging the screen. Then i found out that i need the "USB" to be set on. Now i havent been able to freeze it even with huge pics and lots of programs on the background.

Nice.

See this for details --> [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

Let me know if it works for you too.

---

### Post by nolla on 2007-09-09
Uh. Never mind. It hangs again. 

Strange. It seems to hang more the longer time i use gimp...

---

### Post by fragos on 2007-09-09
Just for reference, I've included the parts of my xorg.conf that relate to my Wacom Graphire4.  I've had the pad for some time, use it daily and only have had it crash once.  Note that my laser mouse and wired touchpad both still worked.  With the next boot all worked again.

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Stylus2" 	"3"  # set button to right click
	Option		"Type"		"stylus"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"Speed"         ".8"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"        "/dev/input/wacom"
	Option		"Type"          "pad"
	Option		"USB"           "on"
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by nolla on 2007-09-09
Seems pretty much similar.

I was thinking that it must be something to do with gimp and xorg arguing over control of the wacom. If i understood correctly, gimp gives the xorg the control of the cursor when switching from the paint area to another window.

Where are the wacom properties in gimp? Not the crappy graphical ui that doesnt work for me anyway.

---

### Post by fragos on 2007-09-09
File-> Preferences-> "Input Devices"-> "Configure Extended Input Devices"-> Mode: give options for Screen, Window or disabled.  Can be set for each device, Pad, Eraser, Cursor and Stylus.  I must be honest and don't know the difference between between cursor and stylus since the cursor moves with the stylus.  I set all of mine to "screen".

---

### Post by nolla on 2007-09-10
No but for me those wont work. When i open the window that is supposed to have those tools, it appears ok, the "eraser" is there and i can change it to "screen". Also the pressure options and such are there. BUT when i switch the eraser to stylus, all the options except the screen/window disappear. Then i try to switch it back to "eraser" that seemed to work and it has not got any options either.

So i was thinking that there must be some file i could edit that controls this stuff in gimp?

---

### Post by fragos on 2007-09-10
I see you have a mix of Mode relative and absolute.  I let that Mode default.  The Gimp GUI does need work.  Try using "xsetwacom" to configure your tablet.

---

### Post by gali98 on 2007-09-18
Well as far as gimp goes, I noticed that you had the pad in xorg.conf, and i know that in gimp you are supposed to leave pad as not anything (i know there's window and screen, use what's left in that list.) I don't think that's it, but you could try it anyway.

---

