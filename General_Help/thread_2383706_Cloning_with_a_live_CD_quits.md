---
title: "Cloning with a live CD quits"
date: 2018-01-28
forum: General Help
---

### Post by danielsender on 2018-01-28
I have a 16.04.3 32b installed and running on a vintage Dell M50. The system works well. I was trying to clone this 320gb disk into an identical other with a live CD - everything in the machine unmounted. First I tried with the Xenial 32b CD disk. I was expecting the job to take several hours. The process started OK, I was able to monitor the progress, but after 10 minutes dd stopped copying, but without returning to the prompt, in other words it hangs. I repeated the process and I again got the same result. Thinking that it could be the live CD, I used another one with Lubuntu, and everything was repeated, although the hanging wasn't exactly at the same location as before with the Ubuntu CD. On the other hand, everything I do on the booted system with the CD runs well after the dd job hangs. What is interesting is if I run 'fdisk -l' at that point I don't longer see the destination disk (/dev/sdc). In other words, is there any reason why a system running off a CD would umount a USB connected disk?

Thanks

---

### Post by danielsender on 2018-01-30
Forget about this. Turns out that I plugged the destination HD into a three-way USB adapter (PATA small, PATA big and SATA) using the PATA small side of the square. If I place the whole thing flat on the table, the connection is not stable, so I placed it in a vertical position. I was able to clone the disk succesfully.

---

