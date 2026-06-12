---
title: "Ati x1950 How do i install it?"
date: 2007-02-22
forum: General Help
---

### Post by fresch1 on 2007-02-22
Im having trouble with X1950..

I followed every guide i could find but i cant get the driver to work..
Every time, i reboot Ubuntu, and the splash screen freezes with a thin green line across the screen.

When i try to reconstruct the xorg.conf file, and choose "ati" instead of "vesa" it does the same.

Does anyone have a solution to this? 
How do i install the driver for my x1950?

My goal is to use Beryl Xgl later..

---

### Post by dbixler on 2007-02-23
You can actually kill two birds with one stone here, go to:

[http://www.ebay.com](http://www.ebay.com)

Then create an auction for the card and sell it now.  Then search on "nvidia" and buy the best card there you can find.

While I'm joking here, I too am in the same boat as you.  I just couldn't leave well enough alone I guess.  I had a working system, using a 6800GT AGP card.  I decided I needed a little more "punch" in my system so I picked up the Radeon x1950 512MB AGP card.  Sadly, I'm now back to Windows and my Ubuntu experience has come to a temporary halt.  I've spent COUNTLESS hours trying to get this card working to no avail (when I say working, I mean working RIGHT).  I have tried every guide on the internet that I could possibly find and none of them worked for me.

Anyhow, thus goes my saga.  I'm now scoping out the best nVidia board I can find for my AGP motherboard or I'm going to upgrade to PCIx and get one of the newer cards.  Take my advice, dump that Radeon.  For gaming on Windows it's a great card.  If you have your heart set on running Linux and Beryl (which is what I wanted) then you've just begun your battle until ATI decides to get off their butts and help.

Regards,
Dave

---

### Post by dbixler on 2007-02-23
Oh, WOW!  I just downloaded the new Radeon drivers from ATI's site (Feb 21st) and BAM, FINALLY, the x1950 Pro is "mostly" working.

1)  I installed the binary drivers from their site.
2)  I completely removed my xorg.conf
3)  I did a reconfigure of the xserver-xorg to create a boiler plate fglrx based xorg.conf file.
4)  I ran aticonfig --initial=dual-head
5)  I ran startx

Problems I see so far:

1) Cursor is messed up.  I'm going to try tweaking xorg.conf
2) Screen switching (<alt><f?> key) really screws up the screen.

This aside, at least it's a START!

More coming...

---

### Post by Netsui on 2007-02-23
You might try the Envy script. I haven't yet had the opportunity to try it. But I know it can install ATi drivers as well as Nvidia drivers. You might try it even though you have your card, "mostly working." It might even out the kinks for you. Again, I haven't tried it, so I'm not completely sure.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You can get the script at the above URL. It should be easy to use and relatively painless.

---

### Post by Asos_Illusionist on 2007-03-16
I'll try using the script above without damaging my fresh installation of ubuntu 6.10 edgy eft..

i'll be in touch..!

---

### Post by smokey edgy on 2007-03-24
I was in the same boat with my x1950 as well: X just hanging; green garbage after the splash screen, etc.

After much effort, I discovered the kernel version that came stock with the Edgy CD I had was version 2.6.17.10-generic. I followed every manual/help document (including envy) with no luck. That was until I updated to 2.6.17-11-generic (something which would have occured had I simply switched the video driver to vesa, ran the update and switched back to fglrx; silly me). This fixed the issues I was having.

---

### Post by Asos_Illusionist on 2007-03-30
All worked ok with the envy script at my ubuntu installation

i'll try it now on my kubuntu one..

---

### Post by 00arthuryu on 2007-03-31
My X1950Pro is working great! can do all the things on beryl with 3 fullscreen video and still runs really smoothly i got mine to work from 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and then for beryl i used 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

but when you get to the startxgl don't use the one on the script use
> 
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"


and then its all good, well for me anyway  :D

---

### Post by Asos_Illusionist on 2007-04-01
> **00arthuryu said:**
> My X1950Pro is working great! can do all the things on beryl with 3 fullscreen video and still runs really smoothly i got mine to work from 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and then for beryl i used 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

but when you get to the startxgl don't use the one on the script use


and then its all good, well for me anyway  :D
Friend... can you post the script inside code brackets cause i need the clear form of it..!! ??

---

### Post by 00arthuryu on 2007-04-01
lol oops sorry

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```#

:D i had to do it twice for some odd odd reason cos it changed the code slightly but its all good now, please tell me if it worked :)

---

### Post by Asos_Illusionist on 2007-04-02
> **00arthuryu said:**
> lol oops sorry
:D i had to do it twice for some odd odd reason cos it changed the code slightly but its all good now, please tell me if it worked :)
i'm gonna try it today or tomorow morning..! 

thanx man! :)

---

### Post by oomingmak on 2007-04-05
> **00arthuryu said:**
> My X1950Pro is working great! can do all the things on beryl with 3 fullscreen video and still runs really smoothly i got mine to work from 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
I used that exact same guide and it hosed my system.

When I rebooted it just kept getting stuck at the very end of the start up progress bar and displayed weird blue splodges across the middle of the screen. I have done clean re-installs and tried so many times, that I'm getting really sick and tired of it.

I also tried Envy, but it would not install. Instructions say just click on the deb file, but I just got some error about dependencies.

](*,)

---

### Post by Asos_Illusionist on 2007-04-06
i've got the same staborn problem..

no solve

any help here..!! ??

:confused:

---

### Post by oomingmak on 2007-04-06
> **smokey edgy said:**
> .... After much effort, I discovered the kernel version that came stock with the Edgy CD I had was version 2.6.17.10-generic. I followed every manual/help document (including envy) with no luck. That was until I updated to 2.6.17-11-generic .... This fixed the issues I was having.
Can you explain to a poor noob how to go about doing this?

I've tried everything else and nothing works. 

I wouldn't mind, but my Ubuntu skills are so non-existent that the only way that I can try to fix the problem is to run the Live CD (which takes AGES) and the install the whole OS to hard disk again, and I have wasted hours repeatedly doing this in an attempt to get it to work.

Otherwise I am left just with a totally useless system that is incapable of completing the boot process.

---

### Post by wussboy on 2007-04-07
I think you can press ESC right at the beginning when GRUB is running and boot into recovery mode.  Once you're there, you can type "sudo dpkg-reconfigure xserver-xconf" and set the driver back to vesa.  Let it set all the other options to what it wants.  I think that will get you back on to the desktop, at least.

I've been having trouble with this card too, and I've had to type the above so many times it's old habit now!  I'm currently still running on the VESA driver.  :(

---

### Post by oomingmak on 2007-04-07
> **wussboy said:**
> I think you can press ESC right at the beginning when GRUB is running and boot into recovery mode.  Once you're there, you can type "sudo dpkg-reconfigure xserver-xconf" and set the driver back to vesa.  Let it set all the other options to what it wants.  I think that will get you back on to the desktop, at least.

I've been having trouble with this card too, and I've had to type the above so many times it's old habit now!  I'm currently still running on the VESA driver.  :(
Thank you very much for your advice. I'll try it and see if it works for me.

This could save me **SO** much time, because at least I can get back to some sort of desktop (rather than having to keep re-installing from scratch).

---

### Post by oomingmak on 2007-04-07
> **00arthuryu said:**
> My X1950Pro is working great! can do all the things on beryl with 3 fullscreen video and still runs really smoothly i got mine to work from 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and then for beryl i used 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

When I follow the beryl guide and get to the "installing needed packages" bit I just get:

"Package libgl1-mesa is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgl1-mesa has no installation candidate"

What can I do to resolve this? :confused:

---

### Post by 00arthuryu on 2007-04-08
> **oomingmak said:**
> 
"Package libgl1-mesa is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgl1-mesa has no installation candidate"


maybe try changing it to 'libgl1-mesa-glx'

> 
When I rebooted it just kept getting stuck at the very end of the start up progress bar and displayed weird blue splodges across the middle of the screen. I have done clean re-installs and tried so many times, that I'm getting really sick and tired of it.


happens on mine as well.. but i just leave it cos it ain't doing any harm and ubuntu boots up perfectly and i really donno why you get so wound up about it to be honest (sorry for my bluntness) unless it doesn't boot up that is :-? 

i've tried using the method 1 in the unoffical ati drivers but it didn't work for me :( and even when i used method 2 afterwards, it didn't work. it only worked with method 2 after a fresh install.

---

### Post by oomingmak on 2007-04-08
> **00arthuryu said:**
> happens on mine as well.. but i just leave it cos it ain't doing any harm and ubuntu boots up perfectly and i really donno why you get so wound up about it to be honest (sorry for my bluntness) 
I'll tell you exactly why I was getting wound up; because it would **NOT** boot.

It would get as far as the splash screen (with the progress bar) and then just at the point when the progress bar got to 100% it would freeze and stay there. I even left it for 15 minutes one time (just to be absolutely sure) but still nothing happened, it was totally locked up. 

I followed the guides word for word on how to install ATI drivers, but despite spending many hours trying to get it to work, it would just keep locking up as soon as I rebooted after installing drivers (which meant that I had no Desktop or any means of trying to fix it other than re-installing).

However, on the advice of another forum user, I switched to the Feisty beta and that at least allowed me to at least get the ATI drivers installed (without trashing the install). 

So that's when I got as far as trying to install Beryl, but that failed too (hence my last post).

---

### Post by Asos_Illusionist on 2007-04-09
god.. i've got the same thing.. it goes all the way to the 99% to 100% and it stops..

---

### Post by 00arthuryu on 2007-04-10
> **oomingmak said:**
> I'll tell you exactly why I was getting wound up; because it would **NOT** boot.

It would get as far as the splash screen (with the progress bar) and then just at the point when the progress bar got to 100% it would freeze and stay there. I even left it for 15 minutes one time (just to be absolutely sure) but still nothing happened, it was totally locked up. 

I followed the guides word for word on how to install ATI drivers, but despite spending many hours trying to get it to work, it would just keep locking up as soon as I rebooted after installing drivers (which meant that I had no Desktop or any means of trying to fix it other than re-installing).

However, on the advice of another forum user, I switched to the Feisty beta and that at least allowed me to at least get the ATI drivers installed (without trashing the install). 

So that's when I got as far as trying to install Beryl, but that failed too (hence my last post).

ohh :( i don't have many things to recommend really cos i'm a noob meself, erm.. but when i had that problem, it was to do with my xorg configuration
```

sudo su
gedit etc/X11/xorg.conf

```

mine is

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

the parts where there was
```

	Driver      "vesa"

```
or 
```

	Driver      "ati"

```
or

```

	Driver      "mesa"

```

needed to changed to 

```

	Driver      "fglrx"

```
and my
```

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```
was on 'enable' i solved this using recovery mode
but like i said i'm a bit of a noob meself lol :( so i donno if i can help

---

### Post by U5tabil on 2007-06-22
Ok i am -- this close from giving up here. I have a Sapphire ATI X1950PRO 512MB AGP card, and i can't get the crap to work :( So now i am stucked with Windows :( And i don't like windows, it smells like crap..
So how is it going? How can i install my card on Ubuntu 7.04?
I have tried Envy script but that just makes everything blank screen. So then i need to reset the xorg.conf file with vesa drivers wich by the way wont change the resolution so that i can use it on my widescreen tv...

Please! I love Ubuntu and i ******* hate windows.. so please don't make me get stuck with this crap...

---

### Post by 00arthuryu on 2007-07-05
if you're using fiesty follow this link 
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
note: ignore method 1, it doesn't work!
envy never worked for me :( and i have a X1950Pro 512MB as well :) mine works great :D

best of luck ;)

---

### Post by harpocratesdk on 2007-07-19
you guys who have made the card work, is it AGP or PCI-Express.. 
think this make a big difference!..

tried everything like #2 but can't make it work either!

---

### Post by oomingmak on 2007-07-19
I got mine working in the end (I'm on 7.04)

I did it using fglrx from ATI web site. Earlier versions didn't work for me, but 2 or 3 versions ago it started working.

I still can't get any composite desktop stuff to work under any circumstances, and 2D desktop performance is rubbish, but at least it does work now.

---

