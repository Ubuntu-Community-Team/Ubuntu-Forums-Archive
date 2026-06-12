---
title: "KDE Partition Manager Options Greyed Out"
date: 2014-02-20
forum: General Help
---

### Post by pfthizzz on 2014-02-20
Kubuntu 13.10. Just installed this morning. x86-64

My hard drive has a bunch of unallocated space at the end, after the swap partition. I want to create a partition there. When I launch Partition Manager from the menu, it asks for my password, which I enter. But all options except unmount are greyed out. Selecting the unallocated space doesn't give me any options except to view the properties. I closed this, opened a terminal. sudo partitionmanager. enter password. Partition Manager comes up. Same thing. 
How can I get this to work?

thanks in advance

---

### Post by monkeybrain20122 on 2014-02-21
> **pfthizzz said:**
> Kubuntu 13.10. Just installed this morning. x86-64

My hard drive has a bunch of unallocated space at the end, after the swap partition. I want to create a partition there. When I launch Partition Manager from the menu, it asks for my password, which I enter. But all options except unmount are greyed out. Selecting the unallocated space doesn't give me any options except to view the properties. I closed this, opened a terminal. sudo partitionmanager. enter password. Partition Manager comes up. Same thing. 
How can I get this to work?

thanks in advance

You need to unmount the partition first in order to do anything to it. If you have one big partition that includes the os you are currently running (your kubuntu) it is not going to work because it can't unmount a partition currently in use. So you need to do this operation in a kubuntu live usb instead of kubuntu on your hard drive.

---

### Post by pfthizzz on 2014-02-21
Thank you for your reply, monkeybrain20122.

I would like to create a partition in the unallocated space. There is currently no partition there, and I am not trying to modify the existing partitions at the front of the disk. Every other partitioning utility I have used in the past has been able to do this. And even with operations on partitions in use (which is not what I am trying to do), you can still make changes that get applied on a reboot. 
Is KDE Partition Manager not getting elevated correctly? Is there possibly some other error happening? Or is KDE Partition Manager not capable of this basic functionality?

Thanks in advance

---

### Post by monkeybrain20122 on 2014-02-21
Well since the unallocated space is not in the current partition it should be able to do it. See screenshots. I don't use kde but I think the kde partition manager is just a gui front end of parted which is the same thing underneath the gui of gparted. Which kde partition tool are you using as I now remember there are several with similar names and one appears to be deprecated.

I don't know of any Linux partition tool that can modify partitions when mounted.

---

### Post by pfthizzz on 2014-02-21
It's definitely unallocated space, not empty space in a partition. I think you may be right about KDE Partition Manager being a front-end for parted, because I did verify parted was installed already. I can open the app by running sudo partitionmanager, so I guess that's the name of it.

thanks

---

### Post by monkeybrain20122 on 2014-02-21
Is it this? [http://www.kde.org/applications/system/kdepartitionmanager/](http://www.kde.org/applications/system/kdepartitionmanager/)

It should work, not sure why it is greyed out. I don't have kde so can't test it. Maybe someone who runs kubuntu will give you better advice.

---

### Post by pfthizzz on 2014-02-21
It might be a bug
[https://bugs.kde.org/show_bug.cgi?id=300692](https://bugs.kde.org/show_bug.cgi?id=300692)

---

### Post by SeijiSensei on 2014-02-21
How many primary partitions are there on the drive?  If you have four, that's all you can have.  The solution is to create a large "extended" partition, but you won't be able to do that unless you back everything up first since you'll have to delete at least one of the current primaries.

Many Windows machines come from the factory with all four primaries in use.  It's one of the biggest obstacles to installing Linux or any other OS in a dual-boot arrangement.

---

### Post by pfthizzz on 2014-02-21
It's a brand new hard drive. There is the Linux system partition, followed by the swap partition, followed by the unallocated space.

---

### Post by pfthizzz on 2014-02-21
It looks like it's a problem with KDE Partition Manager. I just installed gparted and that worked perfectly.

Thanks to everyone who chimed in.

---

