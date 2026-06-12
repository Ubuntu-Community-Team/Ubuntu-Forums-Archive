---
title: "Error during installation timeout: killing"
date: 2012-11-06
forum: General Help
---

### Post by tech291083 on 2012-11-06
Dear Friends,
 
I have a SATA 80 GB hard drive in good working condition, which I wiped out using dban (Dod Short method), then I tried to install Ubuntu 12.04 LTS 32+ bit distro, but it keeps showing the following error, whic does not go away itself during installation. It keep repeating itself on the screen endlessly. I used to wait 30 mins, thinking that it will go away automatically, but that never happened. I need to install Ubuntu on this HDD.I have installed it many times before within 20 mins. Please help me. 
 
```

ata2.00 status drdy
ata2.00 failed command read dma
**Buffer I/O error on device** sda, **logical block** 9
**udevd** [348]: **timeout**: **killing** /**sbin**/**blkid**-o **udev**-p /dev/sda

```
 
Thanks.

I have something to add,
 
A friend of mine recently boght 2 new pcs. I went to his place to help him install Ubuntu 12.04 LTS 32+ bit on both the machines having a 500 GB SATA hard drive each. There I used dban to wipe the original OS that came pre-install with the pcs and then I tried to install Ubuntu, but again there was this same error. I have not been able to solve this issue yet. Does using dban to wipe out (I used the DoD Short method) a hard drive in good condition or even a brand new one cause some sort of problem to the drive, forcing installation of a new OS/Linux distro to become a complicated process? I am sure that my friends 2 new hard drives are working alright and so is mine despite being a bit old. What is the solution to this problem I have encountered 3 times so far on 3 different drives?
 
Thanks.

I just tried to install Ubuntu 12.04 LTS 32+ bit on my hard drive and as usual the installation stopped at the stage called - Preparing to install, where it asks to make sure that the system has atleast 4.9 Gb of space available. I have attached the screenshot to this post. I waited for 30 mins and then terminated the installation process. Then I rebooted the pc with GParted Live CD that I often use to create partitions. I showed me the partitions created during Ubuntu installation and I deleted them all one by and then created a new partition table, not partitions. I refreshed the GParted info by selecting the Refresh Devices entry from the GParted menu. Rebooted the pc with Ubuntu DVD and to my surprised it install without any problem just under 10 minutes as it usually does. 
 
I am not sure as to how that partition table was shown by GParted despite the fact that I was not able to finish the installation and the pc froze completely. 
 
If you wipe out your hard disk completely, then I guess there is nothing left on the disk, but is it the very emptiness that prevents other OS/Distro from installing? Weird and not logical, but I need an anwser, thanks.

Here is the screenshot, where the pc just froze forever on mine and my friend's drives.

---

