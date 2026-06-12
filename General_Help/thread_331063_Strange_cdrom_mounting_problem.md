---
title: "Strange cdrom mounting problem"
date: 2007-01-04
forum: General Help
---

### Post by matrix560 on 2007-01-04
I just installed Ubuntu 6.10 .Now I need to use my Ubuntu cd-rom to make some updates.  I actually have 2 cdroms but the problem is that when I put my cd in the cdrom, Ubuntu mount it not in /media/cdrom but in a different place ( in /media/cdrecorder for the first cdrom and in /media/dvdrecorder  for the second). 

 The problem is that when I click on cdrom a get a folder (Ubuntu 6.10 _Edgy Eft_ - Beta i386 (20060908.2) which is the folder that represent my cd but this folder is empty.  I know that my cd is ok because when I click on cdrecorder or dvdrecorder I can see the content of my cd.

When I wanna update with apt-get or with Synaptic Package manager they tell me to insert my cd.  It's like the cd is not mounted at the good place.

So how can I make the link between cdrecorder (or dvdrecorder) and cdrom  ??

Thank you

---

### Post by kidders on 2007-01-04
Hi there,

The names of the mount points you use for filesystems don't really make any difference. If you'd like to change them though, you can do it by modifying /etc/fstab, or the appropriate udev rule, depending on how your system works.

You can symbolically link two locations with **ln -s**.

---

