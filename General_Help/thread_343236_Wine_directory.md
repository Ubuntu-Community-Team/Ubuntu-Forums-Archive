---
title: "Wine directory"
date: 2007-01-21
forum: General Help
---

### Post by Hillerd on 2007-01-21
Wine installs its Windows fake directory under /home/<my username>.
I'd rather have it on a different partition /<xxx>/wine.

I found this tutorial [http://wiki.jswindle.com/index.php/Advanced_Wine_User_Information#Changing_the_location_of_Wine.27s_installation](http://wiki.jswindle.com/index.php/Advanced_Wine_User_Information#Changing_the_location_of_Wine.27s_installation)
but cannot really make it work. 
Does anyone have experience with this?

Dietmar

---

### Post by dosnlinux on 2007-01-21
You may want to run winecfg and change the drive settings. change C:\ to your new directory.

---

### Post by Hillerd on 2007-01-21
> You may want to run winecfg and change the drive settings. change C:\ to your new directory. 
When I launch winecfg for the first time, it creates the windows directories. And they are under $HOME, whereas I want them somewhere else. So, I think I have to do something after Synaptic and before winecfg.

---

### Post by dosnlinux on 2007-01-25
try running winecgf, let it make the fake windows directory, then change the directory that c:\ points to where you want it and finally move the directories winecfg created to where you want.

---

### Post by dosnlinux on 2007-01-25
If that doesn't work, you may need to change the link in ~/.wine/dosdevices

---

### Post by YokoZar on 2007-01-25
Just move the ENTIRE ~/.wine folder to the other drive, and then create a symbolic link from ~/.wine to there.

---

### Post by Hillerd on 2007-01-27
>  try running winecgf, let it make the fake windows directory, then change the directory that c:\ points to where you want it and finally move the directories winecfg created to where you want.
Thanks dosnlinux, this does it. It is not exactly what I wanted, but is sufficient for the original scope to have the programs installed elsewhere. I updated a how-to in a german forum: [http://www.ubuntu-forum.de/artikel/242/HowTo-Wine---installieren.html](http://www.ubuntu-forum.de/artikel/242/HowTo-Wine---installieren.html)
Moving the whole .wine directory and creating a symbolic link (YokoZar's proposal) did not want to work, it was not able to find some system files.:D

---

### Post by dosnlinux on 2007-01-27
Glad you got it somewhat working the way you want :)

The ~/.wine directory is where wine looks for its configuration files, so you really can't get rid of it completly. (that I'm aware of) The drive letters can be changed though.

---

### Post by talowe on 2007-01-27
> **Hillerd said:**
> Thanks dosnlinux, this does it. It is not exactly what I wanted, but is sufficient for the original scope to have the programs installed elsewhere. I updated a how-to in a german forum: [http://www.ubuntu-forum.de/artikel/242/HowTo-Wine---installieren.html](http://www.ubuntu-forum.de/artikel/242/HowTo-Wine---installieren.html)
Moving the whole .wine directory and creating a symbolic link (YokoZar's proposal) did not want to work, it was not able to find some system files.:D

Not sure of exact syntax, but might try:

export WINEPREFIXCREATE=<path to where you want .wine> winecfg

This works (I think, I only use wine for one program) if you run this before running anything else on a "clean" wine install, i.e <rm -fr ~/.wine>.  I believe you can setup different WINEPREFIX's for testing purposes, etc. but that is beyond my experience.

---

### Post by fain on 2007-06-19
I have this problem but ive tried all in this thread but none works for me.

heres what im trying to do

i have 3 drives in my system. 
1 for os's
the other 2 are for a 320gb sata raid. for games and such.
i have 2 partitions on the ide one for vista and one for ubuntu 40gigs each.
now my wine dir takes up alot of that 40 gigs cause my windows games are in there.
so i want to move at least a virtual drive to the raid for more room.
when i point winecfg to drive_d on the raid partition 1
and move my drive_d folder to the mounted partition
the game will not start any more??
it works fine in my home directory.

i tried moving my whole wine dir to the drive and setting wineprefix to the /mount_point/.wine
i get the same errors.

heres a link to another post i put this error in.
[http://ubuntuforums.org/showthread.php?t=416791]("http://ubuntuforums.org/showthread.php?t=416791")

seems it has to do with some system files and dlls. i do not get these deferred errors when its all in my home dir.

---

