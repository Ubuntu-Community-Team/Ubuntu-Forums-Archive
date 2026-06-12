---
title: "How to Dual Boot Ubuntu??"
date: 2008-05-13
forum: General Help
---

### Post by sunshine12 on 2008-05-13
I have been using Ubuntu since last year, but that was the only system on my PC. Now I purchased new 160GB HDD, and due to some personal reasons have to install Windows.

So, I partitioned HDD in 20GB C: drive   Installed Win XP (NTFS)
                         40GB D: drive   logical drive (NTFS)
                         100GB           Free space

I started the Ubuntu 8.04 live cd and started installing Ubuntu upto the point where you need to partitione HDD, goes to manual partition the HDD and it showed the above stats.

c and d drive is formatted with NTFS file system.

Now I want to install Ubuntu in 50GB space and other 50GB for windows, or may be whole 100GB for Ubuntu.

So, how do I proceed from this point further? I never used dual boot system and never did it in the past.

And I also have my old 20GB HDD preinstalled with Ubuntu, so how can I use that drive?

Thanks.

---

### Post by aysiu on 2008-05-13
Install Windows first.

Then follow these directions:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by sunshine12 on 2008-05-13
Thanks **aysiu** for the quick reply.

What is my concern is I have already installed windows and made other partition (logical drive) with NTFS files system, and now 100GB space is free(NOT formatted).

So, should I use guided partition or Manual partition? Or first I formatt the free space with NTFS?? really confused!! May be sounds naive but wants to make things clear before I do anything!!!

---

### Post by Caram on 2008-05-13
Manual isn't too hard. Just take the space and make one ext3 partition with the option being "/". A swap partition is also recommended.

---

### Post by sunshine12 on 2008-05-13
> **Caram said:**
> Manual isn't too hard. Just take the space and make one ext3 partition with the option being "/". A swap partition is also recommended.

Please can you elaborate more on this? In Manual partitioning should I select the free space and install Ubuntu there?

Thanks for quick response.

---

### Post by Caram on 2008-05-13
Are you installing the latest version? What you'll need to do in the partition editor is click on your freed space and select New. Set the filesystem to ext3 and the option below should be / and put however much space you want, minus 1-2GB. Then go to New on the remaining space and select linux-swap. Then just click Next, and you'll be set!

---

### Post by sunshine12 on 2008-05-13
Thanks Caram,
will do it.

---

### Post by sunshine12 on 2008-06-11
After going in the Manual Partitions, it shows the following inf..

/dev/sda1    ntfs   20GB
/dev/sda5    ntfs   40GB
free space          97GB


When I selected the free space and click on New Partition,
other window opened like "New Partition"

There are some options to choose..

Type of new partition... Primary or Logical
Size
Location.... Beginning or end
use as.... ext3 etc.
mount point... /etc.


Now can somebody please tell me what to choose from Primary/logical, and location Beginning/end, use as ext3 i think and mount point in both ext3 as well as in SWAP..

Cancelled the installation as I am not sure about this steps..

Please someone clarify this things.

Thanks.

---

### Post by sunshine12 on 2008-06-11
Someone please help, So that I can install Ubuntu. 

Thanks

---

### Post by sunshine12 on 2008-06-11
I am talking about this things shown in the image below..

[http://images.howtoforge.com/images/perfect_desktop_ubuntu_804/big/inst8.jpg](http://images.howtoforge.com/images/perfect_desktop_ubuntu_804/big/inst8.jpg)

---

### Post by pmlxuser on 2008-06-11
well for starters you can select 
Type of new partition... ->Primary
Size -> 98000 ,ie 2000 for Swap
Location.... ->Beginning (it just tells the parttioner where to start the partition table in the 
use as.... ->ext3 (the recent table format you can even choose ext2 but ext3 is the modern thing)
mount point... /  (if you want everything to be in one root director / however i would suggest the following

make a separate home Folder partition (it save data if the / system oes wrong).
ie

Type of new partition -Primary
size  ->70000 or something close
use as -> ext3
Mountpoint  ->/home

new partition
type of new partition -> primary
size ->2 x your RAM (recommended)
use as ->swap

new Partition
type of new partion -> primary
size -> 28000 (if you are using the 100GB -this would be the probable remainder if you follow my selection of parttioning)
use as -> ext3
mount pont -> / (for everything to be installed on)

hope it helps

---

### Post by pmlxuser on 2008-06-11
well for starters you can select 
Type of new partition... ->Primary
Size -> 98000 ,ie 2000 for Swap
Location.... ->Beginning (it just tells the parttioner where to start the partition table in the 
use as.... ->ext3 (the recent table format you can even choose ext2 but ext3 is the modern thing)
mount point... /  (if you want everything to be in one root director / however i would suggest the following

make a separate home Folder partition (it save data if the / system oes wrong).
ie

Type of new partition -Primary
size  ->70000 or something close
use as -> ext3
Mountpoint  ->/home

new partition
type of new partition -> primary
size ->2 x your RAM (recommended)
use as ->swap

new Partition
type of new partion -> primary
size -> 28000 (if you are using the 100GB -this would be the probable remainder if you follow my selection of parttioning)
use as -> ext3
mount pont -> / (for everything to be installed on)

hope it helps

---

### Post by sunshine12 on 2008-06-11
Thanks pmlxuser..

Please can you elaborate more on this.. I followed this link

[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

And in this installation there is three options given..

1. **If you want to keep your existing operating system **(e.g. Dual boot with Windows XP), select the first option: "Guided - resize the partition and use the freed space".
2. If you want to delete your existing operating system and you want to let the installer to automatically partition the hard drive for you, select the second option: "Guided - use entire disk".
3. Manual is the third choice at this point and I strongly suggest you to use it **if you don't have any other operating system installed and your hard drive does not contain important data on it.** Follow the instructions below:


Now My concern is that, in this article it suggeste that for dual booting and with other OS installed one should use **"Guided - resize the partition and use the freed space".**


So, what is the right choice here either **manual** or **guided**  Really Confused now!!! Want to make sure that everything will be correct before I install the system.

Thanks.

---

### Post by sunshine12 on 2008-06-11
I already have ~97Gb of free space, so manually partitioning that free space won't create a problem to the other OS(windows XP) or to the data.
I think.. please some one confirm this so I can start partitioning, and install ubuntu.

---

### Post by sunshine12 on 2008-06-11
Please someone help regarding this issue... searched google and it is more confusing..

---

### Post by chronographer on 2008-06-11
Hi. for Linux you need one partition for the system, and one for swap. your swap partition should be 2x the amount of ram you have. I use something lke this: 20 gig for / (root) and ~60gb for /home 20gig for windows, and another ~20gb for 'other operating system' (i.e. debian, or newer Ubuntu of old Ubuntu.

If you are confused, choose guided and choose 'use largest contiguous free space' I believe it says, hold on I'll find a [link.]("https://help.ubuntu.com/community/GraphicalInstall").

also try a google search for 'install hardy'

---

### Post by sunshine12 on 2008-06-11
Now I understand what to do in Manual partitioning. But where I am confused is in installation guide provided in following site

[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

Clearly says that Manual parition is not for dual boot??? For dual boot one should use Guided partitioning.

So, now what I want to know is what mode of paritioning is suitable for me. either Guided or Manual.

Thanks for replying, Now almost near to the solution.

---

### Post by chronographer on 2008-06-12
Manual is for everything. Just make a new partition for linux / one for swap and leave the windows one alone (make sure you DON'T format it). Its what I use for dual boot! 

You will be fine!

---

### Post by sunshine12 on 2008-06-12
> **chronographer said:**
> Manual is for everything. Just make a new partition for linux / one for swap and leave the windows one alone (make sure you DON'T format it). Its what I use for dual boot! 

You will be fine!

make sure you DON'T format it... I think you are talking about the partition installed with windows. So, if I use the free space and don't touch the windows partitions then there will not be any problem.

Thanks chronographer fore reply.

---

### Post by sunshine12 on 2008-06-12
> **pmlxuser said:**
> well for starters you can select 
Type of new partition... ->Primary
Size -> 98000 ,ie 2000 for Swap
Location.... ->Beginning (it just tells the parttioner where to start the partition table in the 
use as.... ->ext3 (the recent table format you can even choose ext2 but ext3 is the modern thing)
mount point... /  (if you want everything to be in one root director / however i would suggest the following

make a separate home Folder partition (it save data if the / system oes wrong).
ie

Type of new partition -Primary
size  ->70000 or something close
use as -> ext3
Mountpoint  ->/home

new partition
type of new partition -> primary
size ->2 x your RAM (recommended)
use as ->swap

new Partition
type of new partion -> primary
size -> 28000 (if you are using the 100GB -this would be the probable remainder if you follow my selection of parttioning)
use as -> ext3
mount pont -> / (for everything to be installed on)

hope it helps


There is one confusion now... pmlxuser says use primary in all partitions, and softpedia installation guide says **primary** for / and **logical** for /home and swap

Now what is this **Primary** and **Logical** types, and what difference they make??

---

### Post by sunshine12 on 2008-06-12
**Primary** or **Logical** is the main dillema now!!!!
10GB for /
89GB for /home
1GB for swap

but primary or logical??

---

### Post by sunshine12 on 2008-06-12
Primary or Logical is the main dillema now!!!!
10GB for /
89GB for /home
1GB for swap

but primary or logical??

Thanks

---

### Post by chronographer on 2008-06-12
Hi. it only matters for windows.. If you have windows installed, don't worry about it! If you don't have windows installed, install it first on a Primary partition.

Maybe a bit more for your / . 15 or 20! (well I just checked, I'm using ~7gig for my install with lots of software installed... so you shouldn't need more than 10-15 actually)

---

### Post by sunshine12 on 2008-06-12
Thanks chronographer.. 

So finally will do manuall partitioning.

---

### Post by sunshine12 on 2008-06-13
Done Partitioning with

15GB for /          primary ext3
84Gb for /home      logical ext3
1Gb for swap        logical

everything gone fine and I restarted the pc after installation completed.

But the next screen came when the computer restarted was ....

[B]GRUB loading stage 1.5

Grub loading please wait....

Error 18[/B]


What to do now....?? Writing this message from Live cd. That / partition should be logical instead of primary?? should I change something in BIOS setting??

Plese reply.... I messed up something or what??

---

### Post by sunshine12 on 2008-06-13
Error 18 is as follows:


18 : Selected cylinder exceeds maximum supported by BIOS This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

---

### Post by sunshine12 on 2008-06-13
Somehow problem solved...

This is what I have done, 

Repartitioned using live cd and used 8Gb for / ... logical
90Gb for /home logical and 1Gb for swap

This solved the problem, don't know how!!

---

