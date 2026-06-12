---
title: "All partitions are gone?"
date: 2007-08-23
forum: General Help
---

### Post by Nevon on 2007-08-23
I have several partitions, spread out over 2 hard drives. On one of these partitions I have Windows XP. All partitions except the ubuntu partition and the swap are NTFS. This has worked perfectly, but now when I logged onto ubuntu, no partitions were shown. It's like they're not mounted anymore.

I have no idea why this happened, but I'm guessing it happened after I installed a partition manager in windows XP. However, I didn't actually do anything with the program before uninstalling it, so I don't see why it would mess anything up.

Anyway, when I go into gparted, I can see all partitions. But they don't show up on my desktop, nor do they show up in the "places" menu. When I go into /media/ I see sda1, sda5 and sb1 (plus cdrom and all that) but they don't contain anything. Before, sda1 was my windows partition (I think), sda5 was my storage partition and sb1 was the second hard drive. 

So, what should I do to get them back? I don't know if they're mounted or not. But since I can't see them anywhere except in gparted, I'm guessing they're not. So how to I mount them?

---

### Post by merlinus on 2007-08-23
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

-merlin

---

### Post by Chymera on 2007-08-23
You get this error if you don't shut windows down nicely. just log into windows again and give it a peaceful shutdown with ye olde red button under start> .

---

### Post by Nevon on 2007-08-23
Oh it works. Thank God that all I had to do was restart windows.

Thanks guys!

---

### Post by Chymera on 2007-08-23
Not to mention it, i had the same problem and was about to give up when i accidentally came across this little detail. :)

---

