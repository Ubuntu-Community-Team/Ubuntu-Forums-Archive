---
title: "Main Menu Application Launcher Icons 14.04"
date: 2015-07-26
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-07-26
Hello,

Can anyone tell me how to locate the icons displayed in the main menu; so that I can re-enter this information in a launcher.

Originally, Disk Usage Analyzer was available under Accessories and for some reason it is no longer there.  I have it available
under System Tools; but when I click on the icon in its Main Menu launcher it just brings me to a list of folders.  In previous
distros clicking on the launcher icon would display the location of that icon; so rebuilding a main menu launcher was pretty easy.

Thanks, Hannibal

---

### Post by gdesilva on 2015-07-27
Hi, normally icons can be found in /usr/share/icons - depending on the icon theme you are using you may have to use the appropriate subfolder. Some applications have their own icons in /usr/share/"name of your app"

---

### Post by coljohnhannibalsmith on 2015-07-27
Thanks for the tip.  I not only found the menu launcher icon for Disk Usage Analyzer; I found all of them.
All of the Menu Launcher icons are found in /usr/share/applications in 14.04.  The bad news is they appear
to be impossible to use.  When I click on the icon in the menu item properties and go to 
/usr/share/applications all I find is a list of scripts like baobab.destop, brasero.desktop, *.desktop, etc.
The Open window doesn't show any icons at all.  The folder view in Nautilus however, shows the icons
but not the scripts even though I have Show Hidden and Backup Files selected.  When I execute the
following code:

ls /usr/share/applications

all that show are the scripts.  This is crazy making.  These obviously aren't the same places even though
they display as such.  Also, I made sure to double-check that I was in the same place according to the
directory path.  What am I doing wrong?

Thanks, Hannibal



Thanks, Hannibal

---

### Post by gdesilva on 2015-07-27
No, /usr/share/applications includes desktop launchers for relevant applications - the actual icon image files are located in /usr/share/icons directory. 

On the other hand if all you need is to have an icon on your desktop for a particular application then just copy the relevant file, eg, /usr/share/applications/brasero.desktop, on to your desktop.

---

### Post by coljohnhannibalsmith on 2015-07-28
I've checked all the folders in /usr/share/icons and I haven't found any relevant icons.
I think it's time for me to break down and find an icon on the web, save it in my home
folder and load it into the menu launcher I'm rebuilding.  I would, however, like to know
where this icon is hiding in the system; it's really puzzling.

Hannibal

---

### Post by CantankRus on 2015-07-28
Most of the default applications have icons in the icon themes and don't install their own icons.
eg 
If you look at the .desktop launcher for Disk Usage Analyzer(baobab) you'll see **Icon=[COLOR="#FF0000"]baobab[/COLOR]**
[ATTACH=CONFIG]263427[/ATTACH]
It will use the baobab.svg in whatever icon theme you are using.

I believe other applications may install an icon to **/usr/share/icons/hicolor/scalable/apps**
This directory is searched so the path to an icon doesn't need to be specified in the .desktop file.
You can check this using synaptic.
eg I installed easystroke.
[ATTACH=CONFIG]263428[/ATTACH] [ATTACH=CONFIG]263429[/ATTACH]

The safest way to edit a .desktop from **/usr/share/applications** is to copy it to **~/.local/share/applications** and then edit this copy.
Desktop files in ~/.local/share/applications will override those in /usr/share/applications for the that user.
To go back to using the default desktop file you just delete the one in **~/.local/share/applications**
eg I copy my nemo.desktop file to **~/.local/share/applications** and specify the path to an icon
and add a couple of quicklist items.
[ATTACH=CONFIG]263430[/ATTACH]

---

### Post by coljohnhannibalsmith on 2015-07-28
Thank you.  Mystery solved.  I found it in /usr/share/icons/Humanity/apps/48.  What a
crucible this was.

Hannibal

---

