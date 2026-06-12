---
title: "Is this partition important?"
date: 2007-04-26
forum: General Help
---

### Post by Toby_rhino on 2007-04-26
I recently installed Feisty and it partitioned my HD the way it wanted. So it split up 60GB into the partitions in the image. My problem is that my previous Edgy install ran off one partition and i would like this to do the same, but there is another ext3 partition that I think is having programs installed on it, hence the 900mb of used space, but the drive says it's empty!

1) Is it safe to remove that other ext3 partition?
 2) if it has programs on it and i remove it how will this affect my system?

Thanks

---

### Post by eentonig on 2007-04-26
Did you check if there were hidden files as well?

---

### Post by Dylnuge on 2007-04-26
Where did you get your computer?

If you built it yourself, then that partition is yours, and you should check for hidden files.

If you bought it, it may be a special partition shipped with your PC for recovery or media playing or something similar. I have never seen one that big, but you never know.

---

### Post by Tomosaur on 2007-04-26
I myself have a recovery partition built into my machine, it's a little over 500mb though, and is formatted as Fat32. Could be worth checking, but I doubt you'll have a Linux recovery partition (which would explain the ext3), and doubt even further that your PC came with Ubuntu preinstalled :S

Best option is to just mount this partition and check what's there. If it's just old crap, you may aswell get rid of it.

There are advantages to dividing your system into partitions though, so you may want to rethink.

---

### Post by Toby_rhino on 2007-04-26
No nothing in hidden files, all that is on that partition is a 'lost + found' folder with nothing in it hidden or otherwise.

This is on my portable HD and i formatted it before i installed, so linux install created it.

---

### Post by Tomosaur on 2007-04-26
> **Toby_rhino said:**
> No nothing in hidden files, all that is on that partition is a 'lost + found' folder with nothing in it hidden or otherwise.

This is on my portable HD and i formatted it before i installed, so linux install created it.

Could just be some relic of the installation - I had files in my trashcan from my old install even though I told the Feisty installer to format the hard drive. If you're sure there's noting important there, I see no harm in wiping it.

Before you do, though, check whether it is in fstab. If it's there, be sure to get rid of it by deleting the relevant stuff in /etc/fstab too.

---

### Post by Toby_rhino on 2007-04-26
cool, thanks for all your help.

I'll try a few things and let you know how it goes.

---

### Post by chrisccoulson on 2007-04-26
The space could just be the journal. I always have some used space on a freshly formatted ext3 partition.

---

### Post by Toby_rhino on 2007-04-26
It worked, the partition is gone. Feisty works fine and apparently no data loss. 

Still unsure exactly why it said it had 900mb of used space as it caused no problems with programs or anything

Anyway, thanks again

---

