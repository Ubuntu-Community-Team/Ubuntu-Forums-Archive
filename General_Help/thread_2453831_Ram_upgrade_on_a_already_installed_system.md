---
title: "Ram upgrade on a already installed system"
date: 2020-11-17
forum: General Help
---

### Post by danworsley2 on 2020-11-17
Hi Guys

I was given an Acer ES1-131 laptop from a friend as it was faulty. I managed to easily fix it and get it running again and I'm going to give it to my son to replace his old Chromebook as it's starting to show its age. Rather than using the stock Windows 10 it came with, I wiped the drive and installed x64 Lubuntu (20.04 LTS)<edit... on it and it runs very well, no hardware issues or anything like that. The laptop currently has 2GB of ram, however with some websites, multiple tabs, games etc it eats up the 2GB and then starts becoming very laggy. It can be upgraded to 8GB so iv ordered a new stick of Ram for it. I've never done a ram upgrade on an already installed Linux machine and I am fairly new to Linux. I'm wondering if I need to do anything with the swap space after the upgrade or if I should remove it completely to free up some space on the drive? Also is there anything else I should do?

Any advice appreciated.

Thanks
Dan

---

### Post by MartyBuntu on 2020-11-17
> **danworsley2 said:**
> Hi Guys

installed x64 Lubuntu 19.04 

19.04 is no longer supported. You'd be best advised to clean install 20.04 or even 18.04 if needed.
Install the RAM, then install Ubuntu.

---

### Post by danworsley2 on 2020-11-17
My mistake! It's 20.04 LTS that's installed, not 19.04, just gone on to the laptop to check as I only downloaded Lubuntu a few days ago.

The reason I'm asking the question is iv spent a bit of time installing and setting up all the apps my son needs. I didn't realise the low ram was going to be a problem until I had already set everything up and started using it. I don't really want to go through it all again if I can help it!

Thanks again

---

### Post by MartyBuntu on 2020-11-17
Just add the RAM. It will be fine.

---

### Post by grahammechanical on 2020-11-17
I upgraded from 1GB ram to 4 GB and Ubuntu did not trip up in any way. The increase in ram will reduce the need to page data in and out of swap. In the past it was recommended that we have a swap partition that is twice the size of ram. That was good advice when ram amounts were not very large. I think that Ubuntu/Lubuntu have switched to a swap file. This only issue I can think of is if the machine is hibernated to disc and the amount of data in memory is greater that the amount of swap space. I may be wrong but I think that hibernation uses the swap partition.

Regards

---

### Post by QIII on 2020-11-17
I upgraded one machine from 64GB to 128GB without incident.

Generally speaking, most OSes don't care about memory upgrades except that architecture may limit the amount that can be used.

---

### Post by aug7744 on 2020-11-17
Try use Seamonkey browser. If not is possible add RAM enable zram using 256 MB.

---

### Post by mastablasta on 2020-11-18
ram is limited by architecture as said. 32 bit Ubuntu PAE kernel supports 64 GB ram. the 64bit version supports 128 GB RAM. so you are well within those parameters.

next you ask about /swap. if you setup up a partition that is 2 GB it is ok. just leave it. if partition is 4 GB that's even better. nowadays they use swap file on ubuntu versions. with 6 GB ram (or you bought 1 stick of 8GB?!?) installed ram is generally not much of an issue.

the problem with 2 Gb is that system takes 500MB quickly, then you have GPU which usually also take at least 512MB and the rest is then left for browsers and other stuff. with 6 or 8GB you will notice a speed increase, but if you replaced HDD with SSD that speed increase is even more noticeable.

with normal usage you will hit maybe 3-4 GB ram, so 6 GB or more should work really well. i had this issue at work laptop. it had 4 GB ram and until recent updates of office it all worked rather well. but then i hit 4 GB with my main applications running (SAP, outlook, MS teams, excel, chrome, calculator...), it started to get really slow. as soon as they added 4 GB ram, i had no more issues with office work. plenty of ram to spare and windows swap file is rarely used.

---

### Post by guiverc on 2020-11-18
If I adjust RAM on a box, I don't make any changes to the system (outside of adding the ram).

I usually
- just boot the system into BIOS/uEFI to confirm it's recognized, then
- fully memtest() the ram, then
- use the machine normally.

I'd generally only adjust SWAP if it was necessary.  (the correct amount of swap will depend on hardware, plus what you'll use the machine for)

However PLEASE NOTE: You currently may not have any swap allocated/utilized (which can slow performance significantly if your machine has limited RAM).  It's not default on a Lubuntu 20.04 LTS install.

Most Lubuntu users it turns out don't want to have swap enabled, so it's not. This surprises me, but I use older hardware which for sure needs swap; alas most Lubuntu users don't have older hardware, just want it for the speed having  plenty of ram.  Thus I'd ensure you have SWAP enabled.

If you haven't swap enabled, you could look at [https://askubuntu.com/questions/1274118/why-lubuntu-20-04-is-running-slow-when-i-use-opera-or-libreoffice](https://askubuntu.com/questions/1274118/why-lubuntu-20-04-is-running-slow-when-i-use-opera-or-libreoffice)

On my boxes with 4GB or less of RAM, I for sure have SWAP setup & enabled.

*I ~recently stole RAM from a box (dropping 8GB down to 4GB) & didn't expect to notice a difference; I was surprised that the difference was very evident... Turns out I'd not enabled swap; which I quickly rectified & the system acted the same with 4GB as it did when it had 8GB of RAM.*

---

### Post by aug7744 on 2020-11-20
Good reply guiverc. If the user only use browses, play media and other similar programs with 4 GB not need swap enabled. Even with 4GB the user can use KDENLIVE editing an 2 hours video and when rendering will use lesse of 4GB if not editing extremely the video. For internet browse will use less.

---

### Post by danworsley2 on 2020-11-20
Thanks guys, appreciate all the advice it's been a good read. I don't use hibernatation, I always prefer to shutdown so that won't be a problem. I forgot to mention the laptop only has a 32gb eMMC so saving space from removing swap is a gain. I will give it a go with swap turned off and see how I get on. New Ram from crucial hasn't arrived yet, hoping to have it by Monday.

---

