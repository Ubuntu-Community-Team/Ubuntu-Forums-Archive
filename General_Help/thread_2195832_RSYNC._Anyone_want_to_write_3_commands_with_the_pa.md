---
title: "RSYNC. Anyone want to write 3 commands with the paths?"
date: 2013-12-26
forum: General Help
---

### Post by mikodo on 2013-12-26
**Would anyone care to write the commands for 3, 4 and 7, so I can see how to do this, properly?**

This is a test. Yes, I want the *****data_file to be in two partitions on my usb drive. In reality, I will use UUID's instead /dev/sda1 etc.

 I don't care much which options I use for testing, but I will suggest as [Psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup"), we use: < rsync -av >
                           
RSYNC TEST

 
[LIST=1]
[*]I will place a **data_file**     on /dev/sda1/~/Desktop/ (My /home/Desktop/ on Xubuntu     12.04). 
[*]Identify where that file is.     (check if it is at /dev/sda1/~/Desktop/**data_file**). 
[*]Write Rsync  command to copy the** data_file** to /media/dev/sdf5/ (partition on usb drive) for     backups). Then, run it. 
[*]Write Rsync command to copy the (**data_file)** in      /media/dev/sdf5/**data_file** to /media/dev/sdf6/ (another partition on     usd drive). Then, run it. 
[*]See if I can use Thunar to open data_file in /media/sdf6/**data_file**. If good, go to 6. 
[*]Delete in     /dev/sda1/~/Desktop/**data_file**. (Delete the** data_file**) 
[*]Write Rsync command to Restore **data_file** from /dev/sdf6/**data_file** to sda1/~/Desktop/. Then, run it. 
[*]Check if I have the **data_file **again on     my desktop. (/dev/sda1/~/Desktop/**data_file**). If yes, then ... 
[*]Celebrate! 
[/LIST]
 
  Thank you.

---

### Post by oldfred on 2013-12-27
These are parts of my rsync file which you can modify. I started with this:
       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
I do not have any error checking other than the exit 0 if it finishes.

I only need this the first time I run it in a new install, but I have it in my file
# ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext3 /dev/sda2 /mnt/backup

echo "starting..."
rsync -aruvlP /mnt/data/Documents /mnt/backup
rsync -aruvlP /mnt/data/Projects /mnt/backup
rsync -aruvlP /mnt/data/Notebooks /mnt/backup
rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup
echo "done"
exit 0

I have another file that has a list of excludes so temporary files are not copied.

 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

      Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

 Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

---

### Post by mikodo on 2013-12-27
Thanks Fred,

I am only trying to learn to run the rsync commands, not a bash script with them.

I did garner some help from the Ubuntu Community link on Rsync. 

Interesting that you responded, as this is part of my plan to place *folders on a Data partition, (back them up too, eventually on another drive, yet) and then be able to symlink them back to the multi-boot distros' root folders, following your guides to do that.

*folders like:

Music
Documents
Pictures
Videos
PDF_Books

and the like ....

Thanks.

---

### Post by oldfred on 2013-12-27
I did that once way back when I converted to a Linux data partition. I already had NTFS shared data partition but only linked it into /home as one link.

But the rsync is the same command. You can also use cp with -a to preserve ownership & permissions.
The issue I always have with cp or rsync is whether I am including the / at the end and then whether I copy just the levels below or not. Sometimes duplicated entire copy.  Somewhere was a thread explaining that but I still mess it up.

I have a script to mount my laptop folders, and another script to copy some folders from laptop (LT). File structure is identical on both systems. Same script but with DT folders mounted in laptop to copy from desktop. 

But these copy specific folders. 
rsync -aruvP /mnt/data_LT/Documents /mnt/data
rsync -aruvP /mnt/data_LT/Projects //mnt/data
rsync -aruvP /mnt/data_LT/PDF /mnt/data

---

### Post by mikodo on 2013-12-27
> **oldfred said:**
> 
The issue I always have with cp or rsync is whether I am including the / at the end and then whether I copy just the levels below or not. Sometimes duplicated entire copy.  Somewhere was a thread explaining that but I still mess it up.


This is helpful as is the rest of this response. What I find helpful here is the knowing that if *you* are struggling with this as I have, than I don't feel so bad about my not knowing. I have asked in similar UF threads, and have not really got answers.

So, this is helpful and I will keep bumbling around trying different things until I think I have it right.

Seasons Greetings, by the way.

---

### Post by mikodo on 2013-12-27
Well, I tried fooling with some commands and got errors, before these commands worked:

                        > rsync -avr /home/mikodo/Desktop/Data_File /home/mikodo/Documents 
&
rsync -avr /home/mikodo/Desktop /home/mikodo/Documents
&
                        This command worked to put the Data_File and contents in a partition in the usb external drive (it had to be the UUID, I found).

 sudo rsync -avr /home/mikodo/Desktop/Data_File /media/d24088a9-87e1-4148-b874-df41ce1dc0d1

Following oldfred's stuff, I can make a /mnt/backup  directory and mount my internal drive /dev/sda10 to it by the following two commands:

sudo mkdir /mnt/backup
&
mount -t ext4 /dev/sda10 /mnt/backup

but, I haven't figured out how the rsync command to transfer data to it like:

sudo                       rsync -avr /home/mikodo/Documents /WHATEVER THE COMMAND IS to write to /dev/sda10

And last then, I need to see how to rsync data from /dev/sada10 to a partition on my usb ext.drive ( /media/d24088a9-87e1-4148-b874-df41ce1dc0d1)


Data_File is really a folder with a .odt file in it. I deleted the results, of the transfers!

Now, I just need to figure out how to write rsync commands to copy data, to different partitions and drives. (well, I got the usb drive command figured).

and ... copy data from partitions and drives to other partitions and drives.

---

### Post by oldfred on 2013-12-27
You just have to create a mount and mount that partition. 
Similar to my backup script does in post #2. Once you create a mount point it says in system unless you delete it. But I transfer script to new install and then forget to create mount and backup does not work as the mount does not exist, so I needed it in script.
And I do not normally mount my backup partition and often reboot, so I have to make sure it is mounted. If already mounted it just gives an error that it is already mounted. If something you already have mounted in fstab then it is already mounted.

---

### Post by mikodo on 2013-12-27
> **oldfred said:**
> You just have to create a mount and mount that partition. 
Similar to my backup script does in post #2. Once you create a mount point it says in system unless you delete it. But I transfer script to new install and then forget to create mount and backup does not work as the mount does not exist, so I needed it in script.
And I do not normally mount my backup partition and often reboot, so I have to make sure it is mounted. If already mounted it just gives an error that it is already mounted. If something you already have mounted in fstab then it is already mounted.
Thanks Fred.

Edit: 

I will try another day.

I need to read through what you have written in post #2 and other guides.

---

### Post by oldos2er on 2013-12-27
Have you tried grsync? You could run a simulation and make a note of the command it displays.

---

### Post by mikodo on 2013-12-27
> **oldos2er said:**
> Have you tried grsync? You could run a simulation and make a note of the command it displays.

No I haven't. Thanks. That may be an angle to pursue, cause I am not getting anywhere with moving data to different partitions or drives. I hope Grsync does that.

---

### Post by mikodo on 2013-12-27
Alright, I need to do something like this, (from Fred's post #2):

> mount -t ext3 /dev/sda2 /mnt/backup
This confirms mtab has already mounted my usb drive with it's partions. Okay, that is not the problem with that!
> sudo mount /dev/sdf5
mount: /dev/sdf5 already mounted or /media/d24088a9-87e1-4148-b874-df41ce1dc0d1 busy
mount: according to mtab, /dev/sdf5 is already mounted on /media/d24088a9-87e1-4148-b874-df41ce1dc0d1

This tells me I have to edit fstab to get be able mount an internal drive partition like below:
> sudo mount /dev/sda10
mount: can't find /dev/sda10 in /etc/fstab or /etc/mtab


---

### Post by oldfred on 2013-12-27
I am no expert on details of mounting, but you have to give the partition a place to mount to. You cannot just say mount a partition.

---

### Post by mikodo on 2013-12-27
> **oldfred said:**
> I am no expert on details of mounting, but you have to give the partition a place to mount to. You cannot just say mount a partition.

I didn't read through and try [following this]("http://linuxexpresso.wordpress.com/2010/03/14/mount-partitions-in-terminal-fstab/") like I thought I would. It looks like a good guide on mounting partitions and setting up auto mounting with Fstab. I may be using this later.

---

### Post by mikodo on 2013-12-28
Taken, from the first page of the thread where I just kept adding to post #6 :

> These worked:

**rsync -avr /home/mikodo/Desktop/Data_File /home/mikodo/Documents **    (I guess it should have been prefaced with sudo).
&
**rsync -avr /home/mikodo/Desktop /home/mikodo/Documents**  (sudo here too, I guess, though it worked without it).
&
                        This command worked to put the Data_File and  contents in a partition in the usb external drive (it had to be the  UUID, I found).

 **sudo rsync -avr /home/mikodo/Desktop/Data_File /media/d24088a9-87e1-4148-b874-df41ce1dc0d1**

Following oldfred's stuff, I can make a /mnt/backup  directory and mount  my internal drive /dev/sda10 with it by the following two commands:

**sudo mkdir /mnt/backup**
&
**sudo mount -t ext4 /dev/sda10 /mnt/backup**

but, I haven't figured out how the rsync command to transfer data to it like:

[B]sudo                       rsync -avr /home/mikodo/Documents /WHATEVER THE PATH IS to write to /dev/sda10 ...
[/B]
And then last, I need to see how to rsync data from /dev/sada10 to a  partition on my usb ext.drive (  /media/d24088a9-87e1-4148-b874-df41ce1dc0d1)

---

### Post by oldfred on 2013-12-28
If you create a mount like /mnt/backup and the mount the partition to that mount point, can you not copy to that mount? Just like my examples?
And then a second mount for the second location. But if an external device, it may have already automounted to a location. Often uses UUID, but I prefer to label partitions so default is the label. I try to remember to create labels when partitioning with gparted, but also have used disks (or disk utility) or command line. 
You then can make the from and to locations either the original from or the from can be the first copy and the to location is the external device.

If an internal drive you can permanently mount with fstab. And may have to set ownership & permissions of LInux formatted. 
       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

      If NTFS you do not need to set ownership nor permissions as it has none, but then how you mount it sets defaults. Also if copying Linux data you will lose ownership & permissions when copied to NTFS.
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

---

### Post by mikodo on 2013-12-28
Alright.

 More things seem to be working. All the below commands are working. 

The making of the directory /mnt/backup

 /mnt/backup is mounted with /dev/sda10

 I can rsync data to /dev/sda10, as I did twice in the commands. 

I was able to rsync data from my internal partition /dev/sda10 to my external drive partition.

Good! Why it wasn't working earlier is a mystery ...

Working commands below:

> sudo mkdir /mnt/backup   (the directory shows in nautilus)

sudo mount -t ext4 /dev/sda10 /mnt/backup     (the mount shows with nautilus, with /mnt/backup)

sudo rsync -avr /home/mikodo/Documents /dev/sda10 /mnt/backup   (data is seen with nautilus in /mnt/backup)

sudo rsync -avr /home/mikodo/PDF_Books /dev/sda10 /mnt/backup    (data is seen with nautilus in /mnt/backup)

sudo rsync -avr /dev/sda10 /mnt/backup/Documents /media/d24088a9-87e1-4148-b874-df41ce1dc0d1  (successfully moved data (Documents) from 

/dev/sda10 to my external drive partition as seen by nautilus)

sudo mount -t ext4 /dev/sda12 /mnt/backup (the mount shows with nautilus, with /mnt/backup) 

sudo rsync -avr /media/d24088a9-87e1-4148-b874-df41ce1dc0d1/Documents /dev/sda12 /mnt/backup ** Seen by nautilus to have transfered Documents from an usb external partition to /dev/sda12 an internal partition with nautilus. (with that I have transfered full circle).

---

### Post by mikodo on 2013-12-28
Question for the knowledgeable:

Do I need to umount the partition  /dev/sda10/ before rebooting, (to save the integrity of the data, in it)?

Addendum:

From Fred, and I guess if I do this, then the partition will be always available after reboot. If I don't do below, then I'll need to umount it before reboots, RIGHT???
> 
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data                 


Thanks.

---

### Post by oldfred on 2013-12-28
If an external device you should unmount with umount (no n)  to make sure all activity is done. 

Only mounts with fstab will be preserved across reboots. That is why I have a script to mount and run rsync to I do not have to run multiple commands each time. If Linux formatted the permissions & ownership will be preserved.

If an external device it will normally automount when you plug it in. But that may or may not be the mount you want. One more reason for labels.

---

### Post by mikodo on 2013-12-28
> **oldfred said:**
> If an external device you should unmount with umount (no n)  to make sure all activity is done. 

Only mounts with fstab will be preserved across reboots. That is why I have a script to mount and run rsync to I do not have to run multiple commands each time. If Linux formatted the permissions & ownership will be preserved.

If an external device it will normally automount when you plug it in. But that may or may not be the mount you want. One more reason for labels.

Alright. I saved everything, umounted my external usb device and rebooted.

Yep, I had to remount the internal (/dev/sda10), and then all the data was again accessible from the drive as before. I don't know about scripts, so I am Okay with running, the command below as needed:   

> sudo mount -t ext4 /dev/sda10 /mnt/backup

The files in the external usb drive's parition, booted up fine with Mtab, and were fully accessible, with nautilus.

I guess, because I only use "linux", I don't need to worry about taking ownership and permissions like fred showed earlier. Right???:

> sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data                      


---

### Post by oldfred on 2013-12-28
What partition format are you copying to?
NTFS does not have permissions & ownership and is ok for data, but not then any system files as they will lose the correct settings.
If you have not set permissions & ownership then you cannot copy yourself until you do. Usually root owns everything until you reset it. But you should only have to set them once and they will be preserved across reboots. Only issue can be if then mounted on a different system.

---

### Post by mikodo on 2013-12-28
> **oldfred said:**
> What partition format are you copying to?
NTFS does not have permissions & ownership and is ok for data, but not then any system files as they will lose the correct settings.
If you have not set permissions & ownership then you cannot copy yourself until you do. Usually root owns everything until you reset it. But you should only have to set them once and they will be preserved across reboots. Only issue can be if then mounted on a different system.

Thanks Fred. I only am copying to Ext4 file systems.

I can open all my copied data with nautilus,in my internal drive and external one, with my regular user. Not super user. So, I don't "think" I need to set perms and ownership. If I start to have any trouble, I have your data to change them, if need be.

Thanks.

---

