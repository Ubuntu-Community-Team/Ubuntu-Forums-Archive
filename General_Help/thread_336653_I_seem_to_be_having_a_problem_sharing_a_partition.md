---
title: "I seem to be having a problem sharing a partition"
date: 2007-01-11
forum: General Help
---

### Post by sharpie05 on 2007-01-11
here is my problem.  I am dual booting MacOS X and Ubuntu (Feisty Fawn) and i have an 18 gigabyte partition on my hard drive i would like to share between the two.  i tried formatting it in ext2, ext3, HFS+... all to not avail.  the closest i came was a fully mountably and writable partition for OS X, but linux would  not recognize it.  another instance gave me a mountable partition in Linux, but i could not write to it, nor could os X see it.  heres how my partiitions are set up, not including the 135 MB or so in front of the os x partition.

Macintosh HD:29.7 GB
**Free Space: 18.7 GB**
Ubuntu: 6.89 GB
Swap: 885 MB

the section of the hard drive that i want to share is bolded.  please help!

also: from my understanding, if i boot up the OS X installation disc and run disk utility, any partition modifications i make will erase all other partitions...  :/

---

### Post by dcstar on 2007-01-12
> **sharpie05 said:**
> here is my problem.  I am dual booting MacOS X and Ubuntu (Feisty Fawn) and i have an 18 gigabyte partition on my hard drive i would like to share between the two.  i tried formatting it in ext2, ext3, HFS+... all to not avail.  the closest i came was a fully mountably and writable partition for OS X, but linux would  not recognize it.  another instance gave me a mountable partition in Linux, but i could not write to it, nor could os X see it.  heres how my partiitions are set up, not including the 135 MB or so in front of the os x partition.
.......

If the MAC supports FAT32 partitions, use one of those.

---

### Post by sharpie05 on 2007-01-12
well, i thought os x DID support Fat32... apparently not because it doesnt show up now.  at least when i formatted for ext3, it would show up.  i didnt have write permissions to the shared drive(with no option for authentication), but i did for the linux partition(with authenitcation).

---

### Post by sharpie05 on 2007-01-12
so theres not other way?  sorry to be impatient... my data is living on borrowed time:/

---

### Post by sharpie05 on 2007-01-12
alright, figured out how to format it to HFS+... its read/writable in both OS's, just requires authentication in linux.  not a problem :D

---

### Post by sharpie05 on 2007-01-12
well, it WAS working... i dont know what happened to break it...  almost ready to give up on linux until i get an external drive which could be a while...

---

