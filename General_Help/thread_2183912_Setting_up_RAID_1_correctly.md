---
title: "Setting up RAID 1 correctly?"
date: 2013-10-26
forum: General Help
---

### Post by Jeffrey Martin on 2013-10-26
Hi,

I want to set up 2x 3TB WD drives in RAID 1 for redundancy. I'm using Ubuntu primarily but i also have to keep Win7 installed to use software such as Adobe CC that is not supported on Ubuntu.

My question is how do you correctly set up RAID 1 so that it can be used and accessed cross-platform, on both Win7 or Ubuntu. Reading suggests software RAID is the way to go, i've read about MDADM, some people also mention that ZFS is great for drive mirroring, although i don't fully understand the diffence between it and what MDADM does.

I want to make sure i set this up right so the array doesn't get corrupted when using multiple OS, if that is a factor at all.

My Mobo (Asus Z-87-PRO) has Intel Matrix RAID, but from what i can tell, it's best to disregard this and set up the RAID array using purely software. Please advise.

Thanks

---

### Post by Jeffrey Martin on 2013-10-26
BTW both Windows and Ubuntu are run off a 256GB SSD drive so the 3TB WD drives are purely intended for data storage.

---

### Post by SaturnusDJ on 2013-10-27
[http://askubuntu.com/questions/59019/how-can-i-access-an-ubuntu-raid-device-from-windows](http://askubuntu.com/questions/59019/how-can-i-access-an-ubuntu-raid-device-from-windows)
So no, mdadm is not the way to go here. For ZFS you can say almost the same thing. Maybe [http://code.google.com/p/zfs-win/](http://code.google.com/p/zfs-win/) works for read only access from Windows, or you can build a VM to host the ZFS and again share this over the network.

The only way that might work is to use the RAID capabilities of your motherboard and create a filesystem that's recognized and writable by both operating systems, like FAT32 I guess.

Concerning data safety it's not a very good idea to use RAID via the motherboard. If you lose the motherboard you might need the exact same model (or same chipset design) to access your data...in the best case.

I suggest you try Virtualbox on Ubuntu, and create a Windows 7 guest.
Other alternative: Wine. But that's a hell too most times.

---

### Post by Jeffrey Martin on 2013-11-01
> **SaturnusDJ said:**
> [http://askubuntu.com/questions/59019/how-can-i-access-an-ubuntu-raid-device-from-windows](http://askubuntu.com/questions/59019/how-can-i-access-an-ubuntu-raid-device-from-windows)
So no, mdadm is not the way to go here. For ZFS you can say almost the same thing. Maybe [http://code.google.com/p/zfs-win/](http://code.google.com/p/zfs-win/) works for read only access from Windows, or you can build a VM to host the ZFS and again share this over the network.

The only way that might work is to use the RAID capabilities of your motherboard and create a filesystem that's recognized and writable by both operating systems, like FAT32 I guess.

Concerning data safety it's not a very good idea to use RAID via the motherboard. If you lose the motherboard you might need the exact same model (or same chipset design) to access your data...in the best case.

I suggest you try Virtualbox on Ubuntu, and create a Windows 7 guest.
Other alternative: Wine. But that's a hell too most times.

Thanks for your reply Saturnus. I have spent an insane amount of time researching all the options, and in short it's similar to what you suggest. 
Virtualbox is not an option, i found one person that did this and said there were risks with data loss.

I have reconsidered how i want to use my system. I will be in Ubuntu/linux the majority of the time. In fact, the ONLY reason i'm dual booting win7 is because i need Adobe CC for my job, and afaik there is no clean solution to run this on linux, i have a performance PC so i want to maximize performance with Adobe. 

In any case, i have decided to do software-RAID in MDADM on linux (RAID1) --  i already have it running to test -- and will manually transfer projects to my windows partition when i need to work on something in Adobe (It's safe to mount Windows partition and write files to it right?)

Some questions:
- If i ever reinstall Ubuntu/Win7/everything or somehow my OS drive fails and i need to start clean, can i re-assemble the raid on any linux dist / ubuntu with MDADM without any hassle or do i need to store some specific (meta)data related to my current array?

- I want to add a hotswap bay to the front of my case, i will keep 1 drive mounted internally and 1 in the bay. Can i just swap out that disk periodically and will it automatically rebuild? 

- What happens if i swap the disks, then one week later swap them again (you put back a disk with old data basically), what happens?

- Can you just add one of the disks from the array to a new linux box and use it to create a brand new array with it?

Thanks!

---

### Post by SaturnusDJ on 2013-11-02
As long as you have the raid members, you're good to go. Personally I backup all raid information to make work in case of a major crash easier.

The hot swapping I don't understand. You want to take one raid 1 member out sometimes? I think that's not the point of raid. It's also not good for HDD health because the other disk will be read/writen completely when you plug the hot one back. (Unless you use a bitmap, but even then you're not using raid how it's supposed to be used.) Maybe you can use LVM for that, I don't know.

Yes, using one raid1 member to create a new raid1 array must be easy and possible. Yet a bit risky cause that base member will be read completely. You would do a re-create with exact the same parameters as the previous array and of course the --assume-clean flag. But this is something you would do one time, in a case that it's really necessary, not daily or weekly...


Remember this: RAID is for uptime and/or speed. Not for safety, not for flexibility.

---

### Post by Jeffrey Martin on 2013-11-02
> **SaturnusDJ said:**
> As long as you have the raid members, you're good to go. Personally I backup all raid information to make work in case of a major crash easier.

The hot swapping I don't understand. You want to take one raid 1 member out sometimes? I think that's not the point of raid. It's also not good for HDD health because the other disk will be read/writen completely when you plug the hot one back. (Unless you use a bitmap, but even then you're not using raid how it's supposed to be used.) Maybe you can use LVM for that, I don't know.

Yes, using one raid1 member to create a new raid1 array must be easy and possible. Yet a bit risky cause that base member will be read completely. You would do a re-create with exact the same parameters as the previous array and of course the --assume-clean flag. But this is something you would do one time, in a case that it's really necessary, not daily or weekly...


Remember this: RAID is for uptime and/or speed. Not for safety, not for flexibility.

With backup "All raid information" you mean backing up the data itself correct? You don't have to backup any mdadm specific data, yes?

So whenever the array is rebuilding/syncing you increase chance of disk failure?

My intention is to backup my data to the cloud, aswell as keeping one physical backup, that's what i want to use the hot-swapping for.

So if i want to do this, i'd have to add a 3nd disk which would be the one being swapped. Then you have two disks which are always present in the array and one which is being swapped out (& stored somewhere). Or will swapping a 3nd disk also put the whole array at risk? -- Will it read/write (rebuild) only that disk or the entire array?

Could you comment on what happens in that situation with swapping (swapping a disk which has been swapped before / old data), it will always rebuild it with the newest data on the already present disk?

Thank you so much.

---

### Post by SaturnusDJ on 2013-11-02
If you have two mdadm raid1 members you just plug them in any system and run the mdadm assemble command and you'll have access. So you don't need to backup metadata. I do backup the mdadm detail and examine outputs and some disk specific information for situations that you might think: "D*mn I should have saved that info." But in normal cases you don't need to. I also backup the most important data to a single hot swappable disk, because (at least at consumer level) RAID isn't really as safe as it looks.

Yes if one disks needs to be rebuilded, the data of the other disk(s) is needed. Without mdadm bitmap enabled the whole disk will be read and the other whole disk will be written I think. This is why so many RAID5 array's fail when just one member dies: Most times the members are purchased and put to use at the same time. If one disk starts to fail because of age, and a new one is put in place, chances are great that another disk will fail because it's of the same age and it's get's a big load of read/write to process all of a sudden.
With bitmap enabled only the changed blocks will be synced.

If you mean a 3rd disk as member of the array, that's just the same. It doesn't help. You can't have plug and play with mdadm without many reads/writes unless using the bitmap (which gives a little performance drop, but makes you oh so happy when your array comes up clean after power failure), but even then you don't want mdadm to do this. Mdadm is not on filesystem level. If you delete one file you'll need to run the 3rd disk as different array (maybe that will give trouble if it's on the same system where his brother members of the real array are already running) then get the file back and save it to the real array, then add the 3rd as member and hope the other 2 won't be overwritten and all that kind of stuff.

If you mean a 3rd disk that will be standalone, that will work. It's like my backup disk. I backup once per month, at filesystem level. Currently I'm using a script that's not checking for changes so I'm wasting a lot of read/writes, but still 50 times less then the whole array size. I'll look into rsync soon. That tool can look if the file is changed and only then copies it. I hope it has the option of keeping the existing file at the backup disk too, so you would create I kind of archive like ZFS does on the fly.

Maybe you should think about a NAS. Accessible from any system at SMB or NFS level.

---

### Post by Jeffrey Martin on 2013-11-02
> **SaturnusDJ said:**
> If you have two mdadm raid1 members you just plug them in any system and run the mdadm assemble command and you'll have access. So you don't need to backup metadata. I do backup the mdadm detail and examine outputs and some disk specific information for situations that you might think: "D*mn I should have saved that info." But in normal cases you don't need to. I also backup the most important data to a single hot swappable disk, because (at least at consumer level) RAID isn't really as safe as it looks.

Yes if one disks needs to be rebuilded, the data of the other disk(s) is needed. Without mdadm bitmap enabled the whole disk will be read and the other whole disk will be written I think. This is why so many RAID5 array's fail when just one member dies: Most times the members are purchased and put to use at the same time. If one disk starts to fail because of age, and a new one is put in place, chances are great that another disk will fail because it's of the same age and it's get's a big load of read/write to process all of a sudden.
With bitmap enabled only the changed blocks will be synced.

If you mean a 3rd disk as member of the array, that's just the same. It doesn't help. You can't have plug and play with mdadm without many reads/writes unless using the bitmap (which gives a little performance drop, but makes you oh so happy when your array comes up clean after power failure), but even then you don't want mdadm to do this. Mdadm is not on filesystem level. If you delete one file you'll need to run the 3rd disk as different array (maybe that will give trouble if it's on the same system where his brother members of the real array are already running) then get the file back and save it to the real array, then add the 3rd as member and hope the other 2 won't be overwritten and all that kind of stuff.

If you mean a 3rd disk that will be standalone, that will work. It's like my backup disk. I backup once per month, at filesystem level. Currently I'm using a script that's not checking for changes so I'm wasting a lot of read/writes, but still 50 times less then the whole array size. I'll look into rsync soon. That tool can look if the file is changed and only then copies it. I hope it has the option of keeping the existing file at the backup disk too, so you would create I kind of archive like ZFS does on the fly.

Maybe you should think about a NAS. Accessible from any system at SMB or NFS level.

Thank you so much again Saturnus.

I'm aware of the pitfalls of RAID in regards to disk failure and data safety. I use my setup for redundancy first and foremost, the second tier of "defense" would be a backup to the cloud.

Like you, i also want to keep a swappable disk for data, and store it externally, in case of theft of my pc or something happening to the cloud backup. Now, i was thinking it would make most sense to just add this disk to the array and have it automatically mirror the data vs. manually writing to an external disk periodically (extra work & you might oversee/or miss some data). Your thoughts?

Would you recommend to enable bitmapping then? If i understand it correct it's only useful when your rebuilding the array with a drive that has a few changed blocks. If you insert a clean drive to rebuild then wouldn't it read/write the whole disk anyway?

I'm aware of NAS, but it's not something i want to do now. I think i can make this work fine first.

Will it be useful for me to store the mdadm detail and outputs you referred to? 

Thanks again!

---

### Post by SaturnusDJ on 2013-11-02
What is 'the cloud' in your case?

If you really want to do it the mdadm way, yes, then go for a bitmap.
That's right, it's only usefull when doing a rebuild, which is basically what you say you want to do every time.

I still recommend not going this way. It's silly because it's kind of using mdadm for something it isn't meant to be used while there are tools that do the job better.

Yes it's useful for situations when the metadata is missing. Also save the initial array creation command and mdadm version. The chance you will need this stuff is like 0,000000001% but I learned the hard way not to take chances on data. ^^

---

### Post by Jeffrey Martin on 2013-11-02
I have yet to test/read up but i was planning on uploading backups to something like AWS or Google (mass storage)

But MDADM is fine right? It's just the hotswap you are not recommending me to do, i understand your point. I will think about how i can best design the structure of my files, would be interesting to know which tools you recommend to make an extra backup to a standalone.

Would you be able to explain how to get that data? -- And with initial command you mean just the "[COLOR=#000000][FONT=Ubuntu Mono]mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc"[/FONT][/COLOR]?

Also some interesting information, when i creat the array as /dev/md0 it becomes /dev/md127 on reboot. Then i renamed my array with a new label "Earth" and it can be managed with both /dev/md127 and /dev/md/Earth. Any problems here?

---

### Post by SaturnusDJ on 2013-11-02
Okay. Sounds good.

Yeah I recommend not using mdadm for member hotswapping because it's really not made to use that way.
Use rsync.

Yes that could be your initial array creation command. Metadata I save is the output of:
```

mdadm --detail /dev/md0
mdadm --examine /dev/sd[b-d]1
blkid -o list
ls -l /dev/disk/by-uuid

```
With this I know exactly which physical disk is which array member number. Because the /dev/sd... listing may change.

Most times the change from 0 to 127 is because the definition isn't in /etc/mdadm/mdadm.conf.
You can use
```

mdadm --detail --scan >> /etc/mdadm/mdadm.conf

```
to fix this.

---

### Post by Jeffrey Martin on 2013-11-03
> **SaturnusDJ said:**
> Okay. Sounds good.

Yeah I recommend not using mdadm for member hotswapping because it's really not made to use that way.
Use rsync.

Yes that could be your initial array creation command. Metadata I save is the output of:
```

mdadm --detail /dev/md0
mdadm --examine /dev/sd[b-d]1
blkid -o list
ls -l /dev/disk/by-uuid

```
With this I know exactly which physical disk is which array member number. Because the /dev/sd... listing may change.

Most times the change from 0 to 127 is because the definition isn't in /etc/mdadm/mdadm.conf.
You can use
```

mdadm --detail --scan >> /etc/mdadm/mdadm.conf

```
to fix this.

Thanks!
OK! I've spent more time on my setup today and i'm back with a few more questions.

I experimented with manually failing a drive and re-adding it, it starts re-building the whole array. Will bitmap alleviate this? (Since no data was changed)

I notice on array creation you can set chunk-size and bitmap chunk size (?), what is advisable?

Before i make my final array how do i completely dismantle the array and clean all the metadata/raid information from the drives (before doing a full ubuntu reinstall) --- I did:
umount /dev/md/mars
mdadm -S /dev/md/mars
mdadm --zero-superblock /dev/sdb /dev/sbc

It worked and i re-assembled the array using --assume-clean (to see if it would not rebuild again, it didn't)

But are these the correct methods?

I also used EXT4 as filesystem and as single partition, is this the best/most efficient one to use for linux?

Then i ran into another problem, if you check the attachment.
Gparted identifies the array as /dev/md127  or /dev/md127p1 even though i've created it as /dev/md/mars and also did the steps you described to add it to the conf.  

You can see it also throws up an error log.

---

### Post by XBNCPRk on 2013-11-03
May I ask, if you have two devices in raid1 and (from what I gathered) want to have a third to swap in and out to keep a synced spare... why not simply use raid5 and double your storage space?

Also, if you want instead to use mdadm and an ext2/3 file system, there are installables for windows that will allow you to read/write to them the exact same as you would for any other system. [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by SaturnusDJ on 2013-11-04
> **Jeffrey Martin said:**
> Thanks!
OK! I've spent more time on my setup today and i'm back with a few more questions.

I experimented with manually failing a drive and re-adding it, it starts re-building the whole array. Will bitmap alleviate this? (Since no data was changed)

Yes. But then use the '--re-add' flag and not the '---add' flag.
> **Jeffrey Martin said:**
> 
I notice on array creation you can set chunk-size and bitmap chunk size (?), what is advisable?

Bitmap chunk size I don't know much about. I suggest not changing the default value.

For chunk size: [https://raid.wiki.kernel.org/index.php/RAID_setup#Chunk_sizes](https://raid.wiki.kernel.org/index.php/RAID_setup#Chunk_sizes)

"For optimal performance, you should experiment with the chunk-size, as well as with the block-size of the filesystem you put on the array." That's mostly true. After I found the best array chunk size, the filesystem automatically choose the best values, according to the calculation of that page (with 4k block size). I verified this with the dumpe2fs command.

If you want to totally max out, also look at the blockdevice readahead for array members, stripe cache size for the array, blockdevice readahead for the array and schedulers for the filesystem.

> **Jeffrey Martin said:**
> 
Before i make my final array how do i completely dismantle the array and clean all the metadata/raid information from the drives (before doing a full ubuntu reinstall) --- I did:
umount /dev/md/mars
mdadm -S /dev/md/mars
mdadm --zero-superblock /dev/sdb /dev/sbc

It worked and i re-assembled the array using --assume-clean (to see if it would not rebuild again, it didn't)

But are these the correct methods?

Correct!
> **Jeffrey Martin said:**
> 
I also used EXT4 as filesystem and as single partition, is this the best/most efficient one to use for linux?

Then i ran into another problem, if you check the attachment.
Gparted identifies the array as /dev/md127  or /dev/md127p1 even though i've created it as /dev/md/mars and also did the steps you described to add it to the conf.  

You can see it also throws up an error log.
I've stopped using gparted. I remember similar results. The best is to use parted.

The results might be the same. If they are, do this:
```

update-initram-fs -u

```
That one actually sends the changes of mdadm.conf to the initram.

---

### Post by SaturnusDJ on 2013-11-04
> **XBNCPRk said:**
> May I ask, if you have two devices in raid1 and (from what I gathered) want to have a third to swap in and out to keep a synced spare... why not simply use raid5 and double your storage space?

Because he wants to have some sort of backup. I still advice strongly against this method.

> **XBNCPRk said:**
> 
Also, if you want instead to use mdadm and an ext2/3 file system, there are installables for windows that will allow you to read/write to them the exact same as you would for any other system. [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Access from windows to mdadm array's is not possible. Now I know you can omit the raid layer when having a raid 1 member...(and I admit I did that sometimes in the past), but you should not do that cause things with the metadata might go wrong, and **will** go wrong if you are writing to the disk instead of doing read-only. The only time you should omit the raid layer is if you are trying to recover and mdadm somehow refuses to give access.

---

### Post by Jeffrey Martin on 2013-11-04
OK, tested everything you mentioned, works fine, thanks again!

The only thing that's still not working is the gparted "bug"/error. I've complety deleted and remade the array using various configurations/names multiple times but it's still throwing up errors across the board.

Using:
mdadm --create /dev/md/Mars --assume-clean --level=1 --bitmap=internal --name=Mars --raid-devices=2 /dev/sd[bc]

Output:
Gparted gives /dev/md127p1 with the error message as in screenshot (previous post)
fdisk -l -u gives: Disk /dev/md127 doesn't contain a valid partition table

It's still using md127 after i've set the .conf and done the initramfs update! Also note here that it's saying no valid partition table while i've done mkfs.ext4 to the raid device.

Some questions:
Before creating the array should i first mkfs.ext4 the individual drives, then create the array and mkfs.ext4 the raid device? -- I used partitioned drives in my first experiments, this time the raid device is partitioned and the individual drives /sd[bc] show as "unallocated" in gparted (no partition)
If you could advise what the correct process would be

I just want to label my drives so they are labeled in the dock, i've done "e2label /dev/md/Mars Mars" (just example)
But my question is if there is any point in naming the raid device itself on creation, or should i just use default /dev/md0 and then e2label it?

---

### Post by XBNCPRk on 2013-11-04
> **SaturnusDJ said:**
> Because he wants to have some sort of backup. I still advice strongly against this method.


Access from windows to mdadm array's is not possible. Now I know you can omit the raid layer when having a raid 1 member...(and I admit I did that sometimes in the past), but you should not do that cause things with the metadata might go wrong, and **will** go wrong if you are writing to the disk instead of doing read-only. The only time you should omit the raid layer is if you are trying to recover and mdadm somehow refuses to give access.


I see what you mean about accessing one half the array... I neglected to remember that it would access only the file system, not the array as a whole. 

I dont understand what you mean by saying 1/2 of an array constitutes a backup though, and that raid5 doesnt. I consider a backup to be against hardware failure, not against user error. No level of RAID will guard against a user doing something incorrect, no more so than a filing cabinet will keep you from lighting your files on fire.

If its user error he wishes to guard against, then keeping a stand alone spare drive and syncing the files with rsync (or some other backup utility) is a far better choice, as it would provide access to an archived copy rather than having to resync the array to access a mistakenly deleted file, or mount the spare as a stand alone degraded array, or however else he would wish to do it.

---

### Post by Jeffrey Martin on 2013-11-04
Would like to hear Saturnus' thoughts on my questions, but to reply: i am definately not guarding for user error as i said, it's firstly hardware failure, and the extra backup is just to be absolutely sure. The RAID could fail, the backup could be stolen in burglary or fire, something could happen with the cloud backup, you just don't know. So i want to keep multiple backups, the RAID is just first line of defense but i want to make sure it's running perfectly.

---

### Post by SaturnusDJ on 2013-11-05
> **Jeffrey Martin said:**
> OK, tested everything you mentioned, works fine, thanks again!

The only thing that's still not working is the gparted "bug"/error. I've complety deleted and remade the array using various configurations/names multiple times but it's still throwing up errors across the board.

Using:
mdadm --create /dev/md/Mars --assume-clean --level=1 --bitmap=internal --name=Mars --raid-devices=2 /dev/sd[bc]

Output:
Gparted gives /dev/md127p1 with the error message as in screenshot (previous post)
fdisk -l -u gives: Disk /dev/md127 doesn't contain a valid partition table

It's still using md127 after i've set the .conf and done the initramfs update! Also note here that it's saying no valid partition table while i've done mkfs.ext4 to the raid device.

Some questions:
Before creating the array should i first mkfs.ext4 the individual drives, then create the array and mkfs.ext4 the raid device? -- I used partitioned drives in my first experiments, this time the raid device is partitioned and the individual drives /sd[bc] show as "unallocated" in gparted (no partition)
If you could advise what the correct process would be

I just want to label my drives so they are labeled in the dock, i've done "e2label /dev/md/Mars Mars" (just example)
But my question is if there is any point in naming the raid device itself on creation, or should i just use default /dev/md0 and then e2label it?
Partition the members so that they are almost the max hdd size (unless you explicitly want smaller members). No max size because: [http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473](http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473)
In fact I've cut out 2GB at the beginning and the end of all members for debugging and whatever the future may bring, but 100MB would already be enough.
No filesystem on the members. Mdadm will override this anyways.
No partition on the array. Better split this at member level, if necessary.
Filesystem on the array.

Maybe that's why gparted is having problems, there won't be a partition on the array. My gparted doesn't even see the array. ;)

Labeling might be useful if you're running tens of arrays. I've never used it. I assume the choice you have there is just flexibility and nothing else.


> **XBNCPRk said:**
> I see what you mean about accessing one half the array... I neglected to remember that it would access only the file system, not the array as a whole. 

I dont understand what you mean by saying 1/2 of an array constitutes a backup though, and that raid5 doesnt. I consider a backup to be against hardware failure, not against user error. No level of RAID will guard against a user doing something incorrect, no more so than a filing cabinet will keep you from lighting your files on fire.

If its user error he wishes to guard against, then keeping a stand alone spare drive and syncing the files with rsync (or some other backup utility) is a far better choice, as it would provide access to an archived copy rather than having to resync the array to access a mistakenly deleted file, or mount the spare as a stand alone degraded array, or however else he would wish to do it.

OK I went a bit in overdraw mode.

Maybe it's safe as in: you won't damage the raid layer, the array will still work...here by assuming the mount tools and any other software don't touch the raid layer.
One thing is sure: The event count is not updated. If you do change data, and not manually specify the other members should use that drive as source (initialize the changed drive as array and add the others), the data will be overwritten.

Agree on the rest. That's what I've pointed out (or tried to).

---

### Post by Jeffrey Martin on 2013-11-15
> **SaturnusDJ said:**
> Partition the members so that they are almost the max hdd size (unless you explicitly want smaller members). No max size because: [http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473](http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473)
In fact I've cut out 2GB at the beginning and the end of all members for debugging and whatever the future may bring, but 100MB would already be enough.
No filesystem on the members. Mdadm will override this anyways.
No partition on the array. Better split this at member level, if necessary.
Filesystem on the array.

Maybe that's why gparted is having problems, there won't be a partition on the array. My gparted doesn't even see the array. ;)

Labeling might be useful if you're running tens of arrays. I've never used it. I assume the choice you have there is just flexibility and nothing else.


Sorry for my late reply but i spent alot of time testing and finalizing.

I thought i was ready to make my final setup but still a few problems.

> **SaturnusDJ said:**
> No partition on the array. Better split this at member level, if necessary."
Necessary? You have to make atleast one partition right?

If i understand correctly:
- I should make an unformatted partition of same size to each of the members in the array (I will follow your example and keep 2GB at beginning and end).
- Then go to create the array, and then add a EXT4 filesystem to the array.


Now my question is, in order to create the partitions you need a partition table as far as i understand. On my primary drive (OS) i've set up as GPT, i assume i should do the same here, and first setup both member drives as GPT, then add an unformatted partition to each and continue as described above.

Also, once the members are partitioned, i should be assembling the array with /dev/sdb***1*** and /dev/sdc***1*** -- instead of plain /dev/sd[b c] -- If i'm right.


Another thing is, i wasn't paying attention during my last test install and accidentally Windows created the EFI boot partition on one of my RAID members, now everytime i assemble the test array MDADM reports : > "Note: this array has metadata at the start and may not be suitable as a boot device. If you plan to store '/boot' on this device please ensure that your boot-loader understands md/v1.x metadata. or use --metadata=0.90"


Any point to zero both drives before making my final array, or somehow wipe the metadata, if there is any that is.. I'm just doing quick formats between test setups now, is it enough?

---

### Post by SaturnusDJ on 2013-11-15
You understand correctly.

Yes if they are >2TB, GPT is the best choice.

Correct. A number behind a device (normally) means it's a partition.

I think that error is normal. Usefull if not done already, yes: [http://ubuntuforums.org/showthread.php?t=2121244](http://ubuntuforums.org/showthread.php?t=2121244)

---

### Post by Jeffrey Martin on 2013-11-16
> **SaturnusDJ said:**
> You understand correctly.

Yes if they are >2TB, GPT is the best choice.

Correct. A number behind a device (normally) means it's a partition.

I think that error is normal. Usefull if not done already, yes: [http://ubuntuforums.org/showthread.php?t=2121244](http://ubuntuforums.org/showthread.php?t=2121244)

I understand that it means it's a partition, but it was more a question, as i was/am unsure if that would be the correct way to assemble: /dev/sdb1 rather than /dev/sdb -- You are basically creating an array with the partitions rather than the drives here, thoughts?


I've studied the post you referenced and i'm running "badblocks -v -w" on both drives now. Do i still need to "zero" it afterwards, or is this command already doing that (as far as i understand from studying that it seems to be...).

---

### Post by SaturnusDJ on 2013-11-17
Yes.

If the test ends with the 0x00 pattern, everything is zero. But it doesn't matter because when you create a RAID parity array, mdadm will do a initial resync to set the correct ones and zeros based on the xor system. As long as you don't skip this initial resync you're good to go. If you do skip this, data corruption may occur I've read.

---

