---
title: "rar files"
date: 2007-02-07
forum: General Help
---

### Post by bluestatic_91 on 2007-02-07
Okay...I got some rar files and I can't extract the files from them. please explain to me how I take files out of a .rar file if you can. Thanks!

---

### Post by rai4shu2 on 2007-02-07
Install rar or unrar using Synaptic or Adept, then double-click on the rar file.

---

### Post by Maestro23 on 2007-02-07
> **bluestatic_91 said:**
> Okay...I got some rar files and I can't extract the files from them. please explain to me how I take files out of a .rar file if you can. Thanks!

Go into Synaptic and search for "unrar". Read about it and install.

---

### Post by bluestatic_91 on 2007-02-07
when I search for unrar, no results come.

---

### Post by ~LoKe on 2007-02-07
Do you have the multiverse repository uncommented?

---

### Post by Maestro23 on 2007-02-07
> **~LoKe said:**
> Do you have the multiverse repository uncommented?

Loke beat me to it.  Use you favorite editor and make sure that is active in your /etc/apt/sources.list

#sudo nano /etc/apt/sources.list

Just delete the "#" in front of the multiverse repo's. Then Save.

Then...

#sudo aptitude update

---

### Post by bodhi.zazen on 2007-02-07
[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

### Post by nalioth on 2007-02-07
> **Maestro23 said:**
> Loke beat me to it.  Use you favorite editor and make sure that is active in your /etc/apt/sources.list

#sudo nano /etc/apt/sources.list

Just delete the "#" in front of the multiverse repo's. Then Save.
Maestro23 is on the right track.  You'll need to find the lines with 'universe' in them and ADD the word 'multiverse' after them.  An easy way is to use gedit to 'find and replace' "universe" with "universe multiverse" and update your apt/synaptic.

Like maestro32 says, remove the # from the front of those lines, too.

---

