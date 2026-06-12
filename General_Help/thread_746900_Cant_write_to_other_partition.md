---
title: "Cant write to other partition"
date: 2008-04-06
forum: General Help
---

### Post by benpari on 2008-04-06
When I installed ubuntu probably 7 or 8 months ago I separated the hard drive into 2 partitions, one that was roughly 30 and one that was roughly 20. 

I originally installed on the 20 gig partition but ended up installing on the 30. I removed all my files on the other partition but the OS was still on it, it would never let me read/write the the other partition from inside the OS on the partition I booted on. This wasnt a problem for a while but I am not in need of the extra space on the other partition but I cant write to it. 

What can I do to just make the other partition usable space? 


Thanks guys. 


If you need other information just ask.

---

### Post by keeler1 on 2008-04-06
So are you saying that you installed it correctly on the 20 gig partion, later installed on the 30 gig partition, and you could not read or write to the 20 gig partition from inside the 30 gig.

You said you deleted everything from the 20 gig partition correct?  If you cant read or write from it then how did you get access to delete everything.

Anyways, if you deleted everything off of it already, I would use gparted or qtparted and repartition it.  Delete the partition and reformat it.  That normally should fix it.

---

### Post by Gen2ly on 2008-04-06
That's odd benpari.  Were you able to seen the partition on the desktop or in the file browser?

I don't wanna go on a limb this early but it's possible the MBR has been corrupted, but lets try a couple things first.

What does "df -h" show you, if you could post it it be great.  Also what about "fdisk -l"?

---

### Post by warp99 on 2008-04-06
If the partition is read only there is an error when mounting the drive. When the system attempts to mount the drive read/write if there's an error it will default to read only. All you have to do is run fsck to check and repair the partition and you should be able to read/write  to the drive:

```
sudo fsck /dev/<name_of partition>
```

Edit:

It the other partition NTFS?

---

### Post by benpari on 2008-04-06
After messing with the partition yesterday it will no longer let me boot up on my normal partition. I am currently on a live boot disk, My plan was to transfer most of my important files over to the 20 gig partition(sda3) then reinstall on my 30 gig partition(sda1)

I still cannot modify the files on either drive but I can view that they are all still there.
I deleted the partition sda3 yesterday and recreated it, All thats on it right now is a file called "lost+found". 

When trying to copy a file from one partition to the other it tells me " error when copying to "/media/disk/". You do not have permissions to write to this folder" 

I tried using the the sudo nautilus command and sudo fsck. nautilus only let me access the files the boot disk created, and sudo fsck didn't do anything. 

df -h gave me this
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
varrun                252M  108K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  116K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
tmpfs                 252M   12K  252M   1% /tmp
/dev/sda3              19G  173M   18G   1% /media/disk
/dev/sda1              35G   32G  1.3G  97% /media/disk-1

and "fdisk -l" literally didn't do anything. 

Unfortunately I am almost completely terminal illiterate.....


Thanks guys.

---

### Post by Rocket2DMn on 2008-04-06
What happens when you try to boot your normal partition?  Is GRUB giving you errors?  If so, try using the Super Grub Disk to reinstall GRUB - [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
What is on your other partition?  Do you want to delete it?  Can you please post the output of
```
sudo fdisk -l
```

---

### Post by benpari on 2008-04-06
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4570    36708493+  83  Linux
/dev/sda2            6998        7296     2401717+   5  Extended
/dev/sda3            4571        6997    19494877+  83  Linux
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris
/dev/sda6            6998        7108      891544+  82  Linux swap / Solaris



What I want to do is move all my important files, which is roughly 12 gigs, from sda1 to sda3 then I will reinstall the OS on sda3. If I had a external hard drive I would just dump everything.....

---

### Post by Rocket2DMn on 2008-04-06
OK, let's mount both partitions from the LiveCD
```
sudo mkdir /media/sda1
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda1 /media/sda1
sudo mount -t ext3 /dev/sda3 /media/sda3
```
You should then be able to move the files from one drive to the other.

You also have 2 swap partitions, so you can delete one of those from System->Administration->Partition Editor on the LiveCD

---

### Post by benpari on 2008-04-06
Would you suggest I delete the bigger or the smaller one, 

-sda5 is 1.44 Gb
-sda6 is 870 mb

---

### Post by Rocket2DMn on 2008-04-06
That depends on how much RAM you have.  Swap is supposed to be 1.5-2x your RAM capacity.  The problem is if you delete one, you are just left with that extra empty space.  I think you may want to consider getting your hands on an external hard drive, backing up all your stuff, then just deleting everything off the drive and starting fresh.  Then you can set it up with just 2 primary partitions (and no logical/extended partition).  1 ext3 root partition, and 1 swap partition.

---

### Post by benpari on 2008-04-06
I think that is what I will do. I will wait till I have access to an external drive, and then see what happens. Until then everything I do on the computer will be done from this live cd.

Thanks for the help.

---

