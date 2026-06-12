---
title: "PCManfm switch user command in Ubuntu 18.04"
date: 2019-07-02
forum: General Help
---

### Post by Robbyx on 2019-07-02
Because gksu does not work with 18.04 I am unable to switch to admin from within pcmanfm.  Does anyone know what the command line should be in the switch user advanced setting of  pcmanfm?

I have tried sudo -H but do not get a change of user.

---

### Post by GhX6GZMB on 2019-07-02
Do you need a full switch to root?
If you just need to modify a system file, use the "Tool" menu in PCManFM, "Open as Root"

---

### Post by Robbyx on 2019-07-02
Tool does not work for me. I click on the file name and then the open as root: the file does not open. No error messages appear.

---

### Post by GhX6GZMB on 2019-07-02
Wrong way round. Click on Tool, then Open as root. A new file window appears where you can browse for the file you need. This file window has root rights. When you find the file, right-click on it and choose the editor you want.

---

### Post by deadflowr on 2019-07-02
pcmanfm on regular ubuntu?
Maybe try
```
pcmanfm admin:///path/to/folder
like
pcmanfm admin:///usr/share/gnome-shell
```
if you want to edit a file
```
gedit admin:///path/to/file
like
gedit admin:///etc/fstab
```

It should give an option to toggle admin users if more than one exist.

---

### Post by Robbyx on 2019-07-02
> **ml9104 said:**
> Wrong way round. Click on Tool, then Open as root. A new file window appears where you can browse for the file you need. This file window has root rights. When you find the file, right-click on it and choose the editor you want.

A new file window does not open in my copy of pcmanfm. 

Looking at Edit-->preferences--->advanced it shows in my copy:

Terminal emulator: gnome-terminal
Switch user command: sudo -H

NB: 
gksu doesn't work any more in Ubuntu 18.04, to open a graphics program

Should I change any of the above?

---

### Post by GhX6GZMB on 2019-07-02
> [COLOR=#000000]A new file window does not open in my copy of pcmanfm. [/COLOR]

Strange. Normal behaviour after selecting "Tool" and "Open as root" is that you'll get a password window, after entering your PW the new file window will open.

---

### Post by Robbyx on 2019-07-03
Following your last comment I completely uninstalled pcmanfm and its dependencies. Then reinstalled just the qt version. The new installation opens the password window and so I now appear to have it working.  

I noticed no indicator that I was in root mode. In the past a red exclamation mark would appear in the toolbar for pcmanfm. Is there a root mode  indicator somewhere that  I have overlooked?

---

### Post by GhX6GZMB on 2019-07-03
On my PCManFM root file window there's a red bar at the bottom saying "root instance".

Mind you, I'm running Lubuntu 19.04, my PCManFM is 0.14.1

---

### Post by Robbyx on 2019-07-03
It seems to be working in that I can edit the fstab file, however, there is no red line or other visual indication that it is in root mode.

---

