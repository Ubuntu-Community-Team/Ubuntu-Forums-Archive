---
title: "Move / to a different partition?"
date: 2008-04-29
forum: General Help
---

### Post by danhm on 2008-04-29
I used to dual boot Windows and Ubuntu on my laptop, but no longer need Windows on it so I formatted it away. Is there away I can easily move everything except for my home directory to what was formerly my Windows partition and keep my /home on what is currently my Linux partition without having to backup my /home and reinstall from scratch?

---

### Post by overdrank on 2008-04-29
> **danhm said:**
> I used to dual boot Windows and Ubuntu on my laptop, but no longer need Windows on it so I formatted it away. Is there away I can easily move everything except for my home directory to what was formerly my Windows partition and keep my /home on what is currently my Linux partition without having to backup my /home and reinstall from scratch?

Hi and you can use gparted on the live cd, it sounds like you are asking just to resize you existing liux partitions make use of the unused partition.

---

### Post by danhm on 2008-04-29
> **overdrank said:**
> Hi and you can use gparted on the live cd, it sounds like you are asking just to resize you existing liux partitions make use of the unused partition.

No, I know that. I want to seperate my root directory from /home. They are currently on the same partition.

---

### Post by sdennie on 2008-04-29
I think overdranks advice is still correct.  You can delete/resize/move/add from gparted using an Ubuntu live disk.  If you delete the Windows partition via gparted, you should be able to extend a linux partition to use up the space.  You could also shrink your current / to something smallish (10G should do it) and use the rest of your disk for /home.  However, depending on the size of your disk and the way you need to move around your partitions for contiguous space, it may take several hours to do (I "moved" a 140G partition 30G forward on my disk the other day and it took about 4 hours).

Edit:

And, once you have a large /home, you can just temporarily mount your new /home directory, tar up your old directory and then untar it into what you want to become your new /home partition.  Then mount that new partition as /home and you are done.

---

### Post by sanus|art on 2008-04-30
Just to add to vor's post - I think you'll have to edit grub/lilo (whatever you're using) for those changes to work.

---

