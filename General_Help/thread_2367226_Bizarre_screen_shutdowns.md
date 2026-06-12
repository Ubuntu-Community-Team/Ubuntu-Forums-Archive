---
title: "Bizarre screen shutdowns"
date: 2017-07-27
forum: General Help
---

### Post by skippylou on 2017-07-27
Ubuntu 12.04LTS.  Kontron KT-690 motherboard .  

I disabled all power saving features and screen lock features and password features in both the OS and the BIOS setup.  Nevertheless the screen goes blank after 10 minutes or so of inactivity.   Hit some keys and display will come back, in a few seconds or in 5 to 10 minutes.  I realize that this is an old processor but 5 to 10 minutes, seriously?

I have used this MB in the past with several Ubuntu versions and no problems.  I don't really want to re-install or upgrade as I have all of my applications working nicely.  If I do have to re-install, would lubuntu be better with this old, slow system?

Any clue as to where or what to look at?

---

### Post by RobGoss on 2017-07-27
12.04 LTS has reached its end of life, 
you might want to install a current version of Ubuntu like 16.04.2, I'm sure you would have better results

---

### Post by mpowers1980 on 2017-08-16
Im having simiilar issues with 17.04 zesty, after several hours of troubleshooting, disabling power management in ubuntu and on bios as well as completely removing xfce4-power-manager. I also tried installing both gnome-screensaver and xscreensaver (not at the same time) to try to override the settings and still nothing works. xset and gsettings changes did nothing either. Also disabled monitor power/energy saving settings.

Finally, I decided to install dconf-editor (because i dont like gsettings) and disabled power settings at the following location - org.gnome.settings-daemon.plugins.power and rebooted.

After 8 hrs of nonsense forums elsewhere, testing and half-hearted solutions, this is the only thing that worked for me. Please also note that I am installed on a desktop computer and not a laptop so power management is pretty much useless for me anyhow. Hope this helps

UPDATE:
Well, here we go again, no further settings changed, no updates to any software or anything, literally just watching youtube and the problem has returned. Went back through all changes that I have made throughout the day and nothing has reverted from my changes but the problem has returned. This one is killin me...

UPDATE: (several more hours)
The problem does not take affect if I dont use the mouse or keyboard upon login lol. Only after the mouse is moved slightly or a key is pressed will the timer initiate. This led me deeper into dconf where there are several locations with input inactivity values. I've located and changed somewhere between 8-10 so far with the problem still continuing. This is getting absurd.

UPDATE: 
I have added the following code to /home/.profile for my only user account as well as root. Upon login, a simple xset q shows me that i have disabled everything i wanted. However, after the same 30 secs of inactivity, something turns screen blanking back on. There's ovbiously somthing that is still overriding but I can't seem to locate it. I'm still fairly certain this is hidden in the hardware somewhere but running out of places to look. Will continue to pry, test and poke around and keep the thread going until a solution is found.

xset -dpms
xset s off
xset s noblank
xset s noexpose

UPDATE:
Newest test included a reinstall of xfce4-power-manager to see if it could regain control over the signaling. Of course I also had to revert all settings back to off after the install as it defaults the values, however still no change. What else could be signalling just the noblanking option to reactivate?

---

