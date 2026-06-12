---
title: "Help Me!! Major System Crash!"
date: 2007-09-16
forum: General Help
---

### Post by omgea404 on 2007-09-16
i installed the nvidia driver and it crashed X i can't get into my interface to restore the backups or anything... :confused:

what do i do?????? i don't want to reinstall Ubuntu again.

---

### Post by Wim Sturkenboom on 2007-09-16
Press <ctrl><alt><F1> once the system has booted and login. Edit /etc/X11/xorg.conf. Search for the section *device* and change the driver to *nv* or *vesa*.
You need root privileges to edit the file (so pefix the editor command with sudo).

I use vi, so *sudo **vi** /etc/X11/xorg.conf*. Replace vi withyour  editor of choice (nano is reasonably user friendly if you don't know how to use vi).

---

### Post by omgea404 on 2007-09-16
how do i login  root?

---

### Post by omgea404 on 2007-09-16
could i edit the file from the live cd?

---

### Post by omgea404 on 2007-09-16
how do i get root so i can edit the file from the LIVE CD? in the file system???

---

### Post by cubeist on 2007-09-16
Carefully reread the instructions somebody already provided!
> **Wim Sturkenboom said:**
> Press <ctrl><alt><F1> once the system has booted and login. Edit /etc/X11/xorg.conf. Search for the section *device* and change the driver to *nv* or *vesa*.
You need root privileges to edit the file (so pefix the editor command with sudo).

I use vi, so *sudo /etc/X11/xorg.conf*. Replace vi withyour  editor of choice (nano is reasonably user friendly if you don't know how to use vi).

so... the command you type after pressing <ctrl><alt><F1> would be something like "sudo gedit /etc/X11/xorg.conf"

and then I would recommend changing the device to "vesa" as that will almost certainly give you basic graphics...

---

### Post by arvevans on 2007-09-16
Open a terminal screen (Menu = Applications/terminal) and enter "man gksudo" followed by hitting ENTER.  This will tell you how to run commands at the root level without logging into the "root" ID on Ubuntu (Ubuntu has no "root" ID that is user accessible).
[CENTER]To scroll up or down in the "man pages" you need to use your 
keyboard's arrow keys.  
To quit viewing a man page you hit the "q" key[/CENTER]

If working from a command line interface, then enter "man sudo" to view the man page for the "sudo" command.
_._

---

### Post by diatribe on 2007-09-16
> **cubeist said:**
> Carefully reread the instructions somebody already provided!


so... the command you type after pressing <ctrl><alt><F1> would be something like "sudo gedit /etc/X11/xorg.conf"

and then I would recommend changing the device to "vesa" as that will almost certainly give you basic graphics...

gedit will not work from a command line, it needs a gui.

---

### Post by omgea404 on 2007-09-16
nano is to hard to work with... all it is a blank screen,

---

### Post by strabes on 2007-09-16
Look, it's not that complicated. ```
sudo nano /etc/X11/xorg.conf
```Make the changes you need, hit Ctrl+O to save, Ctrl+X to exit. Then type ```
sudo /etc/init.d/gdm restart
```

---

### Post by cubeist on 2007-09-16
> **diatribe said:**
> gedit will not work from a command line, it needs a gui.

Indeed! you are correct... good catch :)

---

### Post by omgea404 on 2007-09-16
ended up reinstalling...

is there any way i can backup all my stuff... so i can restore everything if this happens again?

---

### Post by Maestro23 on 2007-09-16
> **cubeist said:**
> Indeed! you are correct... good catch :)


> gksudo gedit

Launches it from command line.

---

