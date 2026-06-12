---
title: "Gparted - Can you remove Windows partition?"
date: 2015-10-18
forum: General Help
---

### Post by qkzoo on 2015-10-18
My current partitions

/dev/sda1     ntfs
/dev/sda2     ntfs
/dev/sda3     extended
  /dev/sda5     ext4
  /dev/sda6     linux-swap
  
Is it possible somehow using gparted to delete/remove or merge the Windows partitions with the Linux partitions?  Basically, I just want to get rid of Windows and merge Linux on to that existing space.  However, it's on the beginning of the drive, so I'm assuming that this isn't possible, and I just need to wipe everything and start fresh, but I wanted to check first.

---

### Post by sandyd on 2015-10-18
Merging is a bit dangerous when space is at the front of the drive unless you are using LVM.

Then, you can just create a LVM PV, and add extra space to the LVM Volume Group.

Above, your setup does not use LVM, as a result, you will need to...

1. Delete the two NTFS partitions
2. Extend the extended partition
3. Extend the ext4 volume.

It will take time for Gparted to shift around the drive data if you want to have a try, so if your not prepared to wait, I suggest reinstalling or using the two partitions just for storage.

---

### Post by qkzoo on 2015-10-18
That's what I was afraid of, certainly sounds like it would be easier to wipe.  Thanks for your help!

---

### Post by Bucky Ball on 2015-10-18
... but that said, easy enough, just time consuming. You can set it up to do all of the above in the one job in Gparted. 

Goes without saying but I'll say it anyway: back up what is valuable in case things go pear-shaped. Good luck. :)

---

### Post by ajgreeny on 2015-10-19
Agreed; as above.

From a personal perspective I can tell you that I have done this in the past with no problems, other than the time it takes, (possibly hours, depending on the speed of your computer and the size of partitions), so provided you have good backups of all you need, there is nothing to lose; if it does go wrong you just start again and clean install over everything.

---

### Post by sammiev on 2015-10-19
I have tried it and it worked with no errors or bugs. ( It did take hours )

That been said, I can do a clean install and be fully up and running with all my data back in place in 30 to 40 min.

Doing a clean install also takes out the clutter.

Always backup first.

---

### Post by yancek on 2015-10-19
Unless sda5, your / partition is filling up, it would seem to me to be a lot simpler to just format the current windows partitions ext4, create mount points for them and put a proper entry in /etc/fstab as suggested above.  Or you could delete sda2, resize sda1 to include the unallocated space formerly occupied by sda2 and do the same process.  You could use this as a separate data partition and would certainly be a lot faster.

---

