---
title: "Resize another Linux partition"
date: 2007-05-27
forum: General Help
---

### Post by Hoffmann on 2007-05-27
Hi,

I have installed Fedora on my Desktop before. That is the only operational system I have on my machine, and I have no free space available. In this context, how can I resize the Fedora partition in order to get free space needed to install Ubuntu as well?

Thanks

---

### Post by merlinus on 2007-05-27
When you boot from the Ubuntu live cd and click Install, it will take you to a partitioning screen (after asking a few questions).  You should be good-to-go from there.

-merlin

---

### Post by rillip on 2007-05-27
If you have no free space, you cannot install Ubuntu and keep Fedora.  If you want to just trash Fedora, you can use the partitioner to set up the needed partitions and format.

Edited for clarity:

I wouldn't recommend keeping your home directory for use as your home directory.  I'm assuming you have your data on a seperate partition from your FC root.  If so, you can skip formating that partition, and then once installed, you can just mount the partition as something else.  I wouldn't keep your home directory from FC for the new home directory because I'm not familiar with making that work - there are bound to be settings that aren't compatible, such as dealing with RPMs, that might cause difficulty.  This is especially true if you were not running the same GUI you will be running on your Ubuntu install.

---

### Post by merlinus on 2007-05-27
For my own learning -- is it not possible to re-size linux partitions with the ubuntu live cd?  Or is it something about fedora?

Thanks.

-merlin

---

### Post by brharri1 on 2007-05-27
Normally, if you boot off the live cd, it would be no problem to resize your current partition and use that freed up space to make a new partition. The problem is that you said you have no free space. If you really mean that, then you cannot just create a new partition out of nothing; you must have free space. If however you do have free space on your fedora partition, then yes, you can use that free space to create a new partition.

Hope this clears things up a little.

---

### Post by Crafty Kisses on 2007-05-27
> **Hoffmann said:**
> Hi,

I have installed Fedora on my Desktop before. That is the only operational system I have on my machine, and I have no free space available. In this context, how can I resize the Fedora partition in order to get free space needed to install Ubuntu as well?

Thanks

In this case, you should buy a external harddrive, and put all your files on there. Although if you still have space left, you can try to resize your partition with the LiveCD or in your Bios.

---

### Post by Hoffmann on 2007-05-27
I need to clarify a thing here: When I said I have no available free space, I mean, that my whole HD is "filled" with Fedora distro.

Hoffmann

---

### Post by Crafty Kisses on 2007-05-28
Hmmm, how big is your HDD?

---

### Post by Hoffmann on 2007-05-28
260 Gb

---

### Post by Crafty Kisses on 2007-05-28
It's possible that you messed up on a partition, so are you sure you don't have any partitions.

---

### Post by Hoffmann on 2007-05-29
> **Codename said:**
> It's possible that you messed up on a partition, so are you sure you don't have any partitions.
I have just one partition with Fedora. The scheme of my HD is as follow:

Filesystem  1K-blocks                             Used              Available Use% Mounted on /dev/mapper/VolGroup00-LogVol00
                                          234443400  26178868       196163312    12% /
/dev/sda1                               101086          16231               79636    17% /boot
tmpfs                                       511868                   0            511868      0% /dev/shm
 
In this context, do you think I can get free space to install Ubuntu besides Fedora?

Thanks.

---

### Post by gslo on 2007-05-29
Hi Hoffmann,
You can use the Ubuntu install disk to create a partition using only free space on your existing Fedora partition. 
As part of the install process it will ask you if you want to do this and will automatically do it for you if you answer yes.
It will create a single root(/) partition and you could add a home (/home) partition.
The swap partition you use with Fedora can be used with Ubuntu so you don't have to create another one.

Hope this helps.

---

