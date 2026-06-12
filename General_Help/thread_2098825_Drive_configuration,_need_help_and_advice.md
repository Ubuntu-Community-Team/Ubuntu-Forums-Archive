---
title: "Drive configuration, need help and advice"
date: 2012-12-27
forum: General Help
---

### Post by nainsurvolte on 2012-12-27
I posted this in the Installation section of the forum, but it may not be at the right place. So I am trying this one.

> Good day,

I am in the process of beefing up my server in terms of capacity which is based on Ubuntu but will also be my media/home server.

My requirements are the following.
1) Have more than 1TB for TV recordings for Mythtv
2) Have about 1TB, redundant for family Photo & Video and the music library.
3) The rest would go to TV shows I recorded and compressed as well as my movie library that I digitized.

My problem is that I have 4x2TB ( 2x2TB WD EARS + 2x2TB WD EARX) .  Without considering the fact that I have 4 physical drives, I was  considering having 2x1TB for the Req. 2, and have 6TB for the rest  (MythTV, Series and Films).

That would mean, from my limited knowledge of Ubuntu (Linux) that I would need to split 2 drive in 2 and group the rest together
ex:

sda [ sda1 1TB ][ sda2 1TB ]
sdb [ sdb1 1TB ][ sdb2 1TB ]
sdc [            sdc 2TB          ]
sdd [            sdd 2TB          ]

[ sda1 1TB ] + [ sdb1 1TB ] in Raid 1
[ sda2 1TB ] + [ sdb2 1TB ] + [            sdc 2TB          ] + [            sdd 2TB          ]

Is this solution pure fiction or possible? And even if it is possible, is there a better way? I am open to suggestions...

Thanks

---

### Post by dabl on 2012-12-27
Although it is still technically "experimental", I have found the BTRFS filesystem very stable for 2 years, on a pair of WD1002FAEX 1T drives.  I installed it with defaults (data striped, metadata mirrored) as shown in the [**[color=green]wiki[/color]**](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices) for multiple drive installation.  That would appear to be a simpler approach for your situation.

If you installed a BTRFS filesystem on all four of your hard drives, then you can mount that filesystem on /mnt/DATA, and the OS will see it as a single directory.  So, you can then make sub-directories as you need:

/mnt/DATA/VIDEOS
/mnt/DATA/IMAGES
/mnt/DATA/DOCS
/mnt/DATA/TV

etc.  And you don't have to be concerned about capacity limitations of individual hard drives.

---

### Post by nainsurvolte on 2012-12-28
Thanks for this interesting suggestion. I read the wiki and I think I understand most of the idea.

If I may try to summarize the advantage of your suggestion, I would end up in a type of JOBD or LVM configuration but, with the filesystem information being mirrored over the different drives. The end result being that if a drive fails, the information on the other drives is still accessible, right?

Another question, knowing that Btrfs and Zfs are being "developed" by Oracle and that in the Wiki there is a few questions comparing them, does Btrfs requires lots of Ram to work the way you suggested?

My problem is that I once looked at Zfs for a solution, but I turned away because of the amount of Ram I have or even that I can put on my motherboard which is not enough to manage Zfs array.

Thanks,

---

### Post by dabl on 2012-12-28
No, btrfs does not use an unusual amount of memory.  I have a conky that shows the top 5 running processes by memory and CPU usage, and the only time I see a btrfs process is when I'm doing some large file-management task on that filesystem.  Otherwise it is far below the Xorg manager and browsers and so forth.

And while Oracle is a listed joint developer, I'm not sure of the extent of their involvement -- it is a GPL / open source project with a fairly broad development team.  I think it was begun by Oracle folks.

My experience was using brand new un-partitioned drives, so if you wanted to replicate my experience, you would use dd or GParted to delete the partition tables on all four of your drives.  Then, with the drives connected and running so that they show up with fdisk, you would use this command to make the filesystem:

```
sudo mkfs.btrfs /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

(assuming the drive IDs are correct for your system)

Then the mount line in /etc/fstab has to name the drives.  Mine is:

```
UUID=c112ed57-0e33-4d4b-82c9-5c55932c529d     /mnt/DATA            btrfs        device=/dev/sdd,device=/dev/sde,compress,space_cache,inode_cache   0    0
```

Figuring out which UUID is the one to use was a little tricky, as I recall, because your drives will have individual IDs, and then the filesystem itself has a UUID, and that's the one you need to use.  When I issue, as root: 

```
blkid
```

I see this:

```
/dev/sda2: LABEL="SDA2" UUID="8cfe2acc-7572-4b45-b25f-ed021bb1d78b" TYPE="ext4" 
/dev/sdb1: LABEL="revodata" UUID="ec21f5b3-7fd4-4f4b-af8d-cf787b147ae8" TYPE="ext4" 
/dev/sdc1: UUID="ac7da829-aebb-46f0-806c-04a4d81a945a" TYPE="ext2" 
/dev/sda1: UUID="bea3a748-3411-4024-acd0-39f3882ddaf9" TYPE="ext4" 
/dev/sdd: UUID="c112ed57-0e33-4d4b-82c9-5c55932c529d" UUID_SUB="549b488c-bad8-408c-9544-9c585411bef2" TYPE="btrfs" 
/dev/sde: UUID="c112ed57-0e33-4d4b-82c9-5c55932c529d" UUID_SUB="e07bcc5b-1f36-4015-a648-b65aca6bf357" TYPE="btrfs" 
/dev/sdc2: UUID="0d939b7d-48f1-47dd-aebe-77e7bd8c3503" TYPE="swap"
```

But when I issue (as root, you would need "sudo" with *buntu):


```
blkid -c /dev/null -o list
``` I see this:

```
device                         fs_type     label        mount point                        UUID
--------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                      ext4                     /                                  bea3a748-3411-4024-acd0-39f3882ddaf9
/dev/sda2                      ext4        SDA2         /mnt/SDA2                          8cfe2acc-7572-4b45-b25f-ed021bb1d78b
/dev/sdb1                      ext4        revodata     /mnt/REVODATA                      ec21f5b3-7fd4-4f4b-af8d-cf787b147ae8
/dev/sdc1                      ext2                     /boot                              ac7da829-aebb-46f0-806c-04a4d81a945a
/dev/sdc2                      swap                     <swap>                             0d939b7d-48f1-47dd-aebe-77e7bd8c3503
/dev/sdd                       btrfs                    (in use)                           c112ed57-0e33-4d4b-82c9-5c55932c529d
/dev/sde                       btrfs                    (in use)                           c112ed57-0e33-4d4b-82c9-5c55932c529d

``` 


I have not experienced a drive failure, so I'm not the expert on exactly what the procedure is to recover with a replacement drive, but I believe it is the case that the mirrored metadata has the necessary information to rebuild the filesystem across the replacment drive.  Or so it says in the wiki ....

---

### Post by nainsurvolte on 2012-12-28
Thanks, definitely a contender.

As for the way to proceed, I will need to create the array 2 by 2. Start with 2, then add 2 more. Considering my situation, I noticed in the wiki that you can add new drives and then synchronize the metadata on the new drives.

The reason for that, for my thread and to request some redundancy for my drives is that I screwed up my JBOD configuration trying to bring it from my NAS to my Linux machine. Bottom line is that what ever I manage to get out of the old drives will sit on the 2 new ones until I reconfigure the old ones copy back and then add the new ones to the group. Hoping to get as much as I can from the current scan which will probably be the last one. [-o<

Maybe a last question, have you seen big differences in management of large files ? For reference, my movies goes from 500MB to almost 2GB, and MythTV recordings can go up to 15GB sometimes. I have seen that Btrfs is really good for small file size...

---

### Post by dabl on 2012-12-28
There is only one type of large file that is a problem on BTRFS, and that is a VM. The problem is not storing the VM, the problem is running it. Last time I tried running a VM on the BTRFS filesystem, it was painfully slow, and it turned out that was a known performance problem due to the design of btrfs.  That was a year or more ago, and since it was no big deal to run my VMs on SSDs, I never have checked to see whether that situation has gotten better.

As far as big videos and things like that, there is no problem at all.  I have about 750GB of data on my BTRFS filesystem, including video files up to 16GB that I made from VHS tapes, and there's no problem working with them.  I also have some fairly large audacity music projects, and no problems at all with any of it.

---

### Post by nainsurvolte on 2013-01-03
I made a few partition using btrfs. So far so good, works well or at  least I see no differences for the moment. It also seem to use much of  the partition space (or maybe it does not show the space use by metadata like standard partitioning, but ext4 shaved 21 GB out of 2 TB from the start).

I have only one issue which is giving me headache for now ](*,)

Every  time my system restart, the name of the devices change as well, even if  I don`t swap cable or add any devices. Therefore, the line in fstab  saying

```
UUID=0286c1cb-735e-4f5f-9bf1-e0ba87725bf0    /media/master-data    btrfs    device=/dev/sdf,device=/dev/sdg,compress,space_cache,inode_cache    0    0
```This portion [...] device=/dev/sdf,device=/dev/sdg ... is of no use and drive does not mount even with UUID for the array. I then have to go in fstab, check with parted -l the 
new device name, edit fstab add remount everything.

I tried to substitute the /dev/sd_ with the UUID of the drives and it does not work, could it accept labels?

Do you have those issues too or what do you do to prevent that from happening... 

Thanks.

---

### Post by nainsurvolte on 2013-01-03
On another topic, what are your thought about the *-autodefrag* option?

---

### Post by nainsurvolte on 2013-01-04
Regarding my mounting issue, I got the solution described in this other thread of mine...

[http://ubuntuforums.org/showthread.php?t=2100614](http://ubuntuforums.org/showthread.php?t=2100614)

Just need to replace the /dev/sd... by /dev/disk/(by-id). Maybe it works for other by-* but funny enough, replacing /dev/sd... by the UUID does not work.

I am still interested by the autodefrag option that can be put in the mounting line ;).

---

### Post by dabl on 2013-01-08
Sorry, I've been off the forum for a few days.

I had not heard of the autodefragment option.  As I recall (I probably should check ...) the btrfs defrag utility actually only defragments the metadata, not the on-disk files.  It probably doesn't matter much for your new filesystems -- these old DOS and Windows habits are far less helpful on the new Linux filesystems than they were on the older drives and MS filesystems.

I do remember having the "shifting device ID" issue early on.  I actually run Debian Sid these days, and that issue went away about a year or more ago.  As I recall it was not directly related to BTRFS but rather to some kernel issues around 3.0. I use the compress and caching options for my 2-drive BTRFS filesystem, as you see in the /etc/fstab entry that I posted earlier.


**Edit:** Check the BTRFS [**[color=green]FAQ Page[/color]**](https://btrfs.wiki.kernel.org/index.php/Problem_FAQ)  It shows that you need to run this at the directory prompt to defrag the on-disk data files:

```
find -xdev -type f -exec btrfs fi defrag '{}' \;
```

I just ran that on my music directory -- it definitely got the drive light flashing for awhile.  :)

---

