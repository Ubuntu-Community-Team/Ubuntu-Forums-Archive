---
title: "[SOLVED] Graphic Problems (Installing Envy)"
date: 2008-02-14
forum: General Help
---

### Post by stuartwood89 on 2008-02-14
My internet is working, so next on my list is the graphics:

This is what I get: 

[http://i147.photobucket.com/albums/r315/stuartwood1989/DSC00443.jpg?t=1203009311](http://i147.photobucket.com/albums/r315/stuartwood1989/DSC00443.jpg?t=1203009311)
(look at the screen position, not the Firefox window)

I've tried adjusting the screen position on my monitor, but it will only move across so far.  The resolution is set to 1440x900, so there shouldn't be a problem.
I tried installing Envy, but when I go to run it, I get 'Error: Dependency is not satisfiable: build-essential'

Anyone know how to get around this?

---

### Post by PmDematagoda on 2008-02-14
Open Software Sources in System>Administration>Software Sources and then enable all the choices in the Ubuntu Software tab but remove the choice for the CD-ROM. After that is done close the window, you will be asked to reload the sources list, do that, after that is done then you should be able to install Envy.

---

### Post by stuartwood89 on 2008-02-14
Thanks, that worked great.  However now that it is installed, I open it and I get an 'Error' dialogue containing 

[COLOR="Red"][I]'dkms

Please install them manually and launch Envy again'[/I][/COLOR]

Sorry to keep asking but I'm completely new to this kind of thing.

---

### Post by PmDematagoda on 2008-02-14
Not really sure about the problem with Envy, but if you wish, I can help you to setup your VGA card manually, provided that it is Nvidia.

---

### Post by stuartwood89 on 2008-02-15
> **PmDematagoda said:**
> Not really sure about the problem with Envy, but if you wish, I can help you to setup your VGA card manually, provided that it is Nvidia.

I have an PCI-e ASUS nVidia Geforce 7600GS, if that helps.

I've changed my resolution to a smaller one for the time being and then stretched it across the screen, but at least I can see the right-hand side of the screen now.  

Obviously I would prefer to have my 1440x900 resolution back and have it in the middle of the screen, but I can't until I get this driver working.

:)

---

### Post by PmDematagoda on 2008-02-15
Ok, so this is what you will need to do to install the driver:-

1) Install the prerequisites for the installation of the driver using:-
```
sudo apt-get install build-essential
```

2) Download the driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run
```

Note:- From here onwards you will be using the CLI(Command Line Interface) until you restart the GUI(Graphical User Interface)

3) Kill the GUI using:-
```
sudo /etc/init.d/gdm stop
```

4) Install the driver using:-
```
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```

5) After installation is complete, restart the GUI using:-
```
sudo /etc/init.d/gdm start
```

Your Nvidia driver should now work.

---

### Post by stuartwood89 on 2008-02-15
Ok I'll try that, but I tried installing the restricted drivers in the restricted drivers menu, which now works.  However I can't get the full visual effects (cube etc) to work.  Shall I disable this driver and use the method you suggested instead?

---

### Post by PmDematagoda on 2008-02-15
The drivers installed by the Restricted Drivers Manager may clash with the driver from Nvidia, so do not try and install the "original" Nvidia driver unless you are willing to take a risk or if the current driver does not work properly.

---

### Post by erginemr on 2008-02-15
Could you please post your "/etc/X11/xorg.conf" file here before attempting anything?

and also the output of the command "glxinfo | grep -i direct"...

---

### Post by stuartwood89 on 2008-02-15
> **erginemr said:**
> Could you please post your "/etc/X11/xorg.conf" file here before attempting anything?
[COLOR="Red"]How do I attach it, the attachment thing doesn't recognise the file.[/COLOR]
> **erginemr said:**
> and also the output of the command "glxinfo | grep -i direct"...
```
[COLOR="Blue"]stuartwood89@Ubuntu:~$ glxinfo | grep -i direct
direct rendering: Ye[/COLOR]s
```
[COLOR="Red"]I've already enabled the restricted driver this morning, but I can disable it I suppose.  Since I enabled it, the display is fine now, but my friend said that it's better to have the proper driver.[/COLOR]

---

### Post by erginemr on 2008-02-15
If your display is fine, that is; if the screen covers your whole monitor area, then you don't have to go fetch the binary installer from NVidia. If "glxinfo | grep -i direct" reports direct rendering as "yes", then you already have the binary driver. Don't bother with NVidia web site, it creates more trouble after a kernel update (which are released once in several weeks which you will automatically download via a regular update).

The "nvidia-glx-*" packages (i.e. those installed by Ubuntu restricted driver manager) are no less then the installer package on the NVIDIA web site in terms of 3D performance, are already binary and are the **proper** drivers.

To get the output of your xorg.conf file, which is responsible from your X server (screen) configuration, you can write down the following in a terminal:

```
gedit /etc/X11/xorg.conf
```
Select and copy all text and paste it here to your next post. But if your problems are resolved, there is no need to do that. Anyway, please post it, so that we can have a final check on the resolution selected in the config file.

---

### Post by stuartwood89 on 2008-02-15
Here you go:

```
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"YM19APR"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"YM19APR"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"	"1440x900"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

The screen does cover the whole monitor area, but I don't get a splash/startup screen.  When I select Ubuntu from the list, my monitor says 'out of range' and I get a blank screen for about 10-20 seconds, followed by the login screen.  Not sure if this is related in anyway, but I'd like to get my splash screen to appear.

Thanks for your help so far :)

---

### Post by erginemr on 2008-02-15
That one is easy. Give me a few hours. I will reply when I get home.

---

### Post by erginemr on 2008-02-15
**For your desktop resolution after the login:**

As the natural resolution of your monitor is 1440x900 px ([http://www.qtds.com/products.asp?recnumber=998](http://www.qtds.com/products.asp?recnumber=998)), you should edit your xorg.conf file to let it select this resolution. You can copy and paste from here to your terminal:

1. First back up your current config file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

2. Then, edit the file with:
```
gksudo gedit /etc/X11/xorg.conf
```

3. Remove the resolution "1440x1440":
```
		Modes		**[COLOR="Red"]"1440x1440"[/COLOR]**	"1440x900"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
```
so that it reads:
```
		Modes		"1440x900"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
```
(Actually, many other resolutions listed hereby are futile too, but anyway.)

4. Save the file and close. Restart X server with Ctrl+Alt+BackSpace.

5. If something goes wrong (unlikely), restore your backup with:
```
sudo cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
```

---

### Post by erginemr on 2008-02-15
**For your desktop resolution before the login (i.e. "out of range" error.):**

The resolution of the splash screen with the Ubuntu logo and orange bar is controlled by another config file **"/etc/usplash.conf"**. What you need to do is to change the resolution to 1440x900, and run a configuration tool to reflect this change to the boot file **"/boot/vmlinuz-2.6.22-14-generic"**. 

But this is a critical file, and if writing to this file fails, you will not be able to boot again. That's why, we should backup as always. 

1. First things first, take a back up of both files.
Assuming that you are also using the same Linux kernel "2.6.22-14-generic", which you can check with:
```
uname -r
```
Backup these two files:
```
sudo cp /boot/initrd.img-2.6.22-14-generic /boot/initrd.img-2.6.22-14-generic.mybackup
```
```
sudo cp /etc/usplash.conf /etc/usplash.conf.mybackup
```

2. Now, edit the first file:
```
gksudo gedit /etc/usplash.conf
```
In my system it reads:
```
# Usplash configuration file
xres=**[COLOR="Red"]1024[/COLOR]**
yres=**[COLOR="Red"]768[/COLOR]**
```
You should edit it to look like:
```
# Usplash configuration file
xres=1440
yres=900
```
Save the file and close.

3. On to writing the new "initrd.img-2.6.22-14-generic" file:
```
sudo dpkg-reconfigure -phigh usplash
```
Make sure that the process has been completed successfully. Otherwise, re-apply the very same command.

4. Finally, reboot to welcome the orange splash screen.

5. This should work, but for some reason if you still get an "out of range" error, try a lower resolution. Given the fact that you are dual booting with Windows, you can get a list of appropriate resolutions from Windows desktop settings.

---

### Post by stuartwood89 on 2008-02-15
```
stuartwood89@Ubuntu:~$ uname -r
2.6.22-14-rt

```

When I try to find the two files to backup, it says the filename doesn't exist.

I'm running Ubuntu Studio by the way if that changes anything.

---

### Post by stuartwood89 on 2008-02-15
Will this have anything to do with the kernal I'm using?

I'm on 7.10 Gutsy BTW.

---

### Post by erginemr on 2008-02-15
Then, you should list the contents of your /boot folder with:
```
ls /boot
```
and find the correct file to backup.

Alternatively, you can use this line:
```
sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.mybackup

```
where the section `uname -r` will input the correct kernel version automatically.

How about dropping "1440x1440" from your xorg.conf file? Did it work?

---

### Post by stuartwood89 on 2008-02-15
Getting rid of 1440x1440 from the xorg.conf file didn't seem to do anything, but I took another look at your post about the splash/boot screen and tried it out.  So now it's all working perfectly.  Thanks very much for your help.


On a slightly different note, do you know why the logoff sound doesn't play even though I've allocated one?  It hasn't played since I installed it.

---

### Post by erginemr on 2008-02-15
Great news! You are welcome.

But the part for getting rid of 1440x1440 was to fix your desktop's screen resolution, not that of the splash screen. If you are sure that your screen runs at 1440x900 @ 60 Hz, which you can check by running Alt+F2 -> "nvidia-settings", then you are good to go.

---

### Post by stuartwood89 on 2008-02-17
Yeah it'a all good now, I'm very grateful for your help and patience.

Do you reckon you tell me how to get my logoff sound working? (I don't think it really justifies starting another thread)

---

### Post by PmDematagoda on 2008-02-17
Go to System>Preferences>Sound and then go to the Sounds tab and set a sound for the Log off.

---

### Post by stuartwood89 on 2008-02-17
> **PmDematagoda said:**
> Go to System>Preferences>Sound and then go to the Sounds tab and set a sound for the Log off.

I tried that, I can get the logon sound to work, not too sure about the others either.

:)

---

### Post by erginemr on 2008-02-17
> **stuartwood89 said:**
> I tried that, I can get the logon sound to work, not too sure about the others either.

:)

Since this is not a very common error and the precise reason is hard to pinpoint, all we can do is to throw wild guesses at you. In this context, to back up PmDematagoda's suggestion, please see the screen-shots I have attached that reflects the state of the "sounds" dialog in my system.

---

### Post by stuartwood89 on 2008-02-17
It all seems to be in order, except I have a different sound card to yours, so the bottom dropdown box in the first screenshot is different.  Anyway, it's not too big of an issue.  I can still listen to my music and everything, just one of those things that will bug me :-({|=  Thanks for all your help guys!!!

---

