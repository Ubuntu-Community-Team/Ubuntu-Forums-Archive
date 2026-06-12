---
title: "Freezes on boot-up screen when I try to install on my laptop (HP-2000)"
date: 2013-03-18
forum: General Help
---

### Post by Number703 on 2013-03-18
I just bought the newest HP-2000 series laptop, came pre-installed with Windows 8. Crappy OS, horrible UI, really need to get back to Ubuntu. Created a bootable USB to try to create a dual boot with Windows/Ubuntu. I've had several issues with the install, so far I fixed the secure boot/boot order problem, and I think I fixed the infamous black screen issue. It no longer goes to a black screen after I select "Try Ubuntu without installing" or the other option, but, I only get as far as the purple 'Ubuntu' screen. The dots under 'Ubuntu' are animated white/orange for a little while, then it just freezes completely. I can't figure out how to get past this and am about ready to give up, with the other issues I've now put in about 8 hours just trying to install Ubuntu, extremely frustrating. Any help?

Some more info:
I've tried with both 12.10 and 12.04, 64 bit. Apparently Windows 8 doesn't work with 32-bit, and when I tried creating a 32-bit USB it just skipped straight to Windows. I had an older HP 2000 series laptop with Ubuntu before this, 12.04 32 bit, it would not allow me to upgrade to 12.10, IIRC it was something to do with the graphics. Not sure if that carries over to this, and whether or not I should try installing 12.04 or 12.10, but as I said I've tried both

When I partitioned the disk space, I was unsure whether to select FAT32 or NTFS for the file system format, but I've tried it both ways and neither solved the problem.

---

### Post by meanmrmustard on 2013-03-18
FAT and NTFS are both Windows file systems.
You need to use ext 3/4 most likely.

I've had similar results installing Ubuntu and variants before and found using the alternate install disk allowed the installation to complete with no problems, though it may be that simply using say, etx 4 will resolve the issue.
Hope that helps.

---

### Post by Number703 on 2013-03-19
Formatted to ext4 filesystem, did not help, same problem.
Alternate install disk didn't work, I made a USB with 12.04 alternate, it came up with an error at "Install CD components" or something like that.

All I want to do is install Ubuntu, why the hell is it this hard???

---

