---
title: "Ubuntu Gusty on USB"
date: 2007-11-28
forum: General Help
---

### Post by justtech on 2007-11-28
I have followed the instructions on pendrivelinux.com to do the persistent Gusty Gibbon install on a 2gb usb thumb drive.  I am handing them out to my clients to try and get them on board with Linux (or at least let them aware that there are easy alternatives).  I have one client though that has a Dell Laptop that will be his default playground for Ubuntu.  Problem is he also wants to be able to stick it into some of his customers computers and show it off without messing up his settings for his Dell.  I was thinking that maybe there might be a way to make it so you would have to login to get into Ubuntu and from that screen have different sessions.  One session be his Dell settings and have his xorg.conf setup for native resolution, sound set properly, etc.  And on another session it would be the basic "Live" style with failsafe settings.  So, I guess I am just curious if this is even possible with this persistent Ubuntu USB drive setup?  Any help would be appreciated.

---

### Post by Sammi on 2007-11-28
You could create two different logon users, which would give two different working environments past the login screen, which each their own settings, but they would still both use the same xorg.conf file. I don't think there is a painless way of changing xorg.conf files during boot up. At least not that I know of.

Easy solution: Just give him two separate USB Flash drives :D

---

