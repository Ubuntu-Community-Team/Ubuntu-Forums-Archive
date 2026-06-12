---
title: "Lost Partition Table"
date: 2007-01-16
forum: General Help
---

### Post by evanmanny on 2007-01-16
Up until recently I had been happily dual booting Windows and Ubuntu on my computer. Then spontaneously Windows stopped booting correctly. I decided to reinstall Windows and figured that I could just reinstall grub on the MBR afterwards. Unfortunately this is proving much harder than I had hoped...

When I put the Ubuntu install cd in and try to reinstall grub it exits with exit code 20. I couldn't really find much information on this exit code on the web. I put in a gparted live cd though and to my dismay the whole drive showed up as unallocated. I have an aching suspicion that this has something to do with grubs failure.

Now I'm thinking that Windows most have overwritten the partition table. There is a glimpse of hope however, as when I'm in the Ubuntu installer it recognizes the partitions. If I execute a shell it asks me whether I want to do it in hda1, hda2, etc. I don't remember 100% but I'm fairly sure that the files were still intact when I executed the shell too. But as soon as the partition manager comes up it once again thinks that the drive is unallocated.

I'm definately in over my head here, if somebody could help me out I would be overjoyed.

---

### Post by evanmanny on 2007-01-16
As an update I've checked that the partitions are all fine when I access them from the rescue shell. Fdisk also lists the partitions as they should be. Any ideas on why gparted and the ubuntu install cd wouldn't be able to see the same partition table that fdisk sees when I'm in the rescue shell?

---

