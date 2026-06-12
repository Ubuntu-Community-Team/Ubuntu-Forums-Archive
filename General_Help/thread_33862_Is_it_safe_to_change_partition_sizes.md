---
title: "Is it safe to change partition sizes?"
date: 2005-05-12
forum: General Help
---

### Post by kvdnberg on 2005-05-12
Hi all,

I have installed Ubuntu a couple of months ago on my laptop, as dual boot with WinXP. At first is was just to experiment, now I use Ubuntu all the time and WinXP hardly ever. I now want to give Ubuntu more space, taking away from a NTFS data partition meant for WinXP. I cleared enough space on the partition and am now ready to resize the NTFS partition and give the space to Ubuntu... but I'm not sure how to do it safely.

I have SystemRescue CD and the latest Knoppix CD, so I can do the resizing from there without having anything mounted. I want to make the NTFS partition smaller and prefereably the main linux partition bigger. Can I just resize both or is that bound to cause trouble? At first install I used partition magic at first to create the space for Ubuntu and afterwards used it because the NTFS partition windows was on was hidden and WinXP wouldn't boot, then partition magic wanted to 'fix' the partition table and my Ubuntu wouldn't boot, so I'm not sure what effect something like this would have on my Ubuntu system.

---

### Post by Kimm on 2005-05-12
depends on what program your using, if your using Knoppix you wount be using Partition magic i recon and I supose you'll use cfdisk or fdisk? As far as I know Partition Magic is a program designed for Windows Partions, so perhaps it writes something to the linux partion that linux does not like. Then again, I have never successfully resiced a linux partion so I supose you have more experiance then me in this field

---

### Post by void_false on 2005-05-12
I have successfully resized my linux partition with Partition Magic 7.0
... And it still works. :)

---

### Post by Ali_Baba on 2005-05-13
You could make a new Linux partition from that free space.Thats what i have done. Gparted is also good program in ubuntu,should handle that resizing.

---

