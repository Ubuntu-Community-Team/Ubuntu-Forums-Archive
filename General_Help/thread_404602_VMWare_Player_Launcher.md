---
title: "VMWare Player Launcher?"
date: 2007-04-08
forum: General Help
---

### Post by SendDerek on 2007-04-08
I was wondering if there was a way for me to create a Desktop Shortcut of my VMWare Player .vmx file.  This way, I can just double click on an icon on the desktop and get into my Windows XP virtual machine.

I have tried to create a launcher that just simply points to the file, but it doesn't execute it or anything.  Does anybody have any tips for me?

Thanks!

---

### Post by zvacet on 2007-04-08
Find vmware in usr/bin and point to it.

---

### Post by SendDerek on 2007-04-08
I think I was just making it harder than it needed to be.  Here's how I accomplished it:

1.)  Right Click and Create Launcher
2.)  Fill In Proper Info:
2a) Type:  Application in Terminal
2b) Name:  *whatever you want the launcher to be called*
2c) Command:  vmplayer /home/[username]/vmware/[nameofvm].vmx

3.)  Enjoy.

---

