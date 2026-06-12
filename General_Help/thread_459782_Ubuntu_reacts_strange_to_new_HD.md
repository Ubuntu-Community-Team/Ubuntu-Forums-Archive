---
title: "Ubuntu reacts strange to new HD"
date: 2007-05-31
forum: General Help
---

### Post by Gio-van-I on 2007-05-31
Hi there

I was hoping to get some words of advice on a my current experience, cause it's driving me nuts...

This is the situation.
My old HD was having some problems due to age/use (western digital 120 GB IDE). So I decided to get a new one (hitachi 500GB SATA).
To keep it short: old one out, new one in. There where no issues from the motherboard (asus a7n8x-e).
I partitioned the disk in the following parts:
*primairy partitions
8 GB / (ext3-Ubuntu)
1 GB swap
16 GB NTFS
*logical partitions
100 GB fat32
100 GB fat32
100 GB fat32
140 GB NTFS
I installed windows and Ubuntu and everything worked fine.
After I installed Azureus things went wrong.
First I tried to save a file to the first fat32 partition. This ended up in receiving a nullpointer exception addressed to the HD.
After that I decided to save the file to my home folder located on the first partition. This went fine for a while but after a while my download speed went from 50 Kb to 0 and back to 50 again. This continued for a while and then the speed ended up at 0.

Now I know the problem isn't related to configuring azureus. I know the program inside out.
I suspect it's some HD issue, but I can't tell what it is.
Anyone know what the problem might be or how I can find out what it is?
Might I have broken a rule with file system sizes or something alike?!

Thanks for any help,
 Gio-van-I

---

