---
title: "[SOLVED] Getting rid of dual boot and windows partition"
date: 2008-07-05
forum: General Help
---

### Post by gardara on 2008-07-05
I have been having a windows/ubuntu dual boot on my laptop for over a year now, but since I haven't booted up windows for about 9 months I have decided to get completely rid of it.
I unmounted my windows partition and erased it with gparted, so now I got 20gb of unallocated space which I would like to merge with my home partition. 
However I can't seem to be able to do that with gparted, the resize/move button is disabled.

Any ides how I can do this?

---

### Post by avtolle on 2008-07-05
For starters, you will need to use a Live CD (the one you have for Ubuntu, or one you create by going to the gparted website). If you were trying to resize while booted into Ubuntu, the / partition was in use.

---

### Post by gardara on 2008-07-05
> **avtolle said:**
> For starters, you will need to use a Live CD (the one you have for Ubuntu, or one you create by going to the gparted website). If you were trying to resize while booted into Ubuntu, the / partition was in use.

Aaah ofcourse the partition can't be in use while I do this... how silly of me :lol:
Thanks for pointing that out :)

---

### Post by sethd32 on 2008-07-05
btw...congrats on ditching windows altogether, its a great feeling isn't it!

---

### Post by gardara on 2008-07-05
> **sethd32 said:**
> btw...congrats on ditching windows altogether, its a great feeling isn't it!

Yup it's a great feeling... I thought I needed to use some windows applications but after having not booted it up for 9 months I found out there is nothing I'm seeking for that's only available for windows.

If I need to use something windows only in the future I think I'll just make a quick virtualbox install and then get rid of it again as soon as possible.

---

### Post by gardara on 2008-07-05
Ok so I booted up a livecd of ubuntu 7.04
I am able to resize the home partition but I am not able to use the free space that is left after the deleted windows partition...
How can I merge that empty space with my home partition?

---

### Post by lswb on 2008-07-05
If the former windows partition is not physically contiguous with the home partiton, they cannot be merged. However, if you want to take the time, you could move things around, (you really do have a /home partition right? not a /home directory on your root partion?) 

Note that while I have never lost data as a result of using gparted for copying/shrinking/expanding partitions, I would never attempt to do so without backing up first. Even if gparted works perfectly, a power failure or something could mess up the whole deal.

Another alternative to consider is to use the partition as is, just put an ext3 filesystem on it and use it for storing music files, pictures, etc. You can make symlinks from your home directory to directories on the new partition.

---

### Post by neilevan814 on 2008-07-16
How would one symlink to a new partition.  the reason I ask is because I have got a bunch of /media partitions in my extended volume..not was I was aiming for ..but things went awry and so be it....so I would like to be able to take full advantage of these partitions ....any suggestions would be great.  I'll include a snapshot of my gparted table.  If you are wondering why dev/sda3 is missing, I originally thought I had set that as a boot partition, but when the install completed, I ended up with a very small media partition..so i just deleted it...things work okay.  What i would really like to do is just remove the two smaller media partitions and group that with the one larger one...but I have a feeling this gets messy....suggestions...yes that is what I need.  Thanks! Neil

---

### Post by chex_m8 on 2008-07-16
0

---

### Post by chex_m8 on 2008-07-16
> **gardara said:**
> Ok so I booted up a livecd of ubuntu 7.04
I am able to resize the home partition but I am not able to use the free space that is left after the deleted windows partition...
How can I merge that empty space with my home partition?

I'm not totally sure about this but one reason they may not be able to merge is because the windows partition was prime and your linux stuff is in an extended partition.

---

### Post by lswb on 2008-07-16
"How would one symlink to a new partition...

The "ln" command makes links, from a terminal you can type "man ln" for all the gory details but it's fairly straight forward:

Say you have a partition that is mounted as /data with a directory /data/media where mp3 files are stored. To make a link in your home directory named Music,

  ln -s /data/media Music

Now you can access Music like any other directory. You could put the link on the desktop if desired. You can make a link like this in several places if you want, they can all be used to access the same directory /data/media, but more conveniently.

The -s option to the link command means to make a symbolic link, rather than a hard link. Usually a symlink is what you would want, and it's required when the link is being made to another partition anyway.

---

### Post by gardara on 2008-07-25
> **lswb said:**
> If the former windows partition is not physically contiguous with the home partiton, they cannot be merged. However, if you want to take the time, you could move things around, (you really do have a /home partition right? not a /home directory on your root partion?) 

This seems to be my problem, why I can't move things around...

> **lswb said:**
> 
Note that while I have never lost data as a result of using gparted for copying/shrinking/expanding partitions, I would never attempt to do so without backing up first. Even if gparted works perfectly, a power failure or something could mess up the whole deal.


What is the best way to back up my partitions? I have some external hdd's with plenty of space where I could store my backups... Can I back it up with gparted?

---

### Post by lswb on 2008-07-25
Using gparted is an easy way and how I do it myself. There is an option to copy a partition. Just copy the partition to one of your USB drives. It can take a while to make the copy, but it's not too bad with USB 2.0 (USB 1.1 is slow though)

---

### Post by gardara on 2008-07-29
> **lswb said:**
> Using gparted is an easy way and how I do it myself. There is an option to copy a partition. Just copy the partition to one of your USB drives. It can take a while to make the copy, but it's not too bad with USB 2.0 (USB 1.1 is slow though)

Allright I did that and it seemed to work, rearranged my partitions like I want them and it all went successfully through.
But my grub doesn't seem to like those changes and every time I try to boot now I get Grub error 17, how should I fix that?

Edit: I think I've fixed it myself with the help of this page: [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Edit2: or maby not, it didn't quite work as I hoped

Edit3: just had to change hd (0,1) to hd (0,0) All fixed now and windows is gone forever! :D

---

