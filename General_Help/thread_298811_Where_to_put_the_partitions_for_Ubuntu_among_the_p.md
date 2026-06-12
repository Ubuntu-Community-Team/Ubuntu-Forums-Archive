---
title: "Where to put the partitions for Ubuntu among the partitions for Win.?"
date: 2006-11-13
forum: General Help
---

### Post by LarsRoan on 2006-11-13
I've just got a brand new PC with a 250 gb hardisk.  Yesterday I installed Win.XP and made two part.'s with the Win's CD.   

Now I have to use the occation and get my first experience with Linux and Ubuntu.  Now I'm facing the menu for making optimal partitions.   In GParted my harddisc (232 gb) looks like this;

/dev/sda1  -  ntfs  -  20 gb                *(C in windows)*

/dev/sda2  -  extended  -  50 gb 
....../dev/sda5   -ntfs  -  40 gb           *(D in windows)*
......new Partition #1  - fat32 -  10  gb    *(this is my proposal)*

unallocated   -   -  163 gb 

And now I'm looking for a good advice for optimal partitions.  My major question is; 

Where shall I put the 3 partitions for Ubuntu (+ one fat32) in the system above?   
/ (ext3)                      10GB
/home (ext3)              50GB
swap                           1GB

Wouldn't it be best to place both the fat32 and Ubuntu just after Windows "D" in the extended partition?  - to get ubuntu as close as possible to the edge?  In such case should I use the unallocated space inside the extended p. , or should I reduce this sice down to D's 60 gb and use the unallocated space AFTER /dev/sda2, doesn't that mean a new primary partition?   As long as I can have up to four primary partitions per disk, or three primary partitions and one  extended partition - as I have, isn't it best to keep the primary free for Vista etc..?

What about "fat32" (shared space) inside the extended p., and finally the last ntfs (E in windows).  The ntfs is for secondary files, downloads...  How do I place this partition at the end of the disc?  By using the unallocated space inside /dev/sda2 (increase this) or the final unallocated space? And then defining "Free Space Following" of 0, isn't it?  

The root (ext3) is Primary and the ntfs and fat32 inside /sda2 is logical, isn't that correct?
I'm sorry for this basic questions.   I'm a noobie.  Please give me some advice so that I can start up and get practical experience with Ubuntu.   The first impression is really positive!

best reg.'s Roan, Norway

---

### Post by taurus on 2006-11-13
Maybe these would help...

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by LarsRoan on 2006-11-13
Thanks taurus.  I've seen your fist link, but unfortunately neither this nor your second link tell me where to put the partitions.   My major question is; to put them inside the extended dev/sda2 or to make a new primary dev/sda3.  
Because I have no experience about Linux, neither partitioning, I feel it's best to be sure.  And then, nothing is better than spesific advice from the community.

---

### Post by taurus on 2006-11-13
You can't install Ubuntu on /dev/sda2 since it's your extended partition.  You can't install it on /dev/sda5 since you already have Windows stuff on it.  On the other hand, you may want to leave 10GB (/dev/sda6) as fat32 so you can share files between XP and Ubuntu.  Therefore, you can use the rest of the space, 163GB, to install Ubuntu on it.  Or you can install Ubuntu on the 10GB and use 163GB to share files between XP and Ubuntu.

---

### Post by strabes on 2006-11-13
20 gigs - Windows (ntfs)
50-whatever gigs - Shared vfat
20-30 gigs - linux (ext3)
10-20 gigs - /home (ext3)
Then after all those you should make a few other partitions so you can try out different linux distros i guess.

---

### Post by LarsRoan on 2006-11-13
Thanks for helping me taurus.   During the last 24 hours I've searched a lot for getting the right info.  Now I'm motivated to take further some step and try Ubuntu.   
I thought it was possible to put Ubuntu also on the extended partition.   When I installed XP two days ago I made two partitions, C and D.  (D is still empty).  My harddisc is 250 gb.  What's your recomm. as long as I will give priority to Win. (still)?  To make a fat32 of 10 gb (as sda6 inside the extended) and then "use" the unallocated area outside /sda2 and then make a new  /sda3 like the picture called "Prepare partitions" here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing).  In that case sda3 will be a new primary, isn't that correct?  (I'm sitting next to the new pc.  As soon as you agree I'll go on and try to run GParted).

---

### Post by taurus on 2006-11-13
Well, it depends if you want to repartition your harddrive all over again, reinstalling XP.  Otherwise, you can install Ubuntu on logical partition.  Since I assume you want to share a bunch of files (music, videos, pictures, etc.) between Ubuntu and XP, may want to make that partition as large as possible in fat32.  10GB for Ubuntu is more than enough.

---

### Post by LarsRoan on 2006-11-13
Because D is empty, could it be an idea to delete or edit the partition so that it's not the extended but /sda2, and THEN define an extended partition and put Ubuntu in /sda3 as an extended?  In that way I will have only /dev/sda1 (windows C) after removing D:

Then I could put both win's D: and fat32 in /sda2.   Is this an alternative?

---

### Post by taurus on 2006-11-13
Yes, you can delete /dev/sda5 and make /dev/sda2 a primary partition of say 180GB (fat32).  Then, leave the rest of space as /dev/sda3 and tell Ubuntu installer to use it to install Edgy on it.  Ubuntu will create two more partitons (logical since you can only have 4 primaries but as many logicals as you want), one for / and one for swap...

---

### Post by LarsRoan on 2006-11-13
Only one further challenge;
I'm not sure how much I will use Ubuntu.  Due to some statistics software I'll still use Windows.  Due to others I think I will still go for ntfs as my primary folder for documents. Further on I "need" a FAT32 partition to share data.  Now it's getting complex for me.  How shall I do this?  One more primary partition?  C and D as separate primary, further one primary as fat32 and then finally an extended for all the linux partitions?

---

### Post by taurus on 2006-11-13
Yes, divide your harddrive to three partitions:  /dev/sda1 where you have XP (NTFS), /dev/sda2 where you share your files between Ubuntu & XP (FAT32), and leave the rest to Ubuntu.  The LiveCD comes with gparted where you can use to delete and resize your harddrive.  Remember to tell the installer to use the empty space at the end and it knows what to do with it.

---

### Post by LarsRoan on 2006-11-13
Thanks!
Sorry, I didn't expressed it clearly;
I will still go for ntfs as my primary folder for documents - and then use a separate partition (not C: in win's).  That means both C and D as ntfs.  Then furhter one common in fat32 and finally Linux.   
Is it possible to put both / , /home and the swap for Ubuntu into /sda2 as a primary partition (and logical), 
and then use the extended for C: (documents), fat32 (common) and maybe a final disc for downloads?
In such case it will be something like figure 1 of [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm) where all the partitions for Ubuntu is inside sda2/  and  the extended is like figure 1.
(I know GParted,  yesterday I started it up - but made no changes)

---

### Post by LarsRoan on 2006-11-13
Now I think I've found the way to do it - by your advice and this info, expecially figure 37; [http://gparted.sourceforge.net/larry/generalities/gparted.htm:](http://gparted.sourceforge.net/larry/generalities/gparted.htm:)  (total capasity 250gb)

/sda1 primary  - C for win's, ntfs, 20 gb
/sda2 primary  - D: -"-, documents, (maybe Vista later), ntfs, 30 gb
/sda3 extended - 
../sda5 logical  -  root, /  -  15gb
../sda6 logical  -  swap  - 1 gb
../sda7 logical  -  /home -  30gb
../sda8 logical  -  windows, fat32, 100 gb (for temp,download, common...)  

(also ref. fig 37, [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm))
It's possible for Ubuntu to boot from an extended partition, isn't that correct?

In this way I will have the major files at the end of the disc, space for Vista if.. if.., further space for 1 primary free...
What do you think?

---

### Post by koenn on 2006-11-13
looks OK, go for it.
I can't judge on the partition sizes you've choosen as that depends on your use of the computer, but you have a seperate partition for system and data under each OS, which is a good idea. Also swap between / and /home is a good idea : keeps the trajecory of the disk read had short if it has to move between swap and either / or /home ... looks fine to me.

Any Linux can boot from an extended partition. 
There used to be a limit to this in that the linux bootable partition had to start before the 1024th cylinder of the disk, but I don't know if that 's still the case, and I don't know where cyl 1024 will be on your disk. 

If you find you can not boot with your proposed configuratyion), just add a small primary partition (100MB max), eg right after hda1, assign /boot to it.

---

### Post by LarsRoan on 2006-11-13
Thank's for your reply.
My disc is 250gb, where to find the 1024th cylinder, I don't know.  
In a new book about Ubuntu I've found this setup (except the second disc for win.documents is fat32), and there the two first one cover 32gb out of 70gb.  That means that Ubuntu's boot partition will be just before the half of the desc.
Ok, now I'll try to fix this by GParted.  Cross your fingers..!

---

