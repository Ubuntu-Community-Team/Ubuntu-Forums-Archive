---
title: "Apache, how do you set /var/www to 2nd HDD?"
date: 2005-10-03
forum: General Help
---

### Post by waynejkruse10 on 2005-10-03
I have rebuilt my server computer, now with a P3 800mhz, 512mb Ram and 2 HDD's. I am doing a fresh install of Ubuntu Hoary on my small HDD (4gb) but i want instead of the /var/www to be on the drive the system is on, i want it to be on the other drive.

Thanks
Wayne

---

### Post by Zelut on 2005-10-03
well you could create a symbolic link at /var/www/ to the second hard drive.  for example your second drive is at /home/drive (whatever) you'd want to try #ln -s /www/var/ /home/drive (I believe).  check out the man pages for ln (man ln) and find the correct syntax.  That way anything in /var/www/ would just point directly to the second drive.

---

### Post by az on 2005-10-03
Breezy has a better tool for setting mountpoints.  As it is in Hoary, you have to do that by hand.

A mountpoint is the way you access a hard drive in your filesystem.

You probably need to add a line in your /etc/fstab like this

/dev/hdb1       /olddrive               ext3    defaults,errors=remount-ro 0       1

Where hdb1 is the device (first partition on hdb) and /olddrive is the name of the directory that will be your olddrive when you mount it.

Then execute 

sudo mount -a

to mount everything.

---

