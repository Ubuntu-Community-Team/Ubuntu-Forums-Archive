---
title: "Installing XP after Gutsy"
date: 2008-02-11
forum: General Help
---

### Post by lhardyl on 2008-02-11
K i want to install xp on a separate partition of my hdd without having to reformat and reinstalling Gutsy

So gutsy is already installed and im looking for a guide that will help me partition my drive so that i can then put my xp install cd in and install it on that partition.

Yer im lost not to sure if its poss as all i can find is people installing xp first and then ubuntu.

so if anyone can point me in the right direction ill be a happy chappy

Thanks in advance

---

### Post by src2206 on 2008-02-11
I have not come across any guide but I can help you (I hope).

First create a separate partition preferable unformatted. Note the position of that partition (ie where it is placed with reference to your existing partition). You can use GParted (Free) to create this partition.

Now. boot with your XP CD and go to the installation and partition stage. In this stage Windows will list tall the available partition and one of that should be marked as unformatted free partition. Remember, XP will not recognise your Ubuntu installation, but it will show this ext3 partition and the SWAP partition as Healthy but unknown partition. 
Choose the Unformatted Free Partition to install Windows. Remember to be very careful at this stage, because choosing wrong partition will mess up everything.

One more thing, Windows should assign Volume Letter "C" to its installation partition. While installing Windows will rewrite the GRUB abd place windows MBR there. So once the installation completes you will not have any chance to boot into Uubuntu. For that there are two options:
1. You ca put an entry corresponding to the location of Ubuntu installation in the [B]boot.ini of XP.
[/B]2. You can install GRUB again.

---

### Post by Shakeysteve on 2008-02-11
Try this site:
[http://www.apcmag.com.au/dualboot](http://www.apcmag.com.au/dualboot)

It has to be the difinitive guide to dual booting between Ubuntu and XP or Vista.
These guys have done their homework!

---

### Post by lhardyl on 2008-02-11
woohoo thank you shakeysteve

---

