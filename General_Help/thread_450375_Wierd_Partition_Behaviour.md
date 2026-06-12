---
title: "Wierd Partition Behaviour"
date: 2007-05-21
forum: General Help
---

### Post by takuhii on 2007-05-21
OK, I'll start from the beginning and hopefully I'll make sense...

I resized an NTFS partition to make way for Ubuntu 7.04, and to allow me to dual-boot the two (I have windows XP on the NTFS partition). Once in Ubuntu (after install, everything worked without a hitch), I realised Windows didn't need that much space and I decided to resize that partition. GNOME Partition Manager allowed me to shrink the NTFS partition further, but wouldn't allow me to add the free space to my EXT3 partition. I then managed to crash Ubuntu, and had to re-install everything, this made matters worse, my partition now look like this:

/DEV/SDA1     -     NTFS Partition (40GB)
/DEV/SDA2     -     EXT3 PARTITION (60GB)
UNSPECIFIED -    60GB
/DEV/SDA3     -     EXT3 Extended (2GB)
UNSPECIFIED -          |_ 50MB
/DEV/SDA4     -          |_ Linux-Swap (2GB)

As you can see I have a load of unallocated space, and I am unable to add it to ANY of my existing partitions. I feel I may have to backup essential data and format the hard drive and start again, I am reluctant to do this as I still require some data from my Windows Partition. Also the system has NEVER EVER dual booted sucessfully, even though I can mount the NTFS partition and access it, I have never been able to boot into windows since I installed Ubuntu. I have followed EVERY tutorial under the sun to make it work and no luck.

Could someone PLEASE help me, as I really am at the end of my tether with this one...

Cheers
Darren

---

### Post by zvacet on 2007-05-21
This is for dual boot in general  

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

And for partitioning download Gparted live CD.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by takuhii on 2007-05-21
Cheers, I think I used the Psychocats tutorial and still failed at it, I'll give these a whirl again tonight. The GPArted things looks interesting. If this fail I'll do a back up and DBAN my HDD :(

Thanks for the help
Darren

---

