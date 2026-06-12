---
title: "Help choosing Advanced Format drive for a server running Ubuntu 18.04"
date: 2018-07-06
forum: General Help
---

### Post by calron on 2018-07-06
Hello, I am completely new to Ubuntu and I am building a server for the very first time.  Unfortunately, I have hit a road block and hoping someone here can help.

This server is being used to run a masternode.  I have everything minus the M.2 drive and SAS drives.
I plan to boot the OS from a Samsung 970 EVO and have 32TB of storage on SAS drives.  The SAS drives I am trying to choose between are either 512e or 4Kn formatted.  I am not sure which of the two to purchase for this build?  I have sent an email asking for some more specifics from the project running the masternodes, but I haven't heard back from them yet.

Once the build is complete, my server will run thru a performance test to see if it passes.  There is a list of servers which have passed, but none of them state whether they are 512e or 4Kn drives.

If you scroll to the bottom of this article, you will see the server requirements for running a masternode:
[https://medium.com/@hpbglobal/hpb-node-plan-06-19-2018-584eae8950bc](https://medium.com/@hpbglobal/hpb-node-plan-06-19-2018-584eae8950bc)

Here is the list of servers which have passed:
[https://medium.com/@hpbglobal/updated-testing-server-list-07-06-2018-60939da1e9fe](https://medium.com/@hpbglobal/updated-testing-server-list-07-06-2018-60939da1e9fe)

I am building my server with an AMD Epyc 7401P and this is the motherboard I chose:
[https://www.supermicro.com/Aplus/motherboard/EPYC7000/H11SSL-NC.cfm](https://www.supermicro.com/Aplus/motherboard/EPYC7000/H11SSL-NC.cfm)

The SAS drives I'm trying to choose between are:
[https://www.amazon.com/Seagate-Enterprise-Capacity-ST8000NM0075-Internal/dp/B014UYHJWS/ref=sr_1_5?s=electronics&ie=UTF8&qid=1530933516&sr=1-5&keywords=seagate+8tb+512e](https://www.amazon.com/Seagate-Enterprise-Capacity-ST8000NM0075-Internal/dp/B014UYHJWS/ref=sr_1_5?s=electronics&ie=UTF8&qid=1530933516&sr=1-5&keywords=seagate+8tb+512e)

[https://www.newegg.com/Product/Product.aspx?Item=N82E16822178843](https://www.newegg.com/Product/Product.aspx?Item=N82E16822178843)


Thank you!

---

### Post by oldfred on 2018-07-07
Do not know servers.

But drives started changing to 4K back in 2010. So 512 sector drives are now older or smaller.
[https://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

And any drive over 2TiB must be gpt partitioned and is normally 4K, but used as 512 logical.
My 1GB drive:
Sector size (logical/physical): 512B/4096B
But my smaller SSD is still 512.
Sector size (logical/physical): 512B/512B

---

### Post by calron on 2018-07-07
Thank you for your help.

If I understand correctly 512 emulated drives were created to bridge the gap between 512n and 4Kn.  512e drives read as 512 bytes, but are 4096 physical.  This sounds exactly like what you have mentioned.  I believe all SSDs are 512e?

I've read that 4K native drives are better for speed and less problems with alignment.  Is there any way for me to partition it so it can be 512b logical/4096 physical.  I would prefer to use a 4Kn drive since I have already ordered them.

Maybe it's best for me to buy the 512e drive instead since it shouldnt have any compatability issues with Legacy systems or other 512 drives?

Sorry if Im not using all the terms correctly, this is completely new to me.

---

### Post by oldfred on 2018-07-07
I have never specified 512 or 4K.
Are the new partitioning tools handle that automatically.
If over 2GiB, only use newer versions of fdisk, as old ones did not support larger drives. You have to use parted, gparted, or gdisk (if gpt).

---

### Post by calron on 2018-07-07
Thank you very much for taking the time to help me out.  I think I will stick to my original plan to install the OS on my SSD and use the 4Kn drives for storage. I like the idea of knowing my 4Kn drives are future proofed. All of my drives are over 2 GiB so I will use a newer version of fdisk as you suggested.  Looks like I still have a lot of work cut out for me, lots of research to do!  Thanks again

---

### Post by oldfred on 2018-07-07
If large drives then you need more info on gpt.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

If your boot drive is smaller, you still can use gpt partitioning. I have used gpt on at least one drive since 2010. Almost all drives are now gpt including most larger flash drives.
If using UEFI you must have an ESP - efi system partition, and if booting with BIOS but using gpt, must have a 1 or 2MB unformatted partition with bios_grub flag for grub to correctly install.

My SSD, but versions of Ubuntu have changed, otherwise still essentially the same.
[https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by calron on 2018-07-07
Wow, lots to read.  You have been a lot of help.  Thank you very much!

---

### Post by calron on 2018-07-07
One more question for you.  I plan on installing Ubuntu 18.04 onto my M.2 drive on Monday.  Then I'd like to install my 4Kn HDD drives on Tuesday went I receive them.  It shouldn't be an issue installing Ubuntu on the M.2 drive before adding the HDDs to my server, right?  I plan to boot the system from the M.2 and use the HDDs as storage.  I do not plan on running any OS other than Ubuntu.

---

### Post by oldfred on 2018-07-07
I do not know servers, you may want to post in the server sub-forum if issues with RAID or LVM.
The standard desktop installer removes anything you do not use. I see it remove lvm2 & some RAID tools. Not sure with Server install, but you can always just add whatever you need.

I have seen many with servers, but not yet real experienced with command line install a lightweight gui like openbox or xfce, not a full Desktop and all its applications. Not familiar with those gui.
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

       [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
[https://ubuntuforums.org/showthread.php?t=2395081](https://ubuntuforums.org/showthread.php?t=2395081)

---

### Post by calron on 2018-07-08
Thanks again.  I will read the articles you linked and ask for more details in the server section if needed.  Enjoy the rest of your weekend.

---

