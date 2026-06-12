---
title: "How can I enlarge the size of my Ubuntu partition?"
date: 2008-03-29
forum: General Help
---

### Post by superbamaman on 2008-03-29
I made the decision to dualboot about two weeks ago. I have an 80gb harddrive and its 60gb Xp 20gb Ubuntu, now that I've tested Ubuntu and found I really like it I want to increase the size of my partition, is there anyway I can do this or do I need to reinstall everything? (I would like to still keep my windows partition because allot of people come over to my house and not all of them like ubuntu)

---

### Post by dcstar on 2008-03-29
> **superbamaman said:**
> I made the decision to dualboot about two weeks ago. I have an 80gb harddrive and its 60gb Xp 20gb Ubuntu, now that I've tested Ubuntu and found I really like it I want to increase the size of my partition, is there anyway I can do this or do I need to reinstall everything? (I would like to still keep my windows partition because allot of people come over to my house and not all of them like ubuntu)

Boot XP and do a few defrags of the Windows drive first, then:

Boot off the Ubuntu Live CD, use the Partition Editor to shrink the XP partition and then expand the Linux partition.

Windows will complain about the different Windows drive size on its next boot, but just let it sort itself out and then it will work as normal after that.

---

### Post by superbamaman on 2008-03-29
thanks, but do I just quit after editing the partitions?

---

### Post by anjilslaire on 2008-03-29
I use a GParted Live CD to do this stuff. It'll let you resize your partitions, then you reboot and your done.
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Works great :)

---

