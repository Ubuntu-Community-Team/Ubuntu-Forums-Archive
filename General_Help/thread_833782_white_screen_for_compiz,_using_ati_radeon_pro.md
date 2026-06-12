---
title: "white screen for compiz, using ati radeon pro"
date: 2008-06-18
forum: General Help
---

### Post by adamb24 on 2008-06-18
I have an ati radeon 128 pro card, and i recently installed hardy. when i tried to install the proprietary driver Ubuntu suggested and rebooted, when i tried to run compiz it gave me a white screen. When i ran fglrxinfo in the terminal it said it was using the mesa driver. Anyone know how to fix this? thanks

---

### Post by Soo on 2008-06-19
I fixed this by installing EnvyNG and reinstalling my ATI drivers when it happened to me.

---

### Post by adamb24 on 2008-06-19
i tried that but it still wouldnt fix the screen, do i need to uninstall the driver ubuntu originally gave me? i thought that env would overwrite it?

---

### Post by Rocket2DMn on 2008-06-19
Is that an old video card from the RAGE series?  If your card is more than 4 or so years old, you may not be able to use the restricted fglrx drivers, you will need the open source "ati" drivers.  I'm not sure that card will support compiz if it is as old as I think it is.
You can remove fglrx with
```
sudo apt-get remove --purge xorg-driver-fgrlx
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE or reboot the computer.

---

### Post by adamb24 on 2008-06-19
its at least 4 years old if not older, i tried to remove the xorg-fglrx info as you suggested but the terminal said it couldnt find the package to remove, i tried the second prompt and nothing changed. i had compiz working on gutsy although i dont remember what steps i followed, it was over 6 months ago. so how can i remove the driver ubuntu installed and use the other?

---

### Post by Rocket2DMn on 2008-06-19
> **adamb24 said:**
> its at least 4 years old if not older, i tried to remove the xorg-fglrx info as you suggested but the terminal said it couldnt find the package to remove, i tried the second prompt and nothing changed. i had compiz working on gutsy although i dont remember what steps i followed, it was over 6 months ago. so how can i remove the driver ubuntu installed and use the other?

That's because I can't spell..., it's fglrx not fgrlx
```
sudo apt-get remove --purge xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg -phigh
```
Sorry about that.
The second command just resets xorg.conf to defaults in case fglrx got added to it.
You can also search Synaptic for it.  You didn't use Envy to install the driver to download a .run file from ATI's website did you?

---

### Post by adamb24 on 2008-06-19
i did actually yes

---

### Post by Rocket2DMn on 2008-06-19
OK, if you used Envy to install the driver, you should be able to uninstall it from there.  As far as removing the when installed with the .run file, you may just be able to use
```
sudo <installer_file>.run --uninstall
``` like you can with nvidia drivers.

---

### Post by adamb24 on 2008-06-19
great thank you, so just one more question, once i uninstall the env driver how do i install the open source one?

---

### Post by Rocket2DMn on 2008-06-19
The open source driver should already be there and kick in automatically when you reconfigure X after uninstall fgrlx.  Just run the second command I've been giving you and restart X.
I believe the package is called "xserver-xorg-video-ati"

---

### Post by adamb24 on 2008-06-19
this is the output for the second command prompt i just wondered if it was supposed to do this

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080619161300

---

### Post by Rocket2DMn on 2008-06-19
Yes, that is normal.

---

### Post by adamb24 on 2008-06-19
ok i followed your command prompts i still get a white screen when i try to load the compiz options, this is the response i get when i type in fglrxinfo  The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx

---

### Post by Rocket2DMn on 2008-06-19
OK that's a start, you don't want fglrx or fglrxinfo.
For now, don't enable compiz, please post the output of:
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```
Then run
```
compiz --replace > compiztest.txt
```
It may do the white screen stuff.  Hit CTRL+C, then type out
```
metacity --replace
``` to get back to where you were.  
Now also post the output of
```
cat compiztest.txt
```

---

### Post by adamb24 on 2008-06-19
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]

sudo dpkg-reconfigure -phigh xserver-xorg

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

### Post by adamb24 on 2008-06-19
cat compiztest.txt
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present.

---

### Post by Rocket2DMn on 2008-06-19
OK, so your card is not what you initially said it was, you said "ati radeon 128 pro card" but it is a Radeon 9800 Pro.  That's OK.  This card DOES use restricted drivers, but rather than using Envy, you should use EnvyNG which is specific for Hardy Heron.
Here are directions for EnvyNG - [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)
Be sure that you remove the Envy that is already there.
You can also try from System->Administration->Hardware Drivers - this may be the better place to start, and if that doesn't work, then use EnvyNG.
I know others have complained about the 9800 pro, hopefully you won't have any problems after this.

---

### Post by adamb24 on 2008-06-20
ya i installed the driver through envy ng and rebooted, when i typed in fglrxinfo in the terminal this was my output

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

---

### Post by Rocket2DMn on 2008-06-20
OK, I'm at a loss.  Right now I will direct you toward this page: [uhelp]community/BinaryDriverHowto/ATI[/uhelp]
it has a couple of notes about Mesa, so just use your web browser's search function to locate "mesa" on the page.  Have a look through each part of the page that mentions mesa (yeah, it's some reading), but hopefully something there will get you back on the right track.
Good luck.

---

