---
title: "How do install open source programs?"
date: 2007-07-10
forum: General Help
---

### Post by StephanGFX on 2007-07-10
I downloaded winrar for linux, and i got these files:

[http://i79.imagethrust.com/i/1222305/screenshotrarfilebrowser.png]("http://i79.imagethrust.com/i/1222305/screenshotrarfilebrowser.png")

How do i compile these so i can install winrar?

---

### Post by aysiu on 2007-07-10
How about just installing *rar* and *unrar* from the repositories?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Happy_Man on 2007-07-10
I believe there is an app called unrar. Installing that gives you the ability to extract .rar files without needing WinRar for Linux. 

```
sudo apt-get install unrar
```


EDIT: NOOOO, Aysiu beat me to it! :p

---

### Post by StephanGFX on 2007-07-10
now when i open package manager it shows this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by aysiu on 2007-07-10
That's weird.

Close Synaptic Package Manager

Open  up [the terminal](http://www.psychocats.net/ubuntu/terminal) and paste in this command: ```
sudo dpkg --configure -a
``` Then try Synaptic again.

---

### Post by StephanGFX on 2007-07-10
now its telling me this lol

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by aysiu on 2007-07-10
Okay. That's weird.

Can you try pasting these commands in (keep Synaptic closed all the while)? ```
wget -c http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
sudo apt-get update
sudo dpkg --configure -a
``` If you get error messages, post them back here. Otherwise, pop into Synaptic again.

---

