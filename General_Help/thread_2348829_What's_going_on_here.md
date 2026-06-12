---
title: "What's going on here?"
date: 2017-01-07
forum: General Help
---

### Post by qe2eqe on 2017-01-07
When I click the shopping bag icon for "Ubuntu Software", and search.... something is wrong? It didn't find frozen bubble and it's telling me that dosbox is non-free... and here's extra stuff on the package names. What is happening, exactly, and how? (screenshot attached)

I'm running a fresh net install where I did the basic system first and apt-get install ubuntu-desktop after. My software sources show that main, universe, and multiverse are enabled, so my only possible explanation isn't explaining anything. Halp? Outside of enabling the microcode drivers from the additional drivers dialog, and downloading a google chrome .deb in firefox, I did everything else via command line. Here's my bash history:

```
    1  cat /proc/cpuinfo 
    2  cat /proc/cpuinfo  | less
    3  lscpu
    4  lm_sensors
    5  reboo
    6  reboot
    7  sudo apt-get install desktop
    8  apt-cache search desktop
    9  apt-cache search desktop | grep ubuntu
   10  sudo apt-get install ubuntu-desktop
   11  sudo apt-get update
   12  sudo apt-get upgrade
   13  sudo apt-get install ubuntu-desktop
   14  sudo apt-get install google-chrome
   15  ping google.com                           ## opening the .deb for google chrome in synaptic told me that no network connection was found. This ping was successful, that was some kind of bug.
   16  sudo dpkg -i /home/john/Downloads/google-chrome-stable_current_amd64               ## experiencing something like [http://askubuntu.com/questions/761210/16-04-cannot-install-anything-from-ubuntu-software-center](http://askubuntu.com/questions/761210/16-04-cannot-install-anything-from-ubuntu-software-center) , only it wouldn't even show me 'installing' I'd click the install button, nothing happened. So I worked around it with dpgkg....

   17  sudo dpkg -i /home/john/Downloads/google-chrome-stable_current_amd64.deb    #tab complete picked up the folder because I extracted the deb like a n00b
   18  hdparm /dev/sda
   19  sudo hdparm -t /dev/sda
   20  sudo apt-get install lm-sensors
   21  sudo apt-get install -f                     # I guess dpkg left some unresolved dependencies
   22  sudo apt-get install lm-sensors
   23  google-chrome
   24  sudo apt-get install google-chrome
   25  firefox
   26  sudo apt-get install amd64-microcode 
   27  sudo reboot
   28  apt-get install lm-sensors
   29  sensors
   30  sudo apt-get install 
   31  sudo apt-get instll sysnbench
   32  sudo apt-get install sysnbench
   33  sudo apt-get install sysbench       #success!
   34  sysbench --test=cpu run
   35  sysbench --test=cpu run
   36  sudo apt-get update && sudo apt-get install gnome-panel gnome-flashback gnome-session-flashback indicator-applet-appmenu
   37  apt-cache search wikidpad
   38  apt-cache search 
   39  sudo apt-get install python
   40  apt-cache search widget | grep wx
   41  sudo apt-get install wx-common
   42  sudo apt-get install python-wxgtk3.0
   43  python /home/john/wikidpad/WikidPad.py
```

---

### Post by howefield on 2017-01-07
Did you get any errors when updating ?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

The "non free" dosbox package is likely a snap package.

---

### Post by qe2eqe on 2017-01-07
> **howefield said:**
> Did you get any errors when updating ?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

The "non free" dosbox package is likely a snap package.


No errors. I think, maybe I had an apport event with "Gnome Software" on the first boot but I'm not sure... I don't remember if I rebooted after or whatnot. I'm just trying to figure out if this is user error or a bug (or maybe both).
```

john@phenom:~$ sudo apt-get update
[sudo] password for john: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                  
Hit:3 http://us.archive.ubuntu.com/ubuntu yakkety InRelease                 
Get:4 http://us.archive.ubuntu.com/ubuntu yakkety-updates InRelease [102 kB]
Get:5 http://security.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]        
Get:7 http://us.archive.ubuntu.com/ubuntu yakkety-backports InRelease [102 kB]                 
Get:8 http://us.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 Packages [144 kB]       
Get:9 http://us.archive.ubuntu.com/ubuntu yakkety-updates/main i386 Packages [142 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu yakkety-updates/main amd64 DEP-11 Metadata [111 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu yakkety-updates/main DEP-11 64x64 Icons [60.3 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu yakkety-updates/universe amd64 DEP-11 Metadata [83.3 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu yakkety-updates/universe DEP-11 64x64 Icons [94.2 kB]      
Get:14 http://us.archive.ubuntu.com/ubuntu yakkety-updates/multiverse amd64 DEP-11 Metadata [212 B]
Get:15 http://us.archive.ubuntu.com/ubuntu yakkety-backports/main amd64 DEP-11 Metadata [212 B]
Get:16 http://us.archive.ubuntu.com/ubuntu yakkety-backports/universe amd64 DEP-11 Metadata [216 B]
Get:17 http://us.archive.ubuntu.com/ubuntu yakkety-backports/multiverse amd64 DEP-11 Metadata [216 B]
Get:18 http://security.ubuntu.com/ubuntu yakkety-security/main amd64 DEP-11 Metadata [8,272 B]     
Get:19 http://security.ubuntu.com/ubuntu yakkety-security/universe amd64 DEP-11 Metadata [2,188 B]
Get:20 http://security.ubuntu.com/ubuntu yakkety-security/multiverse amd64 DEP-11 Metadata [212 B]
Fetched 952 kB in 1s (812 kB/s)     
Reading package lists... Done
john@phenom:~$ sudo apt-get upgrade > lol.tx
john@phenom:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by howefield on 2017-01-08
> **qe2eqe said:**
> .... I'm just trying to figure out if this is user error or a bug (or maybe both). 

Both issues are not user errors, Ubuntu Software is new and not yet completely operational as far as I can tell.

There are a few valid applications that won't display. There are a couple of workarounds, firstly if you are not afraid of the command line you can search for and install packages that way.. eg

```
apt-cache search frozen-bubble
```
```
sudo apt install frozen-bubble
```

or if you want a GUI way of finding software, install an alternative package manager such as synaptic

```
sudo apt install synaptic
```

Dosbox is free, it is marked as non free because it is a snap package and needs an SSO login to install it., except the Ubuntu Software cannot install snaps as yet, confused ? 

As above you can install the dosbox deb package via the command line or synaptic.

```
sudo apt install dosbox
```

---

