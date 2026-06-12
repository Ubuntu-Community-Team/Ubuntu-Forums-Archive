---
title: "ATI drivers - Bad Substitution Error"
date: 2007-04-30
forum: General Help
---

### Post by Ekin on 2007-04-30
So finally after two days of browsing various forums and mailing lists and dont find answers I decided to post here.

My Problem is that after upgrade to 7,04 I cannot make my ATI drivers working. The whole problem is that on older versions I made it run. I have way to make them run on my machine but i need to run official ati drivers for it. But in 7,04 official ati drivers just wont run.

I get: 

 sh ati-driver-installer-8.28.8.run 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution


The line "./ati-installer.sh: 165: Syntax error: Bad substitution" seems to be a problem. I tried to run older ati drivers (they worked perfectly on older versions of ubuntu) but they return the same "Bad substitution" error in 7.04. So it occur to me that there is not a problem with those ati drivers (i hate to say that because i hate whole ATI from the first day i got Linux) but there is a problem with my system. 

Many people posted simmilar threads on this forums askinf for help and only response they got was the links on various how-to - s and scripts. Those how-to - s will not work because they are all using the same method involving original ati drivers (they run it, make packages, instal packages, reconfigure). So please dont answer me with those how-to -s and scripts. I know them all (I am running ubuntu all the way from Breezy and after every system upgrade i needed to install ati drivers again, i even got xgl working for some time). Please help me! (I already reconfigured Xserver-xorg so many times i know how to do it blindfolded with my left hand without keyboard...).

---

### Post by tyler_roach on 2007-04-30
There seem to be some issues with the proprietary ati drivers in Feisty. I did an upgrade from Edgy and also a clean install, and both times my x server would not start at all after I installed the fglrx drivers. I would get an error that read "no screens found."

Maybe this has something to do with the fglrx drivers making two "Device" entries in the xorg.conf file.

Anyway, I have switched to using the open-source "ati" drivers and I'm more than thrilled with them.

---

