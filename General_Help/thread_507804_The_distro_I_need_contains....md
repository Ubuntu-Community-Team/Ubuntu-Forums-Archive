---
title: "The distro I need contains..."
date: 2007-07-23
forum: General Help
---

### Post by sara.meskar on 2007-07-23
Hi you all

I need a distro with VLC, WINE and a good version of OPEN OFFICE.

These softwares have to be a part of the distro - I am an absolute newbie and if I find a distro like this I will surely install it and say goodbye to windows

---

### Post by scrooge_74 on 2007-07-23
download Ubuntu then

---

### Post by stchman on 2007-07-23
> **sara.meskar said:**
> Hi you all

I need a distro with VLC, WINE and a good version of OPEN OFFICE.

These softwares have to be a part of the distro - I am an absolute newbie and if I find a distro like this I will surely install it and say goodbye to windows

Pretty much any distro has those and yes Ubuntu has those.

VLC and WINE are not installed by default in Ubuntu but can be easily installed through Synaptic.  OO2.2 comes on the LiveCD.

---

### Post by Scheater5 on 2007-07-23
All of that is included in Ubuntu, but only Open Office is installed "out of the box."  You can install wine and VLC with a simple command on an internet-enabled Ubuntu install.

```
sudo aptitude update && sudo aptitude install wine VLC
```

Wine and VLC are in the Universe repository, and a couple of things you might want for VLC are in the Multiverse (like the codec for playing dvds), so you'll want to make sure you have them enabled.  If you don't know how to do that, fire up Synaptic Package Manager and under "Settings" you will find "Repositories," and there you can enable them.  Be forewarned, many things in the Universe and Multiverse are illegal in several countries including the US.

---

### Post by stchman on 2007-07-23
> **Scheater5 said:**
> All of that is included in Ubuntu, but only Open Office is installed "out of the box."  You can install wine and VLC with a simple command on an internet-enabled Ubuntu install.

```
sudo aptitude update && sudo aptitude install wine VLC
```

Wine and VLC are in the Universe repository, and a couple of things you might want for VLC are in the Multiverse (like the codec for playing dvds), so you'll want to make sure you have them enabled.  If you don't know how to do that, fire up Synaptic Package Manager and under "Settings" you will find "Repositories," and there you can enable them.  Be forewarned, many things in the Universe and Multiverse are illegal in several countries including the US.

WINE is not in the repositories, wine.budgetdedicated.com must be added.

[http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

---

### Post by Scheater5 on 2007-07-23
Wine is in fact in the Universe.  It's just not the most cutting edge version.

[https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")

---

### Post by sara.meskar on 2007-07-24
I would like something "ready to use", I mean, they're very important for me and I am a newbie... If I have to install something, it should be something inessential! I mean, something I don't miss if something goes wrong!!!

---

### Post by Scheater5 on 2007-07-24
My friend, you have to keep in mind that an operating system itself is not what makes your computer useful.  Have you ever seen a fresh install of Windows?  At least Linux distros give you more than Notepad and Calculator.  Installing software in Ubuntu is quick and painless thanks to the repository system and the beauty of APT, and I highly recommend you get acquainted with this system.  If you cannot handle adding a repository and copying a few commands into a terminal, you are not going to be able to handle configuring Wine - and why exactly do you need VLC as opposed to Totem?

---

