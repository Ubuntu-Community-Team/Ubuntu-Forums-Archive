---
title: "Gparted extended partition help"
date: 2014-06-26
forum: General Help
---

### Post by cannon_dt on 2014-06-26
My existing hdd partition is as below:

```
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  100GB  100GB   primary   ext4            boot
 2      100GB   304GB  204GB   extended
 5      100GB   104GB  4046MB  logical   linux-swap(v1)
 6      104GB   304GB  200GB   logical   ext4
```

I have 648.35 GB unallocated. What I need is as follows:

    I need a 110 GB hfs+ partition to restore my clonezilla backup of Lion OS
    Use around 300 GB of the rest of the unallocated space for data through 1 or more logical partitions
    Keep around 200 GB unallocated for any new OS or even Windows in the future.

My questions: 
1. Is my planning correct? Or should I be doing something else? 
2. If my plan is right then I can create the hfs+ partition right away at the end of the unallocated space using gparted right? This would be a primary partition right at the end of the hdd 
3. For adding 300 gb to my extended partition do I need to use a live CD and then resize? I do not know how to do this 
4. What else do I need to take care of for in terms of being able to login to use my Linux Mint (sda6) again without any hassle.

I have never done this before, so I want to plan this and get things right and not screw up my existing working Mint. So please do feed me explicit steps :)

Thanks, Ananth

---

### Post by ajgreeny on 2014-06-26
First backup everything that you can not afford to lose, just in case something goes wrong.

Now boot to a live *ubuntu system using a DVD or USB, as you may have done when you installed you Linux OS.  From the live system open gparted, right click on the swap partition and choose "swapoff" as the live OS will find swap and use it.  You may also need to check all the other partitions and unmount any that are mounted and show a key symbol next to them.  From this point you should be able to enlarge the extended partition, sda2, either all the way to the right hand end of the disk, or if you really will want to install windows at some point, to the point where there is still 200GB free at the right hand end.  Windows will not boot from a logical partition, hence the need to leave this final 200GB as a primary partition.

You can make any new logical partitions in the now larger extended partition, though for the hfs+ partition you may need to install **hfsplus** in the live system; I have no experience of mac file systems so am not sure about this, and hfsplus may not actually be needed for gparted to make such a partition.

---

### Post by grahammechanical on 2014-06-26
I have never tried to create a primary partition after an extended partition. I would move the extended partition to create unallocated space in the front of the extended partition that I can then create a primary partition out of.

We cannot move or resize partitions that are in use. So, in my opinion, it is always best to run Gparted from a live session. It can take a long time to complete the actions. So, I always run one change at a time instead of placing several actions in a queue.

Oh, back up and be willing to re-install. You never know.

Regards.

---

### Post by cannon_dt on 2014-06-26
@ajgreeny @grahammechanical
Thank you for your replies.
Without the live CD, I can create the hfs+ partition right? I need the live CD only for resizing the extended partition. 
Attaching a gparted image of this (not yet committed task)
[ATTACH=CONFIG]254268[/ATTACH]

Also after resizing etc from the live CD, should I have to alter anything like fstab etc or will boot up be ok? That is what I am concerned about.

Please do let me know.

Thanks,
Ananth

---

### Post by yancek on 2014-06-26
There should be no problem with your proposed solution.  Since you are not modifying the Mint partition, booting should not be a problem and there is no need to modify fstab.  After you get data on that partition, you may want an entry in fstab for the hfs partition.   Then you need to use the Live CD with GParted to resize the Extended partition as suggested above.  There is no problem creating a primary after logical/Extended partitions.

---

### Post by cannon_dt on 2014-06-27
@yancek thanks!
Just one clarification. You said 
```
After you get data on that partition, you may want an entry in fstab for the hfs partition
```
What do you mean by this? I have a clonezilla backup of the hfs+ partition which I intend to restore once I create the new hfs+ partition at the end of the hdd? So please do clarify

Great to know that booting should be ok

Peace
Ananth

---

### Post by yancek on 2014-06-29
Putting an entry in the /etc/fstab file will make it available on boot, other wise you would need to manually mount it each time you want access.  Not sure which option you want.

---

### Post by cannon_dt on 2014-06-29
The hfs partition would be in my grub so that I can launch Mac OS, not sure why I need anything on the fstab. Can you please explain further?

---

### Post by yancek on 2014-06-29
> The hfs partition would be in my grub so that I can launch Mac OS, not sure why I need anything on the fstab.

You don't.  The only reason to do that is so that you can access it from Ubuntu which I assume you also have installed since you are posting on Ubuntu forums.  If it were just a data partition, it would be a good idea to have an entry in fstab.  If it is going to be another OS, the choice is yours.

---

### Post by cannon_dt on 2014-06-30
Ok, I understand what you are saying now. Mea culpa, I should have probably stated that I have managed to get a hackinstosh setup on my AMD linux setup, so I am actually using it as another OS and hence will not be accessing the hfs+ partition on my linux setup. Thanks for the clarification.

Peace
Ananth

---

