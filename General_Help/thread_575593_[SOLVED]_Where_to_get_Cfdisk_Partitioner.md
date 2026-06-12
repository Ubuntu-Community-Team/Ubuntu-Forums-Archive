---
title: "[SOLVED] Where to get Cfdisk Partitioner"
date: 2007-10-14
forum: General Help
---

### Post by RuB3N on 2007-10-14
Where do i get cfdisk? Is there a download website that I can go to or do I have to go to the store and buy it?

---

### Post by RudolfMDLT on 2007-10-14
Open the terminal and type in "cfdisk"?

Why - what are you trying to do?

EDIT - if you want to edit partition tables there are better and easier ways to do it. Gparted or QtParted are better aps to use.

---

### Post by RuB3N on 2007-10-14
I am trying to partition my hard drive to try a new linux op. but i have tried gparted and i had no luck with that. I ended up skrewing things up. I dont want to get rid of my ubuntu b/c i have gotten to the point where i can get my way around fairly well. Always when i skrewed something up i would use Gparted to erase my hard drive and start over. But i really dont want to do that this time. so lots of ppl say cfdisk is the way to go.

---

### Post by RuB3N on 2007-10-14
This is the cf disk partitioner image of my pc. and i want to take 100gb out of this partition to make a 100gb new partition so i can load a new operationg system to it, and have ubuntu on the other.

---

### Post by RudolfMDLT on 2007-10-15
I have some advice and you may not like all of it! :)

You currently have running Ubuntu on 1 partition. Personally I'm running 4:
1) Root
2) Home
3) Swap
4) General stuff

The reason for this is that I can reformat, play end screw around and my Home partition and my Stuff will never be touched. When you install Ubuntu, you will see these options as preset mount points.

 I don't know whether when using cfdisk you will lose all the contents of the drive when you resize the partition. Gparted I know works - use the live disk. What sort of errors did you get last time? remember that when playing with partition tables you must ALWAYS backup the data on the drive or drives that you are working on. 

I recommend backing up the contents of your PC, at least the data you deem important. Reformatting your drive like above, into at least 4 or 5 partitions:

1)Root - 12 gigs
2) home - 10 gigs(or 5, depending on whether you want to use this folder alot)
3)Stuff - 75 Gigs(Games, mp3's videos what ever)
4) Extended partition - You can only ever have 4 partitions in a drive without an extended partition. An extended partition allows you to have much more drives.
4.1)Swap - Ram size times 2
4.2)Other - 100 gigs. You can chop this drive up further of the next OS.

I know this is not the easiest root but I promise you in years to come you will thank me. When Ubuntu crashes - All you need to do is reinstall and remount and all your data will still be there. With out this method you will always have to backup and reformat the entire drive.

Goodluck!

Report back and I'll see where I can help!

---

### Post by az on 2007-10-15
> **RuB3N said:**
> I am trying to partition my hard drive to try a new linux op. but i have tried gparted and i had no luck with that. I ended up skrewing things up. I dont want to get rid of my ubuntu b/c i have gotten to the point where i can get my way around fairly well. Always when i skrewed something up i would use Gparted to erase my hard drive and start over. But i really dont want to do that this time. so lots of ppl say cfdisk is the way to go.

You need to run parted (or Gparted / Qtparted) from a live cd.  The drive cannot be in use when you partition.  Cfdisk cannot make changes to your partition table without deleting the filesystem on it.

---

### Post by RudolfMDLT on 2007-10-15
> **az said:**
> You need to run parted (or Gparted / Qtparted) from a live cd.  The drive cannot be in use when you partition.  Cfdisk cannot make changes to your partition table without deleting the filesystem on it.

Out of all I wrote - The above is the most important! :)  Please do NOT use cfdisk with the live cd!

---

### Post by RuB3N on 2007-10-15
thanks for the advice! and i think that i can do that safely but im not sure how to back everything up onto a cd or dvd. Is there a program that does that automaticly or do i just copy everything and put it onto a cd or dvd?

---

### Post by RuB3N on 2007-10-15
I hope that im not posting on this subject to much.....
But i really want to get this right the first time and thank you very much [COLOR="Red"]RudolfMDLT [/COLOR] your way i think is the best way to go.

i backed up what i needed to keep and than i wiped my hard drive clean with Gparted. but im not real comfortalbe using gparted. so im just going to use the partition editer on the ubuntu live cd that i have. im going to partition it the way you suggested.

in the partition table it has:

|  Device  |  Type  |  Mount point  | Format?  |  Size  |  Used   |

/dev/sda
free space                                                        250059MB


Then it has the option to creat new partition
_____________________________________________________________________

How do i make the right partitions?

1) Root - 12gigs
2) Home - 10gigs
3) Swap - 2gigs (1gig RAM)
4) General stuff - 75gigs
5) Extended partition
5.1)Swap -2gigs
5.2)Other -100gigs

Ubuntu is going to be my main operating System. then my Extended partition is going to be my like op playground. trying new linux ops and stuff.




Thank you for all your help!

---

### Post by RudolfMDLT on 2007-10-15
Hi there! :)

You are not posting too much! :) I live in South-Africa, which means that You're mostly asleep when I'm posting! :P It 04:45 in the morning year - hopefully you are still awake!

Anyway, Using the Create New Partition Option, create and ext3 parition and in the size you need to enter whatever megabytes you want. 1gigabyt = 1000 Mega bytes(actually it's a 1024 but who cares!? ;) ), and then again 1000KiloBytes in 1 megabyte. 

So:


1)Select New Partition: 12000 Mb -ext3
2)Again, select New Partition: 10000 Mb - ext3
3) Again, select New Partition: 1000 Mb - Swap (I have 1 Gig ram and i have never used more than 100 megs in swap - If you are a serious developer, enter 2000 megs here but I doubt you will use it.)
4) Now, create a new parition, but this time, instead of Primary or Seconday, create and EXTENDED partition, use ALL the space left.
4.1)Within the new Extended partition, Again select new partition: 75 gigs ext3
4.2)The rest you can leave black or you can format it ext3 now.

PLEASE NOTE MY ORDER! you MUST create the extended partition as the 4rth - if you are interested ask when you post again and I'll give you a little more detail on why(I'm writing a test in 2 hours! :P )

You don't have to have 2 swap drives, use the same drive for all 5 versions of Linux you want to install.

Wtite down on PEN AND PAPER what drives you sized up for what so that when Ubuntu asks you where you want them mounted you know! :)

Also in the installer note that for example partition 1 will be /dev/sda1 and partition 3 /dev/sda3.

Best of luck,

Rudolf

PS: I Strongly advice you to use Gparted, it is on the live disk and the picture display really helps in seeing what you are doing and giving you understanding! :)

---

### Post by RuB3N on 2007-10-15
Yes im still awake :) i usually dont go to sleep till later even tho i have school. but your last post helps me a whole bunch!! and i use the 1024mb to a gig.

but hopefuly it works......


when i finish partitioning my hard drive and restart my pc and install ubuntu what partition do i install it to?

---

### Post by RuB3N on 2007-10-15
So the first 3 are primary and then the 4th partition is the extended.


i proubly did something wrong but i will post a screen shot of it.







thanks alot! and srry about the spelling.....

---

### Post by RuB3N on 2007-10-15
I get an Error when i try to install ubuntu.

It says


[COLOR="DarkRed"]No root file system is defined
Please correct this from the partitioning menu[/COLOR]



But i dont see a place where i can make a partition *root*.

Do i go back into Gparted to do that?

---

### Post by RudolfMDLT on 2007-10-16
I'm thinking this is in the setup we're talking about before the actual install begins?

When you install Ubuntu, select Manual partitioning. Now, assume you have already done the partitioning of your hard drive you have to define for Ubuntu where to dot what. The folder a drive goes in is called the mount point.

so, 

the 12000 mb drive you will mount as "/"
the 10000 mb drive as "/home"
the 1000 mb drive, you will not mount this because it is formated swap.
the  75Gb you will mount as "/yourfoldername"
and the other drive you can then mount or continue ignoring it.

But please make sure that the extended partition does indeed exists.

The reason the order is important is that as Gparted shows, the drives physically lie next to each other and to resize one, all the other ave to be moved up - having the extended partition on the end means you can resize and play inside that drive without touching your "permanent" drives.

Goodluck,

Rudolf    

PS: this must be really frustrating for you, still not having a working PC - It's now 12:00 noon this side of the globe. I'm going off line 10 hours from now  so if you still have trouble before 10 hours from this post drop me a mail @ [email]rudolfmdlt@gmail.com[/email] and I'll  come on line immediately. ;) Cheers.

EDIT: Please see the attached pick of how MY gparted screen looks

---

### Post by RuB3N on 2007-10-16
this is what i did with the partitions..... i think i mest up somewhere?

---

### Post by RuB3N on 2007-10-16
so do I flag /home as boot?    and do I install ubuntu to /home?

---

### Post by RuB3N on 2007-10-16
this is my latest screen shot of what i did w/ the partitions


i have a feeling i did something wrong.

do i have to install ubuntu for the "Mount point" to show up on the partitioner??

---

### Post by RuB3N on 2007-10-16
Please ignore all of my posts up till you last post because I have been trying new things since then. And this is hopelying my last post about this subject. 

-Am i suppose to format Ubuntu to the 3 first partitions or just one?

-Please correct me if i did something wrong about these partitions!

-this is a screen shot of Gparted.

-I installed Ubuntu on "/" and im not sure if i did it correctly. So please correct me!

---

### Post by RudolfMDLT on 2007-10-16
Perfect! :)

If you get lost with all the new Partitions, post back! :) As well, in your /, /stuff and /home folders, rightclick and click properties, you should notice that the drive size and free space differ. That is because these are the actual locations of your drive C, D and E! :) 

Best of luck further on!

Cheers,

Rudolf

---

