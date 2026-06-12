---
title: "Do I need to create a SWAP partition for this?"
date: 2007-08-15
forum: General Help
---

### Post by Bart_D on 2007-08-15
I have a question regarding swap partitions.  I've installed Ubuntu and XUbuntu and want to install another Linux OS AND IF successful, then I would remove Ubuntu keeping only Xubuntu.  The other OS is Zenwalk and I have to do a manual partition. 

I have 3 partitions with 2 different Linux distros installed, 1 empty partition and have unpartitioned space available.  I created the partitions using Gparted and am quite comfortable with using Gparted.

Here are my partitions (ALL on the same hard drive):
/dev/hda1   ext3     9.82 GB
/dev/hda3   ext3   19.61 GB   boot ------> I want to keep this as boot
/dev/hda4   ext3   14.70 GB   ------> I want Zenwalk to get installed on this partition
and there is some unpartitioned space

dev/hda2                      extended                 5.22 GB
       dev/hda6               linux-swap               2.14 GB
       dev/hda5               linux-swap               3.08 GB

I know that Ubuntu is on hda1(which I will wipe IF the Zenwalk installation goes successfully) and Xubuntu is on hda3(which I want to keep)
Also, judging from their sizes, hda6 might be connected with Xubuntu since it is smaller than Ubuntu just like the space taken up by the OS is smaller for Xubuntu than for Ubuntu.  So hda5 would be associated with Ubuntu....according to me anyhow.

Do I have to select Target Partitions?  And what do I select for the Swap partitions?  When I go to select target partition, the first screen shows me the 2 swap partitions and asks for me to select one or keep the defaulty which is BOTH.  BOTH is a bit scary for me!!!!  If I incorrectly select all the available Swap partitions, could my other Operating systems be wiped out?  Why doesn't it just create a new swap partition for Zenwalk?

If you need me to provide you with some further information, let me know.  Your help would be greatly appreciated.

EDIT:  OR do I need to use this to create a swap partition?  If yes, then would it matter if the partition is created from Ubuntu(which will be deleted later) or Xubuntu?
[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

---

### Post by dougfractal on 2007-08-15
You only need one swap partition (unless  you are doing virtualization). normally double your ram.

the swap is loaded from /etc/fstab  so all you linuxes can point to the one partition.

But i would be tempted to tidy your disk
> remove /dev/hda1 dev/hda5 dev/hda6 dev/hda2 /dev/hda4
add  /dev/hda1  x2 ram (say 2GB) swap
add   /dev/hda2   13.04GB   --> Zenwalk
resize   /dev/hda3  to 14.61GB    --> xubuntu 
add  /dev/hda4 extended  18.61GB
add /dev/hda6  18.61GB   /home     (user data for Zenwalk and xubuntu)

use liveCD gparted to do this.
When installing I miss out the /home partition and edit it in the fstab afterwards.
> 
sudo apt-get install ubuntu-desktop # to have ubuntu and xubuntu

---

### Post by Bart_D on 2007-08-16
> **dougfractal said:**
> You only need one swap partition (unless  you are doing virtualization). normally double your ram.

the swap is loaded from /etc/fstab  so all you linuxes can point to the one partition.

But i would be tempted to tidy your disk


use liveCD gparted to do this.
When installing I miss out the /home partition and edit it in the fstab afterwards.

Can you explain how to tidy up the disk without deleting the installed operating systems as I haven't done anything similar in GParted.

---

### Post by dougfractal on 2007-08-16
You  must use LiveCD 

check for any mounted disk
> mount
if mounted then
> sudo umount /dev/hdaX
 if LIveCD is using swap
> sudo swapoff -a

gparted
ext3 partition can be resized aslong as it is not mounted
so delete all the partitions that you don't what ( **is hda3 the only one you what to keep?**) 

If you are low on free space in hda3 because your /home is full you can create 

add /dev/hda1 x2 ram (say 2GB) swap
add /dev/hda2 13.04GB  format 
write and exit

###############  short of space, do the shuffle ##########
 tmp store your home from hda3 hda2
```
sudo mkdir -p /mnt/tmphome
sudo mkdir -p /mnt/hda3
sudo mount /dev/hda2 /mnt/tmphome
sudo mount /dev/hda3 /mnt/hda3
sudo mv /mnt/hda3/home /mnt/tmphome/
sudo umount /dev/hda3
sudo umount /dev/hda2
```


_back to gparted to finish off_
resize /dev/hda3 to 14.61GB --> xubuntu
add /dev/hda4 extended 18.61GB
add /dev/hda6 18.61GB /home (user data for Zenwalk and xubuntu)

**move to my new home**
```

sudo mount /dev/hda2 /mnt/tmphome
sudo mount /dev/hda5 /mnt/home
sudo mkdir /mnt/home/xubuntu
sudo mv mnt/tmphome/home/ /mnt/home/xubuntu/
```
[B]
fix xubuntu[/B]
```
sudo mount /dev/hda3 /mnt/hda3
sudo mkdir /mnt/hda3/mnt/homes
cd /mnt/hda3/etc
cd ../
rm ./home     #  should be empty
sudo ln -s /mnt/homes/xubuntu/ /home
sudo cp fstab ftab.old
sudo gedit fstab
> /dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 none swap sw 0 0
/dev/hda5 /mnt/homes ext3 defaults 0 2
/dev/hda2 /media/hda2 ext3 defaults 0 2
/dev/hdc    /media/cdrom0   udf,iso9660 user,noauto     0       0
```

If you get grub 21 error on reboot don't panic 
Install zenwalk or use the liveCD and fix
```
grub
> root (hd0,2)
setup (hd0)
```

I can't see any problems, If you are unsure leave out the resize.

---

