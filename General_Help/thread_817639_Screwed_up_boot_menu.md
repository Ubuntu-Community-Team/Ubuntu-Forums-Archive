---
title: "Screwed up boot menu"
date: 2008-06-03
forum: General Help
---

### Post by JESSU on 2008-06-03
I screwed up the boot menu trying to neaten it up. Now when I boot to Ubuntu there is no GUI. Can someone please write a walk through for me? I need to know exactly what to type. I need to edit the boot menu so Windows XP boots defalt. I duel boot with Ubuntu on the second hard drive(D). XP is on the C drive.

I am setting up my old computer for my grandma to use and she only knows how to use XP. She is really computer challanged so I am not even going to introduce her to linux. She doesnt even know what an OS is. I myself am rusty with linux because I am been using my XPS M1330 non stop.

---

### Post by Sam Lars on 2008-06-03
So you have two issues?  The boot menu and the no GUI?
Were you editing the /boot/grub/menu.lst?  If so, could you post that?  XP should be first to make it the default.

---

### Post by JESSU on 2008-06-04
Yep thats what I was editing. Yes there is 2 issues. I can't post it because I don't know how to get to it without the GUI. The one in XP is diffrent.

---

### Post by Sam Lars on 2008-06-04
Once you log in, you can use the nano program to edit files.
```
sudo nano /boot/grub/menu.lst
```
The important part is the section at the bottom with the entries for different kernels.
I'm not sure the no GUI is connected with the menu.lst.

---

### Post by drs305 on 2008-06-04
> **Sam Lars said:**
> Once you log in, you can use the nano program to edit files.
```
sudo nano /boot/grub/menu.lst
```
The important part is the section at the bottom with the entries for different kernels.
I'm not sure the no GUI is connected with the menu.lst.

If you can do what Sam suggests, you might also try File, Open, and then go to /boot/grub and see if you have any backed-up menu lists (e.g. menu.lst~ or menu.list.bak or something that you or a program may have saved earlier). If you do find an older file, you might rename the current menu.lst to something else, open the backup, rename it *menu.lst* and see if it will boot.

Or you can post the results of:
```
cat /boot/grub/menu.lst
```
and someone here can help you.

---

