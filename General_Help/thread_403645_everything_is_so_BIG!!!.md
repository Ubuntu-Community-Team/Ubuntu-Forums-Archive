---
title: "everything is so BIG!!!"
date: 2007-04-07
forum: General Help
---

### Post by taehC on 2007-04-07
Help!  I am using feisty beta and after installing an update, I restarted my computer,  my screen resolution went from 1280x1024 to 800x600, and I can't change it back!  
Anyway to fix it?

---

### Post by tpg on 2007-04-07
You ought to be able to increase the resolution in /etc/X11/xorg.conf; look for the section where it lists resolutions, for example, in my xorg.conf
```

SubSection "Display"
   Depth           16
   Modes           "1024x768"
EndSubSection
SubSection "Display"
   Depth           24
   Modes           "1024x768"
EndSubSection

```
All you should have to do is add "1280x1024" before the list of resolutions. To edit xorg.conf, make sure you open it as root, for example
```
sudo gedit /etc/X11/xorg.conf
```
To apply the settings, restart the X-server with Ctrl-Alt-Backspace. Hope this works! :)

---

### Post by taurus on 2007-04-07
Please use gksudo when you use gedit.

```
gksudo gedit /etc/X11/xorg.conf
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Pikestaff on 2007-04-07
Have you tried reconfiguring xorg?

```
sudo dpkg-reconfigure xserver-xorg
```

It'll ask you what screen resolutions you want towards the end of all its questions; select the one you want with a spacebar.  Then after you reboot you should be able to choose it again...

---

### Post by heimo on 2007-04-07
Tips on previous posts is the place to start, and if that doesn't help, also check:
[http://www.ubuntuforums.org/showthread.php?t=83973]("https://help.ubuntu.com/community/FixVideoResolutionHowto")


(I feel like spamming as I must have posted this link couple hundred times now.)

---

### Post by bapoumba on 2007-04-07
> **heimo said:**
> 
(I feel like spamming as I must have posted this link couple hundred times now.)
lol. That kind of spam is welcome here, thank you heimo \o/

---

### Post by majinebrain on 2007-04-07
I would like to thank you!
hehehe, The last tip, redoing the xserver worked
yay!

---

