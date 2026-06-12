---
title: "Two quick questions..."
date: 2008-06-03
forum: General Help
---

### Post by xoligy on 2008-06-03
1. For some reason Firefox randomly closes and i dnot understand why, im using Firefox 3 Beta 5 (its not updated if there is one)

2. I need to run two copies of the same program (Komodo Edit) this is so i can keep track of where i am on two separate scripts in each one rather than getting confused. (no im no coding wiz im just learning)

---

### Post by Dr.Ninethousand on 2008-06-03
Firefox 3 apparently has some bugs, but I don't really use it..

you could try falling back on Firefox 2..  and you can have both installed at the same time..

to install firefox 2 :

sudo apt-get install firefox-2

---

### Post by xoligy on 2008-06-03
Thanks i'll give FF2 ago later :)

---

### Post by xoligy on 2008-06-03
Ooooh just thought of something else how do i keep a partition on another drive mounted? The drive is in the computer (500gig hd) but split into 3/4partitions and i have to click the icon twice just to access the music partition tis annoying!

Will mention its an ntfs partition!

---

### Post by Dr.Ninethousand on 2008-06-03
you need to add it to your fstab file.

it's simple, but since I don't totally understand if you are trying to get several partitions to mount or what, and I don't know the names of your partitions, I can't give you a good example yet.  I know how though, and can help with more info.

if you don't know how fstab works at all, you can find lots of info about it with a search.

---

### Post by xoligy on 2008-06-03
Ahh right cool its just one partition that i use the most its called "Movies and Music" the others are a rarity maybe once/twice a day is that the info you needed?

in system monitor it says: device: /dev/sdb3 directory: /media/Movies and Music/ type: fuseblk

---

### Post by navneeth on 2008-06-03
Re Firefox: Does it close immediately after you click the icon/menu item, or does it close randomly while you are using it? 

I had Firefox segfaulting a few days ago. See if typing firefox in the terminal results in a Segmentation Fault. If so, crete a new profile and see if that works properly.

```
fireofox -profilemanager
```

---

### Post by xoligy on 2008-06-03
Nah not right away its while using it, like before the first post i wrote the title and about 2lines and then "whoop gone!" been fine before as i browsed

---

### Post by Dr.Ninethousand on 2008-06-03
ok based on that info, it looks like you should add this line to the bottom of fstab:

```

/dev/sdb3    /media/Movies%20and%20Music   ntfs-3g   defaults,locale=en_US.UTF-8    0   0

```

if you don't know how to get into fstab and edit it, you use this command in terminal:

sudo gedit /etc/fstab


note that this won't take effect until a reboot..  I think the %20's are needed to represent blank spaces..  but that may not work..  

if I were you I would create a mount point without any spaces, just because using spaces always leads to some headache  :p


to do that, you could run this, or something similar, in terminal:

sudo mkdir /media/Movies_Folder

and then use that in your fstab line

---

### Post by xoligy on 2008-06-03
Thanks for the info will give it ago tomorrow, i best not loose the 144gig on there or i'll be after you! :'(

---

### Post by Dr.Ninethousand on 2008-06-03
nah, fstab only tells Ubuntu where to place partitions within the file-structure, and who has permission on those partitions etc...  it doesn't change the partitions themselves..

---

