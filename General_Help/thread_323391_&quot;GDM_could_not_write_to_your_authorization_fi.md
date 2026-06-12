---
title: "&quot;GDM could not write to your authorization file . . . &quot; PLUS Hdd NOT Full"
date: 2006-12-22
forum: General Help
---

### Post by Kurt_Alan on 2006-12-22
About 75 people at ubuntuforums.org have had the error message: "GDM could not write to your authorization file . . ." About half posting (including me) solved the problem in recovery mode when they removed excess files after inadvertently filling their hdd.  However, the other half (me, too) still have the same error message after independently confirming that there is plenty of hdd space.  

Here is my /var/log/gdm.0 


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux kurt-desktop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 21 22:10:24 2006
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module mach64 not found.
[drm] failed to load kernel module "mach64"
(EE) ATI(0): [dri] DRIScreenInit Failed
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory

Does anyone have a solution?  aysiu? catlett? tseliot?](*,)

---

### Post by codejunkie on 2006-12-22
> **Kurt_Alan said:**
> About 75 people at ubuntuforums.org have had the error message: "GDM could not write to your authorization file . . ." About half posting (including me) solved the problem in recovery mode when they removed excess files after inadvertently filling their hdd.  However, the other half (me, too) still have the same error message after independently confirming that there is plenty of hdd space.  

Here is my /var/log/gdm.0 


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux kurt-desktop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 21 22:10:24 2006
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module mach64 not found.
[drm] failed to load kernel module "mach64"
(EE) ATI(0): [dri] DRIScreenInit Failed
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory

Does anyone have a solution?  aysiu? catlett? tseliot?](*,)

when you reach the terminal when gdm fails to load, login with your normal user account and enter ```
startx
``` if the xserver still fails to start the problem is most likely with your /etc/X11/xorg.conf file and not gdm. if it does fail to start when you enter the **startx** command this is something you can try 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
then run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` this will replace your xorg.conf file with the default one when you installed ubuntu, if you have done any major customizing to the xorg.conf file like changing video card drivers or special options for xgl etc, you will have to add those again.

if the doesn't work i have also had this problem when i accidentally changed permissions on my .ICEauthority file, i  fixed that by running ```
cd /home/username
``` and then running ```
sudo rm .ICEauthority
``` then running ```
sudo /etc/init.d/gdm restart
``` and ubuntu will create a new one with the correct permissions.

just a warning though be careful when using the **rm** command if your not in the right dir or you enter the command wrong you can remove some things that you need like your whole home dir so just use it with caution.

also just in case that the hard drive space is being reported incorrectly and you are in fact out of space you can also run ```
sudo apt-get autoclean
``` and it will clear out older packages downloaded by synaptic/apt-get that are just hogging space.

hope one of these helps you solve the problem let me know how it goes

codejunkie,

---

### Post by Kurt_Alan on 2006-12-23
I want to thank you for your efforts.  Unfortunately, each solution failed.  At least now I know what the problem is not.

I want to clarify my beginning position.  You said: "when you reach the terminal when gdm fails to load, login with your normal user account and enter startx"

After a normal boot, I reach the GUI log-on splash screen.  Entering my username and password here gives me the error message: "GDM could not write . . ."  and loops me back to the same splash screen.  My access is limited to Recovery Mode from the GRUB menu.  Here I receive a prompt: root@kurt-desktop:~#  and startx will give my my GNOME desktop in recovery mode.

Is there any solution short of reformatting my hdd??  If I uninstall/reinstall GNOME, will this leave my hdd data intact, and just alter my desktop config??

---

### Post by codejunkie on 2006-12-23
> **Kurt_Alan said:**
> I want to thank you for your efforts.  Unfortunately, each solution failed.  At least now I know what the problem is not.

I want to clarify my beginning position.  You said: "when you reach the terminal when gdm fails to load, login with your normal user account and enter startx"

After a normal boot, I reach the GUI log-on splash screen.  Entering my username and password here gives me the error message: "GDM could not write . . ."  and loops me back to the same splash screen.  My access is limited to Recovery Mode from the GRUB menu.  Here I receive a prompt: root@kurt-desktop:~#  and startx will give my my GNOME desktop in recovery mode.

Is there any solution short of reformatting my hdd??  If I uninstall/reinstall GNOME, will this leave my hdd data intact, and just alter my desktop config??

removing and reinstalling all of gnome is very likely to cause you more trouble than you are having now, but you could try this. boot up normally when you see the gdm screen press ctrl + alt + F1 this will take you into the terminal, login with your username and enter 
```
sudo /etc/init.d/gdm stop
``` this will shutdown gdm now enter ```
startx
``` to start gnome, open a terminal and copy and paste this command in the terminal

```
sudo apt-get remove --purge gdm
``` this should remove gdm and all configuration files, this will also remove the **ubuntu-desktop** and a couple other packages but don't worry ubuntu-desktop is just a meta package that tells apt to install a certain set of programs it won't hurt anything removing it, if you have any error messages copy and paste them here so i can take a look at them.

after you've done that run ```
sudo apt-get install ubuntu-desktop
``` and this will reinstall a clean version of the packages it just removed now enter ```
sudo reboot
```to restart the computer and see if it will let you login this time.

hope this helps and let me know how this goes for you.

codejunkie,

---

### Post by Kurt_Alan on 2006-12-24
Thanks for following up with GDM reinstall.  Unfortunately, before I received this post, I reformatted my hard drive.  Glad to have your procedures for future use.

I looked at my GDM log after a clean reinstall of OS, thinking I could have a before and after, in the event that "GDM could not write . . . " appears again.

To my surprise my new log includes many of the same "errors" as my log when I had the GUI problem.  This is the "new" one after re-install:


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux kurt-desktop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 23 19:18:27 2006
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module mach64 not found.
[drm] failed to load kernel module "mach64"
(EE) ATI(0): [dri] DRIScreenInit Failed
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
SetGrabKeysState - disabled
SetGrabKeysState - enabled

I guess these "errors," then, have nothing to do with the error message.  I'm keeping this log for future reference, anyway.  Thanks again.

---

### Post by mbsullivan on 2008-02-08
Hi All,

I know this thread is old, and the problem was "solved" (well, sort of)... For future reference to people with similar problems, this problem may be caused by improper permissions being set on your /tmp directory.

Try: 

```
sudo -s
chown root:root /tmp
chmod 777 /tmp
```

Hopefully this may help somebody experiencing this fairly common problem.
Mike

---

