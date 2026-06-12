---
title: "Need help getting data off borked Mirror Set"
date: 2014-03-24
forum: General Help
---

### Post by nuffnough on 2014-03-24
Hi,

I built a system for a friend a cuple of years back.  SSD for the system slices,   and a mirrored pair of 3tb drives that I used to mount /home.

For reasons that we couldn't prove, the system stopped booting.  It would start the OS bootstrap and hang.   A bit of troubleshooting and we figured that something had borked with the mirror set.  

The frustrating thing is that I cannot get the system to boot to a point where I can load mdadm to look at it.

I have physically removed the drives from the box and attached them to a different system,  but they can't recognize either drive.  

What do I need to do to recover this data?

TIA

nuffi

---

### Post by steeldriver on 2014-03-24
Hello and welcome to the forums

Can you share with us some of the things you have done to try to get the system to see the drives (fdisk? parted? mdadm?)

What kind of system did the disks come out of? some Sparc-based systems use a large ext blocksize which require special techniques to mount on x86.

---

### Post by nuffnough on 2014-03-24
Thanks for the response.   These are standard SATA 3TB drives that have come out of a desktop PC I put together out of standard parts (Asus Mobo, OCZ SSD, WD HDD, etc)

The original system refuses to do anything except freeze at teh very start of boot with the mirror set plugged in, and will only boot into single user mode when I remove it. 

I have physically removed both hard drives from that original system and attempted to read them individually via a caddy that I have on my own home system, but I can't get my system to recognize either drive. 

I have been too worried about data loss to try running fdisk, parted or mdadm on these drives yet.

---

