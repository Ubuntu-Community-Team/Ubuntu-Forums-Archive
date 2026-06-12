---
title: "GTK2 Global menu and undecorate maximized windows problem in Gnome Flashback 20.04"
date: 2020-06-16
forum: General Help
---

### Post by Aleksej on 2020-06-16
Hello! I have installed  gnome-session-flashback on top of Ubuntu 20.04. I also installed the appmenu-registrar package,  which made the indicator-appmenu-applet work. It;s working with LibreOffice,  Gedit, TexStudio, VLC...so far, so good. But, it's not working with  Gimp, Ardour, Audacity (I suppose all of these are GTK2 apps, I know for  sure Ardour is). So, I am facing with two problems here: 1. How  to make all (or most) of the apps  to show their menu in the top bar.  Searching through net for the same problem in MATE or Xfce, I found this  solution
:

 Install appmenu-gtk2-module
 Add gtk-modules="appmenu-gtk-module" to your ~/.gtkrc-2.0



 It worked for Xfce and Mate back then, but it doesn't help here. Maybe I have to change something.


  2, Second problem; I am trying to find a way to undecorate the  maximized windows. Is there some setting in dconf or gconf editor, or any config file which can make this happen. I tried to install several applets, like gnome-window-applets, but I guess the package is too old now.

Any help would be appreciated! Cheers!

---

