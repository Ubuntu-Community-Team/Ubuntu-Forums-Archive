---
title: "Cant reach lubuntu anymore Only shows xp. Help this noob please!"
date: 2013-02-25
forum: General Help
---

### Post by yamach on 2013-02-25
Hello dear heroes and savers!

I had a laptop who was functioning well with Lubuntu installed in it. When i made it i made it 3 partitions 2 large one small, as 

1 large ntsf, 
1 large for lubuntu
1 lubuntu swap

So i installed and used lubuntu only, other part was empty for months. Until few hours ago when i stupidly decided to install xp. And i installed the win xp directly to that partiton which was ntsf.

As a result now my laptop directly open XP and i cant see anything of ubuntu. in win xp in my computer it sees hard disk as %45 of my total, so i think and hope it did not touch the other partition.

Please help me! i am more then willing to completely uninstall xp if it will be any help!!! all my staff is at lubuntu partiton but i cant even smell it!

---

### Post by lmarmisa on 2013-02-25
Your problem is easy to solve. You have to reinstall GRUB 2.

I recommend to follow this procedure:

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

---

### Post by arpanaut on 2013-02-25
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You will just need to reinstall grub into the mbr of your drive and upon rebooting the grub menu should appear with the option to boot Ubuntu or Windows

Post back if that doesn't work.

---

### Post by yamach on 2013-02-26
> **arpanaut said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You will just need to reinstall grub into the mbr of your drive and upon rebooting the grub menu should appear with the option to boot Ubuntu or Windows

Post back if that doesn't work.

solved the problem in minutes with this. Awesome. Another day which windows get my screwed and ubuntu saved my back. Thanks alot!!

---

