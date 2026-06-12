---
title: "bittornado, resoultion and amarok probs"
date: 2005-04-09
forum: General Help
---

### Post by jhands on 2005-04-09
I am having problems doing some thing in hoary.

 first of all how do i install bittornado. the one in the repositories is the old version. is there any guide available. 

second, my screen resolution switches back to 1280*1024 but i alwayz apply 1024*768. i always save the session when i have to shutdown or restart.

third, i installed amarok on ubuntu because i like using it. i installed it using synaptic. so it installed all othere things needed to run amarok.so whenever i try to play a song it does nothing. i also installed kaffeine but it runs perfectly.

---

### Post by jdong on 2005-04-09
For newer bittornado, see [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

I have the latest 0.3.10 client in the staging (beta-testing) tree, and will be marking it stable within the next few days.

---

### Post by artinla on 2005-04-09
What kind of song are you trying to play in amarok?  MP3?


Check your /etc/X11/xorg.conf  and confirm that the first of the modelines is the one that says 1024x768.  You will find the modelines toward the bottom of the file and they all have resolution/color depth entries.  The one at the top is the first one that X tries.  rearrange them to suit your needs.  

Also, remember that Ctrl-alt-minus and Ctrl-alt-plus will cycle through each mode until you find one that works.  This is helpful if you try to set your system to a resolution that is too high and your monitor can't support it.  You can hit ctrl-alt-minus until you have switched to a useable resolution.

---

### Post by jhands on 2005-04-09
this is the bottom part og my xorg.conf file. what do i change coz i dont wanna risk it

> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"MultiSync 77"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


about amarok, im trying to play mp3 files.

---

### Post by artinla on 2005-04-09
Make a backup of the file.

then change the last modeline to say:

 Modes "1024x768" "832x624" "800x600" "720x400" "640x480"

instead of 

 Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

(Each modeline corresponds to the monitor resolutions that apply to each of the possible color depths.. I/E the top line is for 1 bit color, the next is for 4 bit etc.  The one you really need to change is the one that corresponds to whatever color depth you are running on your desktop (24 bit))

then stop X

sudo /etc/init.d/gdm stop

and restart it

startx

As for Amarok:

Check the Ubuntu Multimedia wiki (or HOWTO) I forget which one.

Also, try installing mpg321 (I think you need universe repositories enabled)

sudo apt-get update
sudo apt-get install mpg321

or you can do it with synaptic.

Art

---

### Post by jhands on 2005-04-09
thanks 4 ur suggestions. i uninstalled amarok, it looks like its buggy to me. i adjusted to rhythmbox. :-)

---

