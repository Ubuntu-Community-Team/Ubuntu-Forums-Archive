---
title: "Gnome and Xorg crash hard. Movie Player/Azeurus related?"
date: 2008-01-28
forum: General Help
---

### Post by RKDN on 2008-01-28
While playing an mp3 in Movie Player gnome will suddenly freeze up... I force quit out of Movie Player but then suddenly anything I have open closes and I can't open anything else. 
When I try to log out of gnome all of the icons on the log out dialog are gone leaving only the words. when I click on logout my system completely crashes and I am left with a blinking cursor with a black screen and I have to do a hard reboot.

This same thing would happen when I was downloading files with Azeurus it would say that it couldn't write to a read only file system and then crash. and then the gnome would die off the same as with the Movie Player crash.

---

### Post by RKDN on 2008-01-28
[IMG]http://img401.imageshack.us/img401/5346/screenshothw0.png[/IMG]

---

### Post by RKDN on 2008-01-28
anyone got any ideas?

---

### Post by cdaringe on 2008-01-28
hey man.
well, heres what you can do to get some help comin you're way.
open up a terminal, type "totem". movie player will show up.
then open up a movie or clip that you think will make it fail.
the terminal window will spit out some output when your movie starts playing, and when the error occurs, it will likely have some info.
post to us the output of that terminal.
at least it will help us get started

---

### Post by RKDN on 2008-01-28
I tried what you asked me to do... but there was no output on the terminal... :S

---

### Post by RKDN on 2008-01-28
if it helps any... the error happens instantly if I click on edit in movie player... if I don't then it takes a while of playing the song

---

### Post by RKDN on 2008-01-28
Got it to error out and my computer is dieing as I speak..... hopefully this posts...


(totem:5983): Gtk-WARNING **: Theme directory 32x32/emotexs of theme Aqua-Glade_PNG has no size field

** Message: Error: Could not read from resource.
gstfilesrc.c(814): gst_file_src_create_read (): /play/source:
system error: Input/output error


(totem:5983): Gtk-WARNING **: Error loading theme icon 'gtk-dialog-error' for stock: Failed to read from file '/usr/share/icons/Tango/scalable/status/gtk-dialog-error.svg': Input/output error
rkdn@rkdn-laptop:~$

---

### Post by cdaringe on 2008-02-01
hello again.
this may be above me.

i did some googling on your error to no avail. what kind of file are you playing?  also, might i ask, why are you using mplayer / totem as your audio file player?  perhaps because its just selected by default.  id recommend amarok, rhythmbox, or xmms.  to change your program that opens a music file, right click an mp3(or other media), select properties, then 'open with' and select it from there.  from then on out, all similar type files will open with such and such program that you selected

ill keep my eyes peeled for ya.

---

