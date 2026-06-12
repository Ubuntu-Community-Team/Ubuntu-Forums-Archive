---
title: "Free some space on /"
date: 2013-07-14
forum: General Help
---

### Post by ogoun on 2013-07-14
Hi,

some weeks ago I switched from Arch to Ubuntu and used my old partitions.

/ is 10 GB what was more than enough for Arch.

Now, still using the same programms as before (e.g. LibreOffice, Inkscape, LaTeX, Gimp), I always get a warning that there's no more space on / (250MB remaning).

I already tried apt-get clean but the problem still exists.

So, do you have any ideas what I can do to free some space on / ?

TIA

---

### Post by snowpine on 2013-07-14
Ubuntu is not Arch. 10gb is too small in my opinion for the full-featured (some would argue "bloated") glory that is Ubuntu, especially if you are going to install large apps like LaTex. I recommend to resize the partition using a Live CD and Gparted. 20gb is probably good, but again, it depends on the applications you plan to install. 1TB drives cost less than $100 so there is no reason to cram Ubuntu into 10gb in the year 2013.

---

### Post by vanadium on 2013-07-14
I do have an 8.9 G root partition with Ubuntu 13.04, and no problem whatsoever (6.9 G used currently). However, I have my home on a separate partition and I am redirecting the temporary directories /tmp and /var/tmp from the system partition to the separate home partition using mount bind.

---

### Post by oldos2er on 2013-07-14
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by ogoun on 2013-07-14
Thanks for your replies and the useful link.

I just found another reason for my low disk space: I have 1.2GB full of old kernel images. Wasn't aware of this since Arch just "overwrites" the old one.

---

