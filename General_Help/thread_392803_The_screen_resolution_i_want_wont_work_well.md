---
title: "The screen resolution i want wont work well"
date: 2007-03-24
forum: General Help
---

### Post by Eduardo Serra on 2007-03-24
I installed ubuntu last night, and frankly, is starting to piss me off in some aspects. well, but im trying and i will get used to it eventually, i hope. I need help with a single problem for now. the resolution on my screen is set to 1024x768 and i cant stand that, i need to use 1280x1024, but when i select this option its like instead of really using it, it becomes a larger screen, and i have to use my mouse to scrool to the end of it, like my desktop becomes bigger than my screen instead of fitting "inside" it. is this normal? what can i do?  help is greatly apreciatted

---

### Post by aysiu on 2007-03-24
[This](http://ubuntuforums.org/showthread.php?p=454217) has some good tips.

---

### Post by dfreer on 2007-03-24
One method would be to modify the /etc/X11/xorg.conf file by hand. Start by opening the terminal and enter these commands:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```
There is a bunch of stuff in this file, what you will be looking for is a section that looks like this (this is what mine looks like):
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
**[B]		Modes		"1280x800" "1024x768" "800x600" "640x480"**[/B]
	EndSubSection
	SubSection "Display"
		Depth		4
**[B]		Modes		"1280x800" "1024x768" "800x600" "640x480"**[/B]
	EndSubSection
	SubSection "Display"
		Depth		8
**[B]		Modes		"1280x800" "1024x768" "800x600" "640x480"**[/B]
	EndSubSection
	SubSection "Display"
		Depth		15
**[B]		Modes		"1280x800" "1024x768" "800x600" "640x480"**[/B]
	EndSubSection
	SubSection "Display"
		Depth		16
**[B]		Modes		"1280x800" "1024x768" "800x600" "640x480"**[/B]
	EndSubSection
	SubSection "Display"
		Depth		24
**[B]		Modes		"1280x800" "1024x768" "800x600" "640x480"**[/B]
	EndSubSection
EndSection
```

Note the lines in bold. You will probably want to add *"1280x1024"* to the beginning of each *"Modes"* Line. Reboot. If X server crashes, you can restore the backup of your xorg.conf file with this command:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Hope this helps!

---

### Post by Eduardo Serra on 2007-03-24
all right, i did what the second poster told me and it was already in there, the 1280x1024 code. thanks anyway, im going to try with the poster's one more complicated way.

---

### Post by wj32 on 2007-03-24
Does your monitor actually support 1280x1024? Sorry about the stupid question.

---

### Post by Eduardo Serra on 2007-03-24
yes, im sure. i used it on windows my whole life. and i mean, maybe i wasnt clear with the problem, but the option DOES appear at the "screen resolution" window, but when i select it, instead of putting everything smaller, buttons, windows, everything, it gives me the possibility to move the screen to my right, left up and down. for example, if im at the top, i can see the "application places system", but i have to scroll down to see the taskbar or whatever is called.

---

### Post by Eduardo Serra on 2007-03-24
i need help

---

### Post by Eduardo Serra on 2007-03-24
I posted a problem i had in this topics and haven't got a solution ([http://ubuntuforums.org/showthread.php?t=392385)](http://ubuntuforums.org/showthread.php?t=392385)), this problem is the only one strong enough to get me back crawling to windows... please help!

---

### Post by Eduardo Serra on 2007-03-24
I posted a problem i had in this topics and haven't got a solution [http://ubuntuforums.org/showthread.php?t=392385]("http://ubuntuforums.org/showthread.php?t=392385") this problem is the only one strong enough to get me back crawling to windows... please help!

---

### Post by barney_1 on 2007-03-24
You first post in the other thread is only 9 hours old.  You need to exercise some patience with this issue.  There are a lot of nice people here that will help you with you're problems if you are nice in return.

Give it a few day's more and see if the forums can help you correct your monitor resolution.

---

### Post by pjones0404 on 2007-03-24
what video card do u have and have you installed the correct driver for it? i would also run "sudo dpkg-reconfigure xserver-xorg" and make sure that i select the resolution that i wanted.

these types of thread titles do not help in resolving your issue. a subject that explains the issue will get people who know how to resolve it to look in here. a subect stating that you give up looks like all of the other threads w/ people complaining. also i would continue to use the same thread and not create another thread complaining that you can not fix the problem.

---

### Post by lamalex on 2007-03-24
also the newer version of ubuntu is being released in about 3 weeks, it has a newer version of Xorg which should have better monitor detection. You may want to try installing the beta, it is very stable but you could run into some problems so idk, do what you think is best. or just wait 3 weeks for fiesty final to come out.

---

### Post by taurus on 2007-03-24
Double post.

[http://www.ubuntuforums.org/showthread.php?t=392793](http://www.ubuntuforums.org/showthread.php?t=392793)

---

### Post by Eduardo Serra on 2007-03-25
sorry for the title, and for not being nice. youre right, i am being impatient. but also, im under the idea that if this thread becomes old and goes to page 15 of the forums it wont be read by anyone again.

---

### Post by Eduardo Serra on 2007-03-25
how do i check which video card i have with ubuntu? also, i tried the "sudo dpkg-reconfigure xserver-xorg" but i dont know what to select

---

### Post by alienexplorers on 2007-03-25
Sounds like a refresh rate problem.  What refresh rate are you trying to run.

---

### Post by aysiu on 2007-03-25
> **taurus said:**
> Double post.

[http://www.ubuntuforums.org/showthread.php?t=392793](http://www.ubuntuforums.org/showthread.php?t=392793)
Triple post, actually. I've merged all three.

---

### Post by seshomaru samma on 2007-03-25
> **Eduardo Serra said:**
> how do i check which video card i have with ubuntu? also, i tried the "sudo dpkg-reconfigure xserver-xorg" but i dont know what to select

type 
```
lspci
```
in the terminal to get a list of all your hardware

---

### Post by Eduardo Serra on 2007-03-25
> **seshomaru samma said:**
> type 
```
lspci
```
in the terminal to get a list of all your hardware

ok, thnxs, i have this:
 
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by Eduardo Serra on 2007-03-25
> **alienexplorers said:**
> Sounds like a refresh rate problem.  What refresh rate are you trying to run. i cant select any options there, it only has 85 hz

---

### Post by Eduardo Serra on 2007-03-25
im goint o sleep, tomorrow ill continue this quest. do you think if i install everything from scratch it could make a difference?

---

### Post by seshomaru samma on 2007-03-25
perhaps
but you will learn more by solving this problem
this is a new os for you and the best way to learn is by trying to solve problems

---

### Post by RedSquirrel on 2007-03-25
> **Eduardo Serra said:**
> I installed ubuntu last night, and frankly, is starting to piss me off in some aspects. well, but im trying and i will get used to it eventually, i hope. I need help with a single problem for now. the resolution on my screen is set to 1024x768 and i cant stand that, i need to use 1280x1024, but when i select this option its like instead of really using it, it becomes a larger screen, and i have to use my mouse to scrool to the end of it, like my desktop becomes bigger than my screen instead of fitting "inside" it. is this normal? what can i do?  help is greatly apreciatted

You need to add a line to your /etc/X11/xorg.conf:

```
Virtual 1280 1024
```You would add it to the section for 24 bit if that's what you are using. Here's mine for reference:

```
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1400x1050" "1600x1200" "1024x768" "800x600" "640x480"
                **Virtual         1280 1024**
        EndSubSection

```That says that the virtual desktop should be the same size as the resolution. Here's another thread where I answered this:

[http://ubuntuforums.org/showpost.php?p=2267126&postcount=4](http://ubuntuforums.org/showpost.php?p=2267126&postcount=4)

If you post your xorg.conf file, I can give you very specific instructions if that wasn't clear enough. :)

**EDIT:**

Another option if you're sure you're only going to use 1280 by 1024 is to delete all the other resolution from the **Modes** line:

```
        SubSection "Display"
                Depth           24
                **Modes           "1280x1024"**
        EndSubSection

```

---

### Post by Eduardo Serra on 2007-03-25
i added the virtual line and i still have the problem, ill paste you my code. im going to try deleting the other options, but do i delete the virtual line or not?
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ MV720"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ MV720"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
		Virtual 1280 1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Eduardo Serra on 2007-03-25
all right, this is weird. i erased all of the resolutions except the 1280x1024, and saved and rebooted, and its still the same, when i choose from the menu "screen resolution" i still have all the four options and i can use the 1024x768, am i doing something wrong?:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ MV720"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ MV720"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"  
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"  
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by RedSquirrel on 2007-03-25
> **Eduardo Serra said:**
> i added the virtual line and i still have the problem, ill paste you my code. im going to try deleting the other options, but do i delete the virtual line or not?

Now that I see your xorg.conf, I don't think you need the Virtual line. It is only useful if you have other resolutions in the Modes line that are larger than your chosen resolution (the one that appears first in that list). In my case, I still have 1400x1050 and 1600x1200 in my list, so I need the Virtual line.

I would add the information on **[SIZE=2]HorizSync [/SIZE]**[SIZE=2]and [/SIZE]**[SIZE=2]VertRefresh [/SIZE]**for your monitor. See the section **[SIZE=2]How to edit or add HorizSync and VertRefresh lines[/SIZE]**[SIZE=2] at [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)[/SIZE]

You will need to look in the manual for your monitor or use google to find that information.


Try deleting the other resolutions in the Modes line and see if that works.

**Are you restarting X after you made changes to xorg.conf?** Probably the easiest way to do that is to log out of your environment (GNOME, KDE, ...) and at the login window hit Ctrl-Alt-Backspace. That will restart X with the changes you made to xorg.conf.

---

### Post by RedSquirrel on 2007-03-25
> **Eduardo Serra said:**
> all right, this is weird. i erased all of the resolutions except the 1280x1024, and saved and rebooted, and its still the same, when i choose from the menu "screen resolution" i still have all the four options and i can use the 1024x768, am i doing something wrong?

No, I don't think so. ;) Do you still get that weird behavior if you select 1280x1024?

I was tinkering with Xfce (used in Xubuntu instead of GNOME) last night and in the Screen Resolution settings there I get some strange values too. Are you using GNOME? Is there a setting in Screen Resolution for "**Default**" or something? That's what I select in Xfce so that it will use the resolution I picked in xorg.conf.

Sorry I can't be more helpful. I don't have GNOME installed.

---

### Post by Eduardo Serra on 2007-03-25
no, it only has a "make this the default"

[IMG]http://i3.tinypic.com/2ezqq7p.png[/IMG]

---

### Post by Eduardo Serra on 2007-03-25
I have also tried playing with my monitor settings (brightness, screen position, etc) but it didnt make a difference no matter what I did

---

### Post by NyteGeek on 2007-03-25
> **Eduardo Serra said:**
> all right, i did what the second poster told me and it was already in there, the 1280x1024 code. thanks anyway, im going to try with the poster's one more complicated way.

Are you using a CRT or LCD monitor?

---

### Post by Eduardo Serra on 2007-03-25
> **NyteGeek said:**
> Are you using a CRT or LCD monitor? a CRT

---

### Post by Rui Pais on 2007-03-25
Hi,
your monitor is being detected as a  Compaq MV720.
If that is really the one you have add the following:

```
HorizSync	30.0 - 69.0     
VertRefresh 	50.0 - 100.0	
```
to Section "Monitor" (after Option	"DPMS")
and restart X server.

hth

---

### Post by Eduardo Serra on 2007-03-25
ive made and saved the changes you told, now im going to restart my computer and see

---

### Post by Rui Pais on 2007-03-25
just press Ctrl+Alt+Backspace ;)

---

### Post by Eduardo Serra on 2007-03-25
all right, that crtl alt backspace trick works, hahaha. the changes i made didnt change a thing, i dont know anything about this but ive changed a lot and nothing has changed, i dont think im doing nothing wrong. this is my actual code:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ MV720"
	Option		"DPMS"
	HorizSync	30.0 - 69.0     
	VertRefresh 	50.0 - 100.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ MV720"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"  
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"  
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by dfreer on 2007-03-25
Could this be related to the Intel 915 Graphics problem?

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by Eduardo Serra on 2007-03-25
this is what it tells me when i use this command:

```
eduardo@eduardo-desktop:~$ 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted
```

---

### Post by Rui Pais on 2007-03-25
you may need sudo to run it:
```
sudo 915resolution -l
```

btw did the issue happens if you change the DefaultDepth to 24?

---

### Post by Eduardo Serra on 2007-03-25
> **Rui Pais said:**
> btw did the issue happens if you change the DefaultDepth to 24?

I dont know, how do i change my Default Depth?

---

### Post by Rui Pais on 2007-03-25
> **Eduardo Serra said:**
> I dont know, how do i change my Default Depth?

just change the line (on xorg.conf, Section "Screen") from 
```
DefaultDepth 16 
```
to
```
DefaultDepth 24
```

---

### Post by Eduardo Serra on 2007-03-25
all right, i did it, and the problem persists. i dont notice any difference, whats that depth anyway? 
this is my code as for now:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ MV720"
	Option		"DPMS"
	HorizSync	30.0 - 69.0     
	VertRefresh 	50.0 - 100.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ MV720"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"  
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"  
		Virtual 1280 1024
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
		Virtual 1280 1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Rui Pais on 2007-03-25
> **Eduardo Serra said:**
> all right, i did it, and the problem persists. i dont notice any difference, whats that depth anyway? 
this is my code as for now:

Sorry it didn't work... haven't much hope on this last one, just wanted to make sure...
It means depth of colors "quantity", 24 enable max number of colors that's what usually everybody use.

Not much more ideas for now (maybe trying deleting those "Virtual" lines (not that make much difference but they aren't need... maybe they interfere with the manually set of Horz and vert Sync...)

good luck

---

### Post by victorbrca on 2007-03-25
Maybe something to do with the configuration of your video card on the BIOS?? Just shooting in the dark here...


BTW, I'm a new user too, and I can tell you that it's worth the work and the stress...



Vic.

---

### Post by Eduardo Serra on 2007-03-25
i deleted the "virtual" line and ctrl alt backspaced and tried but it didnt work. this is my actual code: (by the way, thanks for the help and support to everybody, im already sure ubuntu is worth it because of this community. i might not read again this thread until tomorrow night, but please feel free to give me your suggestions)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ MV720"
	Option		"DPMS"
	HorizSync	30.0 - 69.0     
	VertRefresh 	50.0 - 100.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ MV720"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"  
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"  
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Eduardo Serra on 2007-03-25
this is a really weird problem, isn't it?

---

### Post by Eduardo Serra on 2007-03-25
maybe it have something to do with the drivers. i didn't install any by myself, doesn't Ubuntu do that? it would be hard i think, because i have a generic video card, the intel i told you guys in a post before.

---

### Post by RedSquirrel on 2007-03-25
OK, I have been doing a bit of research. The video card has some issues. You have to use the 915resolution package.

Here are some links:

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

What is the output of running the following command (in a terminal):

```
sudo 915resolution -l
```

---

### Post by Eduardo Serra on 2007-03-25
this is:

```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 3
Mode Table Offset: $C0000 + $4d2
Mode Table Entries: 25

Mode 30 : 640x480, 8 bits/pixel
Mode 31 : 640x400, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 40 : 640x480, 15 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 42 : 800x600, 15 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 44 : 1024x768, 15 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 48 : 1280x1024, 15 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4a : 1600x1200, 15 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4c : 1920x1440, 15 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

```

---

### Post by Eduardo Serra on 2007-03-25
well, that certainly looks promising. thanks for all that information, ill read it carefully tomorrow, i wont be able to try tonight because i wont be home. i thank you very much, ill let you know via pm or any other how this ends. Thanks!

---

### Post by RedSquirrel on 2007-03-25
Let's keep the *whole* discussion in this thread so that others experiencing your issue will know how to fix it. ;)

It looks like 915resolution is working properly on your system, so that's good.

[FONT=monospace]```
Mode 58 : 1280x1024, 32 bits/pixel
```[/FONT]

I'm still suprised that you have the problem of your virtual desktop being larger than your screen size (screen 1024x768 and desktop 1280x1024). **How does it look at the login screen?** Is the same issue showing itself there?

Is there a 1280x1024 resolution for a choice in GNOME under Screen Resolution. Have you selected that? (... silly question, but I just *have* to ask!).

I'm sort of running out of ideas, but you might try adding a Modeline for the 1280x1024 resolution to the *Monitor* section of your xorg.conf.

You have to know what vertical refresh rate your monitor supports for 1280x1024. 

I found a suitable Modeline for my box in /var/log/Xorg.0.log.

You may also be able to generate a Modeline using gtf:

```
gtf 1280 1024 <refresh rate in Hz>
```
**EDIT**

Here is my Modeline, for reference. You CANNOT copy it exactly because the resolutions and refresh rates will be different for you; this is just an example.

```
# Here is "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
        Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync

```

---

### Post by alienexplorers on 2007-03-25
Compaq MV720 Monitor
(250-0608)              Specifications                Faxback Doc. # 56224

Model:         COMPAQ PRESARIO MV720 Multimedia Monitor:
Compaq P/N:    341267-001
UPC:           743172694850

Dimensions (H x W x D)
  Unit: ................................ 18.5" x 16.25" x 17.5" (41.8 lbs.)
  Package: ................................ 21.8" x 20.5" x 22" (48.4 lbs.)

Monitor Type: ...................................... Color, multi-frequency

Monitor Chassis: ........................................... 69 kHz digital

Picture Tube: ............................................. 17" flat square

Viewable Image Area: ................................................ 15.9"

Dot Pitch: .............................................. 0.28 mm dot pitch

Display Resolutions:
  [COLOR="Red"]1280 x 1024 ...................................... 60 Hz (max resolution)[/COLOR]
  1152 x 864 ..................................... 75 Hz (max flicker-free)
  1024 x 768: ............................................ 60, 75 and 85 Hz
   800 x 600: ............................................ 60, 75 and 85 Hz
   640 x 480: ............................................ 60, 75 and 85 Hz
  Text Mode: ............................................ 720 x 400 - 70 Hz


[COLOR="Red"] # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync[/COLOR]

Put the modeline in your monitor section of your xorg.conf...  Then save it and hit ctrl+alt+backspace...

---

### Post by Eduardo Serra on 2007-03-26
> **RedSquirrel said:**
> Let's keep the *whole* discussion in this thread so that others experiencing your issue will know how to fix it. ;)

It looks like 915resolution is working properly on your system, so that's good.

[FONT=monospace]```
Mode 58 : 1280x1024, 32 bits/pixel
```[/FONT]

I'm still suprised that you have the problem of your virtual desktop being larger than your screen size (screen 1024x768 and desktop 1280x1024). **How does it look at the login screen?** Is the same issue showing itself there?

Is there a 1280x1024 resolution for a choice in GNOME under Screen Resolution. Have you selected that? (... silly question, but I just *have* to ask!).

I'm sort of running out of ideas, but you might try adding a Modeline for the 1280x1024 resolution to the *Monitor* section of your xorg.conf.

You have to know what vertical refresh rate your monitor supports for 1280x1024. 

I found a suitable Modeline for my box in /var/log/Xorg.0.log.

You may also be able to generate a Modeline using gtf:

```
gtf 1280 1024 <refresh rate in Hz>
```
**EDIT**

Here is my Modeline, for reference. You CANNOT copy it exactly because the resolutions and refresh rates will be different for you; this is just an example.

```
# Here is "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
        Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync

```

Hello im back, ive checked what you said last night and i dont get it. you told me to do all of the 915resolution, but then you told me that it was already done, right? that it was working properly, so i dont know, i didnt do anything with those downloads. and about that modeline code, what exactly should i type now that you know what is my configuration

---

### Post by Eduardo Serra on 2007-03-26
im confused

---

### Post by RedSquirrel on 2007-03-26
I told you to post the output of "sudo 915resolution -l", which you did. I thought you might have to do more with that 915resolution, but after looking at that output, it appears that it's  already setup. Good.

Now, as explained in the second link I gave you, you might have to add a Modeline. alienexplorers has tracked down your monitor info and explained how to add the Modeline to xorg.conf. Try that. ;)

---

### Post by Eduardo Serra on 2007-03-26
do i copy this:

```


# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
```

or this?:

```


Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
```

and where do i add it? i mean, next to what?

---

### Post by RedSquirrel on 2007-03-26
Use either line. The lines are the same. The line with the # in front is just a comment (for human consumption).

Put it in the Monitor section:

```
Section "Monitor"
...
...
...


```

---

### Post by alienexplorers on 2007-03-26
Section "Monitor"
     Identifier     "Monitor0"
    VendorName     "Generic"
    ModelName      "CRT-0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
    [COLOR="black"][COLOR="Red"]ModeLine       "1280x960_70.00" 120.8 1280 1368 1504 1728 960 961 964 999 -hsync +vsync[/COLOR][/COLOR]
    Option         "DPMS"
EndSection

---

### Post by Eduardo Serra on 2007-03-26
omg, this is just unvelievable. i did, added the modeline, and now when i click system>preferences>screen resolution, 1280x1024 is not an option anymore, and not only that, i now have 1600x1200, and the funniest of all, when i select that one i have even MORE space to move my desktop... hahahaha, this is my actual code, i just dont believe it:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ MV720"
	Option		"DPMS"
	HorizSync	30.0 - 69.0     
	VertRefresh 	50.0 - 100.0
	Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ MV720"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"  
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"  
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Eduardo Serra on 2007-03-26
i guess this is it
i dont know what else to do... do you really think that if i wait three weeks the next ubuntu wont haave this problem?

---

### Post by Eduardo Serra on 2007-03-26
i wanted to post you an image of how my desktop looked but when i pressed the prt scrn button it turned out to print an image of the desktop i want, hahaha, instead of what i have. anyway, here it is:

[IMG]http://i14.tinypic.com/2nrlr9y.png[/IMG]

---

### Post by Eduardo Serra on 2007-03-26
this has been moved from the absolute begginers to the general help because i couldnt find a solution, despite all the help i got, thanks to everyone. i still have the problem, lol.

---

### Post by RedSquirrel on 2007-03-27
Change your Modeline from this:

```
 Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
```to this:

```
 Modeline "1280x1024" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
```When you restart X (Ctrl-Alt-Backspace), if your display doesn't look right, press Ctrl-Alt-F2, login, run:

```
sudo nano -w /etc/X11/xorg.conf
```put a # in front of the Modeline (to comment it out). Close the file (Ctrl-x) and say 'y' to save changes.

Then at the prompt, type:

```
exit
```Then press Ctrl-Alt-F7 to go back to the login window.

Then press Ctrl-Alt-Backspace to go back to the display settings that you had before you added the Modeline.

By the way, are you sure you want to use 1280x1024 on a 17" monitor? For me, the type would be too small and the flicker of the 60 Hz refresh rate on a CRT would drive me nuts. :)

---

### Post by Eduardo Serra on 2007-03-27
Isnt there a way I can like reinstall the drivers for the video card?? Like on Windows... also, I think that maybe because its using a generic driver its not really doing everything (like 1280*1024 res) properly

---

### Post by Brudy on 2007-03-27
> **Eduardo Serra said:**
> I installed ubuntu last night, and frankly, is starting to piss me off in some aspects. well, but im trying and i will get used to it eventually, i hope. I need help with a single problem for now. the resolution on my screen is set to 1024x768 and i cant stand that, i need to use 1280x1024, but when i select this option its like instead of really using it, it becomes a larger screen, and i have to use my mouse to scrool to the end of it, like my desktop becomes bigger than my screen instead of fitting "inside" it. is this normal? what can i do?  help is greatly apreciatted

How do I move this post to where I can find it to print it??

---

### Post by dfreer on 2007-03-28
> Isnt there a way I can like reinstall the drivers for the video card?? Like on Windows... also, I think that maybe because its using a generic driver its not really doing everything (like 1280*1024 res) properly
The drivers are inckuded with the kernel. You could always try upgrading to Feisty (7.04) If you haven't already done that, it may have better intel video driver support. You aren't using the generic driver, the generic driver is "vesa". I suppose you could try using that instead of the intel "i810" driver, just to see if it fixes your resolution problems.

> How do I move this post to where I can find it to print it??

What exactly are you trying to do *confused*?

---

### Post by Rui Pais on 2007-03-28
> **Eduardo Serra said:**
> Isnt there a way I can like reinstall the drivers for the video card?? Like on Windows... also, I think that maybe because its using a generic driver its not really doing everything (like 1280*1024 res) properly

Hi again Eduardo,

i read somewhere, (i will try to catch the link...), that some times on ubuntu the default installation for your driver is borked and/or conflicting with another one for nvidia. The solution as far as i remember was exactly remove any conflict file and reinstall. 
Here is how could be done (that answer your question above too, i hope):
```
sudo apt-get remove --purge nvidia-glx
sudo apt-get remove --purge xserver-xorg-video-i810
sudo aptitude install xserver-xorg-video-i810
```

check it too see if helps 
(the worst that can happen is problem persists)

---

### Post by Eduardo Serra on 2007-03-28
i tried that, it didn't work. thanks anyway, ill install feisty when it comes out completely, i don't want a beta. anyway, any help would be appreciated, i still want to fix this one, and if i do, ill wait for feisty, until i really learn how to use edgy. i don't get it, whats left to do?

---

### Post by Eduardo Serra on 2007-03-28
I've learned a lot from this problem, i just hope i cant get Ubuntu to run right sometime. if not, ill have to install some other Linux OS.

---

### Post by Eduardo Serra on 2007-03-28
Aren't there any other problems like mine? i mean, i haven't found a single person who has the same problem than me, a very particular case where you see only a section of your desktop when having a 1280x1024 resolution. I'll keep looking, but i know nothing about Ubuntu, and i can't work with this resolution. now that i think about it, how can i even be sure that what i'm watching is 1024x768? it might be 800x600, because really, i can't stand it, its driving me crazy, and every computer in my college has 1024x768...

---

### Post by Eduardo Serra on 2007-03-29
I reinstalled Ubuntu, and i still have the problem.

---

### Post by RedSquirrel on 2007-03-30
[Here]("http://ubuntuforums.org/showpost.php?p=1494477&postcount=6") is a specific post (part of a larger thread) on setting up enough memory to run higher resolutions for the i810 driver.

---

### Post by Eduardo Serra on 2007-03-30
Well, you won't believe it, but i tried all of those options before reinstalling. I don't get the problem, really, thanks for all your help, you've been very nice

---

### Post by Eduardo Serra on 2007-03-31
I haven´t fixed this issue yet

---

### Post by ramjet_1953 on 2007-04-01
Before changing things again in your xrg.conf file, try this link:

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=Painless+Way](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=Painless+Way)

Also I have found that it is often necessary to patch a scrren resolution to 24 bit, not 32 bit.

It is detailed in this thread.

If you make the changes to the /etc/default/915resolution file, it becomes permanent.

I can't guarantee that this will work for you, but is has helped many.

Good luck!

Regards,
Roger 8)

---

### Post by wonder1 on 2007-04-01
Try finding the correct modeline for your monitor. That should solve the problem.

And also make sure 

in Section "Monitor"
Modeline  "1280x1024" ...

should exactly be the same as

Modes "1280x1024"

in the Section "Screen"

If one  has   _60 and the other does not , then in all probability that mode would not be used . It should match.

---

### Post by wonder1 on 2007-04-01
To see what is happening  and what could be the possible modeline go to 
Var - log - and open the Xorg.0.log

This will give you a wealth of information.

Go to the line 
Supported additional video modes 

This will give you a clue to what should be your modeline

Try posting your log file .

---

### Post by Eduardo Serra on 2007-04-01
This is my log file, is huge:

```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux eduardo-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr  1 14:08:12 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "COMPAQ MV720"
(**) |   |-->Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 8086,2560 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 8086,5247 rev 01 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,5247 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,5247 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,5247 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 8086,5247 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 8086,5247 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 8086,5247 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 8086,0102 rev 01 class 04,01,00 hdr 00
(II) PCI: 01:08:0: chip 8086,1039 card 8086,300e rev 81 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe6a00000 - 0xe6afffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xf0000000/27, 0xffa80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[1] -1	0	0xffa7f400 - 0xffa7f4ff (0x100) MX[B]
	[2] -1	0	0xffa7f800 - 0xffa7f9ff (0x200) MX[B]
	[3] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[4] -1	0	0xffa7fc00 - 0xffa7ffff (0x400) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[9] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[1] -1	0	0xffa7f400 - 0xffa7f4ff (0x100) MX[B]
	[2] -1	0	0xffa7f800 - 0xffa7f9ff (0x200) MX[B]
	[3] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[4] -1	0	0xffa7fc00 - 0xffa7ffff (0x400) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[9] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[5] -1	0	0xffa7f400 - 0xffa7f4ff (0x100) MX[B]
	[6] -1	0	0xffa7f800 - 0xffa7f9ff (0x200) MX[B]
	[7] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[8] -1	0	0xffa7fc00 - 0xffa7ffff (0x400) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[15] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[20] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.6.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(--) Chipset 845G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[5] -1	0	0xffa7f400 - 0xffa7f4ff (0x100) MX[B]
	[6] -1	0	0xffa7f800 - 0xffa7f9ff (0x200) MX[B]
	[7] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[8] -1	0	0xffa7fc00 - 0xffa7ffff (0x400) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[15] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[20] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[5] -1	0	0xffa7f400 - 0xffa7f4ff (0x100) MX[B]
	[6] -1	0	0xffa7f800 - 0xffa7f9ff (0x200) MX[B]
	[7] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[8] -1	0	0xffa7fc00 - 0xffa7ffff (0x400) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 845G
(--) I810(0): Chipset: "845G"
(--) I810(0): Linear framebuffer at 0xF0000000
(--) I810(0): IO registers at addr 0xFFA80000
(II) I810(0): 1 display pipe available.
(II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): Kernel reported 174592 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 698364 kB available
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(II) I810(0): Before: SWF1 is 0x00000108
(II) I810(0): After: SWF1 is 0x00000108
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 8000 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2637
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: CPQ  Model: 3026  Serial#: 1111575114
(II) I810(0): Year: 1999  Week: 34
(II) I810(0): EDID Version: 1.2
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 33  vert.: 25
(II) I810(0): Gamma: 2.60
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): redX: 0.632 redY: 0.335   greenX: 0.295 greenY: 0.593
(II) I810(0): blueX: 0.143 blueY: 0.065   whiteX: 0.279 whiteY: 0.311
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) I810(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) I810(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 25.2 MHz   Image Size:  306 x 230 mm
(II) I810(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 8
(II) I810(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 6
(II) I810(0): Ranges: V min: 50  V max: 100 Hz, H min: 30  H max: 70 kHz, PixClock max 90 MHz
(II) I810(0): Serial No: 934CE48BBAJJ
(II) I810(0): Monitor name: COMPAQ MV720
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 8000 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-70
(II) I810(0): 	VertRefresh 50-100
(WW) I810(0): config file hsync range 28-33kHz not within DDC hsync range 30-70kHz
(WW) I810(0): config file vrefresh range 43-72Hz not within DDC vrefresh range 50-100Hz
Mode: 20 (132x25)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 21 (132x43)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 22 (132x50)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 50
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 23 (132x60)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 60
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 25
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 25
	LinNumberOfImagePages: 25
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 31 (640x400)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 38 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3c (1920x1440)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 40 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 42 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 44 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000


```

---

### Post by Eduardo Serra on 2007-04-01
```
Mode: 48 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 49 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4d (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 52 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1024x768,COMPAQ MV720) mode clock 94.5MHz exceeds DDC maximum 90MHz
Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1280x1024,COMPAQ MV720) mode clock 108MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,COMPAQ MV720) mode clock 135MHz exceeds DDC maximum 90MHz
(WW) (1280x1024,COMPAQ MV720) mode clock 157.5MHz exceeds DDC maximum 90MHz
Mode: 58 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1600x1200,COMPAQ MV720) mode clock 162MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 175.5MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 189MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 202.5MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 229.5MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 234.576MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 204.326MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 195.84MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 195.84MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 195.84MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 190.247MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 190.247MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 160.833MHz exceeds DDC maximum 90MHz
(WW) (1600x1200,COMPAQ MV720) mode clock 148.759MHz exceeds DDC maximum 90MHz
Mode: 5a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 5c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005857
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
(II) I810(0): COMPAQ MV720: Using default hsync range of 30.00-70.00 kHz
(II) I810(0): COMPAQ MV720: Using default vrefresh range of 50.00-100.00 Hz
(II) I810(0): Not using mode "832x624" (no mode of this name)
(II) I810(0): Not using mode "720x400" (no mode of this name)
(II) I810(0): Not using mode "640x350" (no mode of this name)
(II) I810(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(1280x1024,COMPAQ MV720) mode clock 108MHz exceeds DDC maximum 90MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x1024 (pitch 2048)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 85.00Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 85.14Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (850)
(--) I810(0): Display dimensions: (330, 250) mm
(--) I810(0): DPI set to (98, 104)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xffa80000 - 0xffafffff (0x80000) MS[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MS[B]
	[2] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[7] -1	0	0xffa7f400 - 0xffa7f4ff (0x100) MX[B]
	[8] -1	0	0xffa7f800 - 0xffa7f9ff (0x200) MX[B]
	[9] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[10] -1	0	0xffa7fc00 - 0xffa7ffff (0x400) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xffa80000 - 0xffafffff (0x80000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[25] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Before: SWF1 is 0x00000108
(II) I810(0): After: SWF1 is 0x00000108
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 256 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 12288 kByte
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 4 kB for HW cursor at 0x7fff000
(WW) I810(0): xf86AllocateGARTMemory: allocation of 4 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0x7ffb000
(II) I810(0): Allocated 4 kB for Overlay registers at 0x7ffa000 (0x2ec8b000).
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 64 kB for the scratch buffer at 0x7fea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf036c000
(II) I810(0): [drm] mapped SAREA 0xf036c000 to 0xb7f62000
(II) I810(0): [drm] framebuffer handle = 0xf0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 32 kB for the logical context at 0x7fe2000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 2048 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 8192 kB for the back buffer at 0x7000000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 2048 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 8192 kB for the depth buffer at 0x6800000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 9152 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 36608 kB for textures at 0x4440000
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1089 pages failed
	(Cannot allocate memory)
(II) I810(0): 0x81fd288: Memory at offset 0x00020000, size 12288 kBytes
(II) I810(0): 0x81fdb88: Memory at offset 0x07fff000, size 4 kBytes
(II) I810(0): 0x81fc678: Memory at offset 0x07ffb000, size 16 kBytes
(II) I810(0): 0x81fc704: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81fd2c8: Memory at offset 0x07fea000, size 64 kBytes
(II) I810(0): 0x81fde00: Memory at offset 0x07ffa000, size 4 kBytes
(II) I810(0): 0x81fd460: Memory at offset 0x07fe2000, size 32 kBytes
(II) I810(0): 0x81fd480: Memory at offset 0x07000000, size 8192 kBytes
(II) I810(0): 0x81fd4a0: Memory at offset 0x06800000, size 8192 kBytes
(II) I810(0): 0x81fd4c0: Memory at offset 0x04440000, size 36608 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xffa80000
(II) I810(0): [drm] ring buffer = 0xf0000000
(II) I810(0): [drm] init sarea width,height = 1280 x 1024 (pitch 2048)
(II) I810(0): [drm] Mapping front buffer
(II) I810(0): [drm] Front Buffer = 0xf0020000
(II) I810(0): [drm] Back Buffer = 0xf7000000
(II) I810(0): [drm] Depth Buffer = 0xf6800000
(II) I810(0): [drm] textures = 0xf4440000
(II) I810(0): [drm] Initialized kernel agp heap manager, 37486592
(II) I810(0): [drm] dma control initialized, using IRQ 177
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0xf0000000,0x8000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 8 at 0x007df000 (pgoffset 2015)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x07fff000 (pgoffset 32767)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x07ffb000 (pgoffset 32763)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x07fea000 (pgoffset 32746)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x07ffa000 (pgoffset 32762)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x07fe2000 (pgoffset 32738)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x07000000 (pgoffset 28672)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x06800000 (pgoffset 26624)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x04440000 (pgoffset 17472)
(II) I810(0): Before: SWF1 is 0x00001108
(II) I810(0): After: SWF1 is 0x00001108
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 640 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(II) I810(0): Rotating to 0 degrees
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "latam"
(**) Generic Keyboard: XkbLayout: "latam"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+latam+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```



It took me two posts

---

### Post by leroy_30 on 2007-04-21
I had the exact same problem. Compaq Presario MV720 Monitor. Yuck resolution.

Ubuntu reports my onboard video as 82915G/GV/910GL Express Chipset

Here's what I did to fix it.


```
sudo dpkg-reconfigure xserver-xorg
```


Filled in the blanks w/ info from:

[http://support.radioshack.com/suppor...oc56/56224.htm](http://support.radioshack.com/suppor...oc56/56224.htm)

Gave the video 65535 (64MB) Ram to play with.

I don't remember what screen it was on but I did enable all of the "what I call video drivers" to load when X starts. Just so I don't have to remember later. LOL.

Logged Out. CTRL-ALT-Backspace.

Logged In. Changed Resolution.

Whammo Blammo!

works like a champ now!

---

