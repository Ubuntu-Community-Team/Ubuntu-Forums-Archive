---
title: "Grub setup fails"
date: 2007-05-24
forum: General Help
---

### Post by tsantos on 2007-05-24
I have a partition on a hard disk with a Feisty install on it and everything works fine.  The grub on that drive points to my partition for /boot/grub and I never have problems.  I wanted more disk space so I bought another drive and used dd to copy my partition to the new drive.  The new drive didn't have grub on it so I found my Dapper install CD and booted from it.  I then did the following commands in grub:

root (hd0,1)
setup (hd0)
quit

My copy of Feisty is in partition 1 so that should have been a fine thing to do (with the same /boot/grub directory that was on the original setup on the other disk).  The problem is that, when the computer boots, I get a blinking cursor... that's it.  No grub.  If I do the following:

root (hd0,0)
setup (hd0)
quit

Then everything goes back to normal because I have a new Dapper install (for trying to solve this problem) on partition 0.  In fact, I can boot my feisty install from there (the one on partition 1).

Is there something magic about my grub install on partition 1 that makes it just sit there at boot time... drooling?  Since there's no feedback, I can't tell what its problem is.

I'm completely mystified.

-Tom-

---

### Post by booljayj on 2007-05-26
Maybe the error lies in using dd to copy your partition. You may want to try installing Feisty from scratch and manually copying your files over.

---

