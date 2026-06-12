---
title: "flash based mp3 player/SD card wrong capacities"
date: 2005-10-30
forum: General Help
---

### Post by cius on 2005-10-30
I'm using breezy and I have a flash based mp3 player with 256 megs built in and a SD expansion slot with a 512 meg card in it.  When I connect it to my computer, breezy recognizes it and automounts it for me.  However, it only recognizes ths 256 built into the player as 19 megs and the 512 is recognized as 24 megs.  It will not let me put more on these drives.  My particular player is an ilo 256.  I checked the manufacturers site but they don't officially support use with linux.

Anyone have any ideas about how to get this working?

SOLVED!

Okay, I happened to plug my mp3 player into a windows box I have lying around and I noticed that there was a folder on both my internal memory and my expansion card called .trash-myubuntuusername.  I checked the sizes of these directories and guess what?  That's right, they were the exact size of the files I previously "deleted" from the player using nautilus.  I suppose its part for nautilus to send things to the .trash-user folder?  And that it doesn't send it all to the same place, but to a custom .trash on whatever drive its currently working on?  Not sure why else it would do that and not send it to the .trash in my user's home directory...  Anyway, issue solved.  I haven't tried yet, but I'm assuming a simple ls -a and rm .trash-user would do fine for clearing out everything on a linux box.

---

### Post by kspr on 2005-11-03
hehe duuh, i had the same problem. Thanks for the advice.

---

