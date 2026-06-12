---
title: "Mouse scroll broken...Help?"
date: 2006-12-05
forum: General Help
---

### Post by madcow72 on 2006-12-05
Hello!  I installed Automatix2 using the guide on [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")
and, although I'm not sure if it's related, restarted X with the KDE-extras to configure eye-candy, and found that the scroll wheel of my mouse (Microsoft Wireless Laser Mouse 5000) doesn't work properly.  When trying to scroll up or down in Firefox, it browses me forward or backward through the links I just visited.  In Open Office, (or any other program), the scroll simply doesn't do anything.

Here is a sample of my xorg.conf:
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Buttons"	"5"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection
``` 

Also, I gave up and tried to just: ```
sudo dpkg-reconfigure xserver-xorg
```
which gives me the following:  ```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061205132258
dexconf: error: cannot generate configuration file; shared/default-x-server not
set.  Aborting.  Reconfigure the X server with "dpkg-reconfigure" to correct
this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.

```

I'd really love to get my mouse scroll wheel working again!  Also, I'm curious why I can't reconfigure X... Any ideas would be great!  Thanks!

---

### Post by madcow72 on 2006-12-06
Okay, I realized one stupid thing I was doing:  Apparently you can't run dpkg-reconfigure xserver-xorg while actually in X...  Logged out, executed the line from a console, and was able to go through the entire reconfiguration.  

Unfortunately, reconfiguring X didn't do anything as far as fixing the scroll button on my mouse!  Is there any option that I'm just not seeing in "System Settings" under KDE?

---

