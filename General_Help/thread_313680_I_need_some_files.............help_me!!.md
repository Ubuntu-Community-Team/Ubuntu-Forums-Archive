---
title: "I need some files.............help me!!"
date: 2006-12-06
forum: General Help
---

### Post by slyjelly on 2006-12-06
hi there

where can i find (either on my system or download) these files

libaa.so.1, libgpm.so.1, libncurses.so.5 and libslang.so.2

i need them to run a demo on my ubuntu 64

i can find shortcut type files on my system but not the files themselves

i have serached high and low both online and in synaptec and placed a different thread in the games area:

[http://www.ubuntuforums.org/showthread.php?p=1849395#post1849395](http://www.ubuntuforums.org/showthread.php?p=1849395#post1849395)

plz help!!:mad:

---

### Post by CatKiller on 2006-12-06
I don't really understand, but

[libaa]("http://packages.ubuntu.com/dapper/libs/libaa1")
[libgpmg1]("http://packages.ubuntu.com/dapper/libs/libgpmg1")
[libncurses5]("http://packages.ubuntu.com/dapper/base/libncurses5")
[libslang2]("http://packages.ubuntu.com/dapper/base/libslang2")

I've assumed you're on Dapper, since you haven't said. You'll be wanting to download the i386 packages rather than the amd64 or powerpc ones.

---

### Post by slyjelly on 2006-12-06
hi, thx for your reply tho im still stuck

basically i need those precise files to be in the folder where the installer is for the demo to work. i cant find the files on my system, only shortcut files which i cant use, so

im guessing i have to install a package via synaptec that creates those files(ibaa.so.1, libgpm.so.1, libncurses.so.5 and libslang.so.2 ). which package or library shall i install?

if your unclear as to why or maybe need a an explanation from a more expereinced user (im barely dipping my toes into linux), this link should help:

[http://tjwhaynes.googlepages.com/dropteamreview-part5](http://tjwhaynes.googlepages.com/dropteamreview-part5)

thx

---

### Post by slyjelly on 2006-12-06
oops, i forgot again,

my system is ubuntu64 10.0 edgy, (used for gaming mainly)

games run 200% better on linux than w"nkdows

---

### Post by CatKiller on 2006-12-06
Well, the pages I linked to have links to the .deb files that contain the files you want. Once you've downloaded the files, you should be able to extract the files that you're interested in from the .deb files and put them in the folder that you've installed the game to.

The shortcut files will tell you where they are shortcuts to - but they will be to the 64-bit files, and that reviewer specifically said that he needed the 32-bit files in that directory. Which you'll find in the i386 .debs.

---

### Post by SyvanX on 2006-12-06
Are you trying to build the demo from source, or is it a binary?
If it's source code, have you tried building it already, and what are your errors?
If it's a binary, have you tried running it and what are your errors?

This should install the libraries you're looking for
sudo apt-get install libaa1 libgpmg1 libslang2 libncurses5

---

### Post by slyjelly on 2006-12-06
thanks catkiller

my foolishness is highlighted by me not even realising that the filenames listed in your thread were actually links ](*,) 

problem solved...............:D

---

