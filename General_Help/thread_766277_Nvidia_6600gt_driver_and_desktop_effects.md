---
title: "Nvidia 6600gt driver and desktop effects"
date: 2008-04-25
forum: General Help
---

### Post by stjomi on 2008-04-25
Anyone have the Nvidia 6600gt driver installed and working on 8.04?  I am tring to enable desktop effects and cannot do so because of the Nvidia driver.  If you have the driver installed can you post your xorg.conf file?  Any suggestions would be great!

---

### Post by HoYer on 2008-04-25
Hi there

I would suggest using a program called Envy. It can be found here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It automatically detects your Nvidia/Ati graphics card and installs the appropriate driver. Worked great on my Hardy 8.04 64-bit system with my Nvidia 8600gt card.
Install guides are found on the Envy site, but it should be fairly simple.
Hope it'll work out for you.

Hoyer

---

### Post by stjomi on 2008-04-25
Installed Envy but upon restart it went to a blank screen.  I had to boot into recovery mode and clicked on "reconfigure x server".  Ubuntu then booted.  Still no luck with the Nvidia driver!  Please help!

---

### Post by FuturePilot on 2008-04-25
Can you post your xorg.conf
```
cat /etc/X11/xorg.conf
```

---

### Post by NotTheMessiah on 2008-04-25
> **FuturePilot said:**
> Can you post your xorg.conf
```
cat /etc/X11/xorg.conf
```

Here is mine(with the same problem and gpu 6600GT agp):
```

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
```

For some reason it doesn't download the driver like it used to do before(like feisty/gutsy)

---

### Post by YonyonJohn on 2008-04-25
I was having a similar problem this is what I did to fix it:

1) enable all the repositories
* go to system > administration > software sources
* check all boxes under downloadable from the internet
* go to the third - party software tab and check both boxes (this step may not be necessary)
* click close and reboot

2) update repositories
* go to system -> administration -> synaptic package manager
* click reload in the top left (this will take a while, make sure you let it finish)
* close close synaptic package manager and reboot

3) install drivers
* go to system -> administration -> hardware drivers
* the enabled check box should now be un-checked
* check the enabled check box next to the driver you are having problems with
* click enabled on the window that will come up
* reboot

BTW, I'm a Linux noob (switched to Ubuntu yesterday), so some of these steps may be redundant / unnecessary or could probably be done with much less effort in the terminal

---

### Post by NotTheMessiah on 2008-04-25
> **YonyonJohn said:**
> 
1) enable all the repositories
* go to system > administration > software sources
* check all boxes under downloadable from the internet
* go to the third - party software tab and check both boxes (this step may not be necessary)
* click close and reboot

2) update repositories
* go to system -> administration -> synaptic package manager
* click reload in the top left (this will take a while, make sure you let it finish)
* close close synaptic package manager and reboot


BTW, I'm a Linux noob (switched to Ubuntu yesterday), so some of these steps may be redundant / unnecessary or could probably be done with much less effort in the terminal

Yeah that was it. Updating was the first thing that i did but i didn't tick the third party software sources. And then you just refresh the updates and download the nvidia driver when you click the desktop effects.

---

