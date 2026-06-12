---
title: "A few questions"
date: 2007-12-13
forum: General Help
---

### Post by Steeltwist on 2007-12-13
Ok so i've decided to dualboot ubuntu with xp. I kinda know how to do it, but i just wanna make sure i dont screw anything up. I get to the part where it talks about partitioning and i'd like to choose the first option. It says somethin like Resize IDE1 master, partition #1 (hda1) and use freed space or some mess. Well i say how much i want it to use for ubuntu, and a message pops up.

The message says something about all the data on the space i chose would be lost, and that the changes couldnt be undone. What i wanna know is, since i chose free space, do i have anything to worry about? What will be lost? Also, what does it mean it cant be undone? Is it saying linux cant be uninstalled? When i do get it installed, how do you uninstall it if you want to and get all the space back?

Thats about all i need to know. Nooby questions i know. Help would be appreciated.

---

### Post by kpkeerthi on 2007-12-13
It should be pretty safe. But before that, boot into Windows and defragment your drive. Run your favorite defragger atleast twice. This is required to avoid possible data loss when the ubuntu installer resizes the partition. 

Now come back to Ubuntu installer and resize the partition. Do not try to pack your Windows partition too tight. Leave enough free space for Windows. 5GB or more is a good choice. I suggest atleast 10 GB of free space for Windows.

> 
What i wanna know is, since i chose free space, do i have anything to worry about? What will be lost?

You don't have to, generally. But remember you are resizing a partition that already has data in it. It is quite possible that you may lose that data when you are shrinking the partition. To minimize the chance of data loss, I already suggested you to defragment the partition. Ofcourse, there is no guarantee that all your data will remain intact. We can only minimize that risk.

> 
Also, what does it mean it cant be undone?

It means if you happen to lose data while resizing, there is no way to recover the data. 

> 
Is it saying linux cant be uninstalled? When i do get it installed, how do you uninstall it if you want to and get all the space back?

No. You can wipe of linux and use the reclaimed space for Windows. You can use gparted for this (available in Ubuntu Live CD). Vista can do this too.

---

