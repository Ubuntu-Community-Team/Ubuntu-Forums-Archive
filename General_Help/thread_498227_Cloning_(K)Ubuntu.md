---
title: "Cloning (K)Ubuntu"
date: 2007-07-11
forum: General Help
---

### Post by Weaseal on 2007-07-11
So I have 9 computers at a computer center and I want to clone one of the systems that is fully set up to the other systems, however the requirements are pretty specific.  I need the entire hard drive copied (they are dualbooting WinXP and Kubuntu 7.04) to each machine, so each is exactly the same.

Earlier, someone suggested CloneIt ([http://www.ferzkopp.net/~aschiffler/Software/CloneIt/CloneIt.html](http://www.ferzkopp.net/~aschiffler/Software/CloneIt/CloneIt.html)).  This program requires 2 floppies, one for the server machine, and one for the client... the server transmits its entire hard drive image over the network and it is copied onto the client machine, however this program requires floppy drives, and none of my machines have floppy drives.  The program seems like a great idea, though, so I was wondering if anyone knew a program that did exactly the same thing but on CDs?  All of our systems have CD-Rs.

---

### Post by scxtt on 2007-07-11
you could use **partimage** to make a partition image of the "master" box and fire up live cd's on the "slaves" and grab the image over the network and "restore" it to the boxes needing to be cloned ... i  think it just uses NFS, so if that's working on the "master", should be a cinch for the "slaves" ...

---

### Post by Weaseal on 2007-07-12
Partimage says it can't run while the partition is mounted, but how can I run the program without having my root partition mounted??  There's options like SystemRescueCD but I don't have any blanks and my access to getting them is limited.

---

### Post by smoker on 2007-07-12
just a suggestion, i've never tried it:
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

also, the UBCD has some cloning tools included:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by scxtt on 2007-07-12
> **Weaseal said:**
> Partimage says it can't run while the partition is mounted, but how can I run the program without having my root partition mounted??  There's options like SystemRescueCD but I don't have any blanks and my access to getting them is limited.use a LiveCD ;)

1. boot LiveCD on "master"
2. configure networking on "master"
3. install partimage
4. make a partimage backup, stored on a drive that's not being backed up (obviously)
5. reboot "master" and make the partimage file(s) available via NFS
6. boot "slave" off LiveCD
7. configure networking on "slave"
8. install partimage
9. restore "slave" using NFS partimage from "master"

---

### Post by indytim on 2007-07-12
> you could use partimage to make a partition image of the "master" box and fire up live cd's on the "slaves" and grab the image over the network and "restore" it to the boxes needing to be cloned ... i think it just uses NFS, so if that's working on the "master", should be a cinch for the "slaves" ...

A couple of additional points on the above:
1.  To keep things really clean, you should have each of the slave hd's partitioned the same as the master (otherwise your fstab is going to get messed up on the slave's).
2.  The last time I checked, NTFS was still experimental with Partimage.

IndyTim

---

### Post by scxtt on 2007-07-12
i think the partition structure being restored to has to be identical (in size) as the drive from which the image was created ...

what's NTFS have to do w/ anything?

---

### Post by Weaseal on 2007-07-12
> **scxtt said:**
> what's NTFS have to do w/ anything?If you read my original post, you'll note that these machines are dual-booting WinXP :P

Thanks for the ideas.  As to whoever said that the drives have to be the same size for partimage, I do not believe this is correct.  I have read in the documentation that it only copies the used blocks, so theoretically a 20GB partition with only 5GB full could easily be copied into a blank 6GB partition.

Yes, fstab (and maybe grub too) will likely be a problem since I am not cloning the entire disk, but that's what LiveCDs are made for...

I was hoping to have something as simple as CloneIT, but in CD form.  CloneIT copies the entire drive, Windows, Linux, the MBR, the whole kit and kaboodle (so I don't have to go fiddling with fstab and grub on each machine).  If that doesn't exist then I'll probably take scxtt's suggestion and run partimage with a LiveCD.

---

### Post by smoker on 2007-07-12
> I was hoping to have something as simple as CloneIT, but in CD form. CloneIT copies the entire drive, Windows, Linux, the MBR, the whole kit and kaboodle (so I don't have to go fiddling with fstab and grub on each machine). If that doesn't exist then I'll probably take scxtt's suggestion and run partimage with a LiveCD.

see my link above for the UBCD, then read this about customising it with your own boot floppy images for cloneit onto the CD
[http://www.ultimatebootcd.com/customize.html](http://www.ultimatebootcd.com/customize.html)

---

### Post by scxtt on 2007-07-12
> **Weaseal said:**
> If you read my original post, you'll note that these machines are dual-booting WinXP :Poh, yeah - i did read it, i just mentally block anything related to windows ;) ... shouldn't have any problems copying an NTFS partition, i thought there were writing to NTFS issues more than just copying/reading it - and i thought we were past all that :p (ntfs-3g, etc.) - i haven't used a native windows install @ home in yeaaaars ...
> Thanks for the ideas.  As to whoever said that the drives have to be the same size for partimage, I do not believe this is correct.  I have read in the documentation that it only copies the used blocks, so theoretically a 20GB partition with only 5GB full could easily be copied into a blank 6GB partition.yes, it only copies what's used, but if you have a partition that's sized for 20G, 5G used (and a 5G partimage created) - you can't restore it to a partition that's sized @ 10G even tho you only need 5G ... that's how it's worked for me, and we're talking about MINOR differences in size ... doesn't care if it's >=, but it CAN'T be smaller ...
> Yes, fstab (and maybe grub too) will likely be a problem since I am not cloning the entire disk, but that's what LiveCDs are made for...i'm not sure if it copies the MBR, i've neved used it w/ a disk i boot off the MBR ... but if i remember correctly, it can restore an MBR from a partimage backup, so i would imagine it does :)

---

### Post by maestrobwh1 on 2007-07-12
Or... you could use "Clonezilla" like I did when I have 4 identical machines at work.  It boots from CD.  Also supports cloning over a network, but I just chose the local option.

I tried g4l (ghost for linux) and it was not as intuitive. I think it had a click and clone feature.  Check them both out, they are free.

if you have that many machines and can figure out how to use the clone over network, that might be your bet.

I didn't read the entire post... so I am not sure if you have an extra drive which could be a bit faster but I opened up the machines, took the disk out of each and put it into the one I wanted to clone, fired up the CD, got to the GUI and chose the local and clients entire disk.  It did my NTFS W2K partition, and my Kubuntu Edgy partition, along with my fat 32 shared partition, and swap.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by Weaseal on 2007-07-12
Awesome, thanks for the tips about CloneZilla and UBCD.  I'm getting both of those now and I will give them both a look.  I think we're on the right track now.

---

