---
title: "Wacom intuos 3.  works fine except buttons and strip."
date: 2007-07-05
forum: General Help
---

### Post by onzephyr on 2007-07-05
Hello.

 I have a Wacom tablet  Intuos 3   the pen/easer and pressure  work just fine in any program I use.  gimp, inkscape, blender.   As do the buttons on the pen.   My problem is the buttons and strips located on the pad do not work.    

I'm running ubuntu  7.04   desktop.  and  to my knowledge have not modified anything relating to  my wacom tablet in xorg or any other place so far.   Everything that is working is doing so from just the basic install.   

If anyone could point me in the right direction I would be very grateful.  
thank you.

---

### Post by fragos on 2007-07-05
First you need to add an input device called "pad".  My xorg config for a Graphire4 are below:

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
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

You'll also need to add "pad" to the server layout as below

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
EndSection

These actions are required for the keys on your pad to work.

---

### Post by onzephyr on 2007-07-06
Thank you fragos.  

       I added those lines and now the buttons/strip seem to work.   But if I open up gimp and press any of the buttons the menus flicker a little bit but nothing seems to happen.  I know I need to go into  ctrl+k  preferences and go to configure extended input devices.   

           go to   device : pad    mode " not sure what to put"  
           go to  the keys tab.  and I am presented with  entries for  1-8 . 

       But if I place anything into these spots it does not seem to matter.  By this I mean  I placed the hot key for the move tool  "v"  into every button  but once I saved and went back to my image none of the buttons seemed to select the move tool.  
       I must be missing something. but i'm not sure what.  I am getting some kind of input from the keys I can see a flicker responce on screen but nothing changes. 
        
       Also I tested it out in blender and every wacom pad button seem to be mapped to mouse button 3.   but hey least I know they are working now.

       Do I need to get some program so that I can assign  keys?
In the end if possible I would like to have key setting for each of the programs I use.  If that is something I can figure out. 
      Thank you again .

---

### Post by fragos on 2007-07-06
Check out "xsetwacom", it's command line but configures all aspect of the Wacom.

---

### Post by onzephyr on 2007-07-07
thanks fragos. 

    I'll look in to that command and see if I can make sense of it.  
thanks for the reply

---

