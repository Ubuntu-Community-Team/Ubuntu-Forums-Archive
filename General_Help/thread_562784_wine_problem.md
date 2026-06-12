---
title: "wine problem"
date: 2007-09-29
forum: General Help
---

### Post by The Fallen on 2007-09-29
t[B][SIZE="2"][SIZE="3"]his problem occurred after installing ruby browser ( as i think ) any way the problem is : 

wine & win doors was installed and working good suddenly wine is no longer working ( and so Realpayer & Flashplayer ) and when trying to reinstall it i got this messege :[/SIZE][/SIZE][/B]


 
```
sudo apt-get install wine

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: lib32asound2 (> 1.0.12) but it is not going to be installed
E: Broken packages
```

[B][SIZE="3"]and when i tried to install the missing packages manually i have failed because it was nested and i don't know with which package i have to begin and with which i have to end:(:(:(:(

I'm using 7.04 64bit distro ............... so please help ( and try to tell me how to fix realpayer and flash player )

with my regareds[/SIZE][/B]

---

### Post by The Fallen on 2007-09-30
[CENTER][SIZE="3"][FONT="Garamond"]**Hey guys I'm still waiting**[/FONT][/SIZE][/CENTER]

---

### Post by Martje_001 on 2007-09-30
Start synaptic and look if it finds any conflicts. If not do:
```
sudo apt-get update
sudo apt-get install wine
```

---

