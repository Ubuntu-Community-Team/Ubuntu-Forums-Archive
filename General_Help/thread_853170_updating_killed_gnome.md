---
title: "updating killed gnome"
date: 2008-07-08
forum: General Help
---

### Post by mriedel on 2008-07-08
I recently updated my laptop (through the update manager that appears as a tray icon when updates can be installed iirc). After a while it notified me that some updated packages could not be fetched (not mentioning a reason) and whether I want to continue, not mentioning the possibility of damage to the system, let alone the fact that some packages obviously depended on one or more of those which could not be fetched.

After the required restart, I was left with gnome starting up into a white screen and staying there. Can't say whether it's the login manager or the desktop itself, had autologin turned on.

Running apt-get update and apt-get upgrade didn't help, neither did searching for broken packages with aptitude.

So basically:
- How can I fix this?
- Someone should change the notification window to something more scary

---

### Post by Rick Myers on 2008-07-08
I'd give these a whirl. 

Remove packages that are currently stored on your machine for installation and delete unused packages by;
sudo apt-get clean
sudo apt-get autoremove

Note: The -f parameter in the following will "Attempt to correct a system with broken dependencies in place". This is an attempt to repair the installed package. It may be necessary to "remove" to delete corrupt files prior to "install" - sometimes repairs don't work.

Attempt reinstall of GDM;
sudo apt-get -f install gdm
or
sudo apt-get remove gdm
sudo apt-get install gdm

Try reinstalling Gnome;
sudo apt-get -f install gnome
or
sudo apt-get remove gnome
sudo apt-get install gnome

Try reinstalling the whole desktop system;
sudo apt-get -f install ubuntu-desktop
or
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop


Of course, there's backing up the data and a complete reinstall from the CD.

Good Luck!

---

### Post by mriedel on 2008-07-09
thanks for your ideas.

> **Rick Myers said:**
> 
sudo apt-get clean
sudo apt-get autoremove

Attempt reinstall of GDM;
sudo apt-get -f install gdm
or
sudo apt-get remove gdm
sudo apt-get install gdm

Try reinstalling Gnome;
sudo apt-get -f install gnome
or
sudo apt-get remove gnome
sudo apt-get install gnome

Try reinstalling the whole desktop system;
sudo apt-get -f install ubuntu-desktop
or
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

didn't work though.

following some dependency error messages, I ended up with:

*sudo apt-get install -f gnome-desktop-environment*

blah blah depends on gnome-keyring-manager blah blah

*sudo apt-get install -f gnome-keyring-manager*

blah blah blah
E: gnome-keyring-manager has no installation candidate

---

### Post by mriedel on 2008-07-10
bump

---

### Post by mriedel on 2008-07-11
bump

---

### Post by mriedel on 2008-07-13
bump

---

### Post by mriedel on 2008-07-15
bump

---

