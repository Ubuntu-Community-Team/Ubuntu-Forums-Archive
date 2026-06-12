---
title: "System, Preferences, Removable Drives &amp; Media Preferences not found under preference"
date: 2008-03-21
forum: General Help
---

### Post by nelio2k on 2008-03-21
Hi all,

I've been running my desktop with Ubuntu gutsy only for a while now. I just realized that under system -> preference -> Removable Drives & Media Preferences is not there, whereas it is there for my laptop that is also running gutsy. 

I've manually tried to call gnome-volume-properties in the run command box but no avail, whereas in my laptop it shows up. Is there a package I'm missing or something? How come it's not there??

Thanks

---

### Post by plucky on 2008-03-21
Right Click on **System** Select **Edit Menus** Navigate to System > Preferences > Removable Drives and Media and make sure box is ticked.

Good Luck

---

### Post by nelio2k on 2008-03-21
There is no "Removable Drives and Media" that is not checked. As a result, even running gnome-volume-properties is not doing anything.

---

### Post by chrisccoulson on 2008-03-21
Try:
```
sudo apt-get install gnome-volume-manager
```
or, if it's already installed:
```
sudo apt-get install --reinstall gnome-volume-manager
```

---

### Post by nelio2k on 2008-03-21
Thanks. It works...... somehow the package wasn't there... it's weird...

---

