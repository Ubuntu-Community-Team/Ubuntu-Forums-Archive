---
title: "Some mishaps involving the startup load screen and GNOME menus"
date: 2007-08-31
forum: General Help
---

### Post by SomeLuser on 2007-08-31
I wanted to try KDE, and didn't want to fork over another CD, so I installed the package kubuntu-desktop, which installed all of its 'dependencies' that I didn't have already, and I logged out of GNOME when that was done. I logged into my new KDE desktop and didn't like it at all. I logged out, logged back into the GNOME Ubuntu desktop and cleaned out my menus of the KDE app launchers (I put them all in a hidden menu in case I want them later). Then I shut down the computer, came back later and was greeted by the Kubuntu loading screen. I prefer the orange one and don't like KDE, so I sudo-apt-get-removed kubuntu-desktop. I rebooted, expecting my  customary orange loadbar, however the blue one was again the exclusive ruler of the graphical boot. I would like to remedy this.

As for the menus, it seems that while I was KDetoxing my applications menu I accidentally dragged the 'Internet' submenu into the 'Other' submenu. This killed about half of the launchers in the Internet Menu, and I want them back. How do I go about this?

Missing launchers include Ekiga Softphone, Epiphany and Konqueror Web Browsers, Gaim Internet Messenger, NmapFE, and probably more.

This isn't my only problem with the menus; it seems that about half the time I put one launcher in another menu, I have to close the menu editor and open it again to see the result. Otherwise it appears to have failed to copy to that menu (otherwise as in if you leave the menu editor open).

If you have answers to one or more of the problems I described, I would appreciate your input.

---

### Post by dje on 2007-08-31
Have you tried (to get the splash back):
sudo apt-get install ubuntu-desktop
or
sudo apt-get install usplash-theme-ubuntu

As for the missing menu items have you tried:
System >> Preferences >> Main menu and ticked the shortcuts you want

---

### Post by SomeLuser on 2007-08-31
> **dje said:**
> 
As for the missing menu items have you tried:
System >> Preferences >> Main menu and ticked the shortcuts you want


That launcher massacre happened IN main menu (the thing at system>preferences>main menu), unfortunately...

---

### Post by dje on 2007-08-31
can you just make a new internet menu and put new launchers in it? By clicking new item you can create a new launcher, eg the command for firefox would just be firefox. Experiment with possible commands for each launcher if you dont know them until you find one that works, hth

btw, did you get the ubuntu splash back?

---

### Post by SomeLuser on 2007-08-31
I did indeed get the splash screen back, after eventually using the tips at the end of the first post of [this Ubuntu forum thread]("http://ubuntuforums.org/showthread.php?t=205002").

```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by strabes on 2007-09-01
You really really should have used aptitude to install and remove kubuntu-desktop. I guess you could try reinstalling it with aptitude and then re-removing it; I don't know if that will actually work but it's worth a shot.

---

