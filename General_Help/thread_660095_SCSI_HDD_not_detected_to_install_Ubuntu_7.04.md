---
title: "SCSI HDD not detected to install Ubuntu 7.04"
date: 2008-01-06
forum: General Help
---

### Post by medo_87 on 2008-01-06
Hello everybody

I'm trying to install Ubuntu 7.04 on a 16Gb SCSI hard drive. the problem is that ubuntu doesn't see this disk it only sees my IDE hard drive and called it (sda).

I have ran :

sudo fdisk - l

it only sees the sda but not the other drive.

any one can help here please??

---

### Post by dcstar on 2008-01-07
> **medo_87 said:**
> Hello everybody

I'm trying to install Ubuntu 7.04 on a 16Gb SCSI hard drive. the problem is that ubuntu doesn't see this disk it only sees my IDE hard drive and called it (sda).

I have ran :

sudo fdisk - l

it only sees the sda but not the other drive.

any one can help here please??

I would suggest unplugging the IDE drive to force the install onto the SCSI, I would also suggest installing version 7.10.

---

### Post by medo_87 on 2008-01-08
I can't install 7.10 as I have a really slow internet connection to downlowad and I live in Libya where I can't  get the DVD delivery. I only have 7.04 which I got from a friend  in England. 

I've removed the IDE drive and started the live CD again it doesn't detect any hard drives and when I tried to install it I gets to the partition editor and couldn't define a root partition :(

thx for the reply

---

