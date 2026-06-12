---
title: "[SOLVED] Wifi-radar quit"
date: 2007-07-04
forum: General Help
---

### Post by eppoh on 2007-07-04
Put this on the Network forum- but no answer

Suddenly Wifi Radar will no longer run on my laptop. Everything else works, the card, etc... I can connect with the Network Configuration app, but when I start Wifi Radar, it calls up the admin password, I enter it, then...nothing.

Well, it acts like it wants to run but doesn't. No error messages.

I have removed and reinstalled it with no result.

As much as I travel I really need it to work.


thanks for any help

---

### Post by ubuntu.daemon on 2007-07-04
try using wifi-radar out of a terminal and post what code you get back

---

### Post by yopnono on 2007-07-04
Try this:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by fragos on 2007-07-04
A liitle more info would help.  Which Ubuntu release are you running and for how long was your system working properly?  7.04 comes preinstalled with gnome network manager.  If both wifi-radar and gnome network manager are installed they will interfere with each other.

---

### Post by eppoh on 2007-07-07
> **fragos said:**
> A liitle more info would help.  Which Ubuntu release are you running and for how long was your system working properly?  7.04 comes preinstalled with gnome network manager.  If both wifi-radar and gnome network manager are installed they will interfere with each other.

I'm using kernel 2.6.17.-11 ( believe that is edgy?) Has been working fine for at least six months, with Network manager installed.

I tried running from a terminal, now I get

File "/usr/sbin/wifi-radar", line 1414, in ?
auto_profile_order = auto profile_order.split ( ',' )
Attribute Error: 'list' object has no attribute 'split'

I am not sure what would happen if I uninstall Network Manager. Don't want to lose my connection, and be unable to reinstall it.

---

### Post by fragos on 2007-07-07
Edgy it is.  That tells me that the only network manager you have will be what you installed.  It appears that there is a comma in your profile that's causing the problem.  It's probably in a recently added hot spot.  If you can run wifi-radar, check out the configuration settings with an eye toward a comma.  If not, delete your configuration file and when wifi-radar is started next time you can start configuration from a clean install.  I'm not running wifi-radar now so I can't direct you to the configuration file other than to say it probably a hidden file in your home directory.  Open your home directory with nautilus and do Ctrl-h.  Hidden files and directorys all starrt with ".".

---

### Post by eppoh on 2007-07-08
Can't run wifi-radar.
Can't find that config file with the profile. 
anyone know what it is named and where it is located?

Edit: foudn file but could not delete or edit. Tried sudo gedit and even logging in as root. Can not log in as root.
Anyway it is solved. I did a Remove Completely with Synaptic then reinstalled. It works now.

---

