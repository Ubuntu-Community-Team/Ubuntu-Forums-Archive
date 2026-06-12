---
title: "Install error for the Radeon 9200"
date: 2008-02-15
forum: General Help
---

### Post by FleetAdmiral74 on 2008-02-15
```
ed@ed-desktop:~/Desktop$ sh ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

```

So I read another thread here that pointed me to a xorg-fglrx package, but in that i dont see the 9200 listed...does it really support that card though? It goes down to 9500 it seems...

---

### Post by amadeus266 on 2008-02-16
You don't need the proprietary driver with you ATI 9200. I have an ATI All-In-Wonder 9200 and it works out of the box. Not all of the visual effects work but enough of them do to make it  do what you want. My advice would be to go back to the original driver that Ubuntu supplies.

---

### Post by Tatty on 2008-02-19
I also use the open source ati drivers too for my 9200 and it works mostly fine.

But if you did want to try installing the fglrx drivers from the site you have to first convert the installer you are using to a .deb package - because the installer itself only supports Red Hat and SuSE distros.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ati%29#head-e37bdcfed4ae92ac7a5ef5cbcc66c8ad2ebe6c5f]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ati%29#head-e37bdcfed4ae92ac7a5ef5cbcc66c8ad2ebe6c5f")

This link explains how to isntall the latest driver.  However do be careful as the last proprietry driver that supports the 9200 is two years out of date and i dont have a clue how it might react with more modern xorg installations.

Let me know if you have sucess because i would love to try it, but fear getting in trouble for messing up the mythbox if it goes wrong 

:popcorn:

---

