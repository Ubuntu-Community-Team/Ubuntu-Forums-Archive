---
title: "strange crash"
date: 2007-10-08
forum: General Help
---

### Post by petay on 2007-10-08
Hi

I am an avid linux user and apart from the job (winapps development :( ) i use ubuntu whenever and wherever i can, i even use my ubuntu lappy for work with a bit of vmware

Today i got home from work and tried to convert an avi into an mpeg, i had done it earlier at work and it all went well.

it started with a jerky mouse, then things got slower and slower unill when i came back to my lappy a few hours later i found that almost everything from my status bar had vanished and i had no mouse pointer or anything.

after a few resets (ctrl + alt + backspace does nothing, nor any of the F keys to get to a terminal) i managed to squeeze in a ps -fu petay to see what was happening to be greeted with a screen full of the same 3 lines over and over i couldnt keep the system up for long enough to copy and paste but i did get a picture on my mobile hence the poor quality.

i donned the usb boot slax and looked on the hdd for the files which were in use, namely /usr/share/appor...... and /usr/bin/lsb_rel......
i managed to find apport and lsb_release and renamed them to stop them running.

rebooted ubuntu and everything now seems to be working!!!

anyone any ideas if i should change the file names back??? or even what might happen if i dont???

Thanks 

Pete

---

### Post by petay on 2007-10-09
sorry again for the poor image

It is now up and running for work and all seems well!!!
running beryl, evolution, firefox, gaim, skype, gedit, and a vmware full of hexpee and its running like a charm again!!!

Could this be some kind of virus or something???

seems strange how this could suddenly come on!!

---

### Post by Sef on 2007-10-09
> Could this be some kind of virus or something???

There aren't any viruses in the wild for GNU/Linux.   Probably just a hiccup, so don't worry about it, unless it reoccurs.

---

### Post by petay on 2007-10-09
I know that linux is virus free, thats why i use it for email and the web!!

There may become a time though when virusses do start to become a problem. im sure there was a time when windows was virus free!!

it is running ok now because the files that were constantly being run are now renamed so the system cannot find them.

There may be a chance that if i were to change the names back it would all grind to a halt again!!

 there must be something triggering the same apps to be run hundreds of times. rebooting 4 times didnt fix it!!

Pete

---

### Post by petay on 2007-10-10
ok so i changed the names of the files back so that the os could see them again and so far all is well!!!

I will keep my eye on my processes though!!

had it been hexpee i would of formatted by now!!!

Pete

---

