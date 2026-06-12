---
title: "Help!! &quot;X Server is now disabled. Restart GDM when it is configured correctly&quot;"
date: 2007-05-20
forum: General Help
---

### Post by zodoman on 2007-05-20
Hi,  

I tried updating the driver to my GeForce 6600GT AGP video card with this tutorial,
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

I followed it to the letter but during the reboot I got this error "X Server is now disabled. Restart GDM when it is configured correctly".   

I was able to recover enough to get back to my desktop by booting up into recovery mode and doing a "sudo dpkg-reconfigure xserver-xorg" and loaing the "vesa" driver.    At this point, I was just gonna let Ubuntu use the restricted driver again like I had it but enabling this gave me the same "X Server is now disabled. Restart GDM when it is configured correctly" error upon reboot.    

I'm new to Linux, so I don't even know where to start from here to troubleshoot.    Any suggestions will be greatly appreciated.

Thank you.

---

### Post by mbradlcu on 2007-05-20
looking quickly at the howto I'm guessing you've installed the nv drivers from the nvida site. If so when you say you enable the nvidia drivers do you mean setting the driver in the xorg.conf to "nvidia",, and if so check out the /var/log/Xorg.0.log and post the errors found within..

---

### Post by Ub1476 on 2007-05-20
Here's a guide that at least work for ATI cards.. You are not changing much in the xorg.conf file, so if you screw things even more you can simply take it back as it were:)

[Linky]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

You don't need to reinstall of course, just edit the xorg.conf. Maybe you just have to add the stuff in the "Monitor" section.

Please leave a comment if it worked for your graphic card or not.:biggrin:

---

### Post by zodoman on 2007-05-20
> **mbradlcu said:**
> looking quickly at the howto I'm guessing you've installed the nv drivers from the nvida site. If so when you say you enable the nvidia drivers do you mean setting the driver in the xorg.conf to "nvidia",, and if so check out the /var/log/Xorg.0.log and post the errors found within..

Yes, the nv drivers from nvidia.   During the nvidia install, I remember it saying something about the kernel not matching or something like that and if I wanted the installation to connect to the nvidia ftp dadadada........ it said it couldnt find what if it was looking for so asked me if I would like the nvidia installer to compile such and such.... I said YES, figuring it was the thing to do.  Maybe this is what went wrong maybe.    

The only changes I made to my xorg file prior to the driver install is what was suggested in the tutorial, "Change the DISABLED_MODULES=&#8221;" to DISABLED_MODULES=&#8221;nv&#8221;

Here's my Xorg.0.log 


> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux butch-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	[COLOR="Red"](WW) warning, (EE) error, (NI) not implemented, (??) unknown[/COLOR].
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 20 03:03:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA 6600GT"
(**) |-->Input Device "Generic Keyboard"
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
[COLOR="Red"]Error opening /dev/input/wacom : Success[/COLOR]
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
[COLOR="Red"]Error opening /dev/input/wacom : Success[/COLOR]
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
[COLOR="Red"]Error opening /dev/input/wacom : Success[/COLOR]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!


---

### Post by mbradlcu on 2007-05-20
yea, basically that prompt you saw installing the nvidia drivers just means the nvidia didn't have a pre-compiled package for your system so it needed to build it using you're kernel headers,, this is normal.
I've never had to edit that module section you mentioned,, but what I've done is removed the nvidia-kernel-common and nvidia-glx packages,, re-installed the nvidia drivers from the nvidia site.. The just edited the /etc/X11/xorg.conf and changed "nv" to "nvidia",,, the line you currently have "vesa" set to..
looking at your Xorg log it seems this was generated while using the vesa driver so I'm not seeing much.. I would suggest trying the steps I mentioned and see if it works for you... please keep me posted,, good luck!

---

### Post by zodoman on 2007-05-20
Mbradlcu, thank you so much,  

I removed them packages as you suggested and modified my xorg.conf file to "nvidia" manually before the install and when the install asked if I wanted it to modify my xorg.conf file I said, NO.   Rebooted, everything is good.  

Thanks again.

---

