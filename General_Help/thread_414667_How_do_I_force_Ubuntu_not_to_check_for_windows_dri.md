---
title: "How do I force Ubuntu not to check for windows drives?"
date: 2007-04-20
forum: General Help
---

### Post by itchanddino on 2007-04-20
When I install Ubuntu I unplug my windows drive so that it won't even touch it.  So after the install Ubuntu is running fine, so I reconnected my windows drive.  However, now when I use Ubuntu that drive shows up in Nautilus, although it is not mounted.  I thought it was my Ubuntu drive at first, so I clicked it and it mounted my windows drive.  How do I stop Ubuntu from detecting hard drives I don't want it to?  It never did this in Dapper of Edgy.  Thanks!

---

### Post by Compyx on 2007-04-20
The way I would do it is to comment out the offending drives/partitions in /etc/fstab. But if I'm not mistaken you should be able to tell Nautilus not to auto-mount these drives through a menu-driven configuration. Since I've used Gentoo for years, I'm used to configuring everything by hand-editing config-files, so I'm not sure how to do this via a GUI.

---

### Post by uid0 on 2007-04-20
Nautilus isn't auto-mounting the drives, but they show up in the list of available volumes.   I did a little poking around and it looks like you can tweak HAL to make it ignore certain volumes. 

If you start up the Device manager and navigate down to your IDE/SCSI controller you will see all the drives attached to the controller and all the volumes on each drive.  Click on the Advanced tab and you will see all of the options for that particular volume.  

One of the keys there is called "volume.ignore", which is normally set to "false".  I believe if you set that to "true" the volume in question will not show up in Nautilus any more.  Unfortunately, the device manager is read-only, so I'm not sure how to actually tweak the setting.

---

### Post by itchanddino on 2007-04-20
I've still yet to fix this, anyone have any more ideas?

---

### Post by s9am_me on 2007-04-20
hmm I installed Feisty last night and experienced the same thing.  When I rebooted after installation, my windows disk was mounted automatically.  Something that didn't happen in Edgy.  It won't let me unmount either.  Kind of annoying, I like my desktop icon free and clean

---

### Post by Compyx on 2007-04-20
I found out that you can tell Nautilus/Gnome to show or not show mounted volumes on your desktop by editing a key with gconf-editor (run from a shell as normal user, not root):
```
gconf-editor "/apps/nautilus/desktop" &
```
When you uncheck the box with the label 'volumes_visible', the mounted volumes disappear from your desktop.

I still think that you'll have to edit /etc/fstab to not mount drives automatically, by commenting out the entries or by adding the keyword 'noauto' to the <options> column.
I can't show you how such an entry would then look like, since I don't use Windows and haven't done so for at least 5 years. Maybe I can get one of my M$-using family members to allow me to install Feisty on their computers so I can check how it would be done ;)

---

### Post by itchanddino on 2007-04-20
I'd think it would be the same way you would hide any other hard drive from Ubuntu.  And it's not that it's appearing on the desktop, just in the Nautilus browser.

---

