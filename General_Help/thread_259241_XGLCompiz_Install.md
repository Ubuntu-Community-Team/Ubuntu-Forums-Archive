---
title: "XGL/Compiz Install"
date: 2006-08-19
forum: General Help
---

### Post by Zarathu on 2006-08-19
Ubuntu apt-get can't find the "compiz" or "xserver-xgl" packages.  I'm using an AMD64 chip with the 32-bit version of Ubuntu, and I need the proper packages.  Can somebody give me links to the proper packages?

---

### Post by David Corrales on 2006-08-19
[http://www.compiz.net/topic-911-ubuntu-xgl-compiz-packages](http://www.compiz.net/topic-911-ubuntu-xgl-compiz-packages)

---

### Post by Zarathu on 2006-08-20
Yes, but when I install those packages, I get dependency errors.  Example, libc6 - dependency isn't satisfying compiz packages.  I sudo apt-get install libc6 and everything associated with it, they're already up-to-date!

What to do?

---

### Post by David Corrales on 2006-08-20
Just add the beerorkid one, the xgl.compiz.info is broken and outdated!
Which kind of card do you have? I used this howto for Ati and it worked nicely: [http://www.compiz.net/topic-389-compiz-gnome](http://www.compiz.net/topic-389-compiz-gnome)

---

### Post by Zarathu on 2006-08-27
I have an nVidia 7900GT, and I love it to death.  My card is downright sexy.

---

### Post by PriceChild on 2006-08-27
Check out compiz.net for the beerorkid repos.

Have you installed first using the guide found from the sticky in General support in this forum?

---

### Post by IoCaster on 2006-08-27
I'd recommend you start over and just nuke all of the xgl+compiz+cgwd stuff you've already installed to this point. Sometimes it's better to cut your losses and get a fresh start, ya know?

Here's a [link]("http://tazforum.thetazzone.com/viewtopic.php?t=2189") to try if you're using the repo 'nvidia-glx' drivers.

If you feel like going gonzo then you can always use the Automatix Bleeder app and try that.

Go here---->[click]("http://getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix") and scroll down until you find a link to bleeder. The xgl+compiz stuff is included in that package as far as I know and it should be pretty easy to install from that source. YMMV, of course.

HTH

---

### Post by Dinerty on 2006-08-28
[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

Follow this guide mate

---

### Post by Zarathu on 2006-08-31
admin@jessica:~$ compiz
admin@jessica:~$ Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

compiz.real: Couldn't open display :0.0

---

### Post by ayoli on 2006-08-31
make a start script (ie: start-compiz.sh):
```
#!/bin/sh
killall gnome-window-decrator
wait
compiz --replace && gnome-window-decorator
```
replace gnome-window-decorator with cgwd if you want to use themes
make your script executable with:
```
chmod a+x start-compiz.sh
```
the run your script:
```
./start-compiz.sh
```
btw, compiz packages often come with a start script, depends from where you have installed it i guess.
regards.

---

### Post by Zarathu on 2006-08-31
Well, I was actually wondering what exactly my error meant.  Firstly, why exactly is it giving me an error and how does your solution fix it?

I'm not doubting your solution, but I'm always looking to expand my knowledge.

---

### Post by Zarathu on 2006-08-31
admin@jessica:~$ compiz --replace && gnome-window-decorator
compiz.real: No composite extension





admin@jessica:~$ killall gnome-window-decorator
gnome-window-decorator: no process killed


Didn't do much anyway....

---

### Post by Mr_Congeniality on 2006-08-31
> **Zarathu said:**
> admin@jessica:~$ compiz --replace && gnome-window-decorator
compiz.real: No composite extension





admin@jessica:~$ killall gnome-window-decorator
gnome-window-decorator: no process killed


Didn't do much anyway....

lol me and you are having the same issue,

---

### Post by ayoli on 2006-09-01
> **Zarathu said:**
> admin@jessica:~$ compiz --replace && gnome-window-decorator
compiz.real: No composite extension

means composite extension isn't enabled in your xorg.conf then check you have this section in /etc/X11/xorg.conf:
```
Section "Extensions"
        Option  "Composite"     "enable"
EndSection
```

or isnt installed, then :
```
sudo apt-get install libxcomposite1
```

and an for your knowledge:
compiz must be run with --replace to replace the window manager that is already running (eg metacity), and the killall gnome-winow-decorator is to be sure that is not running before running compiz i think.
regards.

---

### Post by Zarathu on 2006-09-01
```
admin@jessica:~$ sudo apt-get install libxcomposite1
Password:
Reading package lists... Done
Building dependency tree... Done
libxcomposite1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
admin@jessica:~$
```

Nope.

```
Section "Extensions"
        Option "Composite" "true"
EndSection




         [ line 152/152 (100%), col 1/1 (100%), char 4321/4321 (100%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell
```

Nope.

---

### Post by Zarathu on 2006-09-01
Update:

```
admin@jessica:~$ compiz --replace gconf cube rotate scale fade minimize zoom place move
admin@jessica:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz.real: glXCreateContext failed
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

admin@jessica:~$ compiz
admin@jessica:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz.real: glXCreateContext failed
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

admin@jessica:~$

```

---

### Post by _simon_ on 2006-09-01
Your code is wrong.

It's

Section "Extensions"
        Option "Composite" "**enable**"
EndSection

---

### Post by Zarathu on 2006-09-02
Changed to "enable," but it still gives the same error.

---

### Post by ayoli on 2006-09-03
you should paste your whole xorg.conf, especially the Section Modules.
do you have a line such: load "glx" ?

---

### Post by Zarathu on 2006-09-03
Oh, this might be of some help....

My xserver wasn't loading anymore, so I was having to do everything in UNIX.  So, I installed lynx and naim, and got busy.  :D

But anyway, I have the GLX attempting to load, but apparently I don't have a "GLX-compatible nVidia driver."  I know it isn't my card, since I have a 7900GT 256 MB PCI-e 16 lanes, so I know that's definitely not it.

```
sudo apt-get install nvidia-glx
```

The above didn't do anything, since I already have that package.  Any advice?

---

### Post by Zarathu on 2006-09-03
Messed around installing different nVidia drivers, none of them did the trick.  So, I commented out the "Option "composite" "enabled"" line as well as the "GLX" line up at the top, and "startx" worked again.

Here's my xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option "NvAGP" "1"
	Option	 "RenderAccel"	"true"
EndSection

Section "Monitor"
	Identifier	"VA902b"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"VA902b"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

Section "Extensions"
	Option "Composite" "enabled"
EndSection

```

I didn't remember it being anywhere near this complicated with SuSE.  I hated SuSE though....

---

### Post by Zarathu on 2006-09-03
Update:  To get my xserver working, all I need to comment out is the "composite" "enabled" extension.  After that, my xserver starts fine, it isn't because of the GLX.

Oh, I'm also getting a "/dev/wacom" error, saying the file/directory doesn't exist.  I tried installing "wacom-tools" but that didn't do dick.

Suggestions?

---

### Post by ayoli on 2006-09-03
dunno for wacom, comment the section in your xorg.conf if you dont use it.
btw why **load "dri"** in section modules is commented ?

---

### Post by hanzomon4 on 2006-09-03
dri.. I think thats for direct rendering, and xgl uses indirect rendering

---

### Post by Zarathu on 2006-09-03
```
 Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
```

I'll try changing it to USB.  Anyway, does anybody have any idea how to fix this?

---

### Post by Zarathu on 2006-09-03
HELL YEAH!!!

I finally got it working.  I decided to change the "nv" in my xorg.conf to "nvidia," since the problem was the driver.  Now, my graphics are running a PISSLOAD faster and XGL works.  I ******* love it.

---

### Post by ayoli on 2006-09-03
glad for yu
have fun now ;)

---

### Post by hanzomon4 on 2006-09-03
> **Zarathu said:**
>   I ******* love it.
Yes... it is nice ;)

---

### Post by Zarathu on 2006-09-04
```
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
admin@jessica:~$

```

Yeah... so, about that....

---

### Post by tribaal on 2006-09-04
I don't know where you picked that from (what log), but my compiz doesn't start either after the latest updates.

Maybe if you tell me where you found what you posted I could check on my system to see if we're experiencing the same problem?

- trib'

---

### Post by matrooswolf on 2006-09-04
compiz breakage here too,
using metacity

---

### Post by usergentoo on 2006-09-04
Mine died to had to remove autostart file to get back into kde.

---

### Post by aussiedini on 2006-09-04
Ditto here

---

### Post by sfranky on 2006-09-04
same here (noob - but compiz was working just fine before upgrade)

---

### Post by gommle on 2006-09-04
Use "compiz-start" instead of the other stuff. Just type it in a terminal.

---

### Post by tribaal on 2006-09-04
yup, "compiz-start" in a terminal works, but all my previous settings are gone, and the window borders are 100% transparent (I can't see the close, minimize/maximize buttons anymore)

All the preferences are unset: I todl compiz not to load some modules (like wobbly), yet starting it by hand does load the said modules. And my shortcuts don't work either ...

Anybody have a more... permanent fix?

- trib'

---

### Post by thepizzaking on 2006-09-04
They've moved away from gconf.  The new configuration tool is 'csm'.  So run 'csm' from the console and edit your settings from there.

---

### Post by tribaal on 2006-09-04
Great :)

Now should I remove all remaning keys in gconf then? Since they aren't used anymore I guess I can do that safely... or not?

Thanks a lot!

- trib'

---

### Post by Dinerty on 2006-09-04
Ok guys heres how I fixed my xgl/compiz after todays new updates, did abit of searching around on these forums and on compiz.net and found that the new updates use "csm" instead of gconf now:

```
compiz-start
```

then

```
chmod 755 ~/.compiz -R
```

then

```
csm 
```

Configure everything to way it was before, then finally add this line to your "Sessions > Start up programs"

```
/usr/bin/compiz-start
```


**Big thanks to all the guys on here and compiz for this quick fix !

---

### Post by matrooswolf on 2006-09-04
> **Dinerty said:**
> 

Configure everything to way it was before, then finally add this line to your "Sessions > Start up programs"

```
/usr/bin/compizstart
```


**Big thanks to all the guys on here and compiz for this quick fix !
compiz-start with a hyphen?
```
/usr/bin/compiz-start
```

And thanks!  That fixed it!

---

### Post by toasted on 2006-09-04
> **tribaal said:**
> Great :)

Now should I remove all remaning keys in gconf then? Since they aren't used anymore I guess I can do that safely... or not?

Thanks a lot!

- trib'

I would think there should be an update that would do that eh?  Other wise how would we do this? Its no longer functional....

---

### Post by gotgenes on 2006-09-06
> **toasted said:**
> I would think there should be an update that would do that eh?  Other wise how would we do this? Its no longer functional....
So does anybody have an answer on how to remove compiz from the gconf registry yet?

---

### Post by Zarathu on 2006-09-10
Is it possible?  What changes should be made?

---

### Post by testube_babies on 2006-09-10
It's definitely possible, depending on the type of video card you have.  Here's a tutorial for the Intel i915, I'm sure there are plenty of other tutorials out there for other cards:

[http://www.ubuntuforums.org/showthread.php?t=134069](http://www.ubuntuforums.org/showthread.php?t=134069)

---

### Post by Zarathu on 2006-09-11
For some reason, when I type "compiz-start &" in my terminal now (I don't have it set to auto-start, don't trust it enough, this is why), my screen turns black.  Sometimes I can't even see my cursor, I have to ctrl + alt + backspace out of it.

Any ideas?

---

### Post by nik on 2006-09-11
Try "compiz-manager".

---

### Post by sethmahoney on 2006-09-11
Generally you'll find more compiz-related info and people in the know about compiz at [www.compiz.net](www.compiz.net)

---

### Post by Zarathu on 2006-09-12
Nevermind, the new one fixed it.

---

### Post by Zarathu on 2006-09-17
Look at this:

```
primary@tammy:~$ compiz
XGL Absent, assuming AIGLX
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
primary@tammy:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
primary@tammy:~$
```

My /etc/X11/xorg.conf :

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
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 	"RenderAccel" 	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "enable"
EndSection


```

Obviously, using an nVidia card.

---

### Post by Zarathu on 2006-09-17
I should also mention that I added all 4 repos and I installed "compiz" "compiz-gnome" etc.

---

### Post by Zarathu on 2006-09-17
bump

---

### Post by ayoli on 2006-09-17
did you configured any conf file to run xgl ? ie: /etc/gdm/gdm.conf-custom
with these lines:
```
[servers] 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```
and to starrt compiz use compiz-manager or compiz-start command instaed of only compiz

---

### Post by Zarathu on 2006-09-18
Alright.  Apparently, that file didn't even exist on my friend's PC.  So, he created a file and added that in it.

Also, I should add that at the login screen under "Select Session," XGL is not part of the options.

Lead to anything?

[EDIT]
I should also mention that I do use "compiz-start &" but I just did "compiz" to show you what I was talking about.

---

### Post by Dinerty on 2006-09-18
you want to edit xorg.conf and set "DefaultDepth" to 24, I know on xgl it is used, not sure on aiglx

---

### Post by spider-man on 2006-09-18
I got that error message when I tried to run compiz, but I hadn't yet restarted the computer (i.e. restarting GDM wasn't enough)

---

### Post by Zarathu on 2006-09-20
So how would I go about adding XGL to the list of possible or selectable sessions at the login screen?

---

### Post by ayoli on 2006-09-20
> **Zarathu said:**
> So how would I go about adding XGL to the list of possible or selectable sessions at the login screen?
here is a way:
first, create an Xgl startup script:
```
sudo gedit /usr/bin/start-xgl 
```
copy these lines:
```
#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
exec gnome-session
```
save, close and make the script executable:
```
sudo chmod 755 /usr/bin/start-xgl 
```
then, make a XGL session for the login manager:
```
sudo gedit /usr/share/xsessions/xgl.desktop
```
put these lines into it:
```

[Desktop Entry] 
Encoding=UTF-8 
Name=XGl 
Exec=/usr/bin/start xgl 
Icon= Type=Application
```
save, close restart gdm:
```
sudo /etc/init.d/gdm restart
```
voila

edit: remove section like this if you have in /etc/gdm/gdm.conf-custom before restarting gdm:
```
[servers] 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

---

### Post by Zarathu on 2006-09-23
Cool.  Compiz gives a normal return integer after executing "compiz-start &" but it crashes GDM.  I tried starting the session in "XGL" at the login screen, but it wouldn't let me.  I got an error saying that it was going to switch me to the default session.  Any ideas?

---

### Post by Zarathu on 2006-09-23
The error says that it failed to start XGL because "/usr/bin/start xgl" could not be found, just FYI.

---

### Post by ayoli on 2006-09-24
> **Zarathu said:**
> The error says that it failed to start XGL because "/usr/bin/[COLOR="Red"]**start xgl**[/COLOR]" could not be found, just FYI.
in red the reason ! i forgot an '-' and you must have just copy/paste my code :) so do this:
```
sudo gedit /usr/share/xsessions/xgl.desktop
```
should look like:
```

[Desktop Entry] 
Encoding=UTF-8 
Name=XGl 
Exec=/usr/bin/start[COLOR="Red"]-[/COLOR]xgl 
Icon= Type=Application
```
save, close restart gdm:
```
sudo /etc/init.d/gdm restart
```

---

