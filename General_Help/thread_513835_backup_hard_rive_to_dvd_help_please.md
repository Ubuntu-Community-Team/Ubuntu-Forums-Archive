---
title: "backup hard rive to dvd help please"
date: 2007-07-31
forum: General Help
---

### Post by dragonwings on 2007-07-31
i have tried 

remastersys and made a live cd runs installer but frezes after grub
                       also made a back up disc didnt work.

clonzilla        live i have got as far as loading it to ram cant figure the rest out .

sysrescuecd  had trouble withformatting dvd+rw stoped at 93%. couldnt put  udf filesystem on it
in general commands didnt seem to work as if they were out of date ????

atponcd        could not find anything to copy apart from it own atponcd file

i am using 3.2 gb of my 80gb hard drive ubuntu 7.04

please if you can help me to make a complete copy of my hard drive and put it on dvd so i dont have to reinstall with dailup every time or if i want to change to anothewr hard drive etc.

basicly    i want to make my own live dvd with installer of my current set up

---

### Post by nimajiman on 2007-07-31
I'm not sure about how to make a live DVD with installer, but one method for backing up your HDD would be to run partimage from a ubuntu live cd. You need one partition you can mount however that is NOT the one you want to backup, so for example if you have / and /home on different partitions, you could mount / from live cd and backup /home to it, and vice versa.

Just pop in a ubuntu live cd, and when it loads uncomment the lines in sources.list (sudo gedit /etc/apt/sources.list) that are commented out (can't remember which repos they are but they're the only ones commented in the file), and then run 

sudo apt-get update
sudo apt-get install partimage

from terminal.

Say you want to backup hda1, and have enough free space on hda2, then mount hda2

sudo mount /dev/hda2 /media (for example - you can mount it where you want)

then run partimage from terminal and follow the programs instructions. 

It takes a bit of getting used to, but I now have a complete snapshot of my harddrive that i can restore if i botch up something terribly. From loading the live cd to beginning backup takes me about 2 minutes, and then you can burn the backed up file to a CD/DVD for storage, and restore it later using the same process (though kind of in reverse) if necessary. If you have a really big HDD, partimage can split the backup file into chunks so you can burn it onto multiple DVD's etc, and can compress pretty well also.

Not sure if this is what you are after, but it might help in the meantime while you search for a more efficient way.

---

