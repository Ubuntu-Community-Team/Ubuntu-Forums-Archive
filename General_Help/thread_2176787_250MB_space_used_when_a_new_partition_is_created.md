---
title: "250MB space used when a new partition is created?"
date: 2013-09-26
forum: General Help
---

### Post by dshgna on 2013-09-26
Hi, just a small curiosity of mine.

When using gparted, I sam that when I created a new ext4 partition, approximately 250MB of free space was used up. I am curious about what this space is used for?

Thanks for everyone who can provide me some hints :D

---

### Post by dcstar on 2013-09-26
All journalled filesystems reserve space, there are already numerous posts on this subject in the forums.

---

### Post by dshgna on 2013-09-29
ok thanks :)
Respectfully, I am asking because my search terms did not give any answer.

---

### Post by 3rdalbum on 2013-09-29
Also, partitions don't completely butt up against eachother. It's not like this:

[------Partition 1---------][------Partition 2-----]

It's more like this:


[------Partition 1---------]............[------Partition 2-----]


And then of course, the filesystem itself takes up space, and reserves space for itself. For every partition you create, you lose space due to the gap between partitions and also due to having a separate filesystem on each partition. I'm not saying "don't create multiple partitions", I'm just saying that it's one of the tradeoffs.

---

