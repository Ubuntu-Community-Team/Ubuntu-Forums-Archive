---
title: "software RAID setup in ubuntu"
date: 2007-11-11
forum: General Help
---

### Post by test006 on 2007-11-11
Hi,
I currently looking into setting up software based RAID file server. I have been reading all about linux software RAID. 
I have following questions:
On my file server how do i install the OS i.e. do i just install the OS in separate HDD with no RAID on it. I was thinking of using 2x 80GB HDDs in RAID 1 configuration for OS installation and 3x 320GB RAID 5 for data storage. Is this possible i.e. have RAID 1 and RAID 5 on the same box?
What happens if the drive with boot partition fails? Does this mean i have lost all my data on 3x 320G HDD RAID?
What happens if for example my motherboard has a fault and i need to get a new motherboard, how can i access the data within the RAID 5?

Will really appreciate your help ...

Thanks

---

### Post by fjgaude on 2007-11-11
> **test006 said:**
> Hi,
I currently looking into setting up software based RAID file server. I have been reading all about linux software RAID. 
I have following questions:
On my file server how do i install the OS i.e. do i just install the OS in separate HDD with no RAID on it. I was thinking of using 2x 80GB HDDs in RAID 1 configuration for OS installation and 3x 320GB RAID 5 for data storage. Is this possible i.e. have RAID 1 and RAID 5 on the same box?
What happens if the drive with boot partition fails? Does this mean i have lost all my data on 3x 320G HDD RAID?
What happens if for example my motherboard has a fault and i need to get a new motherboard, how can i access the data within the RAID 5?

Will really appreciate your help ...

Thanks

I can't answer all your questions but I do know something. The raid5 array can be used with any motherboard, any CPU, etc. Once it is made any Linux that has md and mdadm installed will be able to assemble it as it was. So if your boot drive fails your raid5 array is still good, ready to be used whenever you can re-boot. Yes, you can have raid1 and raid5 on the same box, even raid0 or raid6. <smile>

With regard to raid1, I believe you can handle that using the LiveCD or surely the Alternate CD, and make sure you setup raid during the install.

Now, there is a bug in 7.10, but not in 7.04, that doesn't permit it to boot from a failed raid1 array, one drive gone bad. I've never used such to install an OS. I feel that a good, fast single drive is best for the OS, and an array for data and the like that's separate from that single drive.

The last generation of drives are so fast, and getting faster now, what with the new Hitachi's 134 MB/sec seq read ones. I'm sure Seagate will be out with theirs to compete.

---

### Post by test006 on 2007-11-11
Hi fjgaude,
Thanks for all the info.
Just one point i am still not sure about and maybe you can help me out. 
Let say that i have a PC with one dedicated hdd for OS maybe a 80GB hard drive and i have 3 hdd for my RAID 5 array.
Lets say my motherboard goes faulty and i need to replace it with a new motherboard model. So in this case i will need to reinstall linux on my 80GB  hard drive since this is another model of motherboard. Now once i have linux installed and working how do i tell the raid tool that there is a RAID 5 array already configured on my 3 hdds. I cannot find any info on this part. I am unsure as to how this works and what are commands for bring online the RAID 5 array without losing any data.
Is this possible?

thanks

---

### Post by fjgaude on 2007-11-12
Sure it is possible and automatic. You see, md (multiple devices for raid) puts headers on each of the three drives that tells the kernel how to assemble the array. md is in the kernel, in all the later Linux kernels.

At anytime you can use the command

```
sudo mdadm --assemble --scan --verbose
```

to have the array put back together.

You monitor the array to see if it is healthy with this command:

```
sudo mdadme -D /dev/md[n]
```

The md[n] is the name you have chosen for the array when you create it. The n is 0, or 1, or any number.

Take a slow read, study of the man pages for mdadm:

```
man mdadm
```

It'll take awhile to understand all the features you have but they are there.

Good luck.

---

### Post by test006 on 2007-11-12
Hi,
Just want to understand the following command line:
sudo mdadm --assemble --scan --verbose
In this case --scan will look for a config file in the /etc directory. Does this mean i need to keep a copy of the old config file. Or do i need to just create a config file with all the three hdd listed in it and when i execute this command it will pick all the hdd from the config file and than it will know that those hdds have already got array configured on them and it will just assemble it and bring it online. The way it finds out that they already have an existing array is by using headers on each of the hdd which was put there by the md module.

Is this correct. 

This is based on my understanding on reading the mdadm man page.

Thanks

---

### Post by fjgaude on 2007-11-13
That seems correct. Once the array is made, each time you boot it comes up automatically, because you have put it in your fstab file.

---

### Post by ReturnPrivacy on 2007-12-11
Hi guys,
I'm new to linux. I want to install Ubuntu desktop on one drive, and also have 4 other drives that are setup as software raid 1 (mirror). I want to use this machine as a home file server. During install, can I tell Ubuntu to setup the 4 other drives as raid 1? Will Ubuntu do raid 1?. And, if so, how would I add more drives later to expand the total capacity of the raid 1 array? Can I just install more drives and have Ubuntu expand the array? Is this possible? Can someone please explain to me how to do this Please? I am new, and don't know any commands yet. I have an Asus A7N8X mobo, AMD Athlon XP 2200+ cpu, 1GB ddr ram, Gigabit ethernet pci card, 1 80gb hd for OS, 4 - 500GB hd's for the raid 1 array.

---

### Post by fjgaude on 2007-12-11
> **ReturnPrivacy said:**
> Hi guys,
I'm new to linux. I want to install Ubuntu desktop on one drive, and also have 4 other drives that are setup as software raid 1 (mirror). I want to use this machine as a home file server. During install, can I tell Ubuntu to setup the 4 other drives as raid 1? Will Ubuntu do raid 1?. And, if so, how would I add more drives later to expand the total capacity of the raid 1 array? Can I just install more drives and have Ubuntu expand the array? Is this possible? Can someone please explain to me how to do this Please? I am new, and don't know any commands yet. I have an Asus A7N8X mobo, AMD Athlon XP 2200+ cpu, 1GB ddr ram, Gigabit ethernet pci card, 1 80gb hd for OS, 4 - 500GB hd's for the raid 1 array.

Lots of things to learn and know here. Yes, Ubuntu can do raid1 and raid5. I would use one drive to install Linux on, and the other four in a raid5 array, using mdadm to create the array after that first drive has Ubuntu installed.

raid5 is fast and those four drives will give you 1.5 Terabytes of storage space. You can have one drive fault and the array continues. It is easy to add more drives to a raid5 array as needed.

How are you going to drive, i.e., what controller are you using for the drives; what motherboard, etc.?

Read the man pages for mdadm by entering this in a terminal:

```
man mdadm
```

What you are getting ready to do is a big task and will require you to learn some commands, how to use the command line, but if you are willing I will help as you get ready to actually make the array.

Okay?

---

### Post by rsw686 on 2007-12-11
You should search on Google for tutorials on how to do this. It is quite easy especially if your installing Ubuntu clean as you can use the partition manager. You also need to decide if you want LVM on top of the RAID.

For basic raid with no LVM:
- Create each partition and set the type to linux raid
- Create a raid device md0, md1 etc for each partitioning including all the drives in the RAID array
- Set the raid device to the file format you want (probably ext3 and swap)
- Select the mount point for each raid device

Before you put your important data on the array I highly recommend you learn to use mdadm. You should practice failing a drive, removing it and adding it back. Otherwise when a drive fails if you don't know what your doing you risk loosing all your data.

---

### Post by ReturnPrivacy on 2007-12-15
Hi,
I tried the newest version of the Ubuntu Cd desktop. It ran fine from the cd. It recognized everything. So, now I told it to install. Like I said earlier, I have 1 hard drive 40gb I want to put Ubuntu OS on. I also have 4 -500gb sata drives connected to a pci controller.(seen by ubuntu no problem) I want to set these 4 drives up as Raid 5.  I just started the install. I am now at the "prepare disc space" page, and it is asking me if I want to use guided resize ide master 1 (40gb drive) and use rest of space, guided-use entire disc (has 40gb disc and 4 - 500gb sata drives listed but greyed out) or manual. I am stopping here and waiting for instructions from you guys on what to do at this step. I want the OS to be on the 40gb ide drive, and all of the 4 -500gb sata drives to be a Raid 5 array (software by Ubuntu). Oh, and I plan on adding another pci sata card and adding another 500gb sata drive to the array. I already have the      5th 500gb drive, I just don't have a port to plug it into yet to make it part of the Raid array. So, I will need to know how to get the 4- 500gb sata drives going as a Raid 5 setup, and to know how to add more drives to the Raid 5 setup later. Thanks guys, I am really excited to get this install done and actually have a Linux machine! Eagerly waiting to finish the install!!!!

---

### Post by rsw686 on 2007-12-16
There are two ways of doing this. In the end you will end up with the same setup, just depends on the method you prefer. You can use the installer partition manager to partition all the drives and setup the RAID or you can just use it to partition the 40GB drive and configure the RAID from the command line.

If you want to use the installer. Use the guided partition manger on the 40GB. Now manually partition each 500GB drive creating a partition to use all the space and setting the type to Linux raid. Select the RAID option at the top and create a new RAID 5 device with 4 disks. Back at the partition manager screen you need to set the file type (probably ext3) and mount point for /dev/md0.

Or you just use the partition manager to configure the 40GB and install the OS. Afterwards from the console run the following. You either need to be root or use sudo before each command.

Determine which drives are the 500GB. For the directions we will call them /dev/sdb through /dev/sde 
fdisk -l

Then partition one drive.

fdisk /dev/sdb

Select n for new partition, p for primary, and then 1
Select t for type, fd for linux raid
Select w to save and quit

Now copy that to the remaining 3 drives.
sfdisk -d /dev/sdb | sfdisk /dev/sdc
sfdisk -d /dev/sdb | sfdisk /dev/sdd
sfdisk -d /dev/sdb | sfdisk /dev/sde

Create the array
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sd[bcde]1

Format it with ext3
mkfs.ext3 /dev/md0

Create the mount point folder (call it whatever you would like)
mkdir /data

Add the line to /etc/fstab with the correct mount point folder
/dev/md0        /data           ext3    defaults        0       2

Mount the drive
mount /data

When you go to add your fifth drive, doesn't matter which method you used above, you will run the following. This will take a good amount of time.

Unmount it to be safe
umount /data

Copy the partition to the new drive
sfdisk -d /dev/sdb | sfdisk /dev/sdf

Zero out the RAID superblock
mdadm --zero-superblock /dev/sdf

Add the disk and expand the raid
mdadm --add /dev/md0 /dev/sdf1
mdadm --grow /dev/md0 -n 5

Resize the file system
fsck.ext3 -f /dev/md0
resize2fs /dev/md0

Mount it again
mount /data

---

### Post by jagercola on 2007-12-25
> **rsw686 said:**
> There are two ways of doing this...

Wow, thanks so much for this...  I was debating between Windows Home Server and Ubuntu, but this just  pushed me over the edge in everything I need!

---

### Post by fjgaude on 2007-12-26
> **rsw686 said:**
> There are two ways of doing this.
[...]


Thanks for the fine, detailed instructions... many of us don't have the skill and knowledge that you have. Keep up the good support.

Happy New Year!

---

