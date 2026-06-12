---
title: "software riad, lvm, and autodetection"
date: 2007-04-07
forum: General Help
---

### Post by upgrdman on 2007-04-07
I had my fileserver set up a while ago with four HDDs. two pairs of mirrored HDDs. i used lvm to convert the pair of raid arrays into one big sudo-partition. over time i needed two HDDs for other uses, so i pulled the mirrors, in effect elimination my raid but without telling the computer. after a while my ubuntu install was getting bloated due to my poor choices, so i decided to download 6.10 and install it fresh.

but i forgot to keep my config files. so i have two raid partitions... hda2 and hdc1. they are the two seperate raid arrays, and are no longer mirrored so while they are technically raid... there is zero redundancy. these two "arrays" were part of an LVM group too... and i have no idea where to start to autodetect the arrays and lvm setup to make the data visable again.

what can i do? i forgot most of my knowledge about software raid and lvm, as i setup my system over a year ago.

thanks,
--farrell f.

---

