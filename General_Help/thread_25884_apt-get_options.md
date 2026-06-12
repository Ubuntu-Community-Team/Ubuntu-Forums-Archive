---
title: "apt-get options"
date: 2005-04-11
forum: General Help
---

### Post by cemaytar on 2005-04-11
I have no internet connection. but I have many debians for use. my question is:
can I have an option to download deb files or something (I don't know what files are required for installation) , and then (I will take these files with my usb-flash disk) to install the applications on my pc at home with what commands ? 
briefly : HOW apt-get **** (to download) and apt-get **** (to install)  :|

---

### Post by capi on 2005-04-11
[QUOTE=cemaytar]I have no internet connection. but I have many debians for use. my question is:
can I have an option to download deb files or something (I don't know what files are required for installation) , and then (I will take these files with my usb-flash disk) to install the applications on my pc at home with what commands ? 
briefly : HOW apt-get **** (to download) and apt-get **** (to install)  :|[/QUOTE]
 I believe getting the debian CDs and doing apt-gets off of that would work.

---

### Post by Fab on 2005-04-11
[QUOTE=capi]I believe getting the debian CDs and doing apt-gets off of that would work.[/QUOTE]
 download the .deb file
cd to the directory where the file is
do sudo dpkg -i <file.deb>

works like a charm :)

---

