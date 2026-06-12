---
title: "Implementing a Patch in Ubuntu?"
date: 2007-12-07
forum: General Help
---

### Post by jmg498 on 2007-12-07
I would like to install the following patch in order to get my IBM Thinkpad's Track Point device working properly: [http://people.clarkson.edu/~evanchsa/software/kernel/patches/trackpoint-2.6.11.7.patch](http://people.clarkson.edu/~evanchsa/software/kernel/patches/trackpoint-2.6.11.7.patch)

However, I am unsure how to implement it.  Everything on the web just says to use it but never explains how.  Being rather new at Linux, I'm not really sure.  I believe there is a patch command, but is this what I should use?  Whenever I try patch -p0 patchname it errors out.  I think it's because I'm not patching the right file.

Any suggestions?  Thanks!

---

### Post by MRCeltic on 2007-12-25
I didn't have to install any patches for the trackpoint to work on my thinkpad R40 the only issue that i did have was that my trackpoint scroll wouldn't work.  I'm running Ubuntu 7.10 if the rest of your buttons are working and you are just trying to get the scroll to work in Mozilla and so forth, here's what i had to do to make it work.   

If you want you can back up or old xorg,conf file.  Me after several attempts with my logitech mouse said to hell with it.  And just modded the file I found a few sites about the trackpoint but wasn't sure on them all cause they all showed different sections in the xorg file or had another kind of file.  i just took those two lines from something someone else pointed out on another distro and worked like a charm got lucky i guess.  Let me know if this helps you.


open terminal
sudo gedit /etc/X11/xorg.conf

find this section

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Add these two lines

        Option		"EmulateWheel" 		"on"
	Option		"EmulateWheelButton"	"2"

End Result should look like this

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"EmulateWheel" 		"on"
	Option		"EmulateWheelButton"	"2"
EndSection

---

