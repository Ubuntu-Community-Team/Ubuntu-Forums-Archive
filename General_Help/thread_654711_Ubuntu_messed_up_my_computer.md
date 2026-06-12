---
title: "Ubuntu messed up my computer"
date: 2007-12-31
forum: General Help
---

### Post by NadeMaster on 2007-12-31
Okay.  I installed ubuntu yesterday so i was happy and all and during the installation how big i wanted to make my new partion so i said 180 gb cause i had plenty of extra space in the back of myu hdd.  well dont u know it overwrite xp and now i cant get the damn thing off.  i tired to restore my computer using acronis and i got this grub error.  then i wiped the hdd clean, then tried to restore it, nada (nothing).  Now when i boot my computer grub just keeps popping up for infinity.  I assume it wrote itself in the bios. HELP ME!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Mithrilhall on 2007-12-31
To get rid of Grub Fix MBR....

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by NadeMaster on 2007-12-31
k will get my disc now. thanks

---

### Post by NadeMaster on 2007-12-31
now i may keep linux on my computer but i need to ask something first.  now that i already restored xp is there a SAFE way to install linux without killing xp, i hagve acronis disk director so i can change my hdd to have free space and stuff like that.

---

### Post by meindian523 on 2007-12-31
you may use manual partitioning so that you yourself know exactly where partitions are being made for Ubuntu since you are the one determining them.

---

### Post by NadeMaster on 2007-12-31
when i tried that it was complaining about some swap and root thing.  any ideas for that?

---

### Post by Saint Angeles on 2007-12-31
yeah... if you follow directions, no data will be lost.

when installing ubuntu, during the partitioner theres an option that says:
Guided - use available space (or something along those lines)

if you do it that way, it will resize your current partition, addd the linux partition and then it will install grub.

ive helped about a dozen of my friends dual boot with ubuntu with no problems.

ubuntu didnt mess up your computer, you did.

---

### Post by Saint Angeles on 2007-12-31
> **NadeMaster said:**
> when i tried that it was complaining about some swap and root thing.  any ideas for that?
you want a swap partition thats about the same size as the amount of RAM you got, the remainder of the linux part will be mounted as "/"

---

### Post by meindian523 on 2007-12-31
It was not complaining,you need a minimum of two partitions to install Linux(any flavour)Those are the root(mount point:/,fileystem:ext3,size:usually 8-10 GB) and the swap(filesystem:linux-swap,size:usually 2*RAM).Again,the swap is not ultra necessary if you have 2 GB/more of RAM,but yet it's safe to keep aside half-a-gig for it.

edit: I still +1 manual partitioning,never had a problem with mine or my friends' installs with it.....and I was **not** there to guide them.

---

### Post by NadeMaster on 2007-12-31
k i will try the guided thing, i will make some unallocated space and try that. and if i do it manually i have 2.5 gb of ram, u are saying i need a 5 gb swap?!?!?!?!?!?

---

### Post by meindian523 on 2007-12-31
refer my post above.

---

### Post by EXCiD3 on 2007-12-31
Isnt it also true that if you plan on using Hibernate you will need at least the same size swap as you have RAM? If i remeber right, everything in RAM is stored to the swap partition during hibernation. Then you would need at least 2.5 GB swap.

---

### Post by NadeMaster on 2007-12-31
One last thing, i konw this may sound insane but i need to install a second version of windows xp on here.  so i will have 3 partions (technically 4) the swap, windows xp 1, windows xp 2, and linux.  Will grub be able to recognize two versions of windows xp and give me the option to boot off eithere?

---

### Post by meindian523 on 2007-12-31
Yes,install XP1,XP2,then Ubuntu and if Grub doesn't recognize them,we can help you to edit Grub and get all XPs into the menu. :)

Also,it's recommended that you also create a separate /home partition so that you can save your data and stuff when you upgrade(via clean-install) or change your distro.

---

### Post by NadeMaster on 2007-12-31
k man thanks for all of ur help.  will post back if i need anything else. :)

---

