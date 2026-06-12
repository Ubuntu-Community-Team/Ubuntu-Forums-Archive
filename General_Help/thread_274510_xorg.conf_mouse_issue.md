---
title: "xorg.conf mouse issue"
date: 2006-10-09
forum: General Help
---

### Post by equal on 2006-10-09
sigh. you know when they tell you to make a backup of the file, and you think "pfffffffffffft backup". yeah. go me.

The problem I'm having is this: I tried following the advice given on this page [here ]("http://www.cs.cornell.edu/~djm/ubuntu/")to configure a 5 button mouse (which, if I'm not mistaken should be called a 7-button mouse).

Now I get an error saying line 54 of my xorg.conf file is causing a problem, that "..." is not a valid option.

I tried changing it to what's written in the how-to page. doesn't work. Tried changing it to what's written as the old setup, doesn't work.

If I'm not mistaken though, my original xorg file didn't say
Option "Protocol" "ExplorerPS/2"
It had something other than ExplorerPS/2

any ideas?

---

### Post by wieman01 on 2006-10-10
Does that help?
> Identifier "Mouse"
Driver "mouse"
Option "Protocol" "IMPS/2"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5"
Option "Buttons" "5" 

---

### Post by antw on 2006-10-10
try 

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "Buttons" "7"
	Option "ButtonMapping" "1 2 3 6 7"
	Option "ZAxisMapping" "4 5"
	Option "Emulate3Buttons" "false"

---

### Post by wieman01 on 2006-10-10
And that's the default that should definitely work:
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

---

