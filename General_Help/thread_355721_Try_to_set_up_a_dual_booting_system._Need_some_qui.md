---
title: "Try to set up a dual booting system. Need some quick help."
date: 2007-02-07
forum: General Help
---

### Post by RegularX on 2007-02-07
i've search and scanned some topics but have found nothing that helps me/answers my questions (or maybe i haven't look enough or search for the right stuff).

anyways, after unsuccessfully trying to set up a dual boot system, messing up my partition table, having to back up my data on my macbook using a live cd, and reinstalling windows from recovery a recovery drive i finally managed to boot from i'm going to give it one more shot before i remove all the useless stuff that came with my OEM copy of windows and setting it up the way i like (so if i crash it again its no big loss).

anyways, i'm trying to use norton partition magic to create a partition that unbuntu can use to boot from and am going to switch between the two OSs using norton boot magic.

my plan was to create a new partition (of about 30 gigs) then splitting that up into all necessary partitions to install and boot ubuntu. after trying to set this up myself and installing from the 6.10 liveDVD desktop and getting no where i need some help.

can someone give me some quick (general instructions) for creating the large partition and smaller ones? should i create one large primary partition and then a few logical ones from that? also how many smaller partitions should i have (i know i need one boot and swap) and how big should they be? or a link to a site that tells you how to partition you drive to set up a dual boot windows/lunix system would be great.

i am sorry if my question/problem is confusing i'm a little tired right now and wrote this fast between classes. feel free to ask questions to clarity, call me stupid, or whatever.

---

### Post by Shatrat on 2007-02-07
All you really need is 2 partitions, one a little big bigger than your RAM for swap, and one Ext 3 for /
/boot is on the master boot record, not really a partition per se, certainly not anything you need to worry about.  its handled by the grub install.
You shouldn't need to use partition magic.  if you defrag windows you can shrink the NTFS partition and create the linux partitions on the empty space using the ubuntu liveCD.

---

### Post by RegularX on 2007-02-07
okay, well when i originally tried to install it i tried using gparted on the liveCD. but it failed to partition (i got some error that i can't really remember right now) even after the HD was defraged. that's why i decided to use partition magic.

so i just plan on using that to create the actual partitions and then run the liveCD and install ubuntu onto the partition.

another quick question. do these partitions have to primary or can they be logical? also, i've been getting conflicting reports, some people said the swap would not need to be bigger than 500mb, but i have 1gb of RAM...so what's the deal with that?

oh...one more quick q. if i want to create another partition for my /home i can do that after the OS is installed without much of problem right?

---

### Post by Coelocanth on 2007-02-07
> **RegularX said:**
> okay, well when i originally tried to install it i tried using gparted on the liveCD. but it failed to partition (i got some error that i can't really remember right now) even after the HD was defraged. that's why i decided to use partition magic.

Did your system come with Windows pre-installed from a vendor such as DEll? If so, you may have a hidden recovery partition, which could be the source of the error.

> so i just plan on using that to create the actual partitions and then run the liveCD and install ubuntu onto the partition.

another quick question. do these partitions have to primary or can they be logical? 

A hard drive can only have a maximum of 4 Primary partitions. Windows wants to live on a Primary, but Linux doesn't care, so you can go with Primary or Logical.

> also, i've been getting conflicting reports, some people said the swap would not need to be bigger than 500mb, but i have 1gb of RAM...so what's the deal with that?

If you have a lot of RAM, then you don't need much for swap. With 1 GB RAM, 500MB is probably plenty. I wouldn't go for more than 1GB swap though in any case.

> oh...one more quick q. if i want to create another partition for my /home i can do that after the OS is installed without much of problem right?


You can, but it's far easier to create it when you first install.

---

### Post by RegularX on 2007-02-07
> Did your system come with Windows pre-installed from a vendor such as DEll? If so, you may have a hidden recovery partition, which could be the source of the error.

i didn't know that. i do have a recovery partition but its not hidden or anything (i mean i knew about it and all), but i didn't know that could be a source of error when trying to install. but since i don't have my recovery discs in my possession (and i have no desire to drive all the way home and get them) i think i'll just leave that alone and use partition magic. if anything goes wrong with my PC i don't have a windows CD (thanks to them not being distributed with off the shelve PCs) and no other way to fix it than boot from the recovery drive.

thanks for the help, you have my gratitude. i'll give it a shot after i get home and post if i run into any more problems.

---

### Post by RegularX on 2007-02-07
okay i have a problem. when i go to prepare the mount points i get an error that says "No root file system". but i am mounting a ext3 (logical) partition of 5gb to that mount point ("/"). what gives here?

---

### Post by Bartender on 2007-02-07
Try wiping that partition so it's unformatted and letting the installer reformat it, or wipe it clean and reformat it with a LiveCD or GParted LiveCD.  For some reason a lot of people get that error with a previously formatted partition.  I did in the middle of a partitioning experiment when I asked Ubuntu to install over an existing Linux OS.

---

### Post by RegularX on 2007-02-07
well i select "reformat" from the mount screen, but that doesn't seem to solve my problem. i guess i can try wiping them tho.

if i were to create a partition, the delete it (thus making it unallocated space) does the option "use free space" only write to that unallocated/formated space? if so i think i'm just going to do that and finally end my headache. thanks.

---

### Post by RegularX on 2007-02-07
alright well, i think i'm in business now. after deleting those partitions i created and choosing to use the largest amount of continuous space i'm finally installing. thanks for all the help guys.

---

