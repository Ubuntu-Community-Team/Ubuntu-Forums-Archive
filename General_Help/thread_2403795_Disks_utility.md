---
title: "Disks utility"
date: 2018-10-16
forum: General Help
---

### Post by Phil Binner on 2018-10-16
Ubuntu 16.04 had a very useful utility called "Disks", which could be found by clicking the top left item in the launcher and displaying all programs.  This has never been included in XUbuntu, and does not seem to be present in Ubuntu 18.04.1.

I have tried to install it in XUbuntu by running sudo apt-get install disks, but although it asks for my password and them seems to run OK, no program then appears in the whiskers menu.  Is there any way I can get this program.

---

### Post by The Cog on 2018-10-16
I got as far as figuring out the application is called gnome-disks by running it on an ubuntu system and looking at ps -aux. I can launch it from the command line as gnome-disks. I can't find what package it's installed by. "apt search gnome-disks" returns nothing.

Got it (thanks, google). It's in package gnome-disk-utility.

---

### Post by Phil Binner on 2018-10-16
I have the disadvantage of being a gui man.  How do yo launch it from the command line.

Sorry, forget that.  I answered it myself by running Ubuntu in trial mode.

---

### Post by Holger_Gehrke on 2018-10-16
To find out what package an installed file belongs to, use```
dpkg-query -S complete-path-and-file-name
```

Holger

---

### Post by The Cog on 2018-10-16
To get a command line, look for a Terminal application of some sort.
To install the package: (sudo will want you to repeat your password but won't echo anything as you type)
```
sudo apt install gnome-disk-utility
```
To run it from command line:
```
gnome-disks
```

Thanks, Holger_Gehrke.

---

### Post by Phil Binner on 2018-10-16
THere it is.  Thanks.  The only thing I need to know now is how to change the prefix of this post to solved.

---

### Post by deadflowr on 2018-10-16
> The only thing I need to know now is how to change the prefix of this post to solved.
Click on Thread Tools up above the first post, it'll have an option to mark this thread as solved.

---

