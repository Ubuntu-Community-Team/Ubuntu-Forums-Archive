---
title: "fdisk does not see NTFS drive"
date: 2007-11-27
forum: General Help
---

### Post by SudoPenguin on 2007-11-27
Hi guys

I've installed Ubuntu 7.10 on a new hard drive.

Now I've put in an old NTFS drive with lots of stuff on it I'd like to move to the ext3 partition.

Problem is, sudo fdisk -l doesn't find the NTFS drive...

So how can I find it and mount it? 

(I can see it's there during boot)


Best regards,

Lukas

---

### Post by ajgreeny on 2007-11-27
Could this be a problem with jumpers on the disk?  Is it set as slave to your original master or the other way round?

---

### Post by SudoPenguin on 2007-11-28
OMG!!!

I had set it to the "Master with slave present" setting instead of "Single or master" setting. 

Thanks for making me check again, aj. i had checked already, but somehow failed to see it. 

And I was starting to doubt the excellence that is Ubuntu. (Shame on me)

Now I didn't even have to mount the drive. Ubuntu found the partitions at once and loaded them even though they're ntfs and fat.

Love it.

Best regards, 

Lukas

---

### Post by SudoPenguin on 2007-11-28
Problem solved!

---

