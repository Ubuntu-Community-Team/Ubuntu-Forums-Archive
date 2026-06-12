---
title: "allowing only specific apps for a user?"
date: 2013-04-17
forum: General Help
---

### Post by kurja on 2013-04-17
I want to make a user account (in 12.04lts) for my small kids, where they would only have launch buttons/access to a couple programs of my choosing - a few games, gimp for drawing, access to optical drives but not to anything on hdd outside user folder, etc. I've sought for solutions but it seems gnome nanny isn't developed anymore and won't work on 12.04, and manually configuring everything is, well, not very simple to do. Is there a way to do this - for someone who isn't an elder cli guru?

p.s I wouldn't mind experimenting around with this a bit, I'm looking at upgrading to 64bit version so sometime soon I'm going to do a full reinstall anyway.

---

### Post by dabl on 2013-04-17
I think you want some variant of "kiosk mode".  There are considerably more google hits for KDE/Kubuntu kiosk mode than for Gnome/Ubuntu.

[http://techbase.kde.org/KDE_System_Administration/Kiosk/Introduction](http://techbase.kde.org/KDE_System_Administration/Kiosk/Introduction)

---

### Post by Lars Noodén on 2013-04-17
If you're going to go the kiosk route, there are many ways to do that.  Here is one detailed article on setting up a kiosk:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

---

### Post by kurja on 2013-04-17
KDE kiosk tool sounds like I might get along with it... If I understand correctly, I'd need to install kubuntu-desktop, then I could use that for the kids' account and have their desktop environment controlled by the kiosk tool - and having kubuntu desktop installed would not interfere with my normal unity desktop environment?

---

### Post by Lars Noodén on 2013-04-17
Whether you use plain KDE or the full Kubuntu-desktop, you will be able to switch back and forth between it and Unity at the login screen.

---

### Post by dabl on 2013-04-17
Yes, 

```
sudo apt-get update && sudo apt-get install kubuntu-desktop
``` will set you up to log into either Gnome or KDE.  There's a KDE utility to add users if you want, "kuser", which is real simple to use too. You will have to install it separately -- it is not part of kubuntu-desktop, AFAIK.  To run kuser or any other KDE package with root privileges, use Alt-F2 "kdesudo packagename".  Don't try to "sudo" it -- you'll screw up the user's home folder doing that.

---

