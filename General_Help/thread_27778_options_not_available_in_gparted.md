---
title: "options not available in gparted"
date: 2005-04-17
forum: General Help
---

### Post by #Vizc@ch@ on 2005-04-17
Hi, i'm trying to resize de windows partition so that i can add that new gained space to Ubuntu.

The thing is that when i open gparted and select a partition to resize, the option isn't available  :-? 

What can i do?

---

### Post by TravisNewman on 2005-04-17
what type of partition are you trying to resize? FAT32 or NTFS?

---

### Post by #Vizc@ch@ on 2005-04-17
Ntfs

---

### Post by #Vizc@ch@ on 2005-04-19
Please could somebody help me out with it?, can I do it from the live cd.. i heard that the partitions have to be unmounted.. what's up with this? 
But does the live cd contain gparted?
Thanks

---

### Post by Bob D. on 2005-04-20
> i heard that the partitions have to be unmounted.. what's up with this? 
Appears to be true, I just took a look on my test box. Couldn't touch the / or swap partitions on hda.

To get GParted to work for resizing NTFS partitions you will also need to install 'ntfsprogs', a helper program GParted uses for resizing NTFS partitions.

If your system is set to mount your NTFS partition at boot, removing that command would be easy and make the NTFS partition available. I'm just not sure about adding the space gained to the Ubuntu partition is going to work from the booted drive.

Might be just as easy to download the SystemRescueCD from [http://www.sysresccd.org/]("http://www.sysresccd.org/"). Since it boots a live system from the CD and comes with QtParted on the disk, you can repartition without having to fool around with mounted partitions. It was conceived for just the task you are trying to accomplish.

I don't know if the Ubuntu LiveCD can repartition a drive...I'm sure it has parted (not GParted) but I don't know if it can be used as a utility as you want to do.

Bob

---

### Post by #Vizc@ch@ on 2005-04-20
Ok, thanks!

And as regards partitioning, to add more space to my Ubuntu, should i just resize /dev/hda2 the one mounted on / or should i also resize the swap and extended ?

---

### Post by Bob D. on 2005-04-20
I'm assuming you want more space for storage (/home) and that /home is on the same hard drive as root (/). If this is true, just add the new space to /. There would be no good reason to resize the swap space.

Bob

---

