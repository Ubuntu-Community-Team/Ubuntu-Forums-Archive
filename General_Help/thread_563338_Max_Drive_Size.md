---
title: "Max Drive Size"
date: 2007-09-29
forum: General Help
---

### Post by ke4ram on 2007-09-29
Partitioned a new 250.0g drive into 3 partitions approx 80g each. 


When trying to load 7.04 the partition manager reported 0 free space. Believing this to be a bug I chose ignore and wiped out the XP operating system. Re-did everything and it is again reporting 0 free space even though on the graph it displays 80gig. 


I had no problem when I first used a 20.0g drive. Everything worked fine.

Really don't want to go back to the 20gig drive. Whats happening here?

---

### Post by fjgaude on 2007-09-29
I believe you would get out of trouble if you made one of the partitions into unallocated space, and then let Ubuntu use that to install itself.

---

### Post by ke4ram on 2007-09-30
Did that. Loaded WinXp. Loaded UBU. Went to manual partition.

Here's the error messages...

First Message:

"The information sector has the wrong signature ( a0d7472 ). Select cancel for now and send in a bug report. If your desperate, it's probably safe to ignore".

I ignored it.... Then

Second Message:

"File space is reporting free space as 0 clusters, not 2366998 clusters".

I ignored it... 

Returned to the first message, then second, back to first etc...Merry Go Round

-------------------------------------------------------------------------------------------------------------------------

Next attempt:

Partitioned 2 partitions. Made two logical drives ( D & E )

Loaded UBU. This time I used the Guided Partiton wizard and moved the slider to indicate I wanted to use the entire 'E' partition. No errors... but got operating system error when trying to boot the newly installed UBU. 

Does anyone know of a really good STAND ALONE (Doesn't need Windows!) Partitioning Utility that can handle windows and linux ext3?

An old version of Ranish 2.4 is good but doesn't do ext3.

---

