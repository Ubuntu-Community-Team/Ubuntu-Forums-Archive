---
title: "Grub to look good"
date: 2007-10-06
forum: General Help
---

### Post by Tim4rd2000 on 2007-10-06
How could i get grub to look like this -http://www.zapisnicek.info/images/ubuntu-red.png

---

### Post by DagMan on 2007-10-06
you can download a grub splash screen at gnome-look or you can open an image in GIMP, go to colours and select indexed and change it to 16 colours and name it as an xpm image, most people call it splash.xpm.  gzip it at the command line,
**gzip splash.xpm**
then move it to /boot/grub
**sudo mv splash.xpm.gz /boot/grub/**
then edit /boot/grub/menu.lst so it has a line that says
**splashimage=(hd0,1)/boot/grub/splash.xpm.gz**
where (hd0,1) is the partition where your /boot directory is.  If it's on the first partition then it would be (hd0,0)

If you find an xpm image on the web then it needs to be gzipped.  If it is not xpm image format then open it with GIMP and save it as one then gzip it and move it as above.

---

### Post by eph1973 on 2007-10-06
That particular look comes from the way SUSE sets up GRUB.  If you just want a GRUB splash image, you could add it as said above.  Also, there is a package of splash images available from the repositories, called grub-splashimages.  And finally, I wrote a script you can use to help set up your menu.lst as you like it, located [here]("http://ubuntuforums.org/showthread.php?t=567971").

---

