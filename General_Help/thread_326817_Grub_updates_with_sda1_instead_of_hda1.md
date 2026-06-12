---
title: "Grub updates with sda1 instead of hda1"
date: 2006-12-28
forum: General Help
---

### Post by rianquinn on 2006-12-28
When I do an update, my menu.lst file is updated as well. The problem is the location of the kernel is said to exist on sda1, when in fact it is on hda1. I can change it manually but I have to do this everytime I do an update. How can I tell the update-grub script to setup the menu.lst correctly.

Thanks

---

### Post by anaconda on 2006-12-28
I think I had the same problem...

You can correct the problem by modifying this line in your menu.lst
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

so that your #groot=(hd0,1) points to the correct hard-disk/partition.

---

### Post by anaconda on 2006-12-28
(hd0,1)
means the first hd and second partition
(hd1.1)
would mean second hd and second partition.

so whatever you have as the first number just change it to the other (0 or 1 if you have 2 hd:s)
And just check that the number of the partiton is right too.

---

### Post by rianquinn on 2006-12-28
Well I think I answered my own question here. See, if you have your boot flags setup correctly there is no need for changing which hd to look for grub. All I am looking for is telling the default install for the update-script to install to the hda instead of sda. I foudn the following in the menu.lst

```
# kopt=root=UUID=9dd0c5dc-5f9d-4db9-a197-49320cc1aeb9 ro
# kopt_2_6=root=/dev/sda1 ro

```

Once I changed this it seems to work ok. :)

Thanks everyone for you replies. 

I think that the above replies are for telling grub which grub to use, not which kernel to use. I could be wrong though.

Thanks again..... hope this helps someone else
Rian

---

