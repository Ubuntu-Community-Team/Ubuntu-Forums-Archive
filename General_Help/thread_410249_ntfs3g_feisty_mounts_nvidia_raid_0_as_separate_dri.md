---
title: "ntfs3g feisty mounts nvidia raid 0 as separate drives"
date: 2007-04-15
forum: General Help
---

### Post by unknownprotocal on 2007-04-15
Ok, I have 2 80 gig sata drives in a raid 0 with an nvidia controller, works fine in xp, but after grub messed up my mbr i decided to just only use Kubuntu, I have feisty installed on a 80 gig ide, and in my media folder I see the sda1 and sdd5 drives... I installed ntfs3g with automatix and it mounted the separate drives like that so i read that dmraid might fix it, I installed it and made a file called activateraid in my home dir which contains

[B]dmraid -ay -v
mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/nvidia_aadhfeea /media
/dev/mapper/nvidia_aadhfeea5 /media
/dev/mapper/nvidia_iejgigfa /media
/dev/mapper/nvidia_iejgigfa1 /media[/B]     

and ran it ... with output

[B]RAID set "nvidia_iejgigfa" already active
RAID set "nvidia_aadhfeea" already active
RAID set "nvidia_iejgigfa1" already active
RAID set "nvidia_aadhfeea5" already active[/B]

I have all of my music, movies, and documents on that raid 0... please help me

---

