---
title: "Cant install properly"
date: 2008-03-09
forum: General Help
---

### Post by NeoScavenger on 2008-03-09
I'm dyslectic and beginner, so be patient :)

all was well after installation of the 7.10 Ubuntu, then after updating for the first time, when i try sudo apt-get install build-essential, i get this:

chlj@chlj:~$ sudo apt-get install build-essential
PassWord
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

I found a thread about this problem, but don't know what i can do from it to fix it, or if the problem is elsewhere.

here is a the sudo apt-get update:

chlj@chlj:~$ sudo apt-get update
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates Release              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release               
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Fetched 3B in 0s (7B/s)  
Reading package lists... Done

I DON'T want to reinstall :( plz help me!

---

### Post by mali2297 on 2008-03-09
Open Synaptic and go to "Settings" > "Repositories". If the CD repo is enabled, uncheck it. Then search for build-essential from Synaptic and try to install it.

---

### Post by NeoScavenger on 2008-03-09
> **mali2297 said:**
> Open Synaptic and go to "Settings" > "Repositories". If the CD repo is enabled, uncheck it. Then search for build-essential from Synaptic and try to install it.

None of the installable from CD/DVD is checked, when searching for build-essential here, i only found sbuild.

here is the tread whit the "similer" problem: [Here]("http://ubuntuforums.org/archive/index.php/t-516161.html")

anyway, as i instaled it last night, il try to reinstal ubuntu. Il post here again if the problem hits me again.

---

### Post by NeoScavenger on 2008-03-10
Seams to be working now, :)

---

