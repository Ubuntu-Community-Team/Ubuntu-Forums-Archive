---
title: "Screen resolution too low... :("
date: 2008-07-08
forum: General Help
---

### Post by AsgerJon on 2008-07-08
I have just installed Ubuntu and it's awesome... :D

However, the screen resolution should be something like 1024 x 768, but I can't choose any higher than 640 x 480 !

That kinda sux... :( I have to scroll around A LOT! 

Anyway, I hope that one of you guys can help me. :D I'm off the installing the steam thingy... :D

---

### Post by iaculallad on 2008-07-08
> **AsgerJon said:**
> I have just installed Ubuntu and it's awesome... :D

However, the screen resolution should be something like 1024 x 768, but I can't choose any higher than 640 x 480 !

That kinda sux... :( I have to scroll around A LOT! 

Anyway, I hope that one of you guys can help me. :D I'm off the installing the steam thingy... :D

What video card are you using? To determine that, use the command below in your terminal:

```
lspci | grep VGA
```

Whatever displays, post it.

You could also post your /etc/X11/xorg.conf file:

```
cat /etc/X11/xorg.conf
```

---

### Post by AsgerJon on 2008-07-08
Allright, I think I have an idea to solve it:
Typing the following in the command line:
**sudo dpkg-reconfigure -phigh xserver-xorg**

It then asks for my password, but I can't input it. Nothing happens when I types. Then I hit return and it goes to a new line, then I apparently have limited time to put in the password, but even when I put in password, nothing happens, it simply tells me that the password is incorrect... :(

---

### Post by AsgerJon on 2008-07-08
Here's that config file:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by AsgerJon on 2008-07-08
It would seem that I don't have the "rights" to do anything in the Ubuntu system! How do I get the system to allow me to do something in the system?

---

### Post by iaculallad on 2008-07-08
> **AsgerJon said:**
> Allright, I think I have an idea to solve it:
Typing the following in the command line:
**sudo dpkg-reconfigure -phigh xserver-xorg**

It then asks for my password, but I can't input it. Nothing happens when I types. Then I hit return and it goes to a new line, then I apparently have limited time to put in the password, but even when I put in password, nothing happens, it simply tells me that the password is incorrect... :(

That's normal, you really cant see the characters you typed on the password field. Type it and press enter when you completed you password.

and do:

```
sudo dpkg-reconfigure xserver-xorg
```

Try to answer the questions with your utmost knowledge. Use default answers when you're not sure of what to input.

---

### Post by AsgerJon on 2008-07-08
I'm using this guide to try and change the resolution:
[http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/](http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/)

It asks me to input this followed by my password. I know how to do that now, thanks for the tip. :D
sudo dpkg-reconfigure -phigh xserver-xorg

But when I do it all I get is this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080709025733

---

### Post by iaculallad on 2008-07-08
> **AsgerJon said:**
> 
But when I do it all I get is this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080709025733

The message means that when you updated your current xorg.conf file,  over-writing it with a “custom” version of xorg.conf, it saved the previous version as xorg.conf.20080709025733 in your /etc/X11/ folder. That way, if you ever need to revert to your previous settings of xorg.conf, you can rename xorg.conf.20080709025733 to xorg.conf.

Using the terminal:

```
sudo cp /etc/X11/xorg.conf.20080709025733 /etc/X11/xorg.conf
```

---

### Post by AsgerJon on 2008-07-08
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080709030817

I still get that message, after I go to the settings, and I have changed nothing in the process. I need some help, this low resolution is giving me a headache... :(

---

### Post by AsgerJon on 2008-07-08
My resolution is still far too low, what do I do about it?

I have figured that I can use the terminal thing to do it, but couldn't I also just put the following into that config file:

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1024x768"
        Horizsync       31.5-48.0
        Vertrefresh     56.0 - 65.0
        modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync$
        Gamma   1.0
EndSection

When I then try to save the file, it says that I don't have the rights to do it... :(

---

### Post by iaculallad on 2008-07-08
> **AsgerJon said:**
> My resolution is still far too low, what do I do about it?

I have figured that I can use the terminal thing to do it, but couldn't I also just put the following into that config file:

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1024x768"
        Horizsync       31.5-48.0
        Vertrefresh     56.0 - 65.0
        modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync$
        Gamma   1.0
EndSection

When I then try to save the file, it says that I don't have the rights to do it... :(

The way to do that is:

```
gksudo gedit /etc/X11/xorg.conf
```

So you can have the authorization to save any changes in your configuration file.

---

### Post by AsgerJon on 2008-07-08
Allright, I added the:
Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1024x768"
        Horizsync       31.5-48.0
        Vertrefresh     56.0 - 65.0
        modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync$
        Gamma   1.0
EndSection

To the config file, but I'm still not able to set the screen resolution to anything higher than 640 x 480... :(

It can't be that hard to get a decent resolution, can it?

---

### Post by iaculallad on 2008-07-08
Ok, let's try the manual way. We will use the xorg.conf file you posted above as our working template. So, I must assume that you posted the entire content of xorg.conf file.

First things first: Create a backup of the current configuration file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

Then open the file for editing:

```
gksudo gedit /etc/X11/xorg.conf
```

You're gedit will open up and loads your current xorg.conf file, Select all the texts in the file and delete it, replacing the the lines of texts below (edited version of your xorg.conf file). Save it.

```
Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection

Section "Device"
	Identifier "Configured Video Device"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 30-110
	VertRefresh 50-160
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
        DefaultDepth 24
        SubSection "Display"
        Depth 24
        Modes "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
EndSection
```

If you already saved the file, Log-off your account then log back in. Then try changing your resolution.

---

### Post by AsgerJon on 2008-07-09
Okay, I tried to input your file there, but then my screen went "input not supported" and I had to reinstall Ubuntu. :(

[http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/](http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/)

^^Won't I be able to solve the problem with this tutorial?
The problem with this is that I never actually get the blue xserver-xorg thing opened.

---

### Post by AsgerJon on 2008-07-09
I am able to edit my config file, but I don't get more options for larger screen resolutions in the system > screen resolution...

---

### Post by Paul T. on 2008-07-09
> **AsgerJon said:**
> Okay, I tried to input your file there, but then my screen went "input not supported" and I had to reinstall Ubuntu. :(

[http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/](http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/)

^^Won't I be able to solve the problem with this tutorial?
The problem with this is that I never actually get the blue xserver-xorg thing opened.

Hi, I've been following your threads as I have similar problem, though more to do with refresh rate. However the link you posted states that it won't work with Ubuntu 8.04 Hardy Heron... there's another link for this version here:
[http://www.simplehelp.net/2008/05/29/how-to-increase-the-screen-resolutions-available-to-ubuntu-804-hardy-heron-while-running-in-parallels-desktop/](http://www.simplehelp.net/2008/05/29/how-to-increase-the-screen-resolutions-available-to-ubuntu-804-hardy-heron-while-running-in-parallels-desktop/)

---

