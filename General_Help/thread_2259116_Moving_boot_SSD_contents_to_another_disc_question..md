---
title: "Moving boot SSD contents to another disc question."
date: 2015-01-02
forum: General Help
---

### Post by sir-marky on 2015-01-02
I have Ubuntu 14.10 installed on a Corsair SSD but am becoming a little nervous at the increase of smart errors appearing from it.

I am considering the purchase of a new SSD to take over the role but don't want to reinstall Ubuntu, my programs, configs, etc. from fresh.

If I use clonezilla to image the disc to my BTRFS array and then use that to write to the new SSD, edit grub and reboot, will that work for me?

Am I missing a step or two?

My system has,

[LIST]
[*]120GB Corsair SSD mounted at /
[*]4 x 3TB hard drives in a BTRFS RAID 1 array mounted at /mnt/btrfs
[*]1 x 1TB hard drive containing Windows 8.1 with an option to use it in Grub.
[*]Ubuntu 14.10
[*]32GB RAM
[/LIST]

---

### Post by Bucky Ball on 2015-01-02
Not missing anything I can see. Clone with Clonezilla then plop on a partition as big or bigger than the original (the original partition size, that is, not based on the amount of data in the partition, e.g. 100Gb partition but OS only takes up 20Gb, you still need to use a 100+Gb partition to clone it back to). You can shrink the partition you are going to clone if there is a lot of free space that won't be used (if you have your data on another partition and only the OS on its own partition this might be the case).

Then edit grub or install it using boot repair.

---

### Post by sir-marky on 2015-01-02
Sounds good.
If I replace the SSD with a larger 256GB one given they are now affordable too, can I extend the root partition afterwards to fill the whole disc with gparted or other?

---

### Post by Bucky Ball on 2015-01-02
> **sir-marky said:**
> Sounds good.
If I replace the SSD with a larger 256GB one given they are now affordable too, can I extend the root partition afterwards to fill the whole disc with gparted or other?

Yes, as long as the partition you do the copy to is the same size or larger you should be good to go. Once you know that it is up and booting fine, then boot a Live DVD/USB and expand it with Gparted.

---

### Post by sir-marky on 2015-01-02
Thank you for the information. :p

---

