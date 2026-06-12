---
title: "Can't login anymore!"
date: 2007-06-23
forum: General Help
---

### Post by nerdman978 on 2007-06-23
Hello. This morning I tried logging into my computer but I got a nice little error message and got logged right back out. The error message said "I have detected a/another panel running. I will now (shut down or logout I can't remember)" . Before logging out I heard my login sound and my buddy list and sticky notes apps loaded and I saw them on the screen, and both my top and bottom panels appeared (with no icons on them!). Then all of that disappeared and I was sent back to my gdm login screen. The weird thing is that I haven't messed with anything on my system lately, like editing the xorg.conf file or trying once again to get my graphics drivers to work. And it worked fine yesterday too! Also, I did install a few games yesterday to play with a friend online, but I highly doubt this would affect this. Help please!

---

### Post by Silenus on 2007-06-23
at boot ctrl + alt + f2 or any really. Then try killall &panel I think or & panel. Not sure, then try to start it again. Do you have another window manager? while in the previous steps do sudo apt-get install fluxbox, that way you can at least boot to your files and work around.

---

### Post by RedSquirrel on 2007-06-23
If you're going to install Fluxbox, after the apt-get command above you should do:

```
sudo update-menus
```

to build your Fluxbox menu. If you don't do that then you won't have a menu when you login to Fluxbox and that could be a little annoying. ;)

---

