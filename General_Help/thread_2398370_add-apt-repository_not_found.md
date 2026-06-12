---
title: "add-apt-repository not found"
date: 2018-08-11
forum: General Help
---

### Post by 5tratusxii on 2018-08-11
I'm brand new to ubuntu and am just trying to install firefox as my browser and whenever I try to update it I get the error "sudo: add-apt-repository command not found". I have absolutely no idea what to do next so any ideas would be greatly appreciated!
(Also I've tried to update to version 18 but I'm on 16.4 and it won't update past there, I have no idea if that has anything to do with it but I figure more information can't hurt right?)

---

### Post by deadflowr on 2018-08-11
Which method of updating are you using?
Software updater or terminal command line apt/apt-get?
If apt/apt-get please post back the full output of the update commands run.

---

### Post by ajgreeny on 2018-08-11
Check that you have **python3-software-properties** installed and if not install it.

---

### Post by kc1di on 2018-08-11
Hello 5tratusxii and welcome to Ubuntu,

Fire fox comes as the default.  I'm not sure your trying to install it if so why?  It should be updated with the system updates. 

If your trying to add a PPA the easiest way would be to go to software & updates under settings in the menu and click the other tab then add and enter the info needed. 

[This page]("https://www.tecmint.com/add-remove-purge-ppa-in-ubuntu/") may be of help. The correct command to add a ppa with apt is```
sudo apt-add-repository ppa: <followed by the ppa name>
```
Good Luck :)

---

### Post by 5tratusxii on 2018-08-11
the version I installed came with a browser called NetSurf that looks like something from 2001. and I have typed that exact line of code in so many times that I think I'm going crazy XD.

---

### Post by 5tratusxii on 2018-08-11
I'm trying to access it through the terminal and the error is what I put in my original post "sudo: add-apt-repository: command not found"

---

### Post by 5tratusxii on 2018-08-11
On a side note, I can't seem to even locate the software update app. I can find the package installer but I'm starting to feel like something's off with this version. Can y'all recommend where to download ubuntu itself from? I got it off of a crouton installer so that may be where it's freaking out?

---

### Post by kc1di on 2018-08-11
Please go to a terminal and type this command```
lsb_release -a
```
then post the output here.

---

### Post by 5tratusxii on 2018-08-11
[ATTACH=CONFIG]280709[/ATTACH]

---

### Post by kc1di on 2018-08-12
I'm not sure why Firefox was not installed as default.  But in any case it should be installable from the repository Try installing synaptic if it's not already installed. 
and doing a search for Firefox.  Firefox should be at version 61.xx not 18.  So something has been done to your system where it was removed or never updated if your trying to update to version 18.  That is very old.  

You should not go outside the repositories unless it's absolutely needed.  And that with great care.  There should have been no need to install FF outside of the regular Ubuntu repositories.  
Good Luck.

P.S. it may be better at this point to do a complete reinstall of the system. Back up important files first.

---

### Post by Impavidus on 2018-08-12
add-apt-repository should be available for use via sudo. Firefox should be installed by default, and if not, installable without adding a repository. If you just installed Ubuntu for the first time, it would have been best if you installed 18.04 right away. The upgrade from 16.04 to 18.04 is somewhat delayed, but should be available soon.

Now, you mention you used crouton. Are you using a chromebook? I've no experience with chromebooks, but I know they're designed to put google, not you, in control of your computer, so that may complicate matters.

---

### Post by kc1di on 2018-08-12
Are you using a chromebook?  crouton is an installer for chromebooks not other machines. 
If your on another computer you can download[ ubuntu from here.]("https://www.ubuntu.com/download") gnome desktop
[Kubuntu from here.]("https://kubuntu.org") Kde desktop.
[ubuntu-mate from here]("https://ubuntu-mate.org") - mate desktop
[ubuntu-budgie here]("https://ubuntubudgie.org"). budgie desktop.
[xubuntu here:]("https://xubuntu.org") xfce4 desktop. (my favorite)
[Lubuntu from here:]("https://lubuntu.net") LXDE desktop. 
there are others but those are the major ones. 
good luck.

---

