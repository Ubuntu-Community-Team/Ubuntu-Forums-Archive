---
title: "cloning a new drive?"
date: 2020-02-15
forum: General Help
---

### Post by garyed on 2020-02-15
I'm planning on going to a Solid state drive for my boot drive so i want to clone my older standard HD to a new SSD. I'm thinking about using the dd command to do the clone the since it looks pretty simple. My standard HD is 1TB & I plan on getting a 1TB SSD to replace it with.  I have two questions for anyone familiar with the cloning process. 

1 -  Is the dd command as reliable as typical cloning software or is there a better recommended way to clone the drive?
2 - Will Grub need to be reinstalled or updated to recognize the new drive uuid# ?

---

### Post by yetimon_64 on 2020-02-15
1 - Be EXTREMELY careful when using dd. If you make a mistake it is very easy to overwrite your system partition or, as I have done, overwrite a storage drive. Such accidents are usually totally unrecoverable. Make sure you have everything important  you don't want to lose backed up prior to using dd. It has a few nicknames including the likes of "disk destroyer" or "data destroyer".

There is a wrapper script for dd written by one of the staff members here, sudodus, that may be safer to use and worth checking out...[[COLOR=#0000ff]--Tutorial for mksub--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=1958073&page=88"). I have never used mkusb myself but from what I've read it has quite a few uses for dd, including cloning and writing image files etc. It would be much safer to use such a script than plain dd if you are not familiar with the dd command.

2 - I suspect you may need to run the "grub-mkconfig" command on the new system, though I'm not 100 % sure about that. Await further advice from more experienced helpers with grub issues there.

Regards, yeti.

---

### Post by tea for one on 2020-02-16
I would suggest that you consider using Clonezilla [https://clonezilla.org/](https://clonezilla.org/)

It will allow you to choose source and destination when using the **device-device** option which should reduce the risk of mistakes. 
yetimon_64 kindly pointed out the dangers of dd.

If you clone device to device (i.e. hdd to sdd), your uuids will remain the same.
However, you should **not** have your source drive and target drive connected **after** cloning because you will have duplicate uuids and confusion will occur.

Clonezilla should have no difficulty copying and using grub unless you have some unusual set-up.

If you have Windows installed also, then there are special considerations when changing drives. I do not have Windows so I am unable to elaborate further. The Clonezilla FAQ has some pointers.

If you only have Linux Operating Systems on your hdd, then give Clonezilla a whirl because, in my experience, the source disk will still function perfectly even if the clone to the destination doesn't go as planned.

---

### Post by vidtek on 2020-02-16
Gary-
Clonezilla is your friend.  Forget all other solutions.  The easiest way is to stick it on a bootable thumb drive, run it as root and choose "Expert" not beginner.

Do a disk-to disk clone, choosing your source and destination drives with care!

***When you get to the multiple options screen, there is an option to clone to unalike drive sizes.***
 
Sods law, you will probably find the SDD drive is a few megabytes smaller than the old HDD, so it is important you check this box.

I do this operation on a regular basis, and I have 7 partitions on my 250gb O/S sdd drive.

The EFI partition (fat32) is the most important for booting, I try to make this at least 400mb, the default is about 250mb from my failing memory and I make this the first (dev/sda1).  Then there is a windows hidden 100mb, then my windows 10, about 100gb, then a windows recovery about 500mb, then my Ubuntu partition of about 50gb, my /home partition of 76gb, then some unallocated space for the unequal size of my three 250gb sdd's of different manufacture. See below.

[LIST=1]
[*]Boot partition <>400mb              /dev/sda1
[*]Windows hidden 100mb             /dev/sad2
[*]Windows 10 100gb                     /dev/sda3
[*]Windows recovery <>500mb      /dev/sda4
[*]Ubuntu 50gb                               /dev/sda5
[*]/home 76gb                                /dev/sda6
[*]unallocated
[/LIST]

I have had 100% success with Clonezilla on all three of these drives.

Just take your time and double check each step and you'll be ok.

UUID's will be identical, and you should be able to boot without any extra steps.

I also use a standalone 2-drive cloning dock which makes life much easier!

Cheers, Tony.

---

### Post by TheFu on 2020-02-16
> **garyed said:**
> I'm planning on going to a Solid state drive for my boot drive so i want to clone my older standard HD to a new SSD. I'm thinking about using the dd command to do the clone the since it looks pretty simple. My standard HD is 1TB & I plan on getting a 1TB SSD to replace it with.  I have two questions for anyone familiar with the cloning process. 

1 -  Is the dd command as reliable as typical cloning software or is there a better recommended way to clone the drive?
2 - Will Grub need to be reinstalled or updated to recognize the new drive uuid# ?

Generally, I use ddrescue instead of dd.  ddrescue keeps going after a failed sector is hit and will try multiple times.  dd/ddrescue is only dangerous if you don't read and understand the manpage.  Any other tool is only more complex because it tries to prevent humans from making mistakes.  I suppose these mistakes are common enough to have a cottage industry?

I've never cloned an entire disk from HDD --> SSD. Seems there are enough physical differences to make that less than optimal. If the sectors are misaligned or the sizes are even slightly off, then performance will be impacted.  

Also, this is a good opportunity to 
[LIST]
[*]Ensure GPT is used
[*]Resize partitions
[*]Use LVM, if you like
[*]Add encryption
[*]Test your current backup + restore method
[/LIST]

If you don't have a backup/restore method today, now is the time to get one and test it over and over until it does what you need.

With respect, Clonezilla and other similar tools are great if you need to create a master image for 20-50,000 systems.  Regardless, you still need a backup solution that is run weekly (at least!), supports versioning, doesn't require booting off alternate media, can be installed onto completely different hardware without risks - and clonezilla just ain't that. Clonezilla is more complex than a byte-for-byte clone needs.  Plus, using dd/ddrescue, we can create a file-based, compressed, copy of the partitions, file systems or entire disk just by using normal Unix piping and redirection.

**fsarchiver** can make images, similar to clonezilla or dd/ddrescue, but it can also restore them to smaller partitions without fail provided the actual needed data will fit into the smaller partition.  Just an option.  But it is still an imaging tool, just with a few more options and understanding about select file systems to be a little more efficient.

1% of the time when I don't use my normal restore methods (which is the other 99%), I'd use **rsync** to copy data to the new storage.  rsync can be used to grab the most recent data from my backup tool of choice (rdiff-backup), so nothing special is needed.  Or you can just mirror the partitions using ....
```
sudo ionice rsync -av --stats --progress /source/ /target/
```
Do that for each partition and be happy. I'd use temporary locations for the target to keep out of trouble. Might want to exclude the /target/ from the source if the target is mounted below it.  The problem with not using the restore method of a backup tool is that certain special files will cause problems - like /dev/urandom & /dev/zero - which never runs out of data when asked.  rdiff-backup has an exclude option for that *--exclude-special-files*.  A tiny thing unless you forget it.

If your current install has LVM already, there are many more options by adding a mirror, then breaking it or using **pvmove**.  pvmove is freakin' amazing.

---

### Post by oldfred on 2020-02-16
I always suggest new install.
It also housecleans all the cruft that builds up even with regular housecleaning. 

And as TheFu suggests it is a good time to confirm your backup procedures are correct as you still have original drive to go back to in case you are missing something important.
And if planning to continue to use HDD, you may want to reorganize your system.

---

### Post by garyed on 2020-02-16
Thanks for all the advice,

I really don't want to have to do a fresh install & that is why I want to clone the drive. I just upgraded to Windows 10 on the drive I want to clone & I have two other versions of Ubuntu on that drive too. 
If I reformat the original drive after it is cloned will that change the uuid so it won't conflict with the new SSD?
Here's a gparted view of the drive I want to clone.

---

### Post by HermanAB on 2020-02-16
BTW, all the copy commands work the same and are all equally 'dangerous' to the uninitiated.  You can copy a disk with dd, cat, head, tail and a few even more obscure ones and they will all run at the same speed also, since they are all doing exactly the same thing: Copy a file.

---

### Post by TheFu on 2020-02-16
> **garyed said:**
> Thanks for all the advice,

I really don't want to have to do a fresh install & that is why I want to clone the drive. I just upgraded to Windows 10 on the drive I want to clone & I have two other versions of Ubuntu on that drive too. 
If I reformat the original drive after it is cloned will that change the uuid so it won't conflict with the new SSD?
Here's a gparted view of the drive I want to clone.

You can force a UUID to change.  Having 2 identical UUIDs connected to the same machine when storage is mounted will return to the old "whatever is found first" solution by the kernel/systemd. 
I think there is an easier way than this : [https://www.tecmint.com/change-uuid-of-partition-in-linux/](https://www.tecmint.com/change-uuid-of-partition-in-linux/)  
or
[https://unix.stackexchange.com/questions/12858/how-to-change-filesystem-uuid-2-same-uuid](https://unix.stackexchange.com/questions/12858/how-to-change-filesystem-uuid-2-same-uuid)

---

### Post by vidtek on 2020-02-17
> **garyed said:**
> Thanks for all the advice,

I really don't want to have to do a fresh install & that is why I want to clone the drive. I just upgraded to Windows 10 on the drive I want to clone & I have two other versions of Ubuntu on that drive too. 
If I reformat the original drive after it is cloned will that change the uuid so it won't conflict with the new SSD?
Here's a gparted view of the drive I want to clone.

Gary-

My understanding from your original post was that your needs were a one-off clone from HDD to SDD, not a complex daily/weekly routine.

Forget all the other ideas if that is the case and stick with Clonezilla.  If you really do want ongoing backups, then that is a different question altogether.

If you do want to change the UUID of the old drive that can be done in Windows with diskpart, there are linux alternatives as in the Fu's post.

FS-archiver will clone a saved image to a different size drive, it is in the Ubuntu repos, there is also a QT gui version to make life easier.

Best regards, Tony.

---

### Post by garyed on 2020-03-04
I finally got my 1tb SSD in today so I'm ready for the cloning but I'm not sure if I understand what cloning really does. Please let me know where I'm wrong.  I thought it was virtually a bit for bit copy of the drive where there was no need for any formatting or partitioning at all.  If the source drive was bootable then the cloned drive would boot up just like the source did if i switched them out. I posted a screenshot of my Gparted for the old drive & there is Windows, two versions of Ubuntu & a home partition so there's three different file systems, Fat32 ,NTFS & EXT4. I assumed that if the drive was really cloned that none of the would matter so please somebody let me know if i'm thinking correctly or I'm really in dreamland.  I'm wanting to just pop the cloned drive in & be up & running  
I also made a bootable flash drive with Clonezilla but I'm probably more comfortable with the command line than I am with Clonezilla. If I decide to use dd or ddrescue do you think it would work? 
What if I just did: ```
dd if=/dev/sda of=/dev/sdb
``` where sda=the old boot drive & sdb = the new SSD drive.

---

### Post by vidtek on 2020-03-05
> **garyed said:**
> I finally got my 1tb SSD in today so I'm ready for the cloning but I'm not sure if I understand what cloning really does. Please let me know where I'm wrong.  I thought it was virtually a bit for bit copy of the drive where there was no need for any formatting or partitioning at all.  If the source drive was bootable then the cloned drive would boot up just like the source did if i switched them out. I posted a screenshot of my Gparted for the old drive & there is Windows, two versions of Ubuntu & a home partition so there's three different file systems, Fat32 ,NTFS & EXT4. I assumed that if the drive was really cloned that none of the would matter so please somebody let me know if i'm thinking correctly or I'm really in dreamland.  I'm wanting to just pop the cloned drive in & be up & running  
I also made a bootable flash drive with Clonezilla but I'm probably more comfortable with the command line than I am with Clonezilla. If I decide to use dd or ddrescue do you think it would work? 
What if I just did: ```
dd if=/dev/sda of=/dev/sdb
``` where sda=the old boot drive & sdb = the new SSD drive.

Gary-  To get what you want to do with dd you will need to add parameters so it will copy all permissions and attributes too see the man page, very complex.

You just want a straight clone, an identical copy so I say again, use Clonezilla it is straightforward and always does the job.  Use other methods at your peril.

Tony.

EDIT: Backup vs cloning.  A clone is an exact byte for byte duplication of the original, a mirror image including all UUID's, permissions and attributes (and errors).  A backup is nothing remotely like that, just a copy of the data.

---

### Post by garyed on 2020-03-05
> **vidtek said:**
> Gary-  To get what you want to do with dd you will need to add parameters so it will copy all permissions and attributes too see the man page, very complex.

You just want a straight clone, an identical copy so I say again, use Clonezilla it is straightforward and always does the job.  Use other methods at your peril.

Tony.

EDIT: Backup vs cloning.  A clone is an exact byte for byte duplication of the original, a mirror image including all UUID's, permissions and attributes (and errors).  A backup is nothing remotely like that, just a copy of the data.

Well I got impatient after waiting a couple hours for any replies so I took a shot with dd so I hope I didn't mess things up. I used the dd command & went to bed & just got up so I'm getting ready to test things out.

---

### Post by vidtek on 2020-03-05
> **garyed said:**
> Well I got impatient after waiting a couple hours for any replies so I took a shot with dd so I hope I didn't mess things up. I used the dd command & went to bed & just got up so I'm getting ready to test things out.

I see from your location you're across the pond.
I hope it works out for you.  What was the command you used?

This is the one I would have used:  dd if=/dev/sda1 of=/dev/sdb1 bs=1024 conv=noerror,sync

Tony

---

### Post by garyed on 2020-03-05
I don't want to jinx myself but so far as I can tell everything has worked out fine. I just unplugged my original drive that I was using & plugged in my new 1tb WD Blue SSD & it booted up like normal without even messing with Grub. I can boot into Windows or Ubuntu using the typical Grub menu & everything appears to be transferred over perfectly. I'm going to go over the steps.
First thing is I had three HD's in my system to start out with & they were all the same 1TB Seagate Barracuda SATA drives so i had to figure out which one was the actual boot drive. I don't know if there was a better way but to be sure I disconnected two drives & booted up until I knew I had the right physical drive to clone. On the second try I found the boot drive. I left the other two drives disconnected & connected my new SSD internally so I'm all set up with four drives now when i decide to plug the other two back up.   

So now I just have the one original 1TB boot drive which has 7 partitions ( 1 - Fat32 EFI boot , 2 NTFS for Windows , 3 EXT4 for Linux, 1 Linux Swap )  along with my new SSD in the system ready to boot up. 
I boot up normally & use the terminal command part -l to find the correct disk & double check it by running gparted because I was still a little nervous since /dev/sdb was my boot drive instead of /dev/sda. 
Anyways I just run the dd command ```
 dd if=/dev/sdb of=/dev/sda bs=64k conv=noerror,sync status=progress    
``` 
I estimate it took about 2 hrs. to complete but all I did was plug my other two drives back up & disconnect my original boot drive & everything is running perfectly without any need to do anything. 
So evidently the dd command can work fine for cloning & no need to do anything assuming the target drive is as big as the source drive.
Side note: Before I started the cloning process I checked the drive sizes in Gparted & they showed exactly the same.  

Now what I'm trying to figure out is how to change the UUID on my original drive before I hook it back up. I'm a little confused because there are two separate UUID's for each partition, one UUID & the other PARTUUID . Do I need to change them both on each partition to be safe when hooking the old drive back up?

---

### Post by dragonfly41 on 2020-03-05
I'm looking at Gparted right now in my multi boot setup. If you launch Gparted and examine each partition, select Partition in menu bar the options include New UUID. Also right clicking on any Partition and selecting Information gives more .. information.

[P.S.] When setting up my own SSD recently I read that I needed to leave about 10% of space unallocated. Just a thought.

---

### Post by CelticWarrior on 2020-03-05
> **dragonfly41 said:**
> [P.S.] When setting up my own SSD recently I read that I needed to leave about 10% of space unallocated. Just a thought.

You don't. That's a suggestion from 10 years ago. You can handle SSDs just like HDDs.
The kind of "overprovisioning" achieved by leaving some unallocated space is already done at the factory (the SSDs have a slightly larger capacity than what's user accessible).

---

### Post by garyed on 2020-03-05
I'm wondering if I should start a separate thread on UUID's. Fstab shows two separate UUID's for each partition, one for UUID & one for PARTUUID. Gparted only shows the one UUID.  What doesn't make sense to me is if each partition has its own PARTUUID then why would the drive UUID be different for any of the partitions that are on the same drive. Which UUID does fstab use or does it use both? If I only change the UUID & not the PARTUUID will that keep fstab from getting confused or do I need to change both?

---

### Post by oldfred on 2020-03-05
PartUUID is also guid. Which is with gpt partitioning unique to every partition and is in the primary partition table and backup partition table.

I believe the best tools for dealing with gpt drives is gdisk.
GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html) & 
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


sudo blkid -c /dev/null -o list
Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid
exclude snaps
lsblk -af |grep -sv loop
df | egrep -v /dev/loop
sudo fdisk -l /dev/sd[a-z] # if no NVMe or MMC
sudo parted -l /dev/sd[a-z]

If you change UUID, you need to reinstall grub.

---

### Post by garyed on 2020-03-06
> **oldfred said:**
> PartUUID is also guid. Which is with gpt partitioning unique to every partition and is in the primary partition table and backup partition table.

I believe the best tools for dealing with gpt drives is gdisk.
GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html) & 
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


sudo blkid -c /dev/null -o list
Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid
exclude snaps
lsblk -af |grep -sv loop
df | egrep -v /dev/loop
sudo fdisk -l /dev/sd[a-z] # if no NVMe or MMC
sudo parted -l /dev/sd[a-z]

If you change UUID, you need to reinstall grub.

Thanks,
I've been looking into gdisk & it looks pretty simple to change the PARTUUID with it. I'm not sure if I need to change both the file system UUID & the partition PARTUUID for each partition to keep the two identical drives from getting mixed up but it sounds like a safe idea. I don't see how that would effect Grub as long as I don't mess with the actual boot drive with all the OS's on it.

---

### Post by garyed on 2020-03-06
For all practical purposes I think I'm going to mark this thread as solved. The cloning worked successfully & if I want to keep the original HD as is in the system too then I can just change the UUID's using tune2fs & gdisk to be sure there are no conflicts with which drive is recognized. I had to order a SATA power splitter to handle the fourth drive in the system & now I'm considering just leaving the old HD unhooked up & just keeping it for emergencies. Either way my experience has been as long as your target drive is as big as your source drive then the dd command works fine for a true clone. For me it was simpler than Clonezilla but everybody has there preferences. Thanks to everyone for all the help & input.

---

