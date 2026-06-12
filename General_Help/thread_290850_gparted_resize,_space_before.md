---
title: "gparted resize, space before"
date: 2006-11-01
forum: General Help
---

### Post by mikewhatever on 2006-11-01
Hello to all,

I was trying to resize an NTFS partition on my HP DV5269ea with GParted live CD. It is a 65 GB partition with Windows on it, and in GParted it showed like this: dev/sda1/. I was trying to shrink it to 25 GB to make space fore Edgy Eft and Fat32 storage partition. In the same window, where to choose the new partition size, there were options for free space before and after the partition. I didn't know what they were for, nor did remember anything about it in the documentation, so i ignored them, went straight for the new size option, and typed 25. However, the resize button remained grey and unpressable, until the free size before value remained 0. Changing the value to 1,2,3... and so on made it possible to go on, but I had no idea how much free space should there be, both before and after. I would greatly appreciate some clarification on the subject.
Thanks in advance.

---

### Post by bsussman on 2006-11-01
Quick answer:

NONE before, if you want the win partition to still work.

After?  How much do you want?  there is no single answer.

Of course backup and defragment the disk before doing this somewhat risky operation.

---

### Post by mikewhatever on 2006-11-01
Well..., as I said, there was not option to go on, so, owing to the fact, that I was not sure, I cancelled resizing. Perhaps I'll just try the alternate CD.

---

### Post by mikewhatever on 2006-12-17
OK, although it's been some time since this thread was started, I thought it might be a good idea to post how the issue got resolved. Apparently, GParted could not resize, because it was unhappy with the state of the partition. By accident, having the partition highlighted, I clicked on Partition->Information in the Menu. A window came up with a message about inconsistencies, and the necessity of CHKDSK check. After running the check, I was able to resize the partition the way I wanted, which really only took about five seconds.:-D

---

### Post by Duppy on 2007-01-19
Did you use CHKDSK in windows?

---

### Post by derekdb on 2007-02-06
Many thanks-will follow your cues.  Will probably get there-if not Watch space,   derekdb:)

---

