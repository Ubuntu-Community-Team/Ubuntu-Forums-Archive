---
title: "[swap] how to resize swap?"
date: 2008-05-31
forum: General Help
---

### Post by kakyoism on 2008-05-31
I have 4G RAM, although 3G accepted by Hardy, :(
my swap was currently set to 8G, which is way to big...
Can I reclaim some swap by shrinking it?
How?

Thx!

---

### Post by soapytheclown on 2008-05-31
no idea on the swap resize but if yr only seeing 3gb of ram then its likley yr not using the 64bit edition of ubuntu, prehaps u should try that and it should see all 4gb like mine does :)

---

### Post by Lord Xeb on 2008-05-31
If you have GParted installed (it will be in system>Administration>Partition Editor), use that to resize your swap. You cannot do it while it is in use, so you must do a Live CD to do it. Just go to the swap partition and right click on it and select "Move/Resize" Then set it to how big you want it (it must be in MB). You want your swap to be as big as the amount of ram you have, which is 4GB. Since 3GB is recognize, make your swap 3GB (3072MB). Once you are done, press apply and wait for it to get done.

---

### Post by MythosLegend on 2008-05-31
Just a side note. RAM > swap size means no hibernate.

Edit: Hibernate puts all your ram into the swap partition.
This may cause problems if you have a smaller swap size than RAM.

---

### Post by Lord Xeb on 2008-05-31
O_o what do you mean by that?

---

### Post by tromort on 2008-07-17
> **kakyoism said:**
> I have 4G RAM, although 3G accepted by Hardy, :(
my swap was currently set to 8G, which is way to big...
Can I reclaim some swap by shrinking it?
How?

Thx!

if you want to use the full 4gb, make sure you use the amd64 version of ubuntu and check your bios if there is a memory remapping option.
i had the same problem when i upgraded to 4gb, ubuntu only saw 3,2gb.
but the memory-hole remap option in my bios was disabled, after enabling it ubuntu saw 3,9gb :)

---

