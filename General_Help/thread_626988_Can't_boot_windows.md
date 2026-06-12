---
title: "Can't boot windows"
date: 2007-11-29
forum: General Help
---

### Post by Addicted2Cryptid on 2007-11-29
So I have talked to Gateway and Microsoft, and neither could help me with my problem.
I created two separate partitions on my computer, one for vista, and a new one to put Ubuntu onto.  After using Ubuntu, I decided I wanted to get rid of it and re-install it at a later time, so in order to do this, I just formatted the partition that Ubuntu was on, putting the computer back to how it was.  I think this is where my problem is.  I used to be able to dual-boot using the GRUB loader, and I think I may have deleted this as well.  So in used the system recovery disc that came with my computer, but not even that will put my computer back to how it was.  I formatted the entire c drive, and windows won't start.  I want windows vista back, all I have is the system recovery disc.  Does anyone know how I could do this without having to buy another copy of vista?  No one has been able to so far.  Thanks!

---

### Post by ijason on 2007-11-29
you should not have to buy another copy of vista, you own the license for the program installed on your machine, and that license entitles you to use the product. 

i've heard from several people that vista is very particular about how the drive it's on is formatted, and it sounds like you messed that up when you tried to remove (or when you put it on, in the first place) ubuntu. so, i'm getting the correct idea that you've now entirely reformatted your drive?

there should be a sticker on the back of your computer, or on some of the paperwork that came with the laptop that has your vista serial number. if you can find that then you have a good bargaining chip to demand a copy of vista. 

i would think that the system recovery disk for windows would work. does it see your hard drive ok?

---

### Post by ptn107 on 2007-11-29
Windows Vista is trying to install on a drive with a messed up MBR and partition table.  You should boot the Ubuntu Live CD and use Gparted (system->administration->partition editor) to remove all partitions on the disk and start anew.

---

