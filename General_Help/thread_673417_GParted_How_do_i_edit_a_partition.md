---
title: "GParted How do i edit a partition?"
date: 2008-01-20
forum: General Help
---

### Post by Dojan5 on 2008-01-20
Hmm...
I cant figure out how to use this program...
Sure, it show all the partitions...

|-----/dev/hda1/ 27.94gib----| |-----NTFS blah like 100gib-----|---- |linux swap 14.95gib----| |----hda4 15.something gib----|
Sorry i was too lazy to print all info out...
Well, errm, anyway...
I want to combine hda1 with hda4 and maybe decrease the size on Linux SWAP, i seriously dont need such a big swap... O_o
I forgot how it came there in the first place...
Well, the two EXT3 partitions, i want them combined, i made them for Kubuntu and Ubuntu when i didnt know it was just to install KDE :S
So, now i want to put them together but i cant figure out how to do...
Please help...
Thanks...
/
Joel

---

### Post by Dojan5 on 2008-01-20
Oh no...
I dont think it is possible since i have one as a boot and the other is running on Linux....
So.... it oughta be hard to make it since both would be busy...

---

### Post by pytheas22 on 2008-01-20
I'm a little confused by what you're saying, but if you mean that you can't edit those two partitions with gparted because they would be both in use by your system while it's turned on, all you have to do is get a live CD with gparted on it, like RIPLinux for instance [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/) , and you can edit all of your hard disk partitions from there.

---

### Post by banewman on 2008-01-20
You can use the gparted prog from the live cd - it's in the menu - then the partitions aren't active.
Then you right click a partition and choose one of the options.
Sounds like you may have to delete one partition then grow the other - but I would suggest making a partition for your /home.
:)

---

