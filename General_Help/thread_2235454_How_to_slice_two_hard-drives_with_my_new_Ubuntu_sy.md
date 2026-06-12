---
title: "How to slice two hard-drives with my new Ubuntu system?"
date: 2014-07-21
forum: General Help
---

### Post by patrikmellq on 2014-07-21
Hello.

I have a gaming computer with Windows 8 and will change it to Ubuntu LTS
Now the computer has two hard-drives with 500 GB each.

I want to install the Ubuntu system on one disc and the /home on the other disc.
That way i get /home on a separate disc and don't need to change that when i upgrade to next Ubuntu LTS after 2017

So what directories do i need /root /swap /var ... and so on ...
How large should each directories be?

Cheers Patrik

---

### Post by grahammechanical on 2014-07-21
Have you ever installed Ubuntu using the Something Else option? When we choose that option we set partition with the mount point of / (the place where Ubuntu is installed) and another partition with the mount point of /home. Then we can re-install Ubuntu into the / partition without over writing the /home folder in the /home partition. It should not matter what hard disk the partition is on that you want to be /home.

You will need a partition that you can set a mount point of swap. But the other others such as /var and so on do not worry about. They will appear as folders in the / directory of Ubuntu. Having the option to set them in their own partitions is based upon tradition and not one of modern practicalities.

Regards.

---

### Post by sedawk on 2014-07-21
I recommend to put everything to the first disk (at first) and also to have a big /home on the first disk (say 400-450 GB).
Then I would use a tool like rsync to create a backup of /home on the second disk on a regular basis. If you want to
have something fancy like Time Machine of Apples OS have a look here:
[http://askubuntu.com/questions/112948/is-there-an-application-that-is-like-time-machine-on-the-mac-osx](http://askubuntu.com/questions/112948/is-there-an-application-that-is-like-time-machine-on-the-mac-osx)
(I do something very similar with rsync and "--link-dest" option ...)

---

### Post by oldfred on 2014-07-21
I like to make each hard drive bootable with an install of Ubuntu. I then have data partitions which I mount and link folders into my install. If one drive fails, I can still boot other drive but may get errors on not mounting a data partition, but should in most cases easily run repairs.

       Creating a Dedicated Knoppix Partition for large drives (I use Ubuntu, and have a bit larger partition)
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

If all data is on another drive /home it tiny. Mine is 2GB and 1.5GB is .wine for my Picasa install. So I easily backup /home to other drive, DVD and flash drives. Some data is more valuable or changes more often so I backup some data folders more often than others. 

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by patrikmellq on 2014-07-21
Thanks for all the help, now i have some reading to do :-)

Cheers Patrik

---

### Post by Mark Phelps on 2014-07-21
> I have a gaming computer with Windows 8 and will change it to Ubuntu LTS

Good for you!! -- but I hope it's not your goal to replace the Win8 "gaming computer" with an Ubuntu "gaming computer" -- especially if you intend to play Windows games.

Why? Because you're likely to be very disappointed to discover that a PC that was built to perform well as a Windows PC, will not perform nearly as well running Windows games in Linux.

And, if you were unfortunate enough to buy a machine that has one of the Hybrid/Dual graphics hardware setups, you'll find those don't work well, either.

---

### Post by patrikmellq on 2014-07-24
You make a good point Mark ...

Question:
I read that you should have twice as much /swap then you have memory.
I have 8 GB memory, does this mean i should have 16 GB /swap?

---

### Post by oldfred on 2014-07-24
No.

The old rule of 2X RAM was when you had 256MB or 512MB of RAM. Then it became the same as RAM when you had 2GB of RAM. Then when RAM got larger you needed swap equal to RAM in GiB not GB only if you want to hibernate. With 8GB of RAM you will never use swap unless you edit video which I understand may use all RAM no matter how much you have. I have 4GB of RAM and never use swap. And system boots fast  enough that hibernation would not really save much if anything, and just adds issues.

I still suggest a little swap like 2GB just to have some. But some users report they have no swap and at least so far have not had issues.

---

### Post by patrikmellq on 2014-07-25
Thanks oldfred ,,, now i understand :-)

---

### Post by 3rdalbum on 2014-07-25
> **patrikmellq said:**
> Hello.

I have a gaming computer with Windows 8 and will change it to Ubuntu LTS
Now the computer has two hard-drives with 500 GB each.

I want to install the Ubuntu system on one disc and the /home on the other disc.
That way i get /home on a separate disc and don't need to change that when i upgrade to next Ubuntu LTS after 2017

So what directories do i need /root /swap /var ... and so on ...
How large should each directories be?

Cheers Patrik

Hi Patrik,

The next Ubuntu LTS is in 2016, and the one after that is in 2018.

You don't need to put /home onto a seperate partition or hard drive in order to upgrade. In the olden days (before 2009) if you did a clean install of Ubuntu it would automatically wipe out your /home if it was in the same partition as /. That's no longer strictly true - if you do a clean install using the "Something Else" partitioning method and don't tick the "format" box, it will preserve your existing /home even if it's in the same partition as /

So, while there are slight speed advantages and a lower possibility of filesystem corruption (already very very low on Linux) if you have /home on a different hard disk, it's not necessary to do this for easy upgrades or clean installs.

---

