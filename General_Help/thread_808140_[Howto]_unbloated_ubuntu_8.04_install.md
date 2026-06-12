---
title: "[Howto] unbloated ubuntu 8.04 install"
date: 2008-05-26
forum: General Help
---

### Post by mzruya on 2008-05-26
Installing an unbloated ubuntu install 64/32 bit,
recently i got annoyed with all the apps in my ubuntu install which i dont use, take up space, and might even cause some slow downs, for instance i was unable to prevent trackerd from running in the background, and didn't feel like starting to break gnome or ubuntu desktop..

so after my quest i'll add a few pointers i want to share with you, 

ok.. so i started with an ubuntu server install (you can do command line install from the alternate cd, i just didn't have it)
i didn't install any of the available server services, kept it clean.
booted to the system,

the biggest problem is that except the added software that comes with the default ubuntu install, there are a few essential tools that make everything alot easier (especially the restricted drivers manager, services editor ..........

_**step 1 - remove server kernel and install desktop generic kernel**_ (only if installed from server install)
  * sudo apt-get remove **linux-image-****-server**
  * sudo apt-get install **linux-image-****-generic**
_**step 2 - installing the most minimal gnome desktop**_
  * sudo apt-get install **xorg-core**
  * sudo apt-get install **gdm**
  * sudo apt-get install **gnome-core**
_**step 3 - the desktop**_
  * sudo apt-get install **ubuntu-restricted-extras**   (this is for all the codecs and flash support)
  * sudo apt-get install **firefox-3.0-gnome-support rythmbox gnome-mplayer pidgin transmission file-roller** (my basiclly essential gnome-apps it installs firefox 3 with ubuntu customization, music, and video player and IM, p2p)
_**step 4 - system tools**_
  * sudo apt-get install ubuntu-restricted-drivers-manager linux-restricted-modules-generic (getting those restricted drivers to work and installing the Restricted Driver manager)
  * sudo apt-get install **nvidia-glx-new** (if you have an nvidia card)
  * sudo apt-get install **gnome-system-tools**
  * sudo apt-get install **update-manager**
  * sudo apt-get install **compiz-gnome**
_**step 5 - getting the ubuntu boot splash working again**_
  * sudo apt-get install **usplash usplash-theme-ubuntu**
  * sudo apt-get install **startupmanager** (now open the startup manager and select you're color depth and desired resolution)


that's basically it, and then you can go and add gimp openoffice and everything else you use,
if you have anything to add i'll be glad to see,
in my opinion ubuntu should come as clean as that, or at least let the user in the installation select which packages he wants, so we could avoid the above headache.

results :
[[IMG]http://img399.imageshack.us/img399/5368/75863602ag8.th.jpg[/IMG]](http://img399.imageshack.us/my.php?image=75863602ag8.jpg)
[[IMG]http://img397.imageshack.us/img397/4535/59926941io3.th.png[/IMG]](http://img397.imageshack.us/my.php?image=59926941io3.png)

---

