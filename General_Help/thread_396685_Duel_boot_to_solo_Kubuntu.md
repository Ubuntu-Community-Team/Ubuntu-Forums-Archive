---
title: "Duel boot to solo Kubuntu"
date: 2007-03-29
forum: General Help
---

### Post by Clay_Banger on 2007-03-29
i have been duel booting my system with winxp and kubuntu for a while now, and i have just created and started perminatly using a virtual machine for the only windows program that i need, and now i havent booted up in2 my xp system for a while. so i plan to remove the partition that windows is on and resize all of my other partitions. My current setup is like this:

Partition 1: Fat32: 40gb: WinXp
Partition 2: Linux Swap: 1gb
Partition 3: Ext3: 10gb: Mounted as /
Partition 4: Ext3: 20gb: Mounted as /home/


So i have a few questions:
Where should my extra 40 gig go?
grub is on the boot sector of the windows partition, so by removing that partition, that would remove grub right?
is it ok to have the swap partition as bootable?

---

### Post by zvacet on 2007-03-29
Where do you want them.You can leave where is and use it for your data,music... or you can merge it with your home partition.How to restore grub you can read in **Tutorials&Tips**.Maybe put it in the floppy is good idea.read and choose method wich for you think it is best for you.For resize use Gparted Live CD.It is very good tool.

---

### Post by Clay_Banger on 2007-03-29
yes, i was going 2 use gparted, i already have a live cd burnt 4 it. i guess i will just add the extra data to both of my main partitions as i dont think the swap space needs to b any greater. i could merge my / and /home/ partitions together, but im not sure if this would create any problems. and the swap space wont mind being bootable will it?

---

### Post by zvacet on 2007-03-30
Do not merge root and home.You need home if some day you decide to make new install, reinstall...If home is on separate partition your data are safe and that is what you want.

---

### Post by domzo on 2007-03-30
Why not split your 40Gb into 30Gb extra for /home and 10Gb for a spare (K/X)Ubuntu installation? 

Personally I find it handy to have a spare Ubuntu installation for when I break something on the other one! Also you can do things like try an upgrade on one without risking breaking your other install. And if they both share the same /home directory then you have all your files on either.

Plus if you did this grub would be reinstalled in the new ubuntu! :) 

(If you did this you might want to edit the 'default' line in /boot/grub/menu.list to select which operating system you want to be the default at start up)

---

### Post by Clay_Banger on 2007-04-01
i like that, a spare partition 2 play around with other buntus. i think that will b the go. and keeping root and home separated. thx 4 all ur input ppl.

---

### Post by Clay_Banger on 2007-05-03
ok, i went ahead an deleted my windows partition, but now, during bootup, kubuntu still tries to mount sda1(old windows partition) and fails because it doesnt exist. is there anyway of telling it to never try and mount it again?

---

