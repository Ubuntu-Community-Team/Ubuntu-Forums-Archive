---
title: "Better package installer than QApt?"
date: 2021-06-06
forum: General Help
---

### Post by Tom_ZeCat on 2021-06-06
Most of the time, installing with a deb package and the QApt Package Installer included in Kubuntu is the bomb.  From within the GUI with Dolphin or one of the other file managers, you just right click on the file and choose to load it up with QApt.  The little install GUI comes up, and you click to let it do its thing.  Usually.  Every now and then, I get a deb package to which QApt responds "cannot satisfy dependencies."  So QApt tells you all the dependencies aren't there, but it doesn't identify for you what's missing.  This was the case with the latest VirtualBox deb file: 
virtualbox-6.1_6.1.22-144080_Ubuntu_eoan_amd64.deb

If QApt had some kind of feature to the effect of "click here to see missing dependencies," I could know that to hunt down and install to make the package work.  Either that or it could prompt in the install box something like, "Dependencies are not satisfied.  Do you wish QApt to download and install them?  Y/N."  Then if you chose Y, it would go get them for you.  This must be possible because it did something like that from the command line install.  In the terminal, I went to my Download folder and typed: 
sudo apt install ./virtualbox-6.1_6.1.22-144080_Ubuntu_eoan_amd64.deb

It installed and worked!  So for some reason from the command line, Kubuntu will go out and get whatever resources it lacks, but if you do it with its built-in QApt package installer, it can't do it.  

I do vaguely recall having some other GUI-based package installer for deb files, but I don't remember which one it was or if it was any better than QApt.  It's also been ages since I've used regular Ubuntu.  I've been in Kubuntu since 2012, and have stuck with it except for a couple of years when I went with Linux Mint/KDE.  

I might put regular Ubuntu into the VirtualBox just to re-familiarize myself with it.  

Anyway, if anyone knows of a better application than QApt that comes with Kubuntu, please speak up.

---

### Post by dragonfly41 on 2021-06-06
Gdebi perhaps?

[https://itsfoss.com/gdebi-default-ubuntu-software-center/](https://itsfoss.com/gdebi-default-ubuntu-software-center/)

---

### Post by ActionParsnip on 2021-06-06
I'd just use the command line if it works.
Shrug

---

