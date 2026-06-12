---
title: "Syncing Palm Pilot"
date: 2007-11-20
forum: General Help
---

### Post by afderrick on 2007-11-20
Alright, so I have looked and not found any help at all.  I am trying to sync my Palm TX to my Ubuntu Gutsy OS.  I have tried using JPilot and Evolution and neither of them can find it.  JPilot tells me it has trouble binding.  When  I plug it in in terminal if I type lsusb I see that it recognizes the Palm and I have tried every default mount option it will allow me to, /dev/pilot, usb0, usb1 and a usbtty setting.  This is one of the last 2 things that is keeping me from going full linux and buying a new computer.

---

### Post by l33t_3lv3n_g33k on 2007-11-20
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)
 
I followed that link exactly for my Palm TX on Kubuntu Gusty and it worked flawlessly with JPilot.  
 
Added the udev rule and the visor module.  
 
Haven't tried it with Evolution, but the I don't use Gnome.
 
Would love it if someone managed to get all the PIM stuff to sync with Google Apps...

---

### Post by afderrick on 2007-11-20
Thanks, I will try it out tonight.  Now just to find a MS Money replacement.

---

### Post by afderrick on 2007-11-20
ok, so I followed the instructions and when I sync with either Evolution or JPilot I get an error of 

Device Error on Cradle (/dev/pilot)
Caught unhandled port error

---

### Post by hikaricore on 2007-11-20
> **afderrick said:**
> Thanks, I will try it out tonight.  Now just to find a MS Money replacement.

I'm not sure how advanced msmoney is, but you may want to see if this will fit your needs: [http://kmymoney2.sourceforge.net/index-home.html](http://kmymoney2.sourceforge.net/index-home.html)

I believe it's in the Ubuntu software repos as well.  ^_^

(and useable even if you're in a Gnome (default Ubuntu) environment instead of KDE.

---

### Post by afderrick on 2007-11-20
it is on my list of things to try.

---

### Post by l33t_3lv3n_g33k on 2007-11-21
> **afderrick said:**
> ok, so I followed the instructions and when I sync with either Evolution or JPilot I get an error of 
 
Device Error on Cradle (/dev/pilot)
Caught unhandled port error
 
Post your /etc/udev/rules.d/10-custom.rules and /etc/modules files.
 
And I second the KMyMoney2 suggestion.  Used it before I signed up for [Mint.com]("http://www.mint.com").  There's also a Gnome financial manager.  I think it's called gtkMoney or something of the sort...

---

### Post by afderrick on 2007-11-21
/etc/udev/rules.d/10-custom.rules

BUS=="usb", SYSFS{product}=="Palm Handheld*", KERNEL=="ttyUSB[13579]", NAME{ignore_remove}=="pilot", MODE=="0660"


I have changed a lot of the things trying it different ways.

/etc/modules 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
visor

---

### Post by l33t_3lv3n_g33k on 2007-11-22
That udev-rule looks like the one for Breezy Badger.  Are you using that version of Ubuntu?  You probably want to use this one:

```
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
```

Your modules file looks fine.

Don't forget to press the HotSync button on the Palm TX first, then the Sync button in JPilot

---

### Post by afderrick on 2007-11-23
I had that at once and had changed it around a bit.  So I copied and pasted what you had and the error JPilot is giving me is 

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot Invalid argument
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished


Not sure where to go from here.  Unless maybe I need to hit the buttons quicker?

---

