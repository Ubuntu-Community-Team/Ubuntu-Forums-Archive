---
title: "How to recover deleted OS partition"
date: 2014-09-20
forum: General Help
---

### Post by lolo5 on 2014-09-20
Sorry to be that guy but the threads i saw dont seem to be directly applicable to the help i need. I have a long story so ill ask the question up front. Ubuntu live CD quickformated(?) my HDD. How can i restore the partition and data on my drive to be bootable and once its done can i repair my ubuntu install? Ive tried a lot of tools but i dont know how to use them and i think ive made things worse.

Ubuntu froze halfway through when upgrading from 12LTS to 14LTS through the upgrade manager so i did a hard restart. Broke it. It got to the login screen and was booting as 14LTS (there should not have been a login set) but i couldnt login with account or as guest. I wanted to repair the OS so The first thing i did was download bootrepair. I ran the automatic repair. I realised that boot repair wouldnt help and i 
needed to reinstall ubuntu. I was hoping there was a repair option on the livedisk. I couldnt figure out how so i chose the drive format option, Hoping it would give me a final prompt before the format started. Once i  realised the process had started i whipped the cord out but the damange was done. 

Ive now tried testdisk to try to resotre the drive but i dont know how to use it.  I downloaded rescue remix but its CLI only and i have no idea where to start. Grub doesnt seem to be on the drive either because the computer says there is nothing bootable during boot but bootrepair wont give me the option to reinstall grub.

Thanks very much.

---

### Post by oldfred on 2014-09-20
Hard restarts almost always corrupt file system and doing that midway thru things guarantees major issues.

Do you have any partition table at all, or was that fully erased. You then would need to use testdisk to see if you can restore partitions. Do you have any documentation on exact starts & sizes of partitions before you started. Like a copy of the Boot-Repair summary report or link to it?

I have not had to use testdisk to restore partitions, but its explanation is pretty good. If over time you have changed partitions, it may find several versions or original & newer. You have to select a set with no overlap of starts & sizes. And you need to know if primary or logical. All logicals will then be in the extended partition. Or if newer system with gpt, you do not have to worry about primary and logical.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by lolo5 on 2014-09-21
Im not even sure how to figure out if the partition structure is still there. Ive tried googling but i just have no idea what the difference between partition structures, MBRS and superblocks are. In test disk it doesnt seem to give the option to write an EXT4 partition structure. It only seems to cover ext2 and ext 3.

Heres the first thing i tried to do the fix the system. [http://imgur.com/4C98d3t](http://imgur.com/4C98d3t) i only got as far as the first command before i could get the output i needed to continue. [http://imgur.com/PUr6W3m](http://imgur.com/PUr6W3m) and heres the output when i tried another guide. [http://imgur.com/OLdGRsh](http://imgur.com/OLdGRsh)

Heres test disks optipns [http://imgur.com/DfJXXi6](http://imgur.com/DfJXXi6) [http://imgur.com/67olbKu](http://imgur.com/67olbKu) [http://imgur.com/pBvmFzT](http://imgur.com/pBvmFzT) .
Heres most of what the deep search finds but it doesnt seem to be anything important. [http://imgur.com/oXkrDD1](http://imgur.com/oXkrDD1)

---

### Post by blnl on 2014-09-21
Download Gparted Live CD [http://downloads.sourceforge.net/gparted/gparted-live-0.19.1-4-i486.iso]("http://downloads.sourceforge.net/gparted/gparted-live-0.19.1-4-i486.iso")
Boot from the live CD, then start gparted and you shall see if the partition structure is still there.

If the partitions are there, mount the partitions and backup the data onto an external drive before you do anything else.
Then you can format ubuntu partition using gparted, and install the fresh ubuntu system on that partition.

---

### Post by oldfred on 2014-09-21
Your first posts showed you chrooting into your system, but for that to work the ext4 partition with your Ubuntu install would have to be structurally ok, just not booting and needing updates.

If partitions are shown, you may just need to do fsck. If not there then you need testdisk to restore the partitions.

And if neither work then a new install and restore your /home and your data from your backups.

Better to run testdisk from your Ubuntu live installer in live mode.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

