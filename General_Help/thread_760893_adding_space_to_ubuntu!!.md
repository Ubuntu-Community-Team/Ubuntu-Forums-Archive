---
title: "adding space to ubuntu!!"
date: 2008-04-20
forum: General Help
---

### Post by mahmater on 2008-04-20
well ladies and gentlemen, on my PC I installed both win xp and ubuntu. the problem is that I've allocated only 8 GB for ubuntu. Now that I found it more appealing I'd like to take another 12 GB space from win xp (my total HD space is 40) and add it to my existing ubuntu? how can I manage that?

---

### Post by Joeb454 on 2008-04-20
You could always shrink the Windows XP partition again, and format the 12GB as ext2 (or ext3) and then Mount it in Ubuntu.

That would work like you want :)

---

### Post by mahmater on 2008-04-20
thanx 4 ur reply. u know, I have two problems with that :

1 my win xp 30 GB is split on three partitions C,D and E. that means that each has 10 GB. so which should I shrink? do I have to shrink all of them or there are some limitations?

2. on launching Gparted ,all the partitions have a lock icon in front of them. so I m given no option whatsoever.

many thanx.

---

### Post by sekinto on 2008-04-20
You have to unmount the partitions before you can edit them.

And actually the fact that WinXP is on 3 partitions makes things easier. Move all your data on E to D and/or C and then delete E completely.

---

### Post by elmer_42 on 2008-04-20
I think that if you delete one drive completely and set it to unformatted space, you can resize the Ubuntu partition.

---

