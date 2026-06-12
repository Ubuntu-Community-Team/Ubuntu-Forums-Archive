---
title: "3rd OS installation -- will it mess something up?"
date: 2006-07-01
forum: General Help
---

### Post by greenbmw530i on 2006-07-01
Hey guys, let me first start with what I have going on. I have one hard drive, with 3 partitions. The first partition has Windows XP on it, the second has Ubuntu Dapper, and the third is Linux-swap. Everything works well so far. I'm working on getting a third operating system on my hard drive, however.

I've downloaded the .iso of the desired operating system...and I know how to create and mess with partitions with Acronis Disk Director in Windows XP. I have a feeling that once I create the partition for the third operating system (which will remain unnamed for legal reasons) and install the OS on the partition, GRUB will be messed up (or something else will be).

What can I do during the partitioning/installation process to ensure that the only change to my GRUB menu will be the addition of the third OS.

Thanks a lot in advance!

---

### Post by blackjack6.21.91 on 2006-07-01
I dont think anyone is going to sue you via the Ubuntu Forums.  I don't think anyone is going to spy on your posts and sue you based on something you wrote in the Ubuntu Forums.  If you tell us what it is someone might be able to tell you what's going to happen to GRUB.  Otherwise I think it's something you could reverse as long as you have at least one working OS.  And if you REALLY don't want to tell what the third OS is, try google-ing what the results may be, or on how to restore the GRUB boot menu via a seperate operating system or a liveCD.

fish and chips,
peace and love,
blackjack

---

### Post by reacocard on 2006-07-01
it might help to tell us what the OS is :) 
but if you just tell it not to wrtie anything to the MBR (where GRUB lives) it'll be fine. you'll have to manually an a entry for it to GRUB though.
Also, i think the ubuntu alternative install cd can restore grub if you mess it up, so you might want to have that on hand.

---

### Post by greenbmw530i on 2006-07-01
The OS is OS X 10.4.6. Someone was kind enough to patch it to work on non-apple intel machines and torrent it. I hope that helps  :)

---

### Post by blackjack6.21.91 on 2006-07-01
Lol.  Wish I could get my hands on that.  Got an intel right here..

I would recommend backing up the GRUB menu.lst ( /boot/grub/menu.lst ) to your email or something.  Other than that, just dive in and create a new post if anything goes on.

Fish and chips,
peace and love,
blackjack

---

### Post by greenbmw530i on 2006-07-01
[QUOTE=blackjack6.21.91]Lol.  Wish I could get my hands on that.  Got an intel right here..[/QUOTE]
I heard demonoid.com is a site that has a lot of good torrents ;). But I have no idea...it's not like I used it to download OS X 10.4.6 or anything... **Disclaimer:** Too bad you can't use demonoid.com since it would be illegal to download any copywritten material.

---

### Post by blackjack6.21.91 on 2006-07-01
I went to that site to try to find an appropriate torrent.. not able to decide which one's the best one for me to tell my friends not to download.  Just for reference, I think most of them use Pentium M, so I want to warn them not to download the one that would be most appropriate for their PC's (and most tempting).

Peace,
blackjack

---

### Post by reacocard on 2006-07-01
OS X ... nice. if i had the disk space, i'd try it, but between XP and Ubuntu (and the mess that is my partitioning table) i don't have room.

---

### Post by blackjack6.21.91 on 2006-07-02
ok you guys.  in case anyone want's to try OSX on an intel machine, remember, it would probably be some sort of copywright enfringement to use the torrent I am tarring as an attachment!!  I'm just putting it out here to raise awareness:p 

Peace and love,
blackjack

---

