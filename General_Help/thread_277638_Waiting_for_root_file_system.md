---
title: "Waiting for root file system"
date: 2006-10-14
forum: General Help
---

### Post by rogeriovinhal on 2006-10-14
Hello, there is a problem that is really bugging me out.

I have AMD64 Ubuntu and Kubuntu running on my machine. I compile custom kernel for both of them.

I have a 250GB Sata and a 60GB ATA disks.

Yesterday I used Partition Magic in Windows to resize my NTFS partiton and create another one for linux.

Yesterday I compiled the 2.6.18 kernel for the Ubuntu partition, but it stalled at the "Mounting the root filesystem" and after it "Waiting for root filesystem".

I didn't have time to deal with that, so I went out, and then at night I tried again, but it surprisingly worked.

Today I was happy about it, but suddenly, after I rewrote my menu.lst, it started to stall again, and again and again, until it suddenly stopped stalling, and worked AGAIN.

I recompiled the 2.6.18 kernel, but it starting to stall AGAIN.
Right now I am writing from Kubuntu, which works flawlessly...

What should I do? After like 3 or 4 minutes it improvises a shell, but there isn't any /dev/sdaX, and in /dev/disk/by-path, it only shows the ATA disk...

---

### Post by rogeriovinhal on 2006-10-15
up

---

### Post by ei1 on 2006-10-20
I also had this exact problem *seemingly* spontanteously.  Problem solved when I moved drive from secondary ide back to primary ide cable.

---

