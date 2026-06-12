---
title: "Permission to use spare internal hard drive"
date: 2014-04-22
forum: General Help
---

### Post by troysos on 2014-04-22
I put a hard drive into my computer, formatted to ext4 but now I can't use it. It says I need "root". I searched on this but most people have data on their drive and formatted different so the information is confusing to me. 
What do I need to do to use this spare drive? Thank you!

---

### Post by oldfred on 2014-04-22
Is this an internal drive? If so you may want to add it to fstab to permanently mount it.

But generally you have to have root (yourself) give yourself permission and ownership of the files in the new partition(s) on the new drive. Use chown and chmod commands. $USER is an internal variable for you, or just use your name.

       #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data


 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by Doug S on 2014-04-22
> **troysos said:**
> I put a hard drive into my computer, formatted to ext4 but now I can't use it. It says I need "root".What says you need root?

To use a spare partition on a extra drive on one of my computers, I do this:```
sudo mkdir /media/newhd
sudo mount -t ext4 /dev/sdb3 /media/newhd
cd /media/newhd
sudo mkdir bla
sudo chown doug:doug bla
```and then I have a directory on that drive that I (user doug) own:```
doug@s15:/media/newhd$ ls -l -d bla
drwxr-xr-x 2 doug doug 4096 Apr 22 20:48 bla
```

---

### Post by troysos on 2014-04-23
Yes it's an internal drive. I would like it to mount automatically because it's a HTPC. I'm going to need to do this to 3 more hard drives later on as well.

---

### Post by oldfred on 2014-04-23
Then you can use the templates suggested by Morbuis1 in above link.
You copy his example but use your UUID and create your own mount point like /mnt/video1 or /home/video1 or /media/video1 or what every name and mount you prefer. Use names that make sense for you and create each of those mount points first as Morbuis1's link shows you.

---

### Post by troysos on 2014-04-24
Thanks for everyone helping me but I'm lost here. I'm trying to follow [COLOR=#000000]Morbuis1 commands in the terminal but I'm not doing something right.  

After the very first command I get this ([/COLOR][COLOR=#000000]sudo parted -l)[/COLOR][COLOR=#000000]

 ([/COLOR]Model: ATA Samsung SSD 840 (scsi)Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  242GB  242GB   primary   ext4            boot
 2      242GB   250GB  8237MB  extended
 5      242GB   250GB  8237MB  logical   linux-swap(v1)

Then in the next step all I get is command not found or drive not found. This is what my the path for my drive looks like and what I'm adding to [COLOR=#000000]Morbuis1 commands.
[/COLOR]
/dev/sda1/media/htpc/b860011b-6656-4f12-959e-d639cc692d221

I know this should be easy but it's all very new to me. Thank you.

---

### Post by troysos on 2014-04-24
I just found something else in the General Help  area. Is it fine if I just "[COLOR=#000000]sudo nautilus" go to that drive and change [/COLOR][COLOR=#000000] permissions or ownership of that drive? Is that secure?[/COLOR]

---

### Post by oldfred on 2014-04-24
You are just showing one drive sda. Where is sdb?

Post this and we can give detailed instructions.

sudo parted -l
       sudo blkid -c /dev/null -o list
             sudo cat /etc/fstab

What name do you want for partition.

---

### Post by troysos on 2014-04-24
Only one drive for sda my boot up drive.
That name I would like for this drive is "downloaddrive" I just renamed it that through gparted. That's what it's showing up as now. 

/dev/sda1  ext4             /              50c1e868-0682-470e-8694-ade915b92c15
/dev/sda5  swap             <swap>         95507f7a-a1d1-4730-8d7a-34b612f2f035
/dev/sdb1  ext4    downloaddrive /media/htpc/downloaddrive b860011b-6656-4f12-959e-d639cc692d22

---

### Post by oldfred on 2014-04-24
Post the commands requested in #8 and I can create the exact line to copy and paste into fstab.

---

### Post by troysos on 2014-04-24
Is this what you mean when you said #8?

htpc@htpc-desktop:~$ sudo cat /etc/fstab
[sudo] password for htpc: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=50c1e868-0682-470e-8694-ade915b92c15 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=95507f7a-a1d1-4730-8d7a-34b612f2f035 none            swap    sw              0       0
htpc@htpc-desktop:~$

---

### Post by oldfred on 2014-04-24
Need also:
sudo parted -l
       sudo blkid -c /dev/null -o list

---

### Post by troysos on 2014-04-25
Model: ATA Samsung SSD 840 (scsi)Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  242GB  242GB   primary   ext4            boot
 2      242GB   250GB  8237MB  extended
 5      242GB   250GB  8237MB  logical   linux-swap(v1)


htpc@htpc-desktop:~$ sudo blkid -c /dev/null -o list
device              fs_type   label      mount point             UUID
-----------------------------------------------------------------------------------------------------
/dev/sda1           ext4                 /                       50c1e868-0682-470e-8694-ade915b92c15
/dev/sda5           swap                 <swap>                  95507f7a-a1d1-4730-8d7a-34b612f2f035
/dev/sdb1           ext4      downloaddrive /media/htpc/downloaddrive b860011b-6656-4f12-959e-d639cc69





Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  ext4


Thank you for doing this for me!

---

### Post by oldfred on 2014-04-25
Use Nautilus to unmount current mount of downloaddrive
Then copy & paste the code into fstab

sudo mkdir /media/downloaddrive
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
```
# added for sdb1 media drive
UUID=b860011b-6656-4f12-959e-d639cc69 /media/downloaddrive ext4 relatime 0 2
```


 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

You may also have to run the ownership and permissions command posted in post #2 except now using /media/downloaddrive instead of /mnt/data

---

### Post by kurja on 2014-04-25
oldfred,

gksu is no longer installed by default and pkexec doesn't seem to run graphical applications (without first configuring it to do so, I read). Is there a new recommended method?? I can only think of sudo su -> gedit, to launch graphical gedit with root privileges without installing or configuring something beforehand. I hope there's a better way!!

edit - sudo nano? :(

---

### Post by oldfred on 2014-04-25
sudo nano should work.
I just installed gksu in my 14.04 install and edited some files without issue.

---

### Post by troysos on 2014-05-04
Thank you everyone for helping me out. Everything is working like it should, thank you!

---

### Post by cptrohn on 2014-05-04
I just had this exact same issue yesterday (I couldn't remember the darn command line to take permission.)

I used ```
sudo chown -R user:user /media/user/partition_name
```  the -R makes it recursive so you still have ownership after a reboot etc.

---

### Post by kurja on 2014-05-05
> **cptrohn said:**
> I just had this exact same issue yesterday (I couldn't remember the darn command line to take permission.)

I used ```
sudo chown -R user:user /media/user/partition_name
```  the -R makes it recursive so you still have ownership after a reboot etc.

"[COLOR=#000000]If you specify the -R flag, the chown command recursively descends [/COLOR][COLOR=#000000]the specified directories" as it says on the manpage. Has nothing to do with what happens after reboot (which doesn't change file ownership).[/COLOR]

---

