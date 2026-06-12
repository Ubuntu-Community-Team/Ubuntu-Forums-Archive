---
title: "turning off ubuntu 17.04 after 30 second of inactivity"
date: 2017-05-15
forum: General Help
---

### Post by ghalehnoey on 2017-05-15
hi.
I've upgraded my ubuntu to 17.04 2 months ago.but now i have a problem.
the screen turning off after 30 second of inactivity.
thanks for your help.

---

### Post by Irihapeti on 2017-05-15
Thread moved to **General Help** for a better fit. (Forum Feedback and Help is for problems with the forums software itself.)

---

### Post by ajgreeny on 2017-05-15
Go to System settings from the cog icon top right in the panel and from there "Brightness and Lock" and see if the settings are what you want.

Personally, I always disable the screen lock in that and let xfce4-power-manager settings deal with it, but for Ubuntu I presume there will be something similar that you can use.

---

### Post by ghalehnoey on 2017-05-24
thanks for your recommendation.but that's not work

---

### Post by efflandt on 2017-05-24
If it is a laptop, check BIOS or UEFI settings about power management (especially if operating on battery power).

---

### Post by naburu on 2017-06-30
Do we have any solution to this issue? I have done the full trip over the internet trying all manners of solutions: 
> xset dpms 0 0 0 && xset s noblank && xset s off
> xset -dpms s off s noblank s 0 0 s noexpose
> xset s noblank
> xset dpms force off
> disabled settings in brightness and lock


and all that to no success. Mine goes off after 32 seconds. There is no BIOS setting that relates to screen blanking or power off on my laptop. My model is Dell Inspiron 3000 series 7th generation

---

### Post by mik3e2 on 2017-08-13
I hope this isn't too late to be of any help.

If xset is the problem then 'xset q' will report screen saver timeout greater than 0 and dpms enabled. The command to disable both is 'xset s off -dpms'. Check 'xset q' again to confirm success. The dpms change seems to hold but the screen saver change does not survive a reboot. My ultimate solution is to create a script to run the screen saver part of the command, and create a .desktop file in /home/mike/.config/autostart to run it. I also set the volume to a low startup value.

Here's my code for the script, the filename I use is StartUp.scr:
```
#!/bin/sh
sleep 2
#unset xset
xset s off
#Set Master volume
amixer set 'Master',0 25 unmute
```
After saving the file check properties and make it executable.

Here's my code for the .desktop file, named startup.desktop:
```
[Desktop Entry]
Name=startup
Comment=unset screen saver et al
Type=Application
Exec=/home/mike/bin/StartUp.scr
Icon=/home/mike/Icons/gear-black.png
Terminal=false
Categories=Utility
```
After saving the file check properties and make it executable. The paths in Exec= and Icon= are specific to my setup and should be changed to the local values.

Mike

---

