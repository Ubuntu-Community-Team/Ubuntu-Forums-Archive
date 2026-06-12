---
title: "Questions about mdadm"
date: 2008-05-21
forum: General Help
---

### Post by obscure_detour on 2008-05-21
Hello, I just replied to an older thread, [here]("http://ubuntuforums.org/showthread.php?p=5011506#post5011506"), but realized it was in the archive so I decided to create a new one. I really just need some clarification on a few things as I'm new to mdadm.  Just got mdadm set up on my new hardy box with 3x 750GB drives in a RAID 5 array.

Here is the detail on the array:

```
root@server-desktop:/home/server# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 20 21:24:08 2008
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed May 21 01:22:29 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3460b99b:373d05ed:b33a6fc1:0129fa20
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
```

Now mind you, I have not mounted the array as of yet. Simply making sure everything is done correctly. It being mounted or unmounted wouldn't hinder the speed would it?

Code:

```
root@server-desktop:/home/server# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   1982 MB in  2.00 seconds = 991.22 MB/sec
 Timing buffered disk reads:  516 MB in  3.00 seconds = 171.82 MB/sec
```

Why is the cached reads so low? That's significantly lower than what I've seen is *normal*.

Also, on a side note I was curious once you have the array up and running. How can you go about creating separate partitions for use as /home, /etc?  Are you able to partition /md0(array) as you would a normal physical volume?

Is it best to create separate arrays that are partitioned for this? Or is it best to use LVM on top of the array?

Thanks in advance,

*obscure detour*

---

### Post by obscure_detour on 2008-05-21
Also, I couldn't find any recent documentation outlining if an i386 or 64bit installation would be more beneficial when using mdadm and software RAID.  My assumption would be that 64bit would be faster with the RAID array but I have nothing to back this up.  :)

Any help would be greatly appreciated.

*obscure detour*

---

### Post by fjgaude on 2008-05-21
You have created a filesystem for the array, eh?

It is best to create identical partitions on the individaul drives and then create an array for each partition, IMO.

Your raid5 array looks correct, normal. I use such as only for data, one partition only. Boot from a fast, single drive.

Your cache item shows for what it is, showing memory and CPU speed. The drive is good, very good. It's the speed of two stripped drives, as it should be for raid5.

I don't think 32- or 64-bit is faster for the array, one way or another. Both are good enough especially with what you show for your present array cache thru-put... here's mine, memory at 1066MH, CPU at 4.0GH, 4x raid5:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

To get as high as you are you must be using the very latest 2nd generation perpendicular read/write drives. What brand, please?

---

### Post by obscure_detour on 2008-05-21
Thank you so much for responding so quickly fjgaude :)

I have already created the ext3 filesystem for the array, yes.  To give you more information; I have an AMD X2 2.2GHz FSB@800, 2GB DDR2 800 RAM, 300GB IDE (boot), and 3x [Samsung Spinpoint F1 HD753LJ 750GB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152100") in the RAID 5 array.  They have 32mb of cache.  Maybe why they are so fast?  I created only one partition on each disk to complete the array.  Built the array and then created the ext3 file system within the array.  

I'm sorry to keep repeating things, but to clarify for me and hopefully for other people :-P, is that to have partitions for eg. /home, /etc, or for whatever reason.  You must create those partitions on the disks first.  Then build each array accordingly with those partitions?  So I have to redo everything, right? 

I really just wanted /home to be on the RAID array because people on the network have permission to their /home directories.  Kind of off topic, but if I mount my current array to /raid, is there any way to mount /home to /raid/home?  Or is it better and safer to have separate partition for it?

*obscure detour*

*edit:  I believe you can still get those drives at Fry's for $109.  I snagged three, as that's a steal.*

---

### Post by fjgaude on 2008-05-21
I can't say for sure how to go about what your wish... you can do something like having /home/raid and then use permissions to control who gets to the raid array. Somelike /home/frank /home/judy /home/jim and then soft link each to /home/raid. I use /home/raid and all my data is on the raid. Has worked just fine... my other two computers have access to the raid through SSH and Samba. I never used things like separate partitions for /var and /etc.

You might look into what it takes to use LVM with the array. I've never done it... some have troubles with doing it, other haven't.

Yep, you got a real steal with those really fast drives... I'm about to get one for just my boot OS, something like a Seagate ST3320613AS; it's 2nd generation also. You should have about half what I get for your cache memory/CPU reading. Try it three times and make sure there is nothing going on in the background when you run the hdparm test.

Let us know what happens, how you are doing.

---

### Post by obscure_detour on 2008-05-21
All is well, I decided to just mount it to /raid and remove /home as a shared option.

Anyways, I retested with hdparm:

```
/dev/md0:
 Timing cached reads:   2052 MB in  2.00 seconds = 1026.93 MB/sec
 Timing buffered disk reads:  518 MB in  3.00 seconds = 172.43 MB/sec
server@server-desktop:~$ sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   2088 MB in  2.00 seconds = 1044.55 MB/sec
 Timing buffered disk reads:  516 MB in  3.00 seconds = 171.82 MB/sec
server@server-desktop:~$ sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   2062 MB in  2.00 seconds = 1031.74 MB/sec
 Timing buffered disk reads:  516 MB in  3.00 seconds = 171.79 MB/sec

```

Rebooted, array was mounted automatically after configuration of fstab, and the retests went rather well.  I've started transferring data to them already.  Oh and I can't hear these drives, *period*.  My PSU is a very quiet Antec 500W, it literally makes no noise.  Needless to say, you can't hear them.  I couldn't be happier.  

Question, it created a link in "Computer" browser (Software RAID Device), and it goes nowhere.  Any way to edit the location it goes to or to get rid of it?  Doesn't matter to me either way just curious.

But I believe my file server is complete.

Thanks again,

*obscure detour*

---

### Post by fjgaude on 2008-05-21
Great... I'm not sure how to get rid of the icon, in Computer of Nautilus?

Likely it occurs because it is one of the devices running off of / and is in fstab. I don't get that as mine is off /home. Not sure if that is it.

Can't say why your cache memory/CPU reading is so low. You are off by maybe two times, but I could be wrong... these Intel 45nm CPUs are so much faster than the older AMDs.

Good luck and enjoy your powerful array. <smile>

---

