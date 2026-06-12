---
title: "Clean install of new release of ubuntu"
date: 2008-05-09
forum: General Help
---

### Post by talonstriker on 2008-05-09
I screwed up something pretty badly while upgrading to KDE4.  Now half the applications including Synaptic and KNetwork Manager don't work.  So I want to get rid of the KDE 3 version of Hardy and install the KDE 4 version.  How do I go about doing this?

On a side note, did any one else manage to break their OS 2 days after installing it? :P

And unrelatedly, it IS ok to uninstall Konquerer right (after installing Firefox)?  I have Dolphin so I don't see the point of having Konquerer, which IMO sucks in my limited experience.

---

### Post by gsmanners on 2008-05-09
It's not really a good idea to get rid of KDE 3, as KDE 4 isn't fully functional yet. You need to enable backports:

[https://help.ubuntu.com/community/UbuntuBackports#head-180fe9eb86a3434e066db173a2d276a8c003b913](https://help.ubuntu.com/community/UbuntuBackports#head-180fe9eb86a3434e066db173a2d276a8c003b913)

Then you need to use apt-get or Adept to install kubuntu-kde4-desktop.

Even if you don't use it, you should probably hang on to Konqueror as that has a lot of stuff that other applications in KDE use.

---

### Post by markharding557 on 2008-05-09
konqueror is a core component of kde and it may not function properly without it.
kde3 is very stable so if you want stability use that,kde4 on the other hand is still a work in progress.
to fix your system reboot your computer in recovery mode in the grub menu,you will be taken to a command line log in and 
> sudo apt-get remove --purge kubuntu-desktop
and when complete reinstall kubuntu-desktop
> sudo apt-get install kubuntu-desktop
as you attempted to install kde4 you may need to run
> sudo apt-get remove --purge  kubuntu-kde4-desktop

---

