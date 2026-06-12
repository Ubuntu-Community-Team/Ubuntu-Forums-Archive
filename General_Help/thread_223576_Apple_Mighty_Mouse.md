---
title: "Apple Mighty Mouse"
date: 2006-07-26
forum: General Help
---

### Post by neoncode on 2006-07-26
I have recently gotten an Apple Mighty Mouse for my PC. However in kubuntu it has a few problems...

Firstly, sideways scroll does not work. A little light googleing turns up [this]("http://fob.po8.org/node/165"), that web page supplys a pacth but I have no idea how to apply it. 

Secondly the middle-click(the ball) does, well I don't know what it does. Could someone explain what that button does? Spesificly in web browsers...

And lastly the squeeze click thing does the same thing as the middle-click, is there any way to configure that to do something else, activate kompose for example?

Thank you. I appreciate any help anyone can give me. :D

---

### Post by borg6850 on 2007-04-26
Heyo

Not sure if you are still having troubles, but for the sake of at least having some directions out there....

in your /etc/X11/xorg.conf comment out your existing mouse section and replace it with this:

```

Section "InputDevice"
Identifier "Configured Mouse"
Option "CorePointer"
Driver "evdev"
Option "Name" "Mitsumi Electric Apple Optical USB Mouse"
Option "HWHEELRelativeAxisButtons" "7 6"
Option "Buttons" "8"
EndSection

```

*taken from here:[http://people.debian.org/~terpstra/message/20070412.084711.f738a38d.en.html]("http://people.debian.org/~terpstra/message/20070412.084711.f738a38d.en.html")

On top of that you'll have to make some adjustments in firefox to keep sanity....

> Simply launch Firefox. Enter about:config as the URL and hit enter. Then scroll down the page until you come to this entry:

mouse.horizscroll.withnokey.action user set integer 2

Change it to read:

mouse.horizscroll.withnokey.action user set integer 1

To do this, simply double click on the 2, and a pop-up window will appear; enter 1 and press Return. The only drawback to this (which I have not yet figured out how to solve) is that when I scroll left and right, the directions are reversed. This is still better for me than scrolling forward and backwards through pages.

*taken from here:[http://www.macosxhints.com/article.php?story=20050821141856688]("http://www.macosxhints.com/article.php?story=20050821141856688")


*** Note, this is the stock Xorg in Fiesty

---

### Post by Dagibit on 2007-05-20
Thanks a lot for this guide, borg.

However I have run into a little something: I apparently don't have permissions or something to modify xorg.conf. I would try it from root, but I was already pretty nervous about messing with this stuff (yes, I am a huge noob).
What's the worst thing that could happen from doing this (in fiesty)? Should I go ahead and do this from root?

Again, thanks a LOT!

---

### Post by borg6850 on 2007-05-20
Heyo,

Yes I did forget to mention that modifying those files do need root permissions.

Being a noob is ok, we have all been there.  I just hope that I can help you avoid some of the larger pitfalls I fell into.

My first suggestion would be to backup the xorg.conf file and place it in a new directory (to keep things nice and tidy) in your home directory.  So open your fav. terminal, and punch this in:

```

mkdir ~/xorg-backup
cp /etc/X11/xorg.conf ~/xorg-backup

```

The first line creates a directory in your home directory, the second copies you current (and working) xorg.conf

You can then make the above changes without fear of breaking something.
To answer your question directly, the worst that can happen is that you break X.
This means that your graphical display manager won't work.  You'll see the screen blink a few times, and you'll get a garbled message saying that X didn't start.  Don't panic, this can be fixed.

Exit the error messages  (by either saying yes and watching the error output - this can give you clues as to what went wrong - or saying no).  It'll mention something about the X server not working, and it will disable GDM (the gnome login manager) temporarily.  From there is will drop you to a console login screen.

Login as your previous user (probably you) and execute the following:

```
sudo mv /etc/X11/xorg.conf ~/xorg-backup/xorg.conf.broken
sudo cp ~/xorg-backup/xorg.conf /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

This first command takes your broken xorg.conf and places it in the backup directory so you can have a look at it later, and hopefully figure out what went wrong.
The second command copies your backed up xorg.conf and copies it back (leaving a file behind for future use)
The third command restarts X, now with the old (and working) xorg.conf file.

Now actually implementing the changes can be done with the proper permissions by punching in this:

```
sudo gedit /etc/X11/xorg.conf
```

From there you can make the needed changes.

I should also mention that as a side note... The horizontal scrolling is a little backwards.  Once I have found a solution, I will post it.

If you run into any problems, let me know.

---

### Post by Dagibit on 2007-05-25
VICTORY!!! Horizontal scroll now works, and works perfectly in Inkscape which is all that's really important to me right now. THANK YOU!!!! And good luck on finding the solution to the backwards Firefox problem! :D:D:D:D:D

---

### Post by gojomo on 2007-05-31
My success took a little more work, which I'll record here for future searchers: 

(1) My mouse's name is apparently "Primax Electronics Apple Optical USB Mouse", which I found out by looking at the output of "less /proc/bus/input/devices". Using the wrong name in the xorg.conf mouse section prevents X from starting. (Also, I think I had to plug the mouse in directly, not through the USB hub jacks on my keyboard, for it to appear in "/proc/bus/input/devices" -- though it works fine from there, before and after enabling horizontal scrolling.)

(2) The problem with inverted horizontal scrolling in Firefox can be remedied by changing 'mousewheel.horizscroll.withnokey.numlines' to '1' (from -1). 

The final net changes to my xorg.conf were:

In the 'ServerLayout section, updated mouse line to read:

    InputDevice    "MightyMouse" "AlwaysCore"

Replaced the existing mouse section with:

 Section "InputDevice"
    Identifier "MightyMouse"
    Option "CorePointer"
    Driver "evdev"
    Option "Name" "Primax Electronics Apple Optical USB Mouse"
    Option "HWHEELRelativeAxisButtons" "7 6"
    Option "Buttons" "8"
EndSection

---

### Post by joselin on 2007-06-11
Are you able to use side mouse buttons?

Is the only thing that does not work for me.

Regards

---

### Post by Dagibit on 2007-06-18
The don't work for me either. No big deal to me, though :/

---

### Post by joselin on 2007-06-20
> **joselin said:**
> Are you able to use side mouse buttons?



I answer myself. Side buttons are button8 and button9 and works fine without tweaking.
I knew it reading some posts on xorg's mailing list (can't remember the url), the most important thing is how buttons are configured:

button1 --> left button
button2 --> right button
button3 --> middle button
button4 --> vertical wheel up
button5 --> vertical wheel down
button6 --> horizontal wheel left
button7 --> horizontal wheel right
button8 --> right side button
button9 --> letf side button

After then i tried to configure a beryl action as button8 and works like a charm.

Regards

---

### Post by cawpin on 2007-06-24
> **borg6850 said:**
> Heyo

Not sure if you are still having troubles, but for the sake of at least having some directions out there....

in your /etc/X11/xorg.conf comment out your existing mouse section and replace it with this:

```

Section "InputDevice"
Identifier "Configured Mouse"
Option "CorePointer"
Driver "evdev"
Option "Name" "Mitsumi Electric Apple Optical USB Mouse"
Option "HWHEELRelativeAxisButtons" "7 6"
Option "Buttons" "8"
EndSection

```

*taken from here:[http://people.debian.org/~terpstra/message/20070412.084711.f738a38d.en.html]("http://people.debian.org/~terpstra/message/20070412.084711.f738a38d.en.html")

On top of that you'll have to make some adjustments in firefox to keep sanity....



*taken from here:[http://www.macosxhints.com/article.php?story=20050821141856688]("http://www.macosxhints.com/article.php?story=20050821141856688")


*** Note, this is the stock Xorg in Fiesty

I'm running Firefox 2.0.0.4 on Feisty. The "mouse.horizscroll.withnokey.action" is actually called "mousewheel.horizscroll.withnokey.action" changing this to 1 enables horizontal scrolling and changing the "mousewheel.horizscroll.withnokey.numlines" to 1 (from -1) corrects the direction.

---

### Post by ZERO_SHIFT on 2007-06-27
Will the mighty mouse work with fesity, if so is there a program that has to be installed to enable the bluetooth syncing of the mouse with the computer?

Thanks

---

### Post by nandotron on 2007-07-07
Hi,

I just bought a mighty mouse and am trying to configure it to work with feisty.  So far and I have paired it and it works, except for the side buttons which don't do anything, and the ball which scrolls pages up and down when i move it left and right, and does nothing when i move it up and down.

I think i need to modify my /etc/X11/xorg.conf file but from reading the posts in this thread, it looks like i need to find out the proper name for the bluetooth mighty mouse first.  How do i find this out?  Any help would be appreciated!

Thanks!

Nando

---

### Post by mdneilson on 2007-08-26
You can view attached devices with "less /proc/bus/input/devices" your mighty mouse should be in there.

---

### Post by rapchee on 2007-08-29
is there a way to disable certain buttons? specifically i am annoyed by the side buttons. whenever i squeeze the mouse, the machine stops for a second.
thanks in advance

---

### Post by nandotron on 2007-09-24
Hi,

I followed the instructions but I keep breaking X.  Anyone know if the update to kernel 2.6.20 invalidates the instructions?

---

### Post by nandotron on 2007-09-28
Hi, A little more info:  i have successfully gotten my mighty mouse to work with horizontal scrolling and button 8.  the only problem is that when I restart the computer, X breaks.  here is my original xorg.conf:


> Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	96.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection 



this is the modified xorg.conf that breaks x:

> 
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Mighty Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Mighty Mouse"
Option "CorePointer"
Driver "evdev"
Option "Name" "Apple Computer, Inc. Mighty Mouse"
Option "HWHEELRelativeAxisButtons" "7 6"
Option "Buttons" "8"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	96.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

is anyone can offer a tip it be great! thanks!

---

### Post by spigolo on 2007-10-16
Hi 
I was fiddling with this thing today, and it seems that my mightymouse button6 is the side buttons, and apparently I cant find the button numbers for horizontal scrolling (first 5 as default, 6 is side buttons, 7 and over nothing happens).

so now i got hscroll with the side button, which is really funny but not much of a use. :)

am i the only one with this?

---

### Post by jslmg on 2007-11-09
> **nandotron said:**
> Hi, A little more info:  i have successfully gotten my mighty mouse to work with horizontal scrolling and button 8.  the only problem is that when I restart the computer, X breaks.  here is my original xorg.conf:

Nando, the same thing happened to me! Before I found your post, I reported this problem on this thread:
[http://ubuntuforums.org/showthread.php?t=574631](http://ubuntuforums.org/showthread.php?t=574631)

I had to download a new xorg.conf file, and now I'm back to where I started--no wireless keyboard or mouse.

---

### Post by dillbertdabomb on 2007-12-09
check the mouse name!
that was the problem earlier, i don't have one, but it *might* be it, 
 
Mitsumi Electric Apple Optical USB Mouse

---

### Post by erlyrisa on 2008-04-15
after much stuffing around I finally got some action from my mighty mouse


```
Section "InputDevice"
Identifier "Mouse[1]" #My Mighty Mouse
#	Option		"CorePointer"
Driver "evdev"
Option "Buttons" "8"
Option "ZAxisMapping" "7 6 5 4" #Yeap my side scroll is the wrong way around" -I guess this line means nothing to evdev.
####### I had to add everything!!! -dev name wasn't enough... and according to the manual I should be using the 1st line at least.
Option "Device" "/dev/input/event2"
Option "Dev Name" "Primax Electronics Apple Optical USB Mouse"
Option "Dev Phys" "usb-0000:00:1d.0-1/input0" #hate having to have to use this -> but have no choice.
Option "Emulate3Buttons" "no" #probably no effect (can't tell -it's a touch sensitive mouse!)
	Option		"SendCoreEvents"	"true"
EndSection
```

1....
I can't get it to be the "core pointer" ---> if I delete the "configured mouse" .... than of course Xorg refuses to boot. (it can't find a mouse)... the same goes if I try and get the Synaptics mouse to be core.

...but I don't really want it to be core anyway....

my problem is this...

```


me@mycomputer:~$xinput test "Mouse[1]"
motion a[0]=221 
motion a[0]=223 
motion a[0]=224 
button press   1 
button press   1 
button press   1 
button press   1 
button press   1 
button press   1 
button press   1 
button press   1 
button press   1 
button release 1 

```


when really every button press is supposed to have a button release.... I have no idea what I am to add to the evdev settings.

and for brevity here is the mouse as xinput sees it...
```

me@mycomputer:~$xinput list "Mouse[1]"
"Mouse[1]"	id=2	[XExtensionPointer]
	Num_buttons is 9
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```


PS for any bug developers out their....

clicking on the desktop and dragging with the mouse in this state hangs the desktop (specifically nautilus)

---

