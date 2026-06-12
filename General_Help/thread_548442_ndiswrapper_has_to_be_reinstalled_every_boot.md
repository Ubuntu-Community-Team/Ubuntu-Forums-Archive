---
title: "ndiswrapper has to be reinstalled every boot?"
date: 2007-09-11
forum: General Help
---

### Post by markp1989 on 2007-09-11
After installing the ndiswrapper drivers using this guide:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=fujitsu+siemens+amilo+pro+v2030](http://ubuntuforums.org/showthread.php?t=197102&highlight=fujitsu+siemens+amilo+pro+v2030)
the connection works fine, until i reboot, then the computer acts as if i never installed the drivers. 

It works if i install the drivers again, but then when i restart the drivers go again

Does any one know why this is happening?

information about computer:
Xubuntu 7.04
Fujitsu siemens amilo pro v2030

---

### Post by reckless2k2 on 2007-09-11
from ndiswrapper site:


Once everything works fine you can write the correct modprobe settings to load ndiswrapper automatically when the wlan0 interface is used, by running ndiswrapper -m Note that this doesn’t automatically load ndiswrapper module at boot time. If you want the module to be loaded automatically at boot time, you should configure your module setup, which depends on the distribution. Most distributions will load all modules listed in /etc/modules at boot time. Mandrake 10.x uses /etc/modprobe.preload. For them, you can add a line ndiswrapper in /etc/modules. For Fedora Core5, add a line alias wlan0 ndiswrapper in /etc/modprobe.conf.

If this does not work, instead add a line modprobe ndiswrapper in /etc/rc.d/rc.local

---

### Post by markp1989 on 2007-09-11
> **reckless2k2 said:**
> from ndiswrapper site:


Once everything works fine you can write the correct modprobe settings to load ndiswrapper automatically when the wlan0 interface is used, by running ndiswrapper -m Note that this doesn’t automatically load ndiswrapper module at boot time. If you want the module to be loaded automatically at boot time, you should configure your module setup, which depends on the distribution. Most distributions will load all modules listed in /etc/modules at boot time. Mandrake 10.x uses /etc/modprobe.preload. For them, you can add a line ndiswrapper in /etc/modules. For Fedora Core5, add a line alias wlan0 ndiswrapper in /etc/modprobe.conf.

If this does not work, instead add a line modprobe ndiswrapper in /etc/rc.d/rc.local

sorry i dont really understand what i have got to do, would you be able to give me a link to the original site?

---

### Post by reckless2k2 on 2007-09-12
sorry.....

> write the correct modprobe settings to load ndiswrapper automatically when the wlan0 interface is used, by running ndiswrapper -m

do the 

sudo ndiswrapper -m

> Note that this doesn&#8217;t automatically load ndiswrapper module at boot time. If you want the module to be loaded automatically at boot time, you should configure your module setup, which depends on the distribution. Most distributions will load all modules listed in /etc/modules at boot time.

sudo nano /etc/modules 

add:

ndiswrapper

then reboot.

---

### Post by markp1989 on 2007-09-12
> **reckless2k2 said:**
> sorry.....



do the 

sudo ndiswrapper -m



sudo nano /etc/modules 

add:

ndiswrapper

then reboot.

I did exactly what you said, and it still doesnt work, when i looked in "/etc/modules" ndiswrapper was in the list multiple times, so i deleted all except 1 and rebooted and it still fails to work, im nt sure if this is a problem with xubuntu, because it worked fine with ubuntu

---

### Post by reckless2k2 on 2007-09-12
do you mean to say that when you choose your gnome desktop it works fine and when you switch to xfce it does not? or is this a fresh install or across kernels?

---

### Post by markp1989 on 2007-09-12
> **reckless2k2 said:**
> do you mean to say that when you choose your gnome desktop it works fine and when you switch to xfce it does not? or is this a fresh install or across kernels?

i done a completly fresh install, but it worked fine with teh standard ubuntu install but when i formated and installed xubuntu it started to have problems

---

### Post by reckless2k2 on 2007-09-12
i don't know your situation but you could always just add additional DEs to your current install without blowing them away. i know it's totally off subject but it sounds like something simple is missing. i'd pull ndiswrapper and restart all over again. i've had a lot of success with ndis across various machines without the issues you're having. it sounds like there might've been an early slip up that's affecting all the way down the line. pop it out and pop it back in. hahaha. if so, read up on it real quick how to correctly remove all the stuff before trying again or you will be back int he same place. it should really only take a few minutes. 

as far as desktops, i have gnome, kde, fluxbox, xfce, and blackbox all in my available sessions. the only "biggies" are gnome and kde. you could pretty easy have xubuntu and ubuntu together especially since xfce is like a watered down gnome using all their librarys anyway. hahaha.

---

### Post by viciouslime on 2007-09-12
I know this isn't a whole lot of use right now, but just so that you know, when gutsy is released in october, ndiswrapper will be in the repositories :D

---

### Post by markp1989 on 2007-09-12
> **viciouslime said:**
> I know this isn't a whole lot of use right now, but just so that you know, when gutsy is released in october, ndiswrapper will be in the repositories :D

Thats good to know, october is not that far away

---

### Post by markp1989 on 2007-09-12
> **reckless2k2 said:**
> i don't know your situation but you could always just add additional DEs to your current install without blowing them away. i know it's totally off subject but it sounds like something simple is missing. i'd pull ndiswrapper and restart all over again. i've had a lot of success with ndis across various machines without the issues you're having. it sounds like there might've been an early slip up that's affecting all the way down the line. pop it out and pop it back in. hahaha. if so, read up on it real quick how to correctly remove all the stuff before trying again or you will be back int he same place. it should really only take a few minutes. 

as far as desktops, i have gnome, kde, fluxbox, xfce, and blackbox all in my available sessions. the only "biggies" are gnome and kde. you could pretty easy have xubuntu and ubuntu together especially since xfce is like a watered down gnome using all their librarys anyway. hahaha.

Considering its a fresh install would it make more sence for me to reformat and start again?

---

### Post by markp1989 on 2007-09-14
I decided to reinstall using the standard ubuntu disk, then i installed the ndiswrapper drivers, then i installed xubuntu-desktop and the driver works fine in gnome and xfce.

---

### Post by reckless2k2 on 2007-09-16
that's good to hear. i guess it sounds like something went a little screwy with the xfce ndis install.

---

### Post by grogger13 on 2008-02-18
i would say it was a gnome problem, i have ubuntu running and i have freshly installed several times on this same machine and never had a problem once my wifi was working with ndiswrapper.  On my current install however i have your exact problem, i think its something with just the install in general, but nothing else is wrong with my system(that i can notice) besides this.

Is there any way i could find out what is happening.

---

