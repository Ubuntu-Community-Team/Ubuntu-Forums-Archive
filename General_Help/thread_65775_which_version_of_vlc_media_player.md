---
title: "which version of vlc media player?"
date: 2005-09-15
forum: General Help
---

### Post by 68Firebird on 2005-09-15
Which version of vlc media player will work with Ubuntu?

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by trigg on 2005-09-15
Use the one from the Ubuntu repositories. . .

```
sudo apt-get install gnome-vlc
```


EDIT: if you really want to download it from the website  . . .  use the Debian package

---

### Post by 68Firebird on 2005-09-15
Got it installed. Thankyou.

---

### Post by ngms27 on 2005-09-15
I get the following error when trying to install vlc

Any ideas?


ngms27@ubuntu:~$ sudo apt-get install gnome-vlc
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gnome-vlc

---

### Post by 68Firebird on 2005-09-15
[QUOTE=ngms27]I get the following error when trying to install vlc

Any ideas?


ngms27@ubuntu:~$ sudo apt-get install gnome-vlc
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gnome-vlc[/QUOTE]

I was getting the same or similar error. Check my thread out here, [http://ubuntuforums.org/showthread.php?t=65772](http://ubuntuforums.org/showthread.php?t=65772)

Make sure you have made all the changes and updates. I was pulling my hair out trying to istall programs untill I followed those steps.

---

