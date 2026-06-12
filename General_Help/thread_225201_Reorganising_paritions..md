---
title: "Reorganising paritions."
date: 2006-07-29
forum: General Help
---

### Post by Lunar_Lamp on 2006-07-29
My current partition system is a bit of a mess.  

I have the following partitions:

ntfs windows drive
swap
/
/home

I also have ~20gb of unpartitioned space.  I can't just resize the partitions I want due to the location of the space on the hard drve, and as they are all primary partitions I have to fiddle with logical drives.  My plan to sort it out is this:

Using partimage as per [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) to backup my / and /home partitions.  Delete my swap, / and /home partitions and recreate them the sizes I want them to be.  Use partimage again to copy the wanted files onto the new larger partitions.

What I want to know is whether tehre will be any problems with this - e.g. with grub not liking hard drive's changing around.  What do I need to consider?

---

### Post by jc750kwak on 2006-07-29
Why not just format it and use it to store your music files, photos or video? all of which can grow to consume many Gb's

If you format it as VFAT both Window$ and Linux can access it and you can have all your stuff available to both systems. That's what I do :D 

John

---

### Post by Steveire on 2006-07-29
You can simply resize the partitions. You will just have to move them first. I don't know what you mean about messing with logical drives.

---

### Post by djsroknrol on 2006-07-29
I used partimage to move my whole Ubuntu install to my 2nd HD while I resized my MS & Linux partitions using the GParted live CD...then I copied the Ubuntu partition back to its original partition (a whole lot larger partition) without a hitch...I left the image on the 2nd HD just for emergencies..

---

