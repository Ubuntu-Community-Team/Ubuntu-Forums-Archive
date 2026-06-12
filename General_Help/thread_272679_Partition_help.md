---
title: "Partition help"
date: 2006-10-06
forum: General Help
---

### Post by NoTiG on 2006-10-06
I have two hard drives.... on my second hard drive i want to install a / , /home, and swap partition. On my first partition i already have this..... 

BUT......... when using the partition editor during the install i cannot select my sdb (second sata) hard drive.... for manual partition editing. I can select the sdb hard drive.... and install ubuntu from scratch on it... but i cannot manually select the partitions up because in gparted on the live installer... it won't let me switch from sda to sdb . (some kind of bug, i filed it on launchpad)

So what i tried to do was boot up on my install on sda.... and use gparted from there to edit my second hard drive and setup a skeleton file system on sdb.

Now however, after installing on stb.... ubuntu installed around the partitions i created.

Now it looks like this:

/dev/sdb1     ext 3        # meant to be my root partition
/dev/sdb2     extended
   /dev/sdb5 ext 3         # meant to be my /home partition
   /dev/sdb6 linux swap    # meant to be my /swap
   /dev/sdb7 linux swap    # ubuntu installed swap here while installing
/dev/sdb3    ext 3         # ubuntu installed root here while installing

Ugh this is a mess. Furthermore when i used gparted while booted in my sda install.... i could not set mount points. 

So i guess i willl have to manually do this somehow. Im going to reinstall....... how should i setup a separate home partition? Should i just do abase install, leave however much space i want for the home partition... then afterwords use gparted from sda and create the home partition in the free space.... then somehow mount sdb from sda and copy /home to the new partition? 

It doesnt seem like gparted will let me change mountpoints or edit them. How do i do this????????

Here is a picture of the button that does NOT work during the live install. Right now it shows sdb correctly, but thats because i installed gparted after installing on the hard drive. for some reason it works now everything is installed... but not while installing.

[IMG]http://static.flickr.com/122/262607243_0ebe6d3685.jpg?v=0[/IMG]

---

