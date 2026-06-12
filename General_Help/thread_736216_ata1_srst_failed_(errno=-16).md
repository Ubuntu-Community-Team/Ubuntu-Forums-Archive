---
title: "ata1: srst failed (errno=-16)"
date: 2008-03-26
forum: General Help
---

### Post by Burch on 2008-03-26
I have Windows XP on my HP and I'm trying to get Ubuntu 7.10 to boot live so i can install it.  When booting it doesn't make it to the desktop and i get the ata1: srst failed (errno=-16) problem.

---

### Post by y-aji on 2008-04-10
:bump:
I am having the same problem with a client.  Upon login, they receive "ata4.01: revalidation failed (errno=-5)".  They have the following pc specs:

video card is EVGA 8800gt
processor is intel E2160
mobo is Abit IP35-Pro
HDD 4 Seagate perpindicular drives
Running Hardy Heron 32 bit edition, client side

This problem has also occurred on Feisty, and Gutsy, but before the install even completed.

Any thoughts at all would be highly appreciated.

---

### Post by y-aji on 2008-04-11
I believe we have found the problem.  This may not always fix it, but my individual had 4 gigs of memory, with a 512mb video card.  Apparently a 32-bit system can handle only 4 gigs total between the memory, video and virtual memory, otherwise it gets unstable.  Once we took out the memory, ubuntu worked just fine.

---

### Post by ToddMonty on 2008-04-26
ubuntu 8.04 64bit desktop
4gb ram
intel chipset
8800gt 3??mb graphics

error message prefixed with [124.043548]
[169.466939]
[214.890335]

this setup also recieves the above message. while it may be a RAM issue, it is not limited to 32bit operations though that would be understandable.

removing 2 GB of RAM (leaving 2) give the same error with different prefixes
[116.610505]
[162.033977]
[207.457447]

--edit--
have now downloaded the 32bit version and get the same error styles... an old knoppix boots fine as does an old mandriva live disk.

I can't help but wonder if I should step away from ubuntu to a different linux build. 

All of the above errors are a low def text only presentation prefixed with a BusyBox v1.1.3 header.

---

### Post by mguinn on 2008-04-26
I have the same problem. I have VIA ide interface attached to
a Western Digital drive. It has no jumper, so that will not
fix the problem. As well I only have 1024mb ram to start with.
The video card is gForce with 256mb ram. This drive works fine 
under 7.10, however 8.04 gives ata1: srst failed (errno=-16)
and the drive simply vanishes which leaves me without a fat32
and ntfs partitions.

---

### Post by byteme2588 on 2008-07-17
I have been getting the same error with a DVD-RW drive that is connected through my IDE1 connector. It worked fine with Ubuntu Dapper but I made the mistake of upgrading to Hardy. Now my DVD drive doesn't work and this error causes my computer to take 5 minutes to boot.

Does anyone know what I could do to fix this or if there is an easier way to go back to dapper with out having to do a fresh install?

Thanks,

---

