---
title: "Get Ubuntu7.04 to recognize new partitions."
date: 2007-07-10
forum: General Help
---

### Post by rlmerrick on 2007-07-10
I recently added 2 new partitions to some free space on my hard drive and cannot get the os to recognize them. First I tried grub-install, update  and recheck. I ended up just editing menu.lst. This didn't work so I tried editing fstab and this worked for 2 other partitions that were not previously recognized but not the 2 new ones. I listed the UUID's and copied them into fstab, so I know that much worked  for the old partitions.( fdisk sees  them all so that is covered)
What other file must I edit, or program to run in order to let Ubuntu see these drives?
I know it's something it does on install, but I would prefer not to rerun the install if possible.
(I did try to reinstall but it wanted to format my root partition in order to rewrite the partition table.)
I have searched through the help system and the forum to find a similar problem and solution, but have turned up naught. Any help would be appreciated.   
Thank you

---

### Post by stchman on 2007-07-10
> **rlmerrick said:**
> I recently added 2 new partitions to some free space on my hard drive and cannot get the os to recognize them. First I tried grub-install, update  and recheck. I ended up just editing menu.lst. This didn't work so I tried editing fstab and this worked for 2 other partitions that were not previously recognized but not the 2 new ones. I listed the UUID's and copied them into fstab, so I know that much worked  for the old partitions.( fdisk sees  them all so that is covered)
What other file must I edit, or program to run in order to let Ubuntu see these drives?
I know it's something it does on install, but I would prefer not to rerun the install if possible.
(I did try to reinstall but it wanted to format my root partition in order to rewrite the partition table.)
I have searched through the help system and the forum to find a similar problem and solution, but have turned up naught. Any help would be appreciated.   
Thank you

Follow my procedure to mount partitions.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by bobmerrick on 2007-07-11
:)
Many thanks, it worked. I'll mark the reference for further study.

---

