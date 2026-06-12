---
title: "Looks inside the windows?"
date: 2006-11-30
forum: General Help
---

### Post by telovoyagarcar on 2006-11-30
Ok.. i have Beryl installed and im playing with the themes.
Im also downloading different themes from gnome-look.org.
But the only thing that changes is the surroundings of the windows like the minimize-restore-close window buttons...
the inside of the windows are always the same ugly squared windows 98 style dark gray color  without any gradient effects or more rounded style buttons like im seeing in that website. And i know im not seeing KDE desktops, because i can see the gnome menus on top and botton.

Here is an example..
[http://www.gnome-look.org/content/pre1/46144-1.jpg](http://www.gnome-look.org/content/pre1/46144-1.jpg)

See?.. the scroll bars are different, the buttons a little rounded and better looking, the gray is not as dark, the minimized windows at the bottom panel are also a little rounded.. etc

Where do i change this?

thanks!

---

### Post by Shatrat on 2006-11-30
I believe beryl themes (the .emerald ones) only change the window trim, and GTK themes change the standard buttons and bars and stuff for applications that use GTK widgets, although I'm not all that hip about customizing UIs.

---

### Post by d3v1ant_0n3 on 2006-11-30
Indeed. Grab some GTK+ themes from gnome look ( I love the Murrina ones, but you need the Murrine engine too), and install them via System>Preferences>Themes>Install Theme. You can then select the new theme by clciking on 'Theme Details' and choosing the 'Window Controls' tab.

---

### Post by telovoyagarcar on 2006-12-01
I do not have the "window controls" tab if i go to theme details...
i only have controls and icons tabs..
and another thing.. i don't know if this has to do anything with it but, if i try to go into System>Preferences>windows i get an error message :

Cannot start the preferences application for your window manager

Window manager "beryl" has not registered a configuration tool.

what else can i try?

---

### Post by JoeC21 on 2006-12-01
'Controls' is the section you want for the GTK theme.  You dont have the window border tab because you are using beryl instead of metacity to control the windows.

Use the beryl settings manager when you are using beryl.  If you are just using 'metactiy', then you will be able to open System>Preferences>windows.  This controls actions for metacity.

HTH

---

