---
title: "Running a shell script on module load"
date: 2004-11-14
forum: General Help
---

### Post by tidalwav1 on 2004-11-14
So I wrote a tiny shell script to get my Wireless USB LAN dongle thingy to work. I have to run the script every time I put the dongle into the computer to get the internet working. I was wondering if there was a way to make this script run by itself, with root privelages, when the prism2_usb or p82011 module(s) is (are) loaded so that I don't have to run the script in a shell every time I turn on the computer and want to use the internet.

---

### Post by TravisNewman on 2004-11-14
you can add it to the init.d

put the script (or a symlink) into /etc/init.d and then run 
/usr/lib/lsb/install_initd /etc/init.d/name_of_script

---

### Post by tidalwav1 on 2004-11-15
[QUOTE=panickedthumb]you can add it to the init.d

put the script (or a symlink) into /etc/init.d and then run 
/usr/lib/lsb/install_initd /etc/init.d/name_of_script[/QUOTE]
 But won't that just run the script when the computer starts up? How to I have it automatically run when one or both of the aforementioned modules are loaded? (I am pretty sure the modules are NOT loaded on boot.) Also, the script needs root privelages--I don't want to have to type in a password--will adding it to the init.d automagically give it root privelages?

---

### Post by ynef on 2004-11-15
[QUOTE=tidalwav1]But won't that just run the script when the computer starts up? How to I have it automatically run when one or both of the aforementioned modules are loaded? (I am pretty sure the modules are NOT loaded on boot.) Also, the script needs root privelages--I don't want to have to type in a password--will adding it to the init.d automagically give it root privelages?[/QUOTE]
 Yeah, the scripts run as root.

Since you're such a shell hacker, you can check if the module is loaded by issuing the command:
lsmod | grep name-of-module
And checking what it returns.

Also, if you look closely at the README in /etc/rcS.d/ (the boot runlevel), after S40 the network is supposed to be loaded. You can add your script as S41 or so, which will ensure that the network is "up" by then.

---

### Post by tidalwav1 on 2004-11-15
I already know about lsmod | grep modulename, but I'm not sure how to keep a script incorporating that running in the background, waiting for the USB dongle. I'm also not sure how to do conditional 'if'-like statements in a shell script. Right now the script is very simple...it's just

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="DICKHOME" authtype="opensystem"
sudo dhclient wlan0

...how would I incorporate the 'lsmod | grep prism' into the script?

---

### Post by ynef on 2004-11-15
Sure. Add a call to system in the source code of the module.

---

### Post by tidalwav1 on 2004-11-15
Sorry, just realized my last post wasn't specific enough, and I edited it while you were replying...please reread it :p

---

### Post by TravisNewman on 2004-11-15
[QUOTE=tidalwav1]But won't that just run the script when the computer starts up? How to I have it automatically run when one or both of the aforementioned modules are loaded? (I am pretty sure the modules are NOT loaded on boot.) Also, the script needs root privelages--I don't want to have to type in a password--will adding it to the init.d automagically give it root privelages?[/QUOTE]
 Why don't you just set the module to load at startup?

---

### Post by az on 2004-11-15
Hotplug!  Not Init.d!

The modules gets loaded by hotplug.  There are scripts for this in /etc/hotplug.  Add the script with the appropriate name and it will work.


It actually should be added to hotplug (or linux-wlan-ng) upstream for this module!  WEP support needs to be done here, too...

---

### Post by TravisNewman on 2004-11-15
[QUOTE=azz]Hotplug!  Not Init.d!

The modules gets loaded by hotplug.  There are scripts for this in /etc/hotplug.  Add the script with the appropriate name and it will work.


It actually should be added to hotplug (or linux-wlan-ng) upstream for this module!  WEP support needs to be done here, too...[/QUOTE]
 Yeah, I thought the module was being loaded automatically and that he just wanted to start the script automatically, which would work in init.d wouldn't it? I mean he says he's manually starting it anyway, so the script (not the module) would work there right?

---

### Post by tidalwav1 on 2004-11-15
[QUOTE=panickedthumb]Yeah, I thought the module was being loaded automatically and that he just wanted to start the script automatically, which would work in init.d wouldn't it? I mean he says he's manually starting it anyway, so the script (not the module) would work there right?[/QUOTE]
Well, the module isn't loaded automatically...it's only loaded when I put the dongle into the USB slot.

As for [QUOTE=Azz]There are scripts for this in /etc/hotplug. Add the script with the appropriate name and it will work.[/QUOTE]...what is an appropriate name? :p

---

