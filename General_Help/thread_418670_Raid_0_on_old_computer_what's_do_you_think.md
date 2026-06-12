---
title: "Raid 0 on old computer what's do you think?"
date: 2007-04-22
forum: General Help
---

### Post by Biochem on 2007-04-22
I have a fairly old desktop: 
Pentium III 800 MHz
256 meg ram
HDa 20 gig
HDb 40 gig
no RAID hardware card

My second hard drive is becoming full but the small one (which contains only the OS) has plenty of space. So while I upgrade to Feisty I was thinking to partition  my hard drive this way

HDa1 7 gig Ext3 for OS only
Hda2 13 gig LVM
HDb1 40 gig LVM

This way I will have a smaller filesystem for the OS but a bigger home partition. Both HD are on the same ide controler for the moment so I don't expect any IO speed increase.[LIST=1]
[*]Is it a workable solution or am I heading for trouble?
[*]Are the specs too old? (I have no need for high performance but I don't want to slow down everything to XP speed)
[*]I know that with this kind of configuration I have no redundancy protection. I consider the risk of disk failure as acceptable. However is there any software problem that could corrupt the data as well?
[*]Is there any other issues I should consider?[/LIST]Thank you for your input

---

### Post by rich.bradshaw on 2007-04-22
Don't both drives in a RAID have to be the same size? Otherwise you will just get a RAID of size 13GB, wasting the other 27 on drive 2.

---

### Post by Biochem on 2007-04-22
Well, I seems like I really misunderstood a critical part of information. Raid 0 need everything to be the same size. Thanks Rich for pointing that

After looking around a bit LVM looks like what I'm looking for. However the same issues arise.

---

