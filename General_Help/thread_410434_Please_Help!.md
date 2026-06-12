---
title: "Please Help!"
date: 2007-04-15
forum: General Help
---

### Post by SpeedRacer on 2007-04-15
im very new to ubuntu and linux in general

ok well i got ubuntu with the intention of having a home media center library and when i tried to install linux mce it didnt work so i just figured id get rid of ubuntu partition and reclaim my disc space

big mistake

i ended up screwing up everything and since i dont have a windows disc i cant get rid of grub using the fixmbr method

i was able to get rid of the ubuntu partition but grub still tries to load at startup and of course i get errors all the time

the only OS i can use now is the live cd which is a major pain because it freezes all the time and makes me restart

i had to use my mp3 player to store anything i needed because i cant save to my HD from the live cd

all i need to know is if there is a way to get rid of grub using this live cd

my main windows partition on my HD has a error (screenshot included)

also the partition list is there if needed

altho it says boot next to hda1 i changed that because it wasnt before and i thought changing it would do something but it didnt so ignore that

thanks for the help

---

### Post by dfm21 on 2007-04-15
without a windows cd you can not reinstall the windows boot manager.

you could install grub and make it boot windows...

---

### Post by Famicommie on 2007-04-15
[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

You should be able to make a floppy bootdisk for XP, and use that to run fixmbr.

---

### Post by SpeedRacer on 2007-04-16
im unable to reinstall ubuntu it keeps freezing after i choose to resize the master partition

i figured it was something wrong with my partitions

thanks for the floppy idea ill try to find one around here hehe

---

### Post by FluffyElmo on 2007-04-16
Try *gparted* from the LiveCD, then resize your partition and reboot before trying to install Ubuntu. At least it may give useful error messages. Note that it may not be ossible to resize the partition without data loss if it isn't defragmented.

Also, if a media center is what you're after, MythTV is currently the best choice. If you get Ubuntu reinstalled give it shot... [https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV")

---

### Post by SpeedRacer on 2007-04-16
when i try to manually resize it it wont work so i couldnt resize the partition and when i choose the option to automatically resize the partition it freezes up.... so i dunno how to get ubuntu working cuz i cant install it again

im slightly confused as to which boot i need to use

a little help please?

i have xp home sp2 not sure how much that will help

---

