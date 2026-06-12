---
title: "Ubuntu and Windows DISAPPEARED!! (grub)"
date: 2008-04-12
forum: General Help
---

### Post by Nnako2 on 2008-04-12
Hi everyone. First of all, thanks a lot for your help.
My English is poor but I hope I'll understand your instructions.

My PC has Windows XP and Ubuntu 7.10 in 2 different partitions.

A few days ago, WIndows didn't run on my PC.
When I tried, I was gotten a blue screen with exactly THIS MESSAGE:

error windows stop: 0x00000024 (0x00190203,0x87306de8,0xc0000102,0x00000000)

It wasn't the 1st time this happened to me, so I tried with Windows XP CD to repare it, but this time the only solution in the CD was to format all the partition and reinstall Windows, and I didn't want to lose any data so I did nothing with the CD.

When I rebooted the PC, I used to see Grub where I could choose between Ubuntu and XP (or I was redirected to Ubuntu in 10 secs), but this time Grub had disappeared... It started directly with Windows and the blue screen..

I've also tried Gparted with the Ubuntu CD Live. This is what I get:
-Ubuntu partition (luckyly not empty)
-Windows partition (empty and with an [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] as if there was an error)
-Extended and Linux Swap (locked)
-A Windows partition (that was always in the PC to restore Windows)


I hope I gave you enough information for you to help me.

Thanks a lot again

---

### Post by chewearn on 2008-04-12
I haven't personally used this myself, but a lot of people swear by the supergrub disc for repairing grub:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

