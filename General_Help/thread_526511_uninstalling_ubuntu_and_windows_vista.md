---
title: "uninstalling ubuntu and windows vista?"
date: 2007-08-15
forum: General Help
---

### Post by samee on 2007-08-15
hi i need to completely remove ubuntu version 7.04 and windows vista because i need to install windows xp, then vista then ubuntu. BUT I HAVE A PARTITION ON THE HDD FOR DATA I DONT WANT TO TOUCH.

what is the best way to remove the Ubuntu partitions and vista partition without touching the data partition? 

i have come up with this boot from the live cd and open the partition manager in the live cd and then delete all the partitions for ubuntu and vista and not the data partition and then convert them to NTFS. i believe that the MBR should state nothing at this point, to install xp first then install vista then install ubuntu. 

correct me if i have said any thing wrong etc. thanks in advance

---

### Post by backflop on 2007-08-15
Would it be possible to erase the information on the ubuntu and vista partitions, then make one smaller so you can create a new partition on which to install xp. (probably the former ubuntu partition since it only requires 2 gigs to install compared to vista's recommended 40 gigs). And since can use Gparted to do all partitioning, no data will have to be erased. I think that was what you were looking for anyway.

---

