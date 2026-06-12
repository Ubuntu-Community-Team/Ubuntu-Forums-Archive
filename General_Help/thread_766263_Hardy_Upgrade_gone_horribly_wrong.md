---
title: "Hardy Upgrade gone horribly wrong"
date: 2008-04-25
forum: General Help
---

### Post by Thosbob on 2008-04-25
Ok, just finished upgrading from 7.10 to 8.04. Only problem is that when presented what usually would be the login window I get nothing.  Blank orange, nada, zilch.  I've done some perliminary flailing on the recovery console and have tried reinstalling xserver-xorg gdm and ubuntu-desktop and none of it has worked.  I can still navigate to my home folder and see all my data but I can't log into the GUI.  I'd like to know if there is anything I can do to save my system as a whole (I have a home webserver and a ton of programs installed) and if not if there is a way to mount an external FAT32 drive (USB) or burn DVD/CDs of files from the commandline.

---

### Post by bobthedisease on 2008-04-25
Same here. I have manged to get into the GUI by reconfiguring the xserver then restarting x however i only have 800x600 and my nvidia card doesn't seem to want to play.
Any ideas

---

### Post by Thosbob on 2008-04-25
> **bobthedisease said:**
> Same here. I have manged to get into the GUI by reconfiguring the xserver then restarting x however i only have 800x600 and my nvidia card doesn't seem to want to play.
Any ideas

No clue. How did you reconfigure X? I have a very bare bones system so advanced graphics wouldnt be an issue. I just need basic functionality back.

---

### Post by bobthedisease on 2008-04-25
sudo dpkg-reconfigure xserver-xorg 
follow the step by step questions then do ctrl+alt+backspace that got me back into the gui

---

### Post by Thosbob on 2008-04-25
> **bobthedisease said:**
> sudo dpkg-reconfigure xserver-xorg 
follow the step by step questions then do ctrl+alt+backspace that got me back into the gui

Thanks for the thought but no dice on it.  Still stuck with the hourglass on orange. No login prompt. God bless symbolic links and my webserver. Currently backing up all critical data.

---

