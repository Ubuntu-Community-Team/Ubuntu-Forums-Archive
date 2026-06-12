---
title: "Help with partitioning for an idiot"
date: 2008-05-19
forum: General Help
---

### Post by Frogster on 2008-05-19
Having jumped in feet first with a sink or swim attitude it now six months since i installed Ubuntu. I now have two PC running it and a have just noticed that this machine seems to have three sets of partitions on it! 

I had two failed installs and the third was successful.

How do I get to one swap file and extend into the unallocated space?

All I get when I try to resize in GPARTED is "It is not possible to create more than 4 primary partitions"

Help

---

### Post by Cap'n Skyler on 2008-05-19
i feel your pain frogster
-that is what turned me off from slackware--was getting thru the darn partitioning!!
i *believe* you can and will have to delete any or all of the old partitions
 that you can.then you can re partition the rest of the HD to whatever suits you.i have had multiple linux installs that i did not understand i had done,and did not know how to get rid of the unwanted installs,then some of these were damaged or corrupted (and could not boot)and i had to just do a total clean re install and that squared it all away. 
anyone have partitioning for idiots 101?
i'll be reading it too LOL
:popcorn:

---

### Post by Cap'n Skyler on 2008-05-19
and  i think part of your issue is having them called "primary" partitions.perhaps delete 2 of them and name the new as extended partition.
 will Gparted let you do that?i think it should.:popcorn:

---

### Post by strabes on 2008-05-19
> How do I get to one swap file and extend into the unallocated space?

Boot the ubuntu live CD and run "sudo gparted" from a terminal on the live CD. In gparted, delete the (primary) partitions you are not using. Click on the swap partition and extend it to 2x the amount of ram you have. If you have greater than 1gb of ram, only make it equal to the amount of ram you have.

---

### Post by Frogster on 2008-05-20
Thank you all for your help. I will go a head and sort this out!

Its just another learning curve :)

---

