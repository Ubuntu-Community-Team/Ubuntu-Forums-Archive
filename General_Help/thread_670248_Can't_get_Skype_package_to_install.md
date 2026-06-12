---
title: "Can't get Skype package to install"
date: 2008-01-17
forum: General Help
---

### Post by nmgarnett on 2008-01-17
I'm a very new Ubuntu user... I've downloaded Skype having been prompted to use gdebi-gtk - it seems to download then I get an error mesage in the installer that says:
error: dependency is not satisfiable - libqt4-core.
Can anyone help?
Nick Garnett

---

### Post by linuxwizard on 2008-01-17
You need to install libqt4-core. Go to Synaptic > do a search for > libqt4-core > than install. Now try installing Skype again.

---

### Post by stchman on 2008-01-17
> **nmgarnett said:**
> I'm a very new Ubuntu user... I've downloaded Skype having been prompted to use gdebi-gtk - it seems to download then I get an error mesage in the installer that says:
error: dependency is not satisfiable - libqt4-core.
Can anyone help?
Nick Garnett

Skype is available in the Medibuntu repositories.  To install the Medibuntu repositories use the following info.

I am assuming you are running Gutsy.

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get update
sudo apt-get install skype

```


Hope this helps.

---

### Post by nmgarnett on 2008-01-18
Thanks guys, much appreciated
Nick Garnett

---

### Post by lgambett on 2008-01-18
Suggestion; do not install Skype from the Medibuntu repository. Try first to install Skype 2.0 beta for Linux (with video !) directly from [www.skype.com](www.skype.com). You will find the package for Ubuntu 7.04; it works perfectly also under 7.10 (Gutsy)

---

### Post by plucky on 2008-01-18
lgambett,

The version in the medibuntu repository is the latest version 2.0.0.27.

---

### Post by Christmas on 2008-01-18
You must first install libqt4-core:
```
sudo apt-get install libqt4-core
```
The other dependencies should be installed too, so check for:
```
sudo apt-get install libasound2 libc6 libgcc1 libqt4-core libqt4-gui libsigc++-2.0-0c2a libstdc++6 libx11-6
```
Make sure to have all the repositories enabled (I really don't know if these libraries are in main, universe or multiverse). Then try to install it again:
```
sudo dpkg -i skype-debian_1.4.0.118-1_i386.deb
```

---

