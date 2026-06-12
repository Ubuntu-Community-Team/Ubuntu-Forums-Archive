---
title: "Installing beryl!!! Got problem"
date: 2006-10-18
forum: General Help
---

### Post by lifemaximum on 2006-10-18
hey i tried installing the beryl...i first installed the ATI driver from the ATI website...than i installed beryl , i restarted the xserver and when i login nothing happen...

when i tried breyl manager i got the following ?
```

faz@max-laptop:~$ beryl manager
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
faz@max-laptop:~$
```

Help ? i like to get this thing working on my system...??](*,)

---

### Post by Aberrix on 2006-10-18
which 'how to' did you use?

---

### Post by lifemaximum on 2006-10-18
i dun quite recall....it was in one of the forums... which how to do u recommand??

---

### Post by lifemaximum on 2006-10-18
you know i managed to get the beryl icon on the icon bar, and i can open it and change the setting and stuff....it is just that the setting and all dun take effect...i change the windows manager and windows decorator all to beryl but yet i had see no resualt??

---

### Post by Aberrix on 2006-10-18
[http://ubuntuforums.org/showthread.php?t=219336]("http://ubuntuforums.org/showthread.php?t=219336")

---

### Post by PriceChild on 2006-10-18
Beryl isn't a beginners subject. It is buggy and unstable

*moves to general help*

You will receive more acurate help quicker here.

(btw check my sig for some good guides for beryl)

---

### Post by lifemaximum on 2006-10-18
Dude i used the guide that u suggested... i did the first part now my xserver everytime it loads it shuts down...i mean i can see the desktop and all the icons after the load and suddenly xserver shuts down i tried 

```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure it .... no luck ...

what should i do now??? help ](*,)

---

### Post by PriceChild on 2006-10-18
To start with i would suggest reinstalling your graphics drivers.

If that doesn't work then could you log into a terminal at tty1 (ctrl+alt+f1)

log in, then type "startx"

It will probably crash back to the terminal where you will be able to look at hte crash messages.

---

### Post by lifemaximum on 2006-10-18
dude i did as u said..

there were lots of stuff but i thought following lines are the cause of the problem

( i retyped it mite not be accurate but that is roughly what i got)
```
6:/usr/bin/x11/x(FontFileComplete x LFD+ax85) [0x806d641]

Fatal server error:
Caught signal 11: server aborting

(**) RADEON (0): RADEONLeaveVT
```and etc.


so what should i do now??

---

### Post by lifemaximum on 2006-10-19
i think it mite have something to do with gdm file which i modified ....how can i get it back again ???

---

### Post by lifemaximum on 2006-10-19
i followed this how to get my beryl working..after i tried this one my xserver got problem. it asked for couple of files to be modified... could you please check and let me know what is wrong and which files i need to replace and how. it would be much apperciated.


```
1. Get Radeon Going
First, we need to remove xorg-driver-fglrx

Code:
sudo aptitude remove xorg-driver-fglrxOK now lets grab the newest radeon driver from the compiz/beryl repos.

Code:
gksudo gedit /etc/apt/sources.listAnd add this to the end:

Code:
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglxnow add in the right stuff for the radeon driver:

Code:
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude reinstall libgl1-mesa libgl1-mesa-driOK now we need our Xorg.conf to be ready

Code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.confHere are the areas of interest:

Code:
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

#...

# Leave the identifier and BusID alone, but add the options
Section "Device"
	Identifier	"YOURS HERE"
	Driver		"radeon"
	BusID		"YOURS HERE"
	Option	  "backingstore" "true"
	Option	  "EnablePageFlip" "true"
	Option	  "SubPixelOrder" "none"
	Option	  "AccelMethod" "XAA"
	Option	  "RenderAccel" "true"
	Option	  "AGPMode" "4"
	Option	  "ColorTiling"   "on"
	Option	  "DynamicClocks" "on"
	Option	  "mtrr" "on"
	Option	  "VideoOverlay" "on"
	Option	  "OpenGLOverlay" "off"
EndSection

#...

Section "Screen"
	Identifier	"YOURS"
	Device		"YOURS"
	Monitor		"YOURS"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		# You can put your modes below, for your own resolutions, these are mine:
		Modes		"1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

#...

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSectionNow set up the modules to get the right ones at boot:

Code:
gksudo gedit /etc/modulesMake sure that you have these lines:

Code:
#agpgart # you dont need these two lines, just make sure they are NOT there
#fglrx
drm
radeonAdd a little something to your .drirc to get full resolution support:

Code:
gedit ~/.drirccontents:

Code:
<driconf>
    <device screen="1" driver="r200">
        <application name="Default">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>Now reboot to get the modules to load.

If this didn't work and you got a text login, login and do "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf" and then "sudo /etc/init.d/gdm restart". If you had to do this, you should stop now, you won't be able to get farther.

For the rest of you, log in to gnome and open a terminal and type:

Code:
glxinfo | grep renderingand make sure you get a Yes.

OK Part 1 is done.

2. XGL Time!
So Compiz-quinnstorm forked to Beryl, which is what this howto will now cover.

First, lets install xgl and Beryl:

Code:
sudo aptitude install xserver-xgl beryl emerald-themesNow I dont know about you guys, but I hate switching GDM to XGL, because if it messes up I have to use the text console, so we are going to make our own xgl session.

Code:
sudo gedit /usr/share/xsessions/xgl.desktopHere is the content:

Code:
[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=ApplicationOK now we need to make /usr/bin/startxgl.sh:

Code:
sudo gedit /usr/bin/startxgl.shcontents:

Code:
Xgl -fullscreen :1 -ac -accel xv -accel glx:pbuffer &
DISPLAY=:1
# Start GNOME
exec gnome-sessionnow make it executable:

Code:
sudo chmod +x /usr/bin/startxgl.shOK now log out and press CTRL+ALT+BACKSPACE. Click Options and then Select Session. Choose XGL. Log in and click "Just for this session" just in case it messes up.

To edit beryl related settings, run csm. To edit the window manager themes, run "beryl-settings".
```

---

### Post by lifemaximum on 2006-10-19
is there anything that can replace xserver?

---

### Post by lifemaximum on 2006-10-19
the latest error that i got is 

```
x: warning ; process set to priority -1 instead of requested priority 0
```

anybody knows what should i do now? i am desperate?](*,) ](*,)

---

### Post by hanzomon4 on 2006-10-21
Are you using the beta nvidia drivers, AIGLX, or XGL? Also post your /etc/X11/xorg.conf

---

