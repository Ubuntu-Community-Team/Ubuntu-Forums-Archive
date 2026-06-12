---
title: "Grub freezes at &quot;starting up&quot; when loading xp, but ubuntu is fine"
date: 2007-07-23
forum: General Help
---

### Post by Markelecguitar on 2007-07-23
I have a dual boot setup for ubuntu feisty and xp. It was working firn until i used paragon paritition manger to allow me to install vista. I used paragon to change the size of my xp partition thinking that this would allow me to use the unpartitioned space to create another partition for vista. Partition manager took along time running do i went away and came back to find someone had shut the lid on the laptop. 

I feared it may have stopped the process but all was well. But i was left with unassigned space which i could not use. I then decided to merge the unparttioned space with the xp partition to fix it again and then retry. But this process wnt up to nearly 100% and then said it would take 24 hours.

Obviously somthing was wrong so i restarted only to find at grub when i select xp, it says the initial "starting up..." line, and does not go any further.

I tried using gparted but even with the live cd it gives me errors saying the disk is mounted which i know it is not as i unmouted it. Also when i ran fdisk ,because fsck would not run saying there was block errors and would not even run with the new block list it suggested, and it told me that partition 1 and 2 overlapped

I am far from the most experience linux user in fact im very noobish but i have looked everywhere and tried everything i can and i would appreciate any help.

Thanks in advance
Mark

---

### Post by strabes on 2007-07-23
Sounds like your XP install is toast. You might want to get a second or third opinion via #ubuntu before doing this but you could easily just reinstall windows on the first partition on your drive and then reinstall grub because windows overwrites the MBR. [Here's](http://ubuntuforums.org/showthread.php?t=358183) a page that details how to reinstall windows when you already have ubuntu, and [Here's](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) a page detailing how to reinstall grub after installing windows.

---

### Post by Markelecguitar on 2007-07-23
thanks, thats what my last resort was but if theres any alternative that would be much better as i'd like to understand the problem. At the minuter im guessing the paragon manager was the problem but its a well recommended program so it seems strange. Anyways thanks man and anyone else who thinks they have a solution, id be more than grateful

---

### Post by strabes on 2007-07-23
Well, when it resizes your partitions it has to move data around so when you restarted it was most likely in the process of moving some (critical system) files.

I don't really know if it is possible to salvage your install so like I said, you should get another opinion from someone to whom this has happened before. I've never had a problem like you did when resizing my windows partition.

Anyway, if you decide to reinstall windows, one thing you could do is boot into ubuntu, mount your windows partition, and copy some files that you would like to preserve like the "Application Data" folder which contains things like your firefox profile and other preferences that take a long time to configure (I have 17 firefox extensions)

---

### Post by Markelecguitar on 2007-07-23
Yep did that, i was ok with that fact. I've had to do alot of reinstallations over the years :l 
but thanks for your help, im just gunna reinstall windows onto the partition but first im gunna create an extended partition so i can install vista afterwards

---

