---
title: "Safe to delete this partition?"
date: 2007-08-25
forum: General Help
---

### Post by olavjunior on 2007-08-25
I moved my home some time back, and I think I kept the old partition as backup, or installed feisty on a new partition or something, because now it seems there's a partition I don't use. 

Please see the attached screenshot. It's the sda5 I'm thinking of removing. Am I safe to do this? (I have unmounted sda5 and everything works fine afterwards, that means that I don't use this partition?) My home is on sda7, and I believe my os is on the sda2 (in the right part of gpared). After deleting that partition, I should be able to resize my home to this part, right? 

Any help is appreciated :)

---

### Post by dan171717 on 2007-08-25
a messy disk u got there... anyway you should be able to move it. u need to boot of a live cd to do it as all your partions are mounted

---

### Post by olavjunior on 2007-08-25
Yes, I know, it's very messy :( When I first installed Ubuntu I wasn't aware that you couldn't freely move partitions... stupid.  But thanx! :) Does it matter that it's kinda messy? It will get better now ;-)

**But is it a problem that it's a logical partition, and my home has a greater number (sda7) then sda5?? **(also the swap-partition is greater (sda6)
Is this a problem?

---

### Post by olavjunior on 2007-08-30
Well, you were very wrong! 

Deleting that partition, screwed it all up! Now my home-partition won't get mounted. F...!

---

### Post by forestpixie on 2007-08-30
can you post the output for the following

mount
cat /etc/fstab
sudo fdisk -l

---

