---
title: "Vuze not showing anything other than the name and a blue window"
date: 2015-12-11
forum: General Help
---

### Post by Robbyx on 2015-12-11
The torrent client Vuze opens only to show the name at the top and a pure blue screen in the rest of the window. I have openjdk java 7 runtime installed.  Any ideas how I correct Vuze's startup failure?

Running it from the terminal in Ubuntugnome 14.04 AMD 64,  this is what  I see:

> robins@robins-desktop:~$ vuze
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.17.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.8.2.jar ; file:/home/robins/
UIFunctions/ImageLoad took 0ms
new shell took 150ms
new shell setup took 76ms
skinlisteners init took 0ms
skin init took 75ms
MainMenu init took 100ms
createWindow init took 0ms
skin layout took 0ms
pre skin widgets init took 26ms
hooks init took 0ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@6222adfd
skin widgets (1/2) init took 125ms
skin widgets init took 76ms
pre SWTInstance init took 0ms
Init Core Columns took 76ms
SWTInstance init took 0ms
shell.layout took 50ms
---------SHOWN AT 1449868231958;855ms
Killed
robins@robins-desktop:~$ 


---

### Post by QDR06VV9 on 2015-12-11
I would first uninstall it..
```
$ sudo apt-get remove azureus

```
How to install Vuze 5.5.0 on Ubuntu 14.04, Linux Mint 17.1, Linux Mint 17, Pinguy OS 14.04, Elementary OS 0.3, Deepin 2014,
 Peppermint Five, LXLE 14.04 and Linux Lite 2.0:
```
$ sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu trusty-getdeb apps" >> /etc/apt/sources.list'

$ wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -


$ sudo apt-get update


$ sudo apt-get install azureus
```
**Credit Here:**
[http://linuxg.net/how-to-install-vuze-5-5-0-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/](http://linuxg.net/how-to-install-vuze-5-5-0-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/)

---

### Post by Robbyx on 2015-12-11
Thank you. Following your post it is now working.

---

### Post by QDR06VV9 on 2015-12-11
Good Job>>:D
Kind Regards

---

