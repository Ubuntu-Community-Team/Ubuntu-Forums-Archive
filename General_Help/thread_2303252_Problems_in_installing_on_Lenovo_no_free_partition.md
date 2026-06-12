---
title: "Problems in installing on Lenovo: no free partition"
date: 2015-11-17
forum: General Help
---

### Post by lorenzo-milesi on 2015-11-17
Hi.

I'm trying to install Ubuntu on a brand new Lenovo laptop but I ran into an issue: the computer comes with already 4 primary partitions created!
The first one should be Windows' boot, the second is recovery, the third Windows itself and fourth is the suspend "cache". Given this situation I cannot automatically install Ubuntu.

I was considering to delete the suspend partition, resize the data one, then create the extended ones and recreate the suspend inside that.
The problem with this solution is that that partition appears **unknown** to GParted, so I'm afraid I will not be able to recreate it after Ubuntu installation. 

Has anyone had experiences with Lenovo or such partitions?
thanks

---

### Post by kurt18947 on 2015-11-17
If it's a new machine, I'd think it's UEFI BIOS/GPT partitioned disk  and wouldn't have the 4 partition limit. I don't have a newer machine - I'm just guessing so please wait for someone more knowledgeable than I to check in. It's recommended to use Windows Disk tools rather than Gparted to manipulate Windows partitions.

---

### Post by leunam12 on 2015-11-17
Before you do anything clone your hard drive using clonezilla or another cloning tool; that way if anything goes wrong you can go back to square 1.

Shrink your drive in Windows; press WINDOWS + R then type diskmgmt.msc and right-click the drive and select "shrink volume". When you are done go to Ubuntu live USB , then create the partitions that you need  in Gparted. Make sure that you boot as UEFI. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

