---
title: "[SOLVED] Problems after resizeing partition"
date: 2007-09-30
forum: General Help
---

### Post by ostlund on 2007-09-30
I have a problem with my /home-partition. I first resized it(first it was 50Gb but i haved a lot of space left on the disc so i resized it) with gparted on the liveCD. but after the resize was completed i got some problems. The /home partition has the same amount of space left as before the resize, but instead of getting all the new Gbytes, the new Gbytes are listed as used.
All the data on /home har intact so the data wasent corrupted. Is it some error with the partition table or what?

Like this:
Old /home: 50 Gb (7Gb Free)
New /home: 250 Gb (7Gb Free)

How can i solve this? I guess it has something to do with the partition table.

Edit:
Gparted shows the info above, while "df -m" shows the total size as it was before.  Fdisk says that the same about the size as gparted.

---

### Post by prince_niceguy on 2007-09-30
Use disk analyser to see which directory is taking lot of space. if you can figure it out there might be some hidden directory or something taking all your space.

---

### Post by ostlund on 2007-10-01
I maby expressed myself wrong but 200 Gb of data can't just show up from nowhere. I resized the /home partition and just after that it cant be 200Gb of hidden files. It's the same amount of data if you check it.

---

### Post by az on 2007-10-01
Did you resize the filesystem on the partition?  You may have accidentally only enlarged the partition without telling the filesystem to actually use the rest of the space.

---

### Post by ostlund on 2007-10-01
SOLVED

aZ: Yes that was the problem. Gparted in some way only resized the partition. Therefore fdisk and gparted showed the right new size but "df" didn't. 
"resize2fs" fixed it all.

---

