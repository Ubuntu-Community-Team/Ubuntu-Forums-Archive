---
title: "Gparted Partitioning Problem"
date: 2006-07-23
forum: General Help
---

### Post by kookookachooo on 2006-07-23
Hi, I'm trying to make a logical partition in my unallocated space (for music movies). I click new, and I move the size of the box to what I want. But when I try to change the partition to logical it does not let me select it; all i can select is primary. My question is, does it matter where the box is located? (left or right) and what can I do to make it so I can select logical? Many thanks appreciated in advanced.:D

---

### Post by reacocard on 2006-07-23
logical partitions need an 'extended' partition to hold them. create an extended partition of the size you want, then put the logical partition inside it.

---

### Post by kookookachooo on 2006-07-24
Thanks; sorry but, how would one do that?

---

### Post by reacocard on 2006-07-24
with gparted, of course. extended should be an alternate option to primary and logical.

---

### Post by kookookachooo on 2006-07-24
Hi, I opened up gparted and I selected the unallocated space and pressed new. When I go to select 'Create as' I can only select primary; I cannot select either logical or extended. Any other suggestions or solutions? THanks in advanced.

---

