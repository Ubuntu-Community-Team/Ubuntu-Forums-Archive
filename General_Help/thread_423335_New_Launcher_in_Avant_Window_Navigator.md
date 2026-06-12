---
title: "New Launcher in Avant Window Navigator"
date: 2007-04-25
forum: General Help
---

### Post by brharri1 on 2007-04-25
Hi,

I have AWN installed and working properly (and it seems really nice). However, I am having problems adding new applications to the launcher. Certain ones drag and drop without a problem, other ones I cannot add at all. For instance, it is mainly custom launchers that do not work well. I have a custom launcher with the command 

gksu "nautilus"

among others. I have tried right clicking the desktop, creating a launcher, and then dragging it to the AWN, which does nothing. It seems that only things ending in .desktop work, and if that is the case, my new desktop launchers don't have that ending and I don't know how to add it (just renaming the file does not work). If anyone knows how to fix this, I would appreciate it a lot.

-Brian

---

### Post by Belyel on 2007-04-26
I have found that the best way to make sure  a launcher ends up (and stays on) the AWN deskbar is to create a launcher then move it to the avant-window-navigator directory in /usr/share  .  Then, drag the launcher from that folder to the bar.  It's a few extra steps, but it hasn't failed for me yet, even with custom launchers.

---

### Post by brharri1 on 2007-04-26
Belyel,

Thanks for the reply. I finally got it to work, taking your advice plus some extra. It seems that just being in that particular directory alone was not enough, but still necessary. Right clicking the desktop to create a launcher didn't work either, I had to sudo gedit /usr/share/avant-window-navigator/mylauncher.desktop and put something like this in:

[Desktop Entry]
Encoding=UTF-8
Name=Nautilus-root
Comment=
Exec=gksu "nautilus"
Icon=/usr/share/pixmaps/nautilus.xpm
Type=Application

And then dragging that to the launcher.

It also only worked when I actually specified an icon; leaving that line blank does not work. I'm not sure if the Encoding line makes a difference because I just copied this format from the ubuntuguide.org for a different app. Glad I got this working, I think this bar works much better than gdesklets. 

I have one other question about the bar, its not really a problem, I'm just curious. Sometimes when I load a new app from it, it opens a new icon on the right hand side of the separator (on the 'window list' side) and other times it doesn't create a new icon so that in order to minimize/maximize the window I click again on the launcher button. It's not a problem, I would just like to understand why it sometimes does one way and sometimes the other way.

-Brian

---

