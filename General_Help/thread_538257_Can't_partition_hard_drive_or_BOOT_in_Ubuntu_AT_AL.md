---
title: "Can't partition hard drive or BOOT in Ubuntu AT ALL"
date: 2007-08-29
forum: General Help
---

### Post by mikecomua on 2007-08-29
Hello, I have a 120gb Seagate external drive, which I decided to install Ubuntu on (for no reason). So one day I have decided to boot into Ubuntu and it said something about my hard drive being mounted 35 times and it had to check it. SO then it gave me an error message and said I couldn't boot. After that I booted into XP and tried to make my Csaid partition smaller, using Norton Partition Magic, but it gave me an error message, so I couldn't do that either, Now I can't boot into Xp AND Ubuntu. Now I booted into Ubuntu Live CD and tried to partition my external drive to backup my data, but it said> GParted 0.2.5

Resize /dev/sdb1 from 108.92 GiB to 18.29 GiB    ( ERROR )
     	
check filesystem on /dev/sdb1 for errors and (if possible) fix them    ( ERROR )
     	
e2fsck -f -y -v /dev/sdb1
     	
/dev/sdb1 is mounted.
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Cannot continue, aborting.



========================================

Create Primary Partition #1 (ext3, 90.63 GiB) on /dev/sdb

========================================


How should I
a) bring back my Windows drive to life
b) bring my UBuntu to live
Thx a lot:guitar:

---

### Post by be4truth on 2007-08-30
You can't (shouldn't) check a partition when it is mounted as it is live, hot. If you unmount the partition it isn't live any more and the operating system can do with it without danger. Boot into Live Ubuntu. While doing this Ubuntu will automatically mount /dev/sdb1.

Open a terminal and type 

```
sudo umount /dev/sdb1
```

When you check with ```
mount
``` you should not see any entry for /dev/sdb1.

Now you can run in the terminal

```
sudo fsck -aC /dev/sdb1
```

the -a stands for repair everything automatically and the -C so that you get a progress bar if possible.

If this fails try this one

```
sudo fsck -C /dev/sdb1
```

With this fsck will ask you when it encounters problems and you have to decide (is not always easy, follow your instinct)
I had this problem not one week ago and successfully repaired a partition.

---

### Post by mikecomua on 2007-08-30
Thank you, but I have just installed Ubuntu on my primary hard drive an uninstalled XP.

---

### Post by be4truth on 2007-08-30
You might want to mark the thread solved. Go to the top of this page under Thread Tools.
:popcorn:

---

