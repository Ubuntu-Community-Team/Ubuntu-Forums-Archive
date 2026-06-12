---
title: "i'm trying to add a repository but it says a different one is broken"
date: 2019-08-22
forum: General Help
---

### Post by xeere on 2019-08-22
i type:
```
sudo add-apt-repository ppa:thomas-schiex/blender
```

i get:

```
Hit:1 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease
Hit:2 [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) bionic InRelease      
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                
Hit:4 [https://download.mono-project.com/repo/ubuntu](https://download.mono-project.com/repo/ubuntu) vs-bionic InRelease        
Hit:5 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                      
Hit:6 [http://ppa.launchpad.net/mikhailnov/pulseeffects/ubuntu](http://ppa.launchpad.net/mikhailnov/pulseeffects/ubuntu) bionic InRelease 
Hit:7 [http://ppa.launchpad.net/thomas-schiex/blender/ubuntu](http://ppa.launchpad.net/thomas-schiex/blender/ubuntu) bionic InRelease   
Ign:8 [http://ppa.launchpad.net/wallch/wallch-daily/ubuntu](http://ppa.launchpad.net/wallch/wallch-daily/ubuntu) bionic InRelease     
Err:9 [http://ppa.launchpad.net/wallch/wallch-daily/ubuntu](http://ppa.launchpad.net/wallch/wallch-daily/ubuntu) bionic Release       
  404  Not Found [IP: 91.189.95.83 80]
Hit:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done 
E: The repository 'http://ppa.launchpad.net/wallch/wallch-daily/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

wallch is a wallpaper software which i have removed from my computer and i do not want it

---

### Post by ajgreeny on 2019-08-22
Remove the [http://ppa.launchpad.net/wallch/wallch-daily/ubuntu](http://ppa.launchpad.net/wallch/wallch-daily/ubuntu) ppa from the system then run ***sudo apt update*** to see what happens; it should run without a problem, though that ppa has already been ignored and updating should not be a problem even when it's enabled.

Note also that the blender ppa already seems to be enabled and working.

---

### Post by oldos2er on 2019-08-22
Looks like that PPA hasn't been updated in five years.

---

### Post by xeere on 2019-08-22
how to do this?

---

### Post by ajgreeny on 2019-08-22
> **xeere said:**
> how to do this?
How to do what?

---

### Post by xeere on 2019-08-22
nvm it worked thanks!

---

### Post by ajgreeny on 2019-08-22
Great news! 
Please tell us what it was that worked for you.
It is a great help to other users searching the forum.

---

