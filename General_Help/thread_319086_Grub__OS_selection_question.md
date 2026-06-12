---
title: "Grub / OS selection question"
date: 2006-12-15
forum: General Help
---

### Post by Exillo on 2006-12-15
Hi everyone, 

I've just finished setting up my dual boot with Windows XP. When I turn on the computer and it comes up with the OS selection screen (sorry I'm still unsure about what to call it and whether that is the GRUB or what) I want it to automatically go to XP in 9 seconds rather than Ubuntu in 9 seconds. 

Any answers would be hugely appreciated, thanks!

---

### Post by anaconda on 2006-12-15
edit your /boot/grub/menu.lst
with:
sudo nano /boot/grub/menu.lst
and search the line with 
default 0
and change the 0 to be the number of your windows entry in the grub menu.
Just remember that counting starts from 0..

---

### Post by Exillo on 2006-12-15
Super fast response, I'm not entirely sure *how* to edit my /boot/grub/menu.lst but I'll do some experimenting (or maybe I should have posted this in the absolute beginners forum, hehe).

Thanks!

EDIT: Ok, this is harder than I thought... (well not really :p) 

I went into the terminal and put in /boot/grub/menu.lst and hit enter but it came up with 'Permission Denied'. 

Again, any help would be great. :)

---

### Post by drr422 on 2006-12-15
you should do the following first to back up your menu.lst:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

and then to edit the menu, do the following.

sudo gedit /boot/grub/menu.lst

The reason that you get the permission denied error is that /boot is a "root" owned folder and normal users don't get to edit it.  Normal users usually only get to change things in their individual /home/user directories.  I'm just telling you this so you know whats going on.  The first command that i gave you made a copy of the /boot/grub/menu.lst so that if you accidentally mess it up, you can load a live cd, mount the partition that has the /boot folder, and then you can restore it by copying it back to where it was, with the following:

sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst  

keep in mind that when you mount it on the livecd, it will most likely be mounted in your /media folder, so your commands should reflect that if your trying to restore it.  

The second command opened up the menu.lst with gedit with "sudo" powers (meaning you can edit it and save the changes, or in other words administrative access) .

---

### Post by Exillo on 2006-12-15
Awesome... got it working, thanks heaps guys. :-D

---

### Post by drr422 on 2006-12-15
cool, its nice getting everything working perfectly.  I usually tweak it until i break something.

---

