---
title: "Boot freezes on nvidia card"
date: 2007-04-03
forum: General Help
---

### Post by tmray on 2007-04-03
I installed a fresh version of feisty from a live cd using the integrated graphics card. Then I made the changes to run from my nvidia GeForce fx 5200 card.
I installed nvidia-glx from adept.

I rebooted to BIOS and changed the primary graphics card to PCI. Plugged my monitor into the nvidia card and rebooted.

On start up I got the boot logo and the progress bar gets about 1/4 of the way through and then stops.

any ideas whats wrong?

---

### Post by codejunkie on 2007-04-03
> **tmray said:**
> I installed a fresh version of feisty from a live cd using the integrated graphics card. Then I made the changes to run from my nvidia GeForce fx 5200 card.
I installed nvidia-glx from adept.

I rebooted to BIOS and changed the primary graphics card to PCI. Plugged my monitor into the nvidia card and rebooted.

On start up I got the boot logo and the progress bar gets about 1/4 of the way through and then stops.

any ideas whats wrong?
some motherboards with onboard video cards, won't fully disable the onboard video when you switch it to pci in the bios, it just sets it to use that device first, and if there's no card detected, it uses the onboard instead. 

this confuses x sometimes, because it detects both displays, and you will have to tell it which one to use by setting it in you /etc/X11/xorg.conf file,  if your motherboard has an option to completely disable onboard video in the bios do that first, then at the grub menu choose the recovery mode option for your kernel this will boot you into a terminal without a gui then run this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```this should auto configure the xserver for the nvidia card now press ctrl+alt+delete to restart the computer.

if that doesn't work you have a motherboard that won't completely disable the onboard video, and you'll have to configure the /etc/X11/xorg.conf file to use the pci card this thread should help you do that [http://ubuntuforums.org/showthread.php?p=2278208](http://ubuntuforums.org/showthread.php?p=2278208) hope this helps.

---

### Post by tmray on 2007-04-03
That link you gave me was the way to go. It's up and working now, except that everytime I reboot the screen resolution sets to 800x600 and I have to reset it to 1280x1024. 

How can I get it to keep this screen resolution?

---

### Post by codejunkie on 2007-04-04
> **tmray said:**
> That link you gave me was the way to go. It's up and working now, except that everytime I reboot the screen resolution sets to 800x600 and I have to reset it to 1280x1024. 

How can I get it to keep this screen resolution?

**Before doing this, make sure you only set the refresh rate and screen resolution to something that you know is supported by your video card and monitor, DO NOT try to set it to something higher, because you want a higher resolution but neither the monitor or card support it.**

the above was just a Warning not to overdrive your hardware, because you can damage it if you do. but if the resolution and refresh rate you want set was supported under windows you'll be just fine using the same under Linux.

to set it open a terminal and copy and paste this into a terminal 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
``` 
to backup your current configuration
then copy and paste
```
sudo gedit /etc/X11/xorg.conf
```
now scroll down to the screen section it should look something like this
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"DCLCD DCL9A"
	[COLOR="Navy"]DefaultDepth	24[/COLOR]
	SubSection "Display"
		Depth		1
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Take a look at the [COLOR="Navy"]DefaultDepth[/COLOR] part i highlighted in blue, mine is set to 24. see what yours is set to then go to that line and add the resolution you want to the beginning of that line like i have, then save the file. in order for the changes to take effect you need to restart the xserver, you can do that by logging out and pressing ```
ctrl+alt+Backspace
```
also if you need to you can also specify the refresh rate you want,  just add it to that line like this 
"1280x1024_60" for 60 HZ  "1280x1024_75" for 75 HZ and so on, hope this helps if you have any questions just post them here and i'll try and help you work it out.

---

