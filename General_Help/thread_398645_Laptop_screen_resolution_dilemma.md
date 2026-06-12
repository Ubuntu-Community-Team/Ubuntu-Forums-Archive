---
title: "Laptop screen resolution dilemma"
date: 2007-04-01
forum: General Help
---

### Post by PaulFXH on 2007-04-01
I'm just in the process of tidying up the installation of Ubuntu 6.10 on a HP Pavilion dv1000 laptop (dual boot with XP) and most things are going fine.
However, I'm having trouble with the screen resolution.
In System>Preferences>Screen Resolution, only 1024X768 is given as an option and the actual resolution on the screen seems indeed to be more like 1024X768 than 1280X768. 
However, in /etc/X11/xorg.conf, the Screen section shows only 1280X768 as the only resolution listed.
Here it is:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection


What do I need to do to get 1280X768 as a screen resolution option on the widescreen laptop?

---

### Post by PaulFXH on 2007-04-01
This is an update on where I stand now:
i did a 
```
sudo dpkg-reconfigure xserver-xorg
```
and checked all of the resolutions I thought I might need (1280X768, 1152X768, 1024X768, 800X600, 640X480).
All of these now show up in my /etc/X11/xorg.conf. Nevertheless, in System>Preferences>Screen Resolution the options now available are only 1024X768, 800X600 and 640X480.
The higher resolutions are not available.
It seems that I need to change the vertical and horizontal resolutions in the X-server configuration.
But where do I find what to change them to?

---

### Post by Dream. on 2007-04-01
I had a similar dilema and after much searching and advice I was directed to [http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution](http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution)

It really was quite simple, I hope it helps you out.

---

### Post by PaulFXH on 2007-04-01
Thanks for the suggestion, Dream., but I just couldn't get this to work for me no matter how many variants I tried.
However, I then came across this [thread]("http://www.ubuntuforums.org/showthread.php?t=391091&highlight=screen+resolution+915resolution") (see post #9) which suggested downloading "915resolution" from Synaptic.
This I did and it worked perfectly first time without having to reconfigure the X-server.

---

### Post by strabes on 2007-04-01
Do you have video card drivers installed? 

For open source drivers: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
For closed source drivers (your card might require these): [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

### Post by PaulFXH on 2007-04-01
Thanks strabes
The laptop has an Intel 945G card and the i810 driver is installed.
The second of the links you posted deals exactly with the problem I had and essentially advocates the 915resolution install to get over the "forbidden" resolutions problem which is what I eventually did. 
Just wish I'd seen this earlier.

---

