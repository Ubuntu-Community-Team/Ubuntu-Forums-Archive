---
title: "how adjust and transfer harddisk to SSD drive"
date: 2017-11-13
forum: General Help
---

### Post by captain_rob on 2017-11-13
Hi,

I want to transfer all from my harddisk to my new SSD drive using the command  **sudo ddrescue -v --force /dev/sda /dev/sdb**. However the harddisk is bigger than my SSD.

My sda is 465.76 and sdb is 447.13. I want to use gparted to shrink the capacity of my harddisk (see attachment) Can i shrink only sda1 with 20 GiB after swap off ? And can i use the ddrescue command after that.?

Please help. I have this done never before

---

### Post by oldfred on 2017-11-13
I am a believer in new install. Often easier.
I just  installed 18.04  in a partition I already had, to test what will change and it took about 10 min to install. I do some scripts & copy of some things and after about an hour had a full working system similar to my 16.06 install.
But I have all data in a separate /mnt/data partition which I can link into each install, so all data is same.

You can easily backup list of installed apps, and re-install them. And then copy /home over to new install with rsync or cp (be sure to use correct options).
It also can be a way to confirm that your backup procedures are correct, but you still have old drive to got back to, if you forgot something. 

I think some have used Clonezilla.
 [http://clonezilla.org/](http://clonezilla.org/) 

With any copy like dd, you need to be careful of UUIDs. If not copied exactly then copy will not boot. But if copied exactly like with dd, you cannot reboot with both drives plugged in as you have duplicate UUID and system may not boot into correct partitions.

I see you have an old BIOS/MBR configuration. You may want to consider converting to gpt now as you have new drive. When Windows came out with UEFI. five years ago, I was already starting to convert all drives to gpt to I could move them into a new UEFI system later.

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

