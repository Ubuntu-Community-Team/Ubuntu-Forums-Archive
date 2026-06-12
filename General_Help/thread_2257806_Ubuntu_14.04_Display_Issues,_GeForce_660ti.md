---
title: "Ubuntu 14.04 Display Issues, GeForce 660ti"
date: 2014-12-22
forum: General Help
---

### Post by maussy on 2014-12-22
[COLOR=#000000][FONT=verdana]I am having an issue where every time I initially enter my login to get into the computer, the wallpapers show up but Unity refuses to load or anything else. Any help?[/FONT][/COLOR][COLOR=#000000][FONT=verdana]
System:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Ubuntu 14.04 64 bit[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]i5-3570k[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]8gb ram[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]GeForce 660ti 2gb ram (340 driver)[/FONT][/COLOR]

---

### Post by CantankRus on 2014-12-23
Have you previously been able to load unity with that driver?
Where did you install from? I don't have a 340 nvidia driver.

If you have just messed up compiz try the steps from this post to reset compiz/unity.
[http://ubuntuforums.org/showthread.php?t=2253222&p=13183010#post13183010](http://ubuntuforums.org/showthread.php?t=2253222&p=13183010#post13183010)

---

### Post by Medroo_Eogan on 2015-03-17
> **CantankRus said:**
> Have you previously been able to load unity with that driver?
Where did you install from? I don't have a 340 nvidia driver.

If you have just messed up compiz try the steps from this post to reset compiz/unity.
[http://ubuntuforums.org/showthread.php?t=2253222&p=13183010#post13183010](http://ubuntuforums.org/showthread.php?t=2253222&p=13183010#post13183010)

Ubuntu 14.04 video display problem.
On a sample of one with Nvidia Gforce 6150se video chips set I fort the Tahr and lived.
 I thought it may be a good idea to upgrade from 12.04 to 14.04.  Did that and promptly crashed, as many others seem to have.  Tried all the fixes I could think of and some I haven’t, trawled the Internet and swore a lot to no avail.
Eventually realisation dawned that the problem was with the kernel.  That is when I found that from version 13 on the default display drivers live in the kernel and are pretty much out of reach if things don’t work.  You can do what you like to the config files.  The kernel will always over ride them.
 
Armed with this insight things started to come together.
 
Get yourself a fresh install of 14.04 if you have been messing with the current one.
Now you need a terminal or TTY session.
You may be lucky and be able to access one when the system boots up after the install. “Ctrl alt t” for a terminal or “ctrl alt f1” for TTY.
 
If not you need the grub menu.  Hold the shift key down and boot the computer.  If that doesn’t work try it with f1 key.
 
Once you get grub up select “advanced options” then the line ending in “recovery mode” then “resume”
 
With a bit of luck you will end up in a desktop. Launch a terminal session.  If there is no desktop try for a terminal or TTY session anyway.  Sometimes it works. If all that fails reboot to the grub menu again and select “drop to root shell prompt” wherein you can do what is needed.
 
Now you can edit grub.  A dangerous practise at the best of times.
Do   sudo gedit /etc/default/grub
Find a line that says  GRUB_CMDLINE_LINUX_DEFAULT  “Quite Splash”
Change that to  GRUB_CMDLINE_LINUX_DEFAULT “Quite Splash nomodeset”
Save file and do   sudo update-grub
Reboot
You should now have a desktop with nice big icons.
At this point it is probably worth doing the sudo apt-get update upgrade thing by your preferred method:- via terminal command or update manager.   I had some trouble at this point with broken dependencies.  However it turned out to be a broken local Ubuntu server.  After an hour or so getting nowhere I switched to the main server and all problem disappeared.
 
Next challenge is to get some display drivers installed so you can have more than one icon on the screen at a time.
 
The easy way is to go system settings-software and updates- additional drivers.  A list of recommended drivers should appear after a short wait.  Select one and apply. Or you can do the sudo apt-get install MyPreferedDisplayDriver and sudo apt-get upgrade thing
 
Never managed to get the default Ubuntu driver to behave but didn’t put much effort into it anyway.
 
 
Went back to 12.04 anyway.  Reload after the crash and burn fixed the problem I was having with some legacy gear.  Strange stuff happens

---

### Post by blue_fox on 2015-03-17
> **maussy said:**
> [COLOR=#000000][FONT=verdana]I am having an issue where every time I initially enter my login to get into the computer, the wallpapers show up but Unity refuses to load or anything else. Any help?[/FONT][/COLOR][COLOR=#000000][FONT=verdana]
System:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Ubuntu 14.04 64 bit[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]i5-3570k[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]8gb ram[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]GeForce 660ti 2gb ram (340 driver)[/FONT][/COLOR]
Hi,

I have an issue with similar symptoms: [http://ubuntuforums.org/showthread.php?t=2266382](http://ubuntuforums.org/showthread.php?t=2266382).
I installed LXDE wich seems to work with all drivers. It's possible to use the nouveau driver and to have a working Unity desktop, but the nouveau driver doesn't use much HW acceleration, so (at least on a Centrino Duo ...) the Unity desktop is quite slow, as well as playing videos, ...

Best,
Arne

---

