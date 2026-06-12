---
title: "Remove a partition and redistribute it's capacity ... easily?"
date: 2007-11-27
forum: General Help
---

### Post by bsh on 2007-11-27
Hello people
i have a task i'd have to do, but didn't do it yet coz i'm a lazy b-tard :)
i could do this alone but it's too much hassle, so i thought i ask around here, maybe some of you give me ideas how to do this easily.
ok: when i first tried ubuntu, i wasn't sure if i can use and set it up for my needs, so for safety, i created a dual boot system with the good old win xp on it - just in case i can't get away with ubuntu. but since ubuntu is so cool, i never booted to windows since then. so i'd like to get rid of its partition and redistribute the free space among the other partitions.
partitions are:
#1: primary: with windows xp, mounted in fstab with ntfs3g, read only (this is the one must go)
#2: extended:
       #3: logical: / for ubuntu, ext3
       #4: logical: /home, ext3
#5: primary: for data (shared with samba etc.), ext3
#6: swap
(note: i have had to use extended partition because there were more than 4 partitions)
i am not sure about the partitions' layout, but the windows partition is definitely the first one on the disk.

so i thought i boot from a live cd and remove the partition with gparted and increase the size of the others. that way i'm sure the partitions' numbers and id's would have changed and i'd have to modify my mounts in fstab, plus edit & update the grub, plus adjust some samba & other services. is there anything else i have to take into account?

alternatively i could backup all the partitions, dump the drive and create new partitions (and get rid of the extended partition as well), then restore my backups, and adjust the above.

another alternative would be to just "format" the partition with mkfs, then merge the space with the other partitions - i dunno how to do this but it's surely possible with ext3. this would be the easiest.

anyone with any other ideas?
thanks in advance.

---

### Post by ronmarley1 on 2007-11-27
In a side note, I'd use the gParted LiveCD as opposed to the Ubuntu LiveCD.  You can download the ISO here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

