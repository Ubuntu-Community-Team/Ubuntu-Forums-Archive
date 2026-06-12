---
title: "Adding a windows partition"
date: 2007-02-04
forum: General Help
---

### Post by Dylock on 2007-02-04
howdy
well ive been using ubuntu for some time now but some work i have to do for school has basically forced me to use windows.  Right now I have ubuntu instaled on my 80g HD and plan on use it exclussivly for linux.  I also have a 250g hd that I have been using for 'data' storage.  My intention is to add a 30-40g partition to the 250g 'data' hd to install windows on.  I fired up gparter and started looking around at it, I can resize the partition leaving a new space but now here is my question.  Do I add the new partition as an extended partition or as a primary partition. It seems that the only way to define a filesystem is to choose primary but that doesn't seem right. Also will windows run properly in an extended partition and also my data partition as well.

Any help on this would be great
Thanks
Dylock

---

### Post by kodoku on 2007-02-04
I think boot sectors can only exist on primary partitions, so if you want windows to be bootable, it'll have to be primary.

---

### Post by Dylock on 2007-02-04
will my data partition still function properly under ubuntu?

---

### Post by russo.mic on 2007-02-04
Not only does windows have to be on a primary partition, you need to install windows FIRST, because if you install it as a dual boot on a linux system, it'll run over any bootloader you have running, however most linux distros I know will just find windows and almost without asking just install a bootloader to work right.  

I'm sure theres a way to setup grub manually after a windows install, but i'm not sure what it is!

Good luck!

---

### Post by Dylock on 2007-02-04
so i would of had to install windows before ubuntu, or i have to have the windows partition first?

---

### Post by Dylock on 2007-02-04
ug well ive been reading around on the net and everyone seems to be saying to install windows first otherwise your hosed.  seems like there should be a way.

---

