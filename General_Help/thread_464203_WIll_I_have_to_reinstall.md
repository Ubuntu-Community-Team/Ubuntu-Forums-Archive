---
title: "WIll I have to reinstall?"
date: 2007-06-04
forum: General Help
---

### Post by Fireblend on 2007-06-04
Hello. I downloaded GParted since I wanted to create a new partition to install WIndows on (need it for work, unfortunately) but it seems I can't create partitions since I need to label them first or something and that implies formatting my partition? Is there some way I can do this without killing my beloved Ubuntu install?

And if (as it seems), I'll have to end up formatting, is there some way to save all my applications/preferences and then load them in the new install without having to download/modify all of them all over again? I'd hate having to download everything again, mod everything again and shape it to fit what I want. Specially my apps, it will take a while to download all that again...

Oh, and just a comment, but if I'm not mistaken, GParted is the one who creates the partition during installation, no? Why doesn't it label the partition then so if I want to create partitions later it'll be easier...?

---

### Post by pak33m on 2007-06-04
Hi there,

Have you tried a virtual of your Windows install? I used to run a Windows image for work through VMware Workstation but was incredibly memory intensive.  Now I just use vpnc and rdesktop to connect at work.

I just posted about Virtualbox [http://www.virtualbox.org](http://www.virtualbox.org) which is another piece of the vitalization software out there.  I have been using it on my Ubuntu 6.10 Edgy laptop for Ubuntu 7.04 Studio with 1GB RAM without any problems, especially in memory.  

If you have a the Windows software why not try to create an image.  In this way you will not have to perform any partitioning or most importantly have Windows installed on your hard drive!?

---

### Post by Fireblend on 2007-06-04
My 512 RAM would never handle it, and I need some memory-eating programs like a couple of programming languages. I have thought about that, but it wouldn't really work.

---

### Post by John.Michael.Kane on 2007-06-04
gparted should allow you to resize your current partition.

When you open gparted there should be a box in the right corner labeled /dev/sda select it.

Once you have the drive in question  selected you will see you current partition set up.

Click the partition you want to resize next a  box should come up giving you the option to select the amount space you want to you use.  one this done you can use gparted to format the partition to ntfs, and install windows on it.

Note you may have to unmount the drive first. before doing the above.


The other option is backing up your home folder provided you did make a separate partition for home, and reinstall windows first, and then ubuntu second.

---

### Post by Fireblend on 2007-06-04
Hmm, unmount it first? As in right-click->unmount while in GParted? won't that kill the system or something since it's my only partition? (other than grub, of course). And what if I don't have my home folder in other partition? can I just copy-paste it into a new install and expect everything to work?

---

