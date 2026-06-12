---
title: "Deleting desktop folders that you don't have permission to delete. (Fesity)"
date: 2007-08-09
forum: General Help
---

### Post by ThunderWhale on 2007-08-09
I accidently installed a program to my desktop instead of where I wanted to install it, and now I can't delete it.  I want to completly remove the program, but I can't find it in Synaptic Package Manager, nor the add/remove program list.  Also, I can't just delete the icon from the deskop.  I tried right-clicking the icon and changing permissions, but all the options are greyed out.

Attached is a picture of the icon.

Any help would be greatly appreciated!

Thanks a lot!

[IMG]http://img468.imageshack.us/img468/3465/screenshotqq0.png[/IMG]

---

### Post by djrobthaman on 2007-08-09
I think you'd have to either run the deb (did you install from a deb?) and then I think it gives you an option to uninstall or type in the terminal sudo apt-get remove <packagename>

---

### Post by ThunderWhale on 2007-08-09
I installed it from a .bin that I made executable.  The thing is, I can't find the package in the synaptics package manager, and I don't know the name of the program to do sudo apt-get remove.

The program's name is Real Player, but that doesn't work for apt-get remove.

---

### Post by djrobthaman on 2007-08-09
the easiest thing to do is open synaptic and search for real player.  I'm sure you'll find the package that way, but could you post the contents of the bin file here?

---

### Post by ThunderWhale on 2007-08-09
> **djrobthaman said:**
> the easiest thing to do is open synaptic and search for real player.  I'm sure you'll find the package that way, but could you post the contents of the bin file here?

I tried searching synaptic for both "real player" and "realplayer"  no dice on either.  I don't know how to post the contents of the .BIN. 

It is the standard .BIN from [www.realplayer.com](www.realplayer.com)

---

### Post by vexorian on 2007-08-09
you can do alt+f2 gksu nautilus then head towards /home then your account and find your desktop and punish the lizard.

edit: ignore previous sentence: read this: [http://www.linuxforums.org/forum/debian-linux-help/35708-uninstall-realplayer-10-a.html](http://www.linuxforums.org/forum/debian-linux-help/35708-uninstall-realplayer-10-a.html)

---

### Post by ThunderWhale on 2007-08-09
> **vexorian said:**
> you can do alt+f2 gksu nautilus then head towards /home then your account and find your desktop and punish the lizard.

edit: ignore previous sentence: read this: [http://www.linuxforums.org/forum/debian-linux-help/35708-uninstall-realplayer-10-a.html](http://www.linuxforums.org/forum/debian-linux-help/35708-uninstall-realplayer-10-a.html)

Thanks a lot! This solved my problem!

---

