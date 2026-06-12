---
title: "resolution problem"
date: 2007-10-21
forum: General Help
---

### Post by homisolaris on 2007-10-21
right, ive just made this huge mistake now, ive searched around on the forums but cannot find a mistake similar to this..

i have just updated from fiesty to gusty, and everything has been running fine. no problems, no glitches.

i decided to increase the resolution of the screen, and now every time i boot up ubuntu, after the ubuntu loading screen, my monitor just goes black. 

i am currently using the ubuntu live CD, to try and research and solve the problem

is there anyway of perhaps editing the xorg.conf or such other element from whilst being on the live cd that would help?

---

### Post by ihcnet on 2007-10-22
Once your screen goes black, hit CTRL+ALT+F2 to bring up a virtual terminal. Login with your user name and password. Then edit your xorg.conf file with ```
sudo nano /etc/X11/xorg.conf
``` Nano's pretty straightforward to use, the commands are listed at the bottom of the terminal, just remember that '^' means CTRL. For instance ^x or ctrl+x will exit nano. Good luck.

---

### Post by homisolaris on 2007-10-22
i try using the ctrl+alt+F2 combination after the ubuntu loading screen, but the screen still remains black?

---

### Post by musther on 2007-10-22
When you turn on the machine, do you go to grub (for selecting what to boot), or does it just flash past with a quick message, something like:

```
GRUB

Starting stage 2

Press escape for menu
```

If so, press escape and select the 'recovery mode' nearest the top of the menu.  This will boot to a command prompt and then you can do the:

```
sudo nano /etc/X11/xorg.conf
```

And edit the file, look for the section looking something like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

And remove the highest resolution option from each line, save and reboot, that 'should' do it.  

Note that in Gutsy you may well find references to default, and failsafe in your xorg.conf (I did when sorting out a machine yesterday), you only need to change the default ones, leave failsafe.

I assume there's some way to make X drop to the new flashy failsafe xorg.conf GUI.  By default it won't drop to that if it thinks it's working, and in your case, although it sounds like your resolution is too high for your monitor, the computer doesn't know that, and thinks it is working normally.

---

