---
title: "How to change boot order on 6.06 LTS server edition"
date: 2007-07-11
forum: General Help
---

### Post by monkeyz on 2007-07-11
i have windows xp on one partition and ubuntu server on the other. I was wondering how i could get windows xp to boot up. Right now, it is just booting up ubuntu.

just a side note, whenever i use the gedit command, it says "command not found."

thanks!!

---

### Post by 5-HT on 2007-07-11
> **monkeyz said:**
> i have windows xp on one partition and ubuntu server on the other. I was wondering how i could get windows xp to boot up. Right now, it is just booting up ubuntu. 

You can make XP the default OS to boot. /boot/grub/menu.lst is nicely commented and tells you how to do so. 
> **monkeyz said:**
> 
just a side note, whenever i use the gedit command, it says "command not found."
Are you running X on the server? Gedit is an X program so you'll need to install a GUI and then gedit if you want to run the program (which is not installed). 
Vim and nano are excellent CLI text editors BTW.

cheers,

---

