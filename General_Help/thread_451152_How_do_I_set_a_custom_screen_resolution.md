---
title: "How do I set a custom screen resolution?"
date: 2007-05-22
forum: General Help
---

### Post by jmccnz on 2007-05-22
Hi there,

I am running a Ubuntu dual boot with Mac OSX and an Apple 20" Intel iMac.

I want my Ubuntu screen res to fit the wide-screen I am using, my OSX screen res is 1600x1200. I would like the same on Ubuntu. 

Does anyone know how I can set a custom screen resolution?

Thanks

---

### Post by DoctorMO on 2007-05-22
You need to reconfigure xorg to support new resolutions. have you tried to select the resolution through the screen tools? is the resolution you need available?

If it's not then you need to add it to the monitor section in /etc/X11/xorg.conf unfortunately I do not know of any GUI tools for doing this at this moment.

---

### Post by bung33 on 2007-05-22
I had to undergo a similar procedure when I wanted a screen resolution of 1440x900. Type the following command...

```
sudo gedit /etc/X11/xorg.conf
```

Scroll down towards the bottom until you see the screen section...

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	32
		Modes		"1440x900"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

```

Notice how I simply prefixed each modes line with my monitor's resolution of 1440x900. You must first restart the x server before changing your resolution. Do this by pressing Ctrl-Alt-Backspace. Then simply change the screen resolution in the preferences menu. Be sure you have installed your video card drivers before doing this though. I would also make a backup before modifying any settings...

---

### Post by jmccnz on 2007-05-24
Hi,

Thanks for the replies!

I did what you said, but accidentally made a mistake and then upon reload Ubuntu could not detect the graphics settings.

I know where the problem is and what I need to change back, problem is I can't get back into Ubuntu all I see is a black screen with white writing - I think it is the startup checks or something.

Can I change the xorg.conf file from outside of the graphical interface? If so, how?

Thanks for your help.

---

### Post by jmccnz on 2007-05-25
Anyone know? I really need help as I can't get into Ubuntu at the moment.

Thanks.

---

### Post by ezrollers on 2007-05-25
ctrl + alt + f4 (or any other function key. I think Ubuntu uses f7 as the graphical one, so avoid f7)

that should open a new session.

Login to that console session.

Then modify xorg.conf

alternatively, you could try the rescue broken system boot option on the ubuntu cd

---

### Post by bung33 on 2007-05-28
He won't be able to login graphically because the x server won't start as long as the configuration file is corrupt. Type this command...

```
sudo vi /etc/X11/xorg.conf
```

Now you can edit the file from the command line. VI can be difficult to use, so you might want to take a look at their website for more commands or...

```
man vi
```

Once you edit and save the configuration file, Ctrl+Alt+Backspace will restart the x server and send you to the  graphical login screen...

---

### Post by ramjet_1953 on 2007-05-28
Doesn't the Apple use the Intel graphics chipset?

If this is so, you have two options.

Use either the new Intel driver

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel
[/COLOR]
Or use the older 915resolution package

[COLOR="Red"]sudo apt-get install 915resolution[/COLOR]

Regards,
Roger :cool:

---

