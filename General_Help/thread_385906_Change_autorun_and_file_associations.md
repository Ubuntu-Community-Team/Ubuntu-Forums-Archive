---
title: "Change autorun and file associations"
date: 2007-03-16
forum: General Help
---

### Post by montgoss on 2007-03-16
Where do I change autorun and other file associations?

Things I'd like to change:
inserting a DVD movie - causes some unheard of media player to autorun.  I would like to use VLC.
double-clicking a .avi - causes the same unheard of media player to autorun.  I would like VLC or maybe mplayer
connecting my iPod - causes some music player to run that can't actually manage the files on the iPod.  I want gtkpod (the one I compiled because that's the only version that supports my 5G iPod).

I "grew up" on Windows.  But the Windows way of "right-clicking -> run with -> always use this program" doesn't work.  I don't really care that it doesn't work (although you could add it to the "run with" dialog).  I just want to know what does work.

Thanks!

---

### Post by 23meg on 2007-03-16
To change file associations, right click the file, click "Properties", go to the "Open With" tab and choose the application you want.

For "autorun", go to System / Preferences / Removable Drives and Media.

---

### Post by qamelian on 2007-03-16
To change file associations, right-click on a file of the type you want to change and select Properties. One of the tab in the properties box allows you to change the association. (Can't remember the name of the tab and I'm not home on my Ubuntu box right now)

---

### Post by arrrghhh on 2007-10-15
ok changing file associations is easy - what i want to do is change what program runs when a disc is inserted.  i could take or leave autorun, but it is a nice feature - now why won't it run vlc instead of totem?

i use xfce - i don't see a 'removable drives and media' anywhere.

---

### Post by wormser on 2007-10-15
> **arrrghhh said:**
> ok changing file associations is easy - what i want to do is change what program runs when a disc is inserted.  i could take or leave autorun, but it is a nice feature - now why won't it run vlc instead of totem?

i use xfce - i don't see a 'removable drives and media' anywhere.

You might need to right click on the menu and go to edit menus and check removable drives and media.

System> Preferences> Removable Drives and Media> Multimedia tab> Video DVD Discs> Put the command for the program you want to open.  Put in vlc %m.

---

### Post by arrrghhh on 2007-10-16
> You might need to right click on the menu and go to edit menus and check removable drives and media

System> Preferences> Removable Drives and Media> Multimedia tab> Video DVD Discs> Put the command for the program you want to open.  Put in vlc %m.

maybe i'm missing something here...

when i go to the menu editor i get this window
[img]http://img263.imageshack.us/img263/442/screenshot1ay1.png[/img]

i don't see anywhere to 'enable' Removable Drives and Media...


i've always wondered about this, because i'd like songbird to be under the 'multimedia' section, not on the main menu... i couldn't figure out how to place items within the sub-menus from that menu editor window...

---

