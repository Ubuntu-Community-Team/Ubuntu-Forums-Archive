---
title: "Partition HDD Help please"
date: 2015-06-08
forum: General Help
---

### Post by maknib on 2015-06-08
Hey ll im very new to Ubuntu, never used it 
my pc was playing up so i wiped windows off completelya nd installed only ubuntu, it looks awesome but i want to put windows on now..
im downloading an ISO of windows 7 and then can put my key in and set it up but im having issues partitioning

Ive downloaded GParted
i have:
/dev/sda1  ext4 Size 1.8tb Free 1.75
/dev/sda2 /extended Size 15gb 
   .dva.sda5 Linux-swap Size 15gb used 15gb

I would like to partition the hdd and leave 500gb for the linux and the rest for windows but gParted will not allow me to resize

any hep would be great

---

### Post by user1397 on 2015-06-08
you must unmount the drive first before gparted will allow you to partition it.  you can unmount it directly from gparted, or by going to the file browser and right clicking on the correct drive and select "unmount"

---

### Post by Bucky Ball on 2015-06-08
You can't resize partitions when they are mounted and you have the OS booted on one of them. Boot from the Live media, Try Ubuntu, launch gparted, resize.

Confused about your current partitioning. Doesn't make a lot of sense to me. What is on sda1, apart from the fact it is EXT4, and how much of the 2Tb does it use? 

You have a 15Gb /swap in a 15Gb extended partition??? Any reason for this? You don't need more than 2Gb unless you hibernate with a LOT of resource hungry apps open (that will be using some of your RAM, and that is rare). If you fall in to the latter category, though, the /swap should be same size as your installed RAM. Very unlikely you are going to need more than 2Gb, though.

Also, have you installed Ubuntu in EFI mode or legacy?

---

### Post by Bucky Ball on 2015-06-08
> **ubuntuman001 said:**
> you must unmount the drive first before gparted will allow you to partition it.  you can unmount it directly from gparted, or by going to the file browser and right clicking on the correct drive and select "unmount"

If OP is trying to resize the OS partition, which I have a feeling is what's happening, they must boot from Live media to resize the / partition. ;)

---

### Post by maknib on 2015-06-08
i dont know about the partitions
all i did was wipe and install ubuntu and thats it now im trying to resize the partition so i can get windows back on

iget an error trying to unmount and im assuming because im on the OS right now

---

### Post by Bucky Ball on 2015-06-08
Repeat: Boot from the live media (disk or USB)> Try Ubuntu> launch Gparted when at a desktop> resize.

---

### Post by user1397 on 2015-06-10
> **Bucky Ball said:**
> If OP is trying to resize the OS partition, which I have a feeling is what's happening, they must boot from Live media to resize the / partition. ;)
yup, I should've probably led with that

---

### Post by cariboo on 2015-06-11
Even if you repartition the drive you are going to run into problems, Windows needs a partition at the start of the first hard drive in the system, and if you can't do that the only cure is a complete installation. It is probably easier to do fresh installs of both.

---

