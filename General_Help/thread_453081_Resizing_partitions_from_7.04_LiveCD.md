---
title: "Resizing partitions from 7.04 LiveCD?"
date: 2007-05-24
forum: General Help
---

### Post by sheniferous on 2007-05-24
I currently have both XP and FF installed on my Fujitsu P5020. When I installed FF I didn't resize the partitions correctly and am left with a swap file partition that is much smaller than I want.

I currently have a 120GB drive and have allotted 30GB for XP and the FF is allotted 70GB with the swap being only a meager 2GB and a XP backup partition of 2GB.

[IMG]http://farm1.static.flickr.com/219/511778122_39940e6ad9_o.jpg[/IMG]


I would like to resize the FF partition to 30GB with the swap resized to fill the void and recognizable by both XP and FF.

What would be the best way to do this? Through the FF 7.04 LiveCD running GParted? What steps are necessary to do this?

Thanks a lot in advance!

---

### Post by joriad on 2007-05-24
I burned a downloaded gparted iso image to a separate cd and ran gparted that way and not through the fiesty live cd.

---

### Post by ivesjd on 2007-05-24
Either way should work, it would probably be easier to use the live cd since I'm guess you already have it.

---

### Post by sheniferous on 2007-05-24
Okay, when I unmount the FF partition and resize it, I'm left with 40Gb of unallocated space and there's no way for me to resize the remaining swap file, anyone have any insight into this? Thanks for the responses so far!

---

### Post by joriad on 2007-05-24
Where is the unallocated space in relation to the swap partition?

---

### Post by loathsome on 2007-05-24
I had to unmount the partition I was going to work on **before** I launched gparted!

---

### Post by ezrollers on 2007-05-24
> **sheniferous said:**
> I currently have both XP and FF installed on my Fujitsu P5020. When I installed FF I didn't resize the partitions correctly and am left with a swap file partition that is much smaller than I want.

I currently have a 120GB drive and have allotted 30GB for XP and the FF is allotted 70GB with the swap being only a meager 2GB and a XP backup partition of 2GB.


Your swap partition is more than plenty.

I seem to recall that as a general rule

ram =< 1 GB                            swap = ram i.e 1 GB
1GB < ram < 4 GB                   swap = 0.75 ram
ram > 4 Gb                              swap = 0.5 ram

You could delete both the swap partition and the 40 GB one and reallocate them as you see fit.

---

### Post by joriad on 2007-05-24
> **sheniferous said:**
> Okay, when I unmount the FF partition and resize it, I'm left with 40Gb of unallocated space and there's no way for me to resize the remaining swap file, anyone have any insight into this? Thanks for the responses so far!

I found this at [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html)
> 4.4.2. How large can my swap space be?

Currently, the maximum size of a swap partition is architecture-dependent. For i386, m68k, ARM and PowerPC, it is "officially" 2Gb. It is 128Gb on alpha, 1Gb on sparc, and 3Tb on sparc64. An opteron on the 2.6 kernel can write to a 16 Tb swap partition. For linux kernels 2.1 and earlier, the limit is 128Mb. The partition may be larger than 128 MB, but excess space is never used. If you want more than 128 MB of swap for a 2.1 and earlier kernel, you have to create multiple swap partitions (8 max). After 2.4, 32 swap areas are "officially" possible. See setting up swap for details.

footnote: "official" max swap size: With kernel 2.4, the limit is 64 swap spaces at a maximum of 64Gb each, although this is not reflected in the man page for mkswap. With the 64 bit opteron on the 2.6 kernel, 128 swap areas are permitted, each a whopping 16 Tb! (thanks to Peter Chubb for the calculation) 

depending upon your system you may be maxed on the particular swap, however you may be able to create another swap partition

---

