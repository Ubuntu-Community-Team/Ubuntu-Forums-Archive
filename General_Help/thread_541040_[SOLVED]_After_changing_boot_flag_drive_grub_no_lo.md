---
title: "[SOLVED] After changing boot flag drive grub no longer sees xp"
date: 2007-09-02
forum: General Help
---

### Post by Super TWiT on 2007-09-02
I was having a problem getting grub to see my install of DSL-N and as an experiment changed the drive that had the boot flag to the dsl-n partition using Gparted.  When I ran sudo update-grub it didn't find DSL-N or xp.  I changed the boot flag back to the way that it was with Gparted and ran sudo update grub again and it  see xp or DSL-N.  Is there any way to get grub to see xp and maybe DSL-N?

---

### Post by Nathan_M on 2007-09-02
Try checking that the name of the partition hasn't changed. I've made that mistake several times.

---

### Post by Super TWiT on 2007-09-02
Thanks for replying:KS  I checked and the partition names are still the same.

---

### Post by raul_ on 2007-09-02
Just to be sure, the boot flag must be checked in both Linux and Windows's partitions

---

### Post by Super TWiT on 2007-09-02
Thanks for replying:KS I don't think Gparted will let me flag both the Linux partition and the XP one.  It only lets me choose one.  It was by default the XP partition so that is what I set it to.

---

### Post by raul_ on 2007-09-02
I have both my partitions flagged, because Grub only "sees" the partitions that are boot flagged, otherwise, there is no point in "booting" them

---

### Post by Super TWiT on 2007-09-02
This might not have been the best way to fix the problem but here goes.  I installed Ubuntu on another partition, copied the menu.1st file from it, formatted the partition, and finally I overwrote the menu.1st file with the copied one.  There was probably a better way to do it but I wasn't able to find it.  (I didn't look that hard!:))  Thanks everybody who helped me!:KS  This community is great!

---

