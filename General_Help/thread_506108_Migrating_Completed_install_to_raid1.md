---
title: "Migrating Completed install to raid1"
date: 2007-07-21
forum: General Help
---

### Post by Gruelius on 2007-07-21
Hey everyone,
At the moment a pc has a 160gb ide disk in it fully setup. I plan to make this into a raid1 array with another 160gb disk. i am however confused as to how to go about doing this.

This guide here [http://trinityhome.org/misc/bootable-raid1.html](http://trinityhome.org/misc/bootable-raid1.html) suggests i copy the partition table, then make 3   2nd disk + missing raid 1's then format/copy the data over. I can understand that section

i am not so sure however about the Lilo part, how do grub users do that?

thanks
julius

---

### Post by Gruelius on 2007-08-09
Bumppp?

---

### Post by fjgaude on 2007-08-10
Have you taken a read of these HOW-TOs:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

They show Grub... you have to educate yourself to be able to visualize what is to be done. Good luck.

frank

---

### Post by psusi on 2007-08-10
Format the new disk using the same partition layout you have now, only tag the partitions as type linux raid instead, and use mdadm to initialize the partitions as raid1 sets with only a single volume.  Then copy all files from the old drive to the new drive.  Then setup grub on the new drive and get it to boot.  Once that is done, change the partitions on the old drive over to raid and use mdadm to add them as a second mirror to each of your md devices.

---

