---
title: "BTRFS, RAID 1 and how is the data distributed with three or four disks?"
date: 2014-05-12
forum: General Help
---

### Post by sir-marky on 2014-05-12
I am new to BTRFS having come from the traditional RAID background.  I  am looking to set up a BTRFS array on my home server with 3 (possibly  four) 3TB disks with the RAID1 setup (at least until RAID5 becomes  stable).

I have been reading as much as I can before taking the  plunge and set up a test scenario with an external drive and three  partitions but I am still a little confused how the data is distributed  in a three disk setup and what happens if I loose a disk or two?

Can anyone help enlighten me?

---

### Post by matt_symes on 2014-05-12
Hi

> **sir-marky said:**
> I am new to BTRFS having come from the traditional RAID background.  I  am looking to set up a BTRFS array on my home server with 3 (possibly  four) 3TB disks with the RAID1 setup (at least until RAID5 becomes  stable).

I have been reading as much as I can before taking the  plunge and set up a test scenario with an external drive and three  partitions but I am still a little confused how the data is distributed  in a three disk setup and what happens if I loose a disk or two?

Can anyone help enlighten me?

If you don't get an answer here, I would consider asking this question in #btrfs on freenode. 

The developers use that IRC channel all the time and they may be able to help you or point you in the direction of useful documentation for you.

Kind regards

---

### Post by matt_symes on 2014-05-12
Hi

Excellent. I'm glad you got some help in there ;)

I've been lurking in that channel on and off for a while now, picking up useful information, but you can't get better than talking to the people who really know btrfs such as darkling.

Kind regards

---

### Post by sir-marky on 2014-05-13
You were right.  The #btrfs channel was helpful.  I now understand things a lot more.  Darkling was excellent explaining things to me.

---

