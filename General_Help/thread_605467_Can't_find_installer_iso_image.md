---
title: "Can't find installer iso image"
date: 2007-11-07
forum: General Help
---

### Post by dominoeastmint on 2007-11-07
Hello.Trying to install Kubuntu w/Wubi on Windows XP (Fat32).
After rebooting to Ubuntu, & going through the  first couple of steps, installer displays error for cd. Searching hard drives it can't find installer ISO image it says. Back to XP,I tried uninstalling & moving the .exe to the saved CD ISO folder & running again but nothing. back to Ubuntu I tried up & down every which way trying all the install options I could, but it keeps searching for that ISO & not finding it. Can't seem to find option for network install either (or not?) Further down menu I am able to choose mirror &  partially install base files until error & then goes back to searching hard drives for ISO.
I also have an extra hard drive which I was able to format with the installer. Ideally I would like to install there. I was planning to install on my Windows drive & then transfer over later as per instructions found. Either way I would prefer to avoid having to download/burn/ install from CD at this point. Does the Wubi  EXE have to be run from any specific location? What am I doing wrong?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:


Help *is* appreciated. 

Domino

---

### Post by ago on 2007-11-07
What version of wubi are you using? what is your iso?

---

### Post by dominoeastmint on 2007-11-07
Wubi 7.04.04. Kubuntu 7.04-alternate-i386.iso in c:/wubi/install .

---

### Post by ago on 2007-11-07
You may want to try wubi 7.10 with ubuntu-7.10-DESKTOP.iso

---

### Post by dominoeastmint on 2007-11-07
I am still looking for 7.10, where can I find it?

---

### Post by ago on 2007-11-07
[www.wubi-installer.org/devel/minefield](www.wubi-installer.org/devel/minefield)

---

### Post by Manav Kataria on 2008-01-05
Hi! DominoEastMint! :)

Could you find/fix this problem ? 

You might wanna try reading the syslog as mentioned by ago here: 
> **ago said:**
> Do a clean installation again, if that happens hit Alt+F4 and see if there is any relevant error. To look at older error hit Alt+F2 and then run "nano /var/log/syslog"

-Manav

---

