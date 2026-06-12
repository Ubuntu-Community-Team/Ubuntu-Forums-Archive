---
title: "Help with partitioning and installation."
date: 2014-01-19
forum: General Help
---

### Post by golfnut72 on 2014-01-19
I have a laptop that had a 500GB HD running a dual boot with Win 7 and Ubuntu 12.04.  The HD developed bad sectors and I had a hard time booting to either OS.  Through many long hours and countless reboots I was able to make a windows system recovery disk and save a system image to an external HD.  I've now replaced the HD with a new WD 750GB HD and successfully re-installed Win 7.  However, I now have ~265GB of unallocated space on the new drive.  The drive contains two primary partitions (system and C:) and a logical drive (the unallocated space).  I'd like to install Ubuntu 12.04 (or later, if necessary; I just already have a 12.04 disk) but want to use the unallocated space as opposed to eating up more of the Win 7 partition.

So the question for the gurus is this:  Will Ubuntu install in the unallocated space or not?  While I appreciated everyone's dedication to Linux, I have to keep Windows for work purposes, so please don't suggest that I chuck it.

Any help you can give will be greatly appreciated.  Thanks!

---

### Post by sgage on 2014-01-19
Yes, you can install Ubuntu into the unallocated space, though if it's a logical drive, it's not unallocated. Unallocated means it's not part of a partition. For it to be a logical drive, there has to be an extended partition, with the logical drive inside of that.

Where are you seeing it presented as a logical drive? In the Windows partition manager?

---

### Post by cptrohn on 2014-01-19
Personally I would download gparted live or use the built in disk formatting tool in Windows 7 and make 1 single partition that is NTFS and then run the ubuntu installer and re-install that way.  the install for the dual boot always seems to go much smother for me that way.

Here is my question though,  why not just Ubuntu as the only OS and then install Windows in a virtualbox?

---

### Post by The Cog on 2014-01-19
I have to agree with the above two posts: It is not clear at the moment what the current partitioning setup is. Can you fire up the Ubuntu installer live CD, and run 
```
sudo parted -l
```
and post the results. 
eason is, if the rest of the disk is in a partition, then it is probably not the right type for Ubuntu to install into - you may have to delete it.

---

### Post by golfnut72 on 2014-01-19
Thanks for your help folks. I apologize, but I can't seem to copy a screenshot from Windows Disk Manager into the box here.  I've copied it below:

Line 1: Volume: Blank Layout: Simple Type: Basic File System: Blank Status: Healthy (Active, Recovery Partition) Cap: 1.46 GB Free Space: 1.46 GB
Line 2: Volume: C: Layout: Simple Type: Basic File System: Blank Status: Healthy (Boot, Page File, Crash Dump, Primary Partition) Cap: 431.32 GB

In the graphic representation below it shows 22.03 GB of free space, followed by 243.82 GB unallocated space.  That's where I'd like to load Ubuntu.

CPTROHN, when you talk about operating Windows in a Virtualbox you're way over my head.  The amount of frustration I've experienced over the last two weeks - just to get the machine working again - makes me pause when it comes to making too many additional changes.

The Cog, I'll try running the code and be back shortly.

---

### Post by golfnut72 on 2014-01-19
Here's what I get when I run your script:

Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number         Start                       End                          Size                        Type                                         File system                         Flags
 1                     1049kB                1574MB                1573MB                   primary                                        ntfs                                      boot, diag
 2                     1574MB                 465GB                   463GB                     primary                                        ntfs
 3                    465GB                    488GB                 23.7GB                extended                                                                          lba

It appears that Ubuntu isn't reconizing the unallocated space, which is where I'd like to install the SW.  What do you folks suggest?

Again, thanks for your help!

---

### Post by The Cog on 2014-01-19
You seem to have two different types of unallocated space. 

The 23G free space is occupied by an "extended" partition. An extended partition is one that is intended to act as a container, with other "logical" partitions inside it (to overcome the limit of 4 primary partitions). But in this case, there are no other partitions inside - it's just an empty container. 

The rest of the unallocated space, 260 GB, is truly unallocated.

I don't know which of those two spaces the Ubuntu installer would choose if left to decide itself. If you are happy to give all 283G to Ubuntu, then I would suggest that you could either delete partition 3 or expand it to encompass the rest of the unallocated space too. Both these can be done with gparted on the live CD. The windows disk manager can probably delete the extended partition, I don't know about expanding it. Either way, the Ubuntu installer will create the partitions it needs in the space.

---

### Post by golfnut72 on 2014-01-19
Thanks for your help!  I need to do some research on gparted and will give it a shot.

Thanks again!

---

### Post by oldfred on 2014-01-20
Part of the issue is the existing extended partition. You can only have one extended partition that can have an unlimited number of logical partitions.
Either delete extended partition or better to just make extended partition larger with gparted to include all of the unallocated space. 
Default side by side install of Ubuntu with just / & swap should then work. If for any reason it does not offer side by side and show Windows do not use any auto install options. You may have left Windows hibernated or it need chkdsk after a resize and installer may not see the partition and overwrite it.
If you want /home or data partitions then use gparted to create those as logical partition and use manual install or Something Else to format and mount those. You can also use manual install to create partitions if desired.

---

