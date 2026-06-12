---
title: "Google earth black"
date: 2012-11-14
forum: General Help
---

### Post by Derek10 on 2012-11-14
I have downloaded the .deb for Google Earth and installed it successfully.

The Earth's surface is entirely black with the line borders showing up fine. I've tinkered its setting to no avail. In Windows 7 it's fine. 

I think it may have to do with video controller or drivers but I have not any other 3D app to check it out.

I am using a netbook, Samsung N145 with Intel Atom N455 and Intel 3150 Graphics. Lubuntu 12.10 i386 recently installed,

Many thanks for any help.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227185&d=1352923571[/IMG]

---

### Post by Locus Kiesselbachi on 2013-02-11
Hello!
Do you have graphical drivers up to date?

---

### Post by Bufeu on 2013-02-11
Installed the latest graphics drivers for your graphic card?

---

### Post by Impavidus on 2013-02-11
Intel graphics, so no proprietary drivers required (or even available).

---

### Post by Bufeu on 2013-02-11
Try this out:[QUOTE=https://help.ubuntu.com/community/GoogleEarth#Troubleshooting]If the installer was started with sudo, googleearth  will be started as root, but still using the home folder of the normal  user (who started sudo). Thus Google Earth will place its configuration  files into the user's home folders, but with root as the owner. The  normal user cannot use Google Earth, because the settings cannot be  saved. The display will not contain a globe, but only a black space and  some settings will be grayed out. To fix this problem, delete the Google Earth configuration directory:```
sudo rm -Rf .config/Google .googleearth
```[/QUOTE]

---

