---
title: "Forgot how to install then run SimpleIDE tar"
date: 2014-07-07
forum: General Help
---

### Post by CARLYN on 2014-07-07
Hi, Ive istalled everthing , its a compiler and IDE but im not getting it right to  'run'  this is the final stage where all I want to do is run it for the first time ?

i type   [COLOR=#000080]*** ./simpleide  ***[/COLOR]in the directory and I get an error message 

[COLOR=#000080]mike@Doom:~/Documents/SimpleIDE-0-9-45$ ./simpleide 
bash: ./simpleide: No such file or directory
mike@Doom:~/Documents/SimpleIDE-0-9-45$ [/COLOR]




These are the instructions I am trying to follow, I hope the picture helps ?
**INSTALL**
**1. Unpack SimpleIDE with $ tar -xjf SimpleIDE-packagename.bz2**
**2. Change directory $ cd SimpleIDE-version.**
**3. Setup with $ sudo ./setup.sh $USER (or use root $ ./setup.sh username)**
**4. SimpleIDE workspace:**
** a. Remove ~/Documents/SimpleIDE to get a new copy of the workspace.**
** b. On first run ./simpleide will install ~/Documents/SimpleIDE files.**
**5. Previous users should remove the ~/.config/ParallaxInc/SimpleIDE.conf file.**
**RUN**
**1. Run with $ ./simpleide**
**2. SimpleIDE Compiler Properties should have:**
** a. Compiler /opt/parallax/bin**
** b. Loader path /opt/parallax/propeller-load**
** c. Workspace ~/Documents/SimpleIDE**
[B]3. SimpleIDE should start with the Welcome.c demo

[ATTACH=CONFIG]254546[/ATTACH]
[/B]

---

### Post by ubudog on 2014-07-07
Hi,

Are you sure you've run the setup.sh script?

---

### Post by CARLYN on 2014-07-07
yes i am sure

---

### Post by steeldriver on 2014-07-07
Based on your screenshot, there is no executable called simpleide in the toplevel install directory ./

In fact it looks like 'sudo setup.sh' installs everything to opt, and installs a wrapper script /usr/bin/simpleide (which should be on your PATH, so you should be able to run it by typing 'simpleide' - **without** the leading ./)

---

### Post by CARLYN on 2014-07-07
just waking up(late night)  thx I will try and report back !!

---

### Post by CARLYN on 2014-07-07
Many thanks to you steeldriver !

---

### Post by rigidigital on 2014-07-20
[[IMG]http://i1272.photobucket.com/albums/y390/mike_lynch2/Screenshotfrom2014-07-21074454_zps31498fcd.png[/IMG]](http://s1272.photobucket.com/user/mike_lynch2/media/Screenshotfrom2014-07-21074454_zps31498fcd.png.html)

Hi,
       Sorry Ive got the same story to tell. after formatting and reconfiguring my operating systems or reinstalling. You were right the first time when you told me to type    simpleide  and that worked.

Ive now repeated the steps and I am getting errors when I type simpleide      neeed your help please !

doom@doom-System-Product-Name ~/Documents/SimpleIDE-0-9-45 $ sudo ./setup.sh
[sudo] password for doom: 
Propeller GCC not installed
Installing Propeller GCC
Simple IDE not installed
Installing SimpleIDE

doom@doom-System-Product-Name ~/Documents/SimpleIDE-0-9-45 $ simpleide
/usr/bin/simpleide: 4: /usr/bin/simpleide: /opt/simpleide/bin/SimpleIDE: not found
doom@doom-System-Product-Name ~/Documents/SimpleIDE-0-9-45 $

---

