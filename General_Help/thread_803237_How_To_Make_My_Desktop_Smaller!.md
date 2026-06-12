---
title: "How To Make My Desktop Smaller!?"
date: 2008-05-22
forum: General Help
---

### Post by eAi-T0ky0 on 2008-05-22
Hey All ... I Want Make My Desktop Icons Smaller Bec i have alot of icons on my desktop and it take all my screen i want make my screen big and make icons small This My Screen Shot From My Desktop 

[http://img509.imageshack.us/my.php?image=63185120gw8.jpg](http://img509.imageshack.us/my.php?image=63185120gw8.jpg)


And this what i talking about make my screen like that screen on this pic >>>> [http://img156.imageshack.us/my.php?image=93284290cc4.jpg](http://img156.imageshack.us/my.php?image=93284290cc4.jpg) 


Any one can help me with this?! :(

---

### Post by boyce1 on 2008-05-22
To change the size of your desktop icons, you right click on the icon and stretch the icon size. 

Looking at that desktop, all the user has done is arranged his pictures and files around the desktop, and used Screenlets for the weather stuff.

To add screenlets, go to the Synaptic Package Manager, and search and install Screenlets.

---

### Post by dark_harmonics on 2008-05-22
Increasing your screen resolution will reduce the icon size if your display is capable. Also if go to a terminal and type: ```

 sudo gconf-editor
```
Browse under / then apps then nautilus then change the default_zoom_level from standard to small.

---

### Post by Forlong on 2008-05-22
Do not run gconf-editor with sudo!

---

### Post by eAi-T0ky0 on 2008-05-22
> **boyce1 said:**
> To change the size of your desktop icons, you right click on the icon and stretch the icon size. 

Looking at that desktop, all the user has done is arranged his pictures and files around the desktop, and used Screenlets for the weather stuff.

To add screenlets, go to the Synaptic Package Manager, and search and install Screenlets.

i think about make icons small work ok But how to make my desktop smaller "NOT JUST ICONS"!!! like that desktop picture i know about screenlet i talking about the size of Screen!!! look at this 
[http://img156.imageshack.us/my.php?image=93284290cc4.jpg](http://img156.imageshack.us/my.php?image=93284290cc4.jpg)

you can see that size of that screen and mine from first picture ... that's what i talking about i want to make my desktop smaller and "NOT JUST ICONS"


> **dark_harmonics said:**
> Increasing your screen resolution will reduce the icon size if your display is capable. Also if go to a terminal and type: ```

 sudo gconf-editor
```
Browse under / then apps then nautilus then change the default_zoom_level from standard to small.

i did that but there was nothing!!! :(

---

### Post by eAi-T0ky0 on 2008-05-22
i think it must be do something with "Screen Resolution" Or With "Screen And Graphics"  i don't know ... but i doing something here!!!

in some topic talk about Screen Resolution i opened my terminal and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

it do something!!! then i try to reboot my pc after that!! it was something happened that make my panels not allow then i thinking about going to my Desktop Effects and select that Extra then it msg me and tell me something about my VGA Card that my card is "nVidia" on that msg i press OK!!! After That msg me again to reboot pc then i do reboot it again ... and go to my Screen Resolution it was nothing happened!!! i just see that pic on Screen Resolution A Screen wrote on it "Unknown" i don't know what's it!!! and when i go to my Screen And Graphic i can't found my type of my screen ... it Samsung 713 N and on Choose Screen there was nothing about 713 N ... there was 713 V ... 

Any Idea? :(

---

### Post by eAi-T0ky0 on 2008-05-22
there was somethings else 

1 - ```
sudo nvidia-settings
``` Not Working

2 - When i opened my ```
sudo gedit /etc/X11/xorg.conf
``` I THINK IT MUST BE LIKE THAT 
```
  Section "Screen"
        Identifier "Default Screen"
        Device "ATI Technologies Inc RS482 [Radeon Xpress 200]"
        Monitor "hp L2035"
        DefaultDepth 24
        SubSection "Display"
                Depth 1
                Modes "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 4
                Modes "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 8
                Modes "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 15
                Modes "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 16
                Modes "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

What you want to do, is look at the "Default Depth" line, and match that to "Depth" line to figure out which stanza you want to edit.

Once you have figured out which one (for instance, I'd be editing the section that looks like this, since my DefaultDepth is set to 24)

       SubSection "Display"
                Depth 24
                Modes "1600x1200" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
``` 

Or Something like that!!! But it not like that :(

[COLOR="Red"]That's my /etc/X11/xorg.conf[/COLOR]

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```


There Was SomeThing Not Install?! I DON'T KNOOOOOOOOOOOOOOOOOOOW 

BUT PLEASE HELP :( :( :(

---

### Post by eAi-T0ky0 on 2008-05-23
up!!!

---

