---
title: "Need help moving boot partion to new drive"
date: 2014-03-10
forum: General Help
---

### Post by sturdy on 2014-03-10
Hi,

I want to move my Saucy install to a partition on another drive (ssd). I thought I had accomplished same except every time I boot to the ssd partition it actually boots from the original copy on the hd. The ssd partition remains unmounted. Here is what I did:

Used "dd if=old of=ssd" to copy old partition to new ssd partition. Flagged ssd partition as bootable. Ran Boot Repair to fix Grub.

Clearly there seems to be something in the copied files that continues to point to the old hd. I looked at fstab but it looks okay (to me). Can someone point me in the right direction? TIA

Sturdy

---

### Post by oldfred on 2014-03-10
Better to just do new install.

Only if not leaving same drive connected may dd copy work as a back for a drive on the shelf for emergeny boot.
Your dd also copied UUID, you have to change UUID, edit fstab & reinstall grub. Plus usually some other changes depending on install. 
Often quicker or easier to to reinstall and copy /home over.

But with SSD & rotating drive, I have / (root) on SSD, actually two 28GB / partitions on my 64GB SSD. One current & one future and then I have all data in data partitions on rotating drive. The only thing remaining in /home is hidden settings. I even move larger data partition like Firefox & Thunderbird to data partition.

---

### Post by sturdy on 2014-03-10
Thanks oldfred, of course you are correct. I've been doing this stuff for more years than I care to remember and I still tend to get lost in the chase. Often it is more expedient to start from the beginning.

---

