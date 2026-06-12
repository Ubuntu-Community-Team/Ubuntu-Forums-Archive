---
title: "How to resize boot partition (also / partition) with unallocated space"
date: 2018-11-07
forum: General Help
---

### Post by daveparkinson on 2018-11-07
[IMG]https://i.imgur.com/oXECg7L.png[/IMG]

so i'd like to extend /dev/sda1 the 3.42 gb of free space but... it looks like its on a separate partition.  even though everything is on one physical drive /dev/sda .. which by the way is a samsung evo 500 ssd. not sure if that matters

1) how can i expand my root partition /dev/sda1 with the free space?
2) is moving partitions really really really bad on a ssd ?  i already moved the /home partition (/dev/sda5) to the right to free up this space.
3) what did i do wrong if anything?

booted into a previous install of ubuntu on a separate drive.  

your thoughts appreciated!

---

### Post by oldfred on 2018-11-07
Your 3GB is inside the extended partition. 
If unallocated, you should just be able to move start of unallocated to start of sda2.
Then unallocated is next to sda1 & you can expand it.

Note if you used gpt partitioning whether UEFI or BIOS boot, you would not have the issued of 4 primary partitions and then requirement for extended partition and logical partitions.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Also what do you have in sda1? If you moved /home, it should be a lot smaller. 
This is my 18.04 install using under 8GB, with all data in separate data partition, so / is just the system files.
```
/dev/sda4        25G  7.6G   17G  32% /

 


```

---

### Post by Impavidus on 2018-11-08
I fully agree with oldfred.

Adding the unallocated space to sda1 will increase sda1 with just 12%. Whatever caused sda1 to be almost full, will probably make it again almost full pretty soon. As it seems most of your data is in sda5 (/home partition?), I think it may be better to do some cleaning on sda1.

---

### Post by daveparkinson on 2018-11-08
> **oldfred said:**
> Your 3GB is inside the extended partition. 
If unallocated, you should just be able to move start of unallocated to start of sda2.
Then unallocated is next to sda1 & you can expand it.

Note if you used gpt partitioning whether UEFI or BIOS boot, you would not have the issued of 4 primary partitions and then requirement for extended partition and logical partitions.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Also what do you have in sda1? If you moved /home, it should be a lot smaller. 
This is my 18.04 install using under 8GB, with all data in separate data partition, so / is just the system files.
```
/dev/sda4        25G  7.6G   17G  32% /

 


```

sda1 is / including all data applications etc... i installed a lot of software i suppose .. for ubuntu 18.04

---

### Post by daveparkinson on 2018-11-08
I'll look into those links in a bit; but trying to solve this right now....  if I try to expand partition /dev/sda1 it seems i cannot.  [IMG]https://i.imgur.com/3g9BXhO.png[/IMG]

---

### Post by Impavidus on 2018-11-08
First move the start of sda2 to the right, then expand sda1. Currently your unallocated space is inside sda2, which is a container for more partitions.

28GB is a lot, even if you installed several large application. I suggest you investigate.
[https://ubuntuforums.org/showthread.php?t=1122670](https://ubuntuforums.org/showthread.php?t=1122670)

---

