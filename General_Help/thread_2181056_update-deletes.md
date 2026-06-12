---
title: "update-deletes"
date: 2013-10-16
forum: General Help
---

### Post by Mark_Keith on 2013-10-16
uname -a Linux Vixen 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux  

Installed ubuntu 12.04, then added xfce desktop.  (think it was last year?)  

I saw flac 1.3.1 came out so tried install dep packages hoping to pull in dependances.  Well, in the process (which failed) apt-get update/grade did a partial distro? upgrade. and also deleted a lot of packages.    

Now, starting the system, the login screen is gone.  When it starts, shows Xubuntu with the dots beneath.  then little bit some the starting text be under that. mouse moves or keypresses doesn't do anything. 
I can control-alt-f1 to a terminal, login and and startx.  which brings up the xubuntu desktop. tried installing and forcing reinstalling lightdm to see if that issue.  

Any clues what to look for?  
Wolf

---

### Post by Mark_Keith on 2013-10-21
well, this seems to have helped.
sudo apt-get install ubuntu-desktop
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter

Wolf

---

