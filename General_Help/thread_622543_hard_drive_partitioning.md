---
title: "hard drive partitioning"
date: 2007-11-24
forum: General Help
---

### Post by catiusca on 2007-11-24
Got a 500GB hard drive and would like to set it in three. One for the system, and the other two for storage. I don't know the filesystem or what is it called in Ubuntu that Ubuntu uses for the partitions, but I used to have my HDD in NTFS in Windows. Now I need someone to give me a good suggestion on how large should be each partition and I think there will be aswap too or so. Pardon my newbie knowledge. I would like to keep 200GB and 200G for the second and third partition and the rest for first which will be the OS and remaining for swap or if not the full for OS. Whatever is best. THank you.

---

### Post by mikewhatever on 2007-11-24
You could allocate about 20 GB for root, 1 GB for swap. This would give you the basic setup. For more advanced schemes --> [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
The file system Ubuntu uses is ext3.

---

### Post by Zenguy on 2007-11-24
Yes, from my experience the previous post's suggestion would work well. You may consider also setting up a Home partition too. This will save you some trouble if you decide to upgrade or change distributions. I would probably set it up as:

20 GB /root (EXT3)
1 GB /swap
? GB /home (EXT3)
? GB (data drive 1) (EXT3 or FAT32 if you need to share with a dual boot Windows)
? GB (data drive 2) (EXT3 or FAT32 if you need to share with a dual boot Windows)

Keep in mind that you can resize the partitions in the future using GPARTED or another tool. If you go with my suggestion, you will need to create a logical partition to group some of the data partitions together due to the 4 primary partition limit.

How you cut up drive drive really depends on what you plan on using the data drives for.

---

### Post by catiusca on 2007-11-25
Thanks both for your replies. So i

I will be using the hard drive for one OS only. In this case, if I don't go with the /home partition I can do the following without problems?

example:

20 GB /root (EXT3)
1 GB /swap
100 GB (hda 1) (EXT3)
100 GB (hda 2) (EXT3)

What's the difference between /root partition and /home? I kind of know but am not that sos ure if I understood it. The recommended swap partition size is 1GB? I read about 2 GB too, what about if choosing to go with let's say, 5GB for swap?

---

### Post by sirdilznik on 2007-11-25
> **catiusca said:**
> Thanks both for your replies. So i

I will be using the hard drive for one OS only. In this case, if I don't go with the /home partition I can do the following without problems?

example:

20 GB /root (EXT3)
1 GB /swap
100 GB (hda 1) (EXT3)
100 GB (hda 2) (EXT3)

What's the difference between /root partition and /home? I kind of know but am not that sos ure if I understood it. The recommended swap partition size is 1GB? I read about 2 GB too, what about if choosing to go with let's say, 5GB for swap?

I believe you (and the other posters) mean the root partition ( / ) not root's home folder ( /root ).  This can be confusing, I know.  In Linux you always have a "root" user.  Root is the super-user or administrator and has full power and control over the system.  Generally you do not run as root except when you really have to (generally you use sudo to do that anyhow) and run as a user most of the time which has limited permissions.  /root is the root (or Administrator) home folder.  In contract / is referred to as root since it is the base off of which all other folders stem from (it is the tree trunk for the tree)  I believe the suggestion was for a 20 GB / and NOT 20 GB /root.  It is a very important difference.

/home is where user's home folders go by default.  If you make a user named "john" he will have a home folder /home/john.  The user will have full permissions on anything that goes into that folder (while having limited permissions in other areas) and this is often where programs and settings used by that user specifically are stored.  The advantage of putting /home on it's own partition is that if you ever decide to try a different distribution or OS, You can keep your old /home partition and set the new system up to use old partition so you can use your data from before.  For example you are not sure whether you want to use Ubuntu, Fedora, or Mandriva.  You can set up a different root ( / ) for each system (assuming you have the hard drive space) but still share the same /home partition for all 3 systems thus having the same exact user data in each case.

---

### Post by Zenguy on 2007-11-28
Yes, sorry for the confusion, and thanks for the correction.

The root partition is labeled by the partition editor as "/' not "/root" (minus the quotes)

I also suspect that when you get down to it, your root partition may end up being HDA1 and then the others will follow sequentially from there. The partitioning software will allow you to change the label of your first drive to "/" and also assign one of the data partitions to "/home" You may want to spend a little time playing with the partition editor to explore all of the options.

Declaring the "/home" label will also help you when the next version of Ubuntu comes out, if you want to do a clean install. Linux is very good about keeping the program data separate from the executables, but you have to have them on separate partitions to keep it simple.

P.S. Give some thought to putting the two data partitions into a logical partition. If you want to dynamically split them into three (or more) drives in the future, it will be a lot easier if they are already in a logical partition.

---

