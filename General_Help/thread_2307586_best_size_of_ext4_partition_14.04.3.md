---
title: "best size of ext4 partition 14.04.3"
date: 2015-12-26
forum: General Help
---

### Post by Kris_M on 2015-12-26
When the cd(dvd) installed me as a dual boot on my SDD it took all of the free 70gh for the ext4 (plus a little for swap)
Cool.
Got 14.04 running perfectly for me and looking at playing. (dual boot)(grub customizer)

Want to reduce the size of the ext4 partition (I assume with parted (boot from cd) )
But what size? <---    (currently "6.6gb/70gb")   10gb?  20gb?
I do not keep things like iso's on it - those are on my HD - safety!
I backup (internally with BACKUP of course) but externally with clonezilla (partition to image)(12 restores so far)(love it!!!)

Looking to 16.04 ... :)


GA-Z87N-WIFI mobo, i5 4670K, CoolerMaster Hyper TX3 hsf, 8GB ballistix  1600(2x4), UBUNTU 14.04.3 LTE, Win7 Pro x64 SP1 current, Sammy 250GB Evo  SSD, BitFenix Prodigy black case.

---

### Post by yancek on 2015-12-26
15-25GB is usually sufficient for a root filesystem partition.  Use the rest of the space for data partitions.  You can use parted or GParted which should be on the installation medium you used to install Ubuntu.  You can also download GParted and put it on a CD and boot that way.  You won't be able to modify the partition with GParted on an installed system.

  [http://gparted.org/download.php](http://gparted.org/download.php)

GParted Manual at the link below.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by Kris_M on 2015-12-26
Thanks!!!
I've got GPARTED on a CD (burned it a couple days ago) so I'll use that. Always best to be prepared!

Do you know if CloneZilla (also on a CD) cares about the size of the ext4 it's restoring to? - in other words if I backed it up when it was a 70gb can I restore that img to a 15gb (where only 6.6gb is used)?

Thanks!!!

EDIT: now 18GB

---

### Post by matt_symes on 2015-12-26
Hi

> **Kris_M said:**
> When the cd(dvd) installed me as a dual boot on my SDD it took all of the free 70gh for the ext4 (plus a little for swap)
Cool.
Got 14.04 running perfectly for me and looking at playing. (dual boot)(grub customizer)

Want to reduce the size of the ext4 partition (I assume with parted (boot from cd) )
But what size? <---    (currently "6.6gb/70gb")   10gb?  20gb?
I do not keep things like iso's on it - those are on my HD - safety!
I backup (internally with BACKUP of course) but externally with clonezilla (partition to image)(12 restores so far)(love it!!!)

The size of any partitions is really a personal decision and will depend on how you plan to use Ubuntu.

You may very well get 100 different answers from 50 different people :)

I would stick to a root partition (/), a home partition (/home) and a swap partition if memory is low and/or you plan to hibernate.

10G for / is probably adequate unless you plan to install lots of software. Some users like more space.
Your home partition will really depend on how you plan to use Ubuntu. I would suggest anything from 10G upwards for a desktop installation.

> Looking to 16.04 ... :)

GA-Z87N-WIFI mobo, i5 4670K, CoolerMaster Hyper TX3 hsf, 8GB ballistix  1600(2x4), UBUNTU 14.04.3 LTE, Win7 Pro x64 SP1 current, Sammy 250GB Evo  SSD, BitFenix Prodigy black case.

Currently 16.04 is in development. 

Many people will wait for the first point release (16.04.1 in July/August time frame) before upgrading if they want a more stable desktop. This is especially useful for less experienced with Ubuntu users who maybe unsure how to fix issues, report bugs or may not be happy with workarounds that may occur while bugs are being shaken out.

Kind regards

---

### Post by Kris_M on 2015-12-26
> **matt_symes said:**
> Hi

<snip>
Currently 16.04 is in development. 

Many people will wait for the first point release (16.04.1 in July/August time frame) before upgrading if they want a more stable desktop. This is especially useful for less experienced with Ubuntu users who maybe unsure how to fix issues, report bugs or may not be happy with workarounds that may occur while bugs are being shaken out.

Kind regards



Thanks!

I went with 18GB - that leaves me 49gb to play and test with on the SSD.

Yes, in full agreement with that - and would triple boot when I do: 14.04.3, 16.04.1, win7. - Run both until I'm sure.  Always leave an escape!

However it's playtime!
I put the daily 16.04 (d/l 12-26-15) on a USB and played with it for a bit.  Was shocked at how good it was! I will post a little feedback on the dev forum(that the devs don't look at! - LOL)

Thanks again!

---

### Post by yoshii on 2015-12-26
gParted needs to be on a bootable LiveCD it can't just be on a CD or DVD as a backup file.  Just in case anybody was wondering.

---

### Post by mansonfan78 on 2015-12-27
Clonezilla can not, by default, restore an image to a smaller drive/partition (regardless of actual used space).  It's technically possible, but I've never gotten it to work reliably.  Best to make a new backup once everything is resized.

---

### Post by Kris_M on 2015-12-27
Thanks! Done!

---

### Post by matt_symes on 2015-12-27
Hi

> **Kris_M said:**
> Thanks! Done!

It sounds like you are nicely prepared for 16.04 :)

If this has answered your current questions then please mark this thread as SOLVED using the thread tools over post #1.

It'll help others looking for a similar solution and is a simple way you can give back to the community.

Kind regards

---

### Post by Kris_M on 2015-12-27
Thanks! :)

---

