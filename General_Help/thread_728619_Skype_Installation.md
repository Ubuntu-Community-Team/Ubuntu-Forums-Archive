---
title: "Skype Installation"
date: 2008-03-19
forum: General Help
---

### Post by mlyons16 on 2008-03-19
Hey, 

I'm trying to install skype via the repositories, so I add: 

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

I reload,

and then search for skype package and mark for installation.. problem is that it depends on the package: 

libqt4-core... but it doesnt install so i hit a roadblock.... help.

---

### Post by itix on 2008-03-19
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

download the 7.04 package here. It worked for me and the Gdebi package installer builds the dependencies itself.

---

### Post by mikewhatever on 2008-03-19
You can grab libqt4-core from here --> [http://packages.ubuntu.com/gutsy/i386/libqt4-core/download](http://packages.ubuntu.com/gutsy/i386/libqt4-core/download).
However, it's a good idea to check your repositories, because if you could not download it from Synaptic, something must be wrong. [https://help.ubuntu.com/community/Repositories?highlight=%28repositories%29](https://help.ubuntu.com/community/Repositories?highlight=%28repositories%29)

---

### Post by vishzilla on 2008-03-19
I would recommend adding the Medibuntu repos
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install skype
```
Before this, go to Synaptic and search for Skype, if its installed kindly completely remove it

---

