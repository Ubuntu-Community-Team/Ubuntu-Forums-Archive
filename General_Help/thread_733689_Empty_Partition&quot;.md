---
title: "Empty Partition????&quot;"
date: 2008-03-24
forum: General Help
---

### Post by Ed933 on 2008-03-24
Ok.....here's my problem - 

I was using PCLinuxOS happily until it started randomly crashing ... so I replaced it with Ubuntu 7.10 and I'm lovin' it. Before that, I created an ext3 partition where I put all the stuff I used in PCLOS. I access it from Ubuntu as "/media/sda2" and ... IT'S EMPTY?! 

I check it as root...still nothing.

Is there any way around this?

---

### Post by Kiri on 2008-03-24
Can you type this into the terminal and post the result:

fdisk -l


This will tell us if sda2 is indeed the correct partition with the data from pclos in it
Also, how did you mount the disk?

---

### Post by erginemr on 2008-03-24
Welcome to Ubuntu!

The folder is empty probably because you haven't mounted it yet. You should first try to mount it with:
```
sudo mount -t ext3 /dev/sda2 /media/sda2
```
and there should be an existing sda2 directory under /media.

If this command works, then you need to edit your /etc/fstab file to let the system automatically mount it.

So, what are the outputs of the following commands?
```
cat /etc/fstab
```
```
blkid
```
```
sudo fdisk -l
```

---

