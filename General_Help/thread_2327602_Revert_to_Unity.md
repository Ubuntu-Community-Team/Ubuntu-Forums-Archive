---
title: "Revert to Unity"
date: 2016-06-12
forum: General Help
---

### Post by alex549 on 2016-06-12
I tried install ubuntu-gnome-desktop, but want to go back to using Unity now.  I selected Unity at login, but now my desktop is black, I cannot right click, and many of my programs are missing from the Unity search.  I used "sudo apt-get remove ubuntu-gnome-desktop" to uninstall.  Any thoughts?  THanks

---

### Post by X-RED_Tech on 2016-06-12
You can try to reinstall ubuntu-desktop but I'm not sure if you need to remove some of what was installed before. Removing the metapackage won't probably remove nor undo what gnome desktop installed or changed.

---

### Post by alex549 on 2016-06-12
I just tried and that didn't help.  I guess I really messed up the desktop : /

---

### Post by Frogs Hair on 2016-06-12
Hello and Welcome !

If you still have terminal access try the following and reboot . If the terminal is missing you can execute the command from TTY by pressing F1. 

 ```
sudo apt-get install --reinstall ubuntu-desktop  
```

---

### Post by alex549 on 2016-06-12
THanks for the tip!  Pretty much everything is working, I see the side panel and what not, I just cannot interact with the desktop or change the photo.  I suppose it's not a big deal.

---

### Post by deadflowr on 2016-06-12
Open a terminal and try this command:
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
Unity has the file manager handle the desktop. Gnome does not.
The command resets it so that it does.
Hope it helps.

---

### Post by alex549 on 2016-06-12
You're a hero!  Thank you very much

---

### Post by Rex Bouwense on 2016-06-12
> **deadflowr said:**
> Open a terminal and try this command:
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
Unity has the file manager handle the desktop. Gnome does not.
The command resets it so that it does.
Hope it helps.
Thank you.  This saved us a lot of time.  I learned something today so the day has not been wasted.

---

