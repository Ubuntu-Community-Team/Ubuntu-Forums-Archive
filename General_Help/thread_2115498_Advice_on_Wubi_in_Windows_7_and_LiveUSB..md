---
title: "Advice on Wubi in Windows 7 and LiveUSB."
date: 2013-02-13
forum: General Help
---

### Post by zemega on 2013-02-13
I want to ask for general advice on two things. First is Wubi in Windows 7 Starter. For now, I do not get any problem, and that is because I'm only using Ubuntu 12.04 to run some necessary programs for my study. Is it advisable to keep it this way?, Or should I make a separate partition and install manually Ubuntu 12.04 (not Wubi)? 

The second question is, due to hard disk breakdown in my office, I'm using Ubuntu 12.04 on a 16GB USB. I used netbootin on another pendrive and installed 12.04 into the 16GB USB. And this situation is likely to stay for a few months (bureaucracy in replacing the harddisk). Is it okay to continue installing Ubuntu updates to the USB? I put my data and files in other USB, so the whole 16GB is just for the OS, updates and programs. Would it run out of space? There's some system lag/hang when I'm downloading GBs of data online or using torrent. Should I get an external HDD instead and install Ubuntu/Xubuntu on it? Again, this might last few months, so would installing Ubuntu as FAT32 would be alright instead of ext?, as I would like to use the external HDD for data storage as well (I'm alright with partitioning the HDD, though I'm not fond of it). Even then, its because I'm running specific programs that utilise the office PC to the maximum (all 4 processors on 100% usage for few hours, reading and writing from RAM).

---

### Post by black3agl3 on 2013-02-13
> **zemega said:**
> I want to ask for general advice on two things. First is Wubi in Windows 7 Starter. For now, I do not get any problem, and that is because I'm only using Ubuntu 12.04 to run some necessary programs for my study. Is it advisable to keep it this way?, Or should I make a separate partition and install manually Ubuntu 12.04 (not Wubi)? 
It is generally advised to install Windows and Ubuntu on separate partitions if you plan on using ubuntu regularly. Wubi is mostly for users who want to try out ubuntu with the option of easily removing it.
I have managed to run ubuntu for two or three months using wubi without problems.. Longer than that the updates tend to break the system... dunno why

> **zemega said:**
> 
Would it run out of space?  
Depends on what you do. How much space do you have left?

> **zemega said:**
> 
Should I get an external HDD instead and install Ubuntu/Xubuntu on it? 

That is exactly what i would have done in your case, given that you seem to think they will take ages to fix the HDD, unless you want to continue using your pen drive so that you can complain to them and give them some incentive to fix the broken HDD faster....


> **zemega said:**
> 
Again, this might last few months, **so would installing Ubuntu as FAT32** would be alright instead of ext?, as I would like to use the external HDD for data storage as well (I'm alright with partitioning the HDD, though I'm not fond of it).
Dont know if this is possible... though even if possible, my guess is that Ubuntu would run slower...
In your shoes, I would simply go with partitioning. How much space does your external HDD have?

> **zemega said:**
> 
Even then, its because I'm running specific programs that utilise the office PC to the maximum (all 4 processors on 100% usage for few hours, reading and writing from RAM).
hmm... I didnt quite get this part?
EDIT: you seem to say your requires mostly processing power and RAM but not so much storage space... Am i right?

---

### Post by zemega on 2013-02-13
Yeah, I usually turn on the PC at the office, load up my binaries directly into the RAM, and just ran my calculation at full power (running things directly from RAM takes less than a quarter time compared to reading writing binaries from spinning HDD). I guess my first question is answered then. External HDD is pretty cheap at my place, so I guess I'll keep things the way it is now. Thanks for your answer, it help me clear out some things. It says File System is using around 11.5 GB and I have free 4.5GB.  Is that bad for the future?

Edit:
Disk Utility shows me I have 12GB of ext4, 4.3 GB of Extended and 4.3GB of Swap Space. its a 16GB SanDisk Cruzer Pop.

---

### Post by C.S.Cameron on 2013-02-13
On external HDD's I make the first partition NTFS for use as data transfer and storage for both Windows and Linux computers.
I make the second partition ext4  "/".
I make the third partition ext4 "/home", which helps with upgrades.
The forth partition is used as swap space.

Ubuntu seems to run much faster on USB hard disk than on USB flash drive. 

A 16GB Flash drive should survive many updates unless you are keeping vacation photos, movies, etc on it.

---

### Post by black3agl3 on 2013-02-14
> **zemega said:**
> Yeah, I usually turn on the PC at the office,** load up my binaries directly into the RAM**, and just ran my calculation at full power (running things directly from RAM takes less than a quarter time compared to reading writing binaries from spinning HDD).
Just curious... how do you do it?

> **zemega said:**
> 
It says File System is using around 11.5 GB and I have free 4.5GB.  Is that bad for the future?
Well... just check your disc usage from time to time... If you estimate that your disk space usage is growing too fast and that you are going to need more than 16 GB anytime soon get that external HDD already... Otherwise continue using your pen drive since you seem to like it... 
In the end the choice is yours \\:D/

> **zemega said:**
> 
Disk Utility shows me I have 12GB of ext4, 4.3 GB of Extended and 4.3GB of Swap Space. its a 16GB SanDisk Cruzer Pop. 	

I kind of lost you here... 12+4.3+4.3 = 20.6 :confused: more than 16?

---

### Post by zemega on 2013-02-14
12+4.3+4.3 = 20.6, I'm lost as well, that's why I'm asking. its what the disk utility say. To load file into RAM, you just copy the files into /dev/shm/, also write to the same folder as well. When you need to do tedious and repetitous calculation and reading and writing at the same time, the speed of writing and reading is what limits the speed of my task. Even if the PC has quad processor 3.2 Ghz, it is wasted when the speed of writing and reading of your HDD limits everything. Don't get me wrong, Its just that what I need involves lots of reading and writing binaries at the same time. But the RAM used does not show up in System Monitor, so be careful with the amount you use and the amount your OS and program needs.

---

### Post by oldfred on 2013-02-14
The extended partition is a container for all of the logical partitions and will equal the sum of all the logical (and any unallocated if any). So if you only have 4.3 with a 4.3 swap, you have one logical partition that is swap and it is fully contained in teh 4.3 extended partition. You cannot count that twice.

       Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by black3agl3 on 2013-02-14
> **oldfred said:**
> The extended partition is a container for all of the logical partitions and will equal the sum of all the logical (and any unallocated if any). So if you only have 4.3 with a 4.3 swap, you have one logical partition that is swap and it is fully contained in teh 4.3 extended partition. You cannot count that twice.

So @zemega created a primary partition + an extended partition with a logical within it? Isn't it possible to create two primary partitions on the pen drive and use one of them for swap?

---

### Post by oldfred on 2013-02-14
Flash drive is like a small hard drive. I have several flash drives with multiple partitions. I even now use gpt partitioning on flash drive (first to prove it worked and learn how to use it, then just because it is newer).

As long as you do not need more than 4 partitions with MBR, you can have up to 4 primary partitions. 

Ubuntu usually defaults to swap in an extended so you have flexibility to add more logicals if need be. But flash drives are small and then you usually do not need more than four. But some newer flash drives are getting larger and cost is coming down.

---

### Post by zemega on 2013-02-14
Since the PC I'm using has 4GB Ram, do I need that 4.3 GB as swap space? After all, I can just use other USB as swap space provider, and I don't really run other prgram when I'm concentrating on my work. I do agree that flash drive are getting cheaper and faster, a 64 GB only cost me 1 week worth of food, so I can just fast for 1 week. Because I think flash drive are more stable and faster than HDD, and cheaper than SSD.

---

