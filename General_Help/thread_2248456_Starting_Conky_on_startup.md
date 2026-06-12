---
title: "Starting Conky on startup"
date: 2014-10-15
forum: General Help
---

### Post by Comicalizard on 2014-10-15
Hey guys and gals, I recently switched from Windows 7 to Ubuntu 14.04 for good. However, I am a COMPLETE noob. I have looked at several guides and found numerous ways that may possibly work but I do not understand much of what is said in any of them. I have installed Conky and would like to run a specific theme upon startup. A helping hand would be more than appreciated right now!

---

### Post by ecophobia on 2014-10-15
If you have already install it correctly, you just need to follow instructions outlined here [http://nfolamp.wordpress.com/2012/09/07/starting-conky-during-startup-on-unity/](http://nfolamp.wordpress.com/2012/09/07/starting-conky-during-startup-on-unity/)

if you need to install it -->
[http://www.unixmen.com/install-conky-lua-ubuntu-14-0413-1013-04-debian-fedora-linux-mint-opensuse/](http://www.unixmen.com/install-conky-lua-ubuntu-14-0413-1013-04-debian-fedora-linux-mint-opensuse/)

Switching from Windows to Linux is brave if you don't know how to  work in command line [http://linuxcommand.org/](http://linuxcommand.org/)

Good luck

---

### Post by CantankRus on 2014-10-15
There are 2 ways to run conky.
**1)** Running just "**conky**" looks for and loads a config placed @ **~/.conkyrc**
If there is no config here it loads the included sample config @ **/etc/conky/conky.conf **
This is the normal way when running just the one conky. 

**2)** You can load a config from any location by using the **-c** option.
eg```
 conky -c [COLOR="#FF8C00"]/path/to/conky-config[/COLOR]
```
Specifying a config allows you to run more than one conky. The config can be named whatever you like.

--------------------------
For startup you use the **-p <secs>** conky option to pause the start of conky
to allow the window manager to load.
eg 
```
conky -p 15
```
or
```
conky -p 15 -c [COLOR="#FF8C00"]/path/to/conky-config[/COLOR]
```
[COLOR="#FF8C00"]Path to your config[/COLOR]. Right clicking on your config in the file browser and selecting copy will copy the correct path to the clipboard for pasting.

---

