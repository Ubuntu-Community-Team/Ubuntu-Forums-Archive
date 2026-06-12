---
title: "Wubi installer and LAN with proxy authentication"
date: 2008-07-04
forum: General Help
---

### Post by gagliaudo on 2008-07-04
Dear friends,
my OS is -by now- WIN XP SP3; I'm trying to join Ubuntu community and I'm trying to use Wubi Installer but -with the last version of it- it's impossible for me to have the install process, getting an undefinde error (maybe http error ???)
I'm within a LAN with proxy authentication (username and password).
Any suggestion ??? ](*,)
Thanks a lot to everybody!!!

---

### Post by ago on 2008-07-04
Download the desktop CD 8.04.1 ISO manually from releases.ubuntu.com/8.04.1 and place it in the same folder as wubi.exe

---

### Post by gagliaudo on 2008-07-04
> **ago said:**
> Download the desktop CD 8.04.1 ISO manually from releases.ubuntu.com/8.04.1 and place it in the same folder as wubi.exe
Ago I have discovered we are both Italian, so I continue this thread within the Italian Forum... Anyway, after having done what you said, have I to click (stupid question but I'm really a newbie of Wubi and Ubuntu...) on wubi.exe in order to install ubuntu ???
Thanks a lot !!! Paolo

---

### Post by ago on 2008-07-04
> **gagliaudo said:**
> Ago I have discovered we are both Italian, so I continue this thread within the Italian Forum... Anyway, after having done what you said, have I to click (stupid question but I'm really a newbie of Wubi and Ubuntu...) on wubi.exe in order to install ubuntu ???
Thanks a lot !!! Paolo

Yes run wubi from the same folder where you have the ISO. Note that you have to use wubi.exe downloaded from wubi-installer.org as the version within the CD cannot detect local files.

---

### Post by prshah on 2008-07-04
> **gagliaudo said:**
> 
 I'm trying to use Wubi Installer but getting an undefinde error (maybe http error ???)
I'm within a LAN with proxy authentication (username and password).


If you have the desktop (live) CD, then you don't need to download either Wubi _or_ the ISO; the desktop live CD already has the proper setup. Insert the CD, then wait till the autorun screen comes up; now select the 2nd (?) option, similar to "Install in Windows". That will launch the Wubi contained within the CD, and the same CD will be used for the installation process; you can later download updates, after installation is complete.

---

### Post by studyhard888 on 2008-07-04
> **ago said:**
> Yes run wubi from the same folder where you have the ISO. Note that you have to use wubi.exe downloaded from wubi-installer.org as the version within the CD cannot detect local files.


in fact ,the most simple way to install ubuntu with wubi is mount the ubuntu.iso in windows and run wubi. then what you do next is waiting ....

---

