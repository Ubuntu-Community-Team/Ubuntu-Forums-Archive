---
title: "[SOLVED] Errorcounts are broken? Uncool..."
date: 2007-09-26
forum: General Help
---

### Post by horrorpunk138 on 2007-09-26
So I finally got a wireless stick that works with 7.04. (Linksys WUSB54GC)

I followed this thread and got it working with no problem.

[http://ubuntuforums.org/showthread.php?t=516649&highlight=WUSB54GC](http://ubuntuforums.org/showthread.php?t=516649&highlight=WUSB54GC)

Afterward though (after a restart), I get a notification that says something to the effect of.....

"A error ocurred, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: `Error:BrokenCount >0`


I did that, (package manager) and I know that THIS is what's in question.

"User friendly KDE frontend for wireless network connection
Wireless Assistant scans for wireless access points and displays link quality,
encryption and other useful information. When user wants to connect to a
network, Wireless Assistant opens up its wizards and guides the user through
Wi-Fi settings. After a successful connection is made the settings are
remembered so next time the user won't have to enter them again.

Homepage: http://wlassistant.sourceforge.net/"


I wanna fix that, but I'm sick of 'fixing' myself a wireless connection. Would I lose all my "new" settings?

Forgive me, I'm still very new to this. I'm using Ubuntu, NOT Kubuntu. I was under the impression that KDE business was Kubuntu stuff, no?

---

### Post by horrorpunk138 on 2007-09-26
Nevermind. 

If same situation happens to anyone else, just run 

```
sudo apt-get install -f
```

and the problem fixes, I'm still online and all changes made to network are still there.

---

