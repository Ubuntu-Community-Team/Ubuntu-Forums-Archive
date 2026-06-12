---
title: "I upgraded RAM, now what about Swap?"
date: 2015-08-19
forum: General Help
---

### Post by Petro Dawg on 2015-08-19
When I installed Ubuntu I had 3 Gig of RAM and the Ubuntu installer set aside about 3 Gig of Swap space.  Since then I upgraded my RAM to 8 Gig.  In the past, when I upgraded RAM I always shrunk my Linux partition and increased the Swap space to match the RAM I had installed, it was usually only 2 to 4 Gigs or so (my computers have always been cheap and/or ancient).  On this system I am dual booting with Win7 and only have 40 Gig of HD space set aside for Linux.

The question is, should I even bother increasing the Swap space now that I have 8 Gig of RAM?  Is sacrificing another 5 Gig of my available 31Gig of HD space worth the trouble, or am I ever even likely to use any Swap at all with 8 Gig?  I was considering deleting my Swap partition altogether and expanding my Linux part ion to recapture the 3 Gig lost to Swap in the original install, but not entirely sure if that would cause any issues down the road.

---

### Post by monkeybrain20122 on 2015-08-19
Do you really need swap with 8 G of ram? Anyway. I am in same situation, upgraded ram from 4 to 8G but have not changed swap (6G) suspension still works so I am not going to touch it.

---

### Post by tgalati4 on 2015-08-19
The only capability that you lose is the ability to hibernate.  During hibernation, a RAM snapshot is copied to swap so the computer can shut down completely.  The kernel will lock out hibernation if the swap is not large enough to capture the RAM snapshot.

---

### Post by monkeybrain20122 on 2015-08-19
> **tgalati4 said:**
> The only capability that you lose is the ability to hibernate.  During hibernation, a RAM snapshot is copied to swap so the computer can shut down completely.  The kernel will lock out hibernation if the swap is not large enough to capture the RAM snapshot.

True but hibernate is disabled anyway.

---

### Post by nerdtron on 2015-08-20
I won't suggest you increase your swap, but at least here's a solution that will increase the swap without repartitioning/re-installing the OS. Downside - it will create a new 8GB file as a swap.

Steps to add a swapfile:

Turn off swap first. You won't see any swap on "free -m"
# swapoff -a

The following dd command example creates a swap file with the name &#8220;myswapfile&#8221; under /root directory with a size of 8GB
# dd if=/dev/zero of=/root/myswapfile bs=1M count=8192
1024+0 records in
1024+0 records out

# ls -l /root/myswapfile
-rw-r--r--    1 root     root     1073741824 Aug 14 23:47 /root/myswapfile

Change the permission of the swap file so that only root can access it.
# chmod 600 /root/myswapfile

Make this file as a swap file using mkswap command.
# mkswap /root/myswapfile
Setting up swapspace version 1, size = 1073737 kB

Enable the newly created swapfile.
# swapon /root/myswapfile

You now have the new swapfile as your system swap. But after reboot, you'll revert back to your original swap
To make this swap file available as a swap area even after the reboot, add the following line to the /etc/fstab file. Remove/Comment the original swap entry.

# cat /etc/fstab
/root/myswapfile               none                    swap    sw        0 0

Verify whether the newly created swap area is available for your use.
# swapon -s
Filename                        Type            Size    Used    Priority
/dev/sda2                       partition       4192956 0       -1
/root/myswapfile                file            1048568 0       -2

# free -m
Note: In the output of swapon -s command, the Type column will say &#8220;file&#8221; if the swap space is created from a swap file.

---

### Post by tgalati4 on 2015-08-20
You can create multiple swap partitions and multiple files as designated swap files.  As long as they are listed in /etc/fstab correctly, they will all add up to a total swap pool.  You can't mix 32-bit and 64-bit swap pools (from a multi-boot system), nor encrypted versus unencrypted swap pools.

---

### Post by Petro Dawg on 2015-08-20
Re-sizing partitions is something I've done countless times in the past and isn't a big issue for me.  However, I didn't know, or have forgotten, that swap files could be made.  So the question now is... If I create an 8 Gig file for Swap, will it permanently eat up 8 Gig just like a bigger swap partition would? Or would it shrink if the HD filled up to fit the available space?  I've also read in the past about not filling up the Linux partition more than 80% to prevent fragmentation.  Would that 8 Gig swap folder count towards my 80%?  If so, I think it would be better to dedicate a partition fully dedicated to Swap... 

(40G * 0.8) - 8G = **24**G available for storage with 8G swap folder

(40G - 8G) * 0.8 = **25.6**G available for storage with 8G swap partition

So am I right in thinking that removing the swap partition altogether would just keep me from being able to hibernate and have no other effects?   I do not seem have hibernate option anyway and it's not something I normally do.

---

### Post by Yellow Pasque on 2015-08-20
I would not make any change to the system unless you're doing something that uses a ton of memory (like running multiple VM's). If you have 8GB of RAM and you fill up a 3GB swap partition, then either you need more RAM (because you're using a ton of it) or some process is rapidly leaking memory and will soon ground the system to a halt regardless of how big the swap is.
BTW, a swap partition performs better than a swap file.

---

### Post by tgalati4 on 2015-08-20
Yes, swap permanently uses disk space whether it is a file or a partition.  The 80% rule only applies to your active file system mounts:

```
df -h
```

You can go 90% and the system automatically reserves 5% for house-keeping, but if something goes wrong, you don't have much room to fix things.  So 80% is a safe number.  Fragmentation goes up when the file system gets full.

> tgalati4@Mint17 ~ $ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        70G  9.1G   58G  **14%** /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            982M  4.0K  982M   1% /dev
tmpfs           200M  1.3M  199M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            997M   30M  967M   3% /run/shm
none            100M   36K  100M   1% /run/user


The number in bold is the one to watch.  It's the / (root) partition.  When it gets full, (and it contains /home/user), you will have problems.

---

### Post by Petro Dawg on 2015-08-21
Thanks everyone for your input.  Since I'm not likely to do much more than store documents, surf the internet, or check emails on my Linux partition; I decided to leave partitions alone for now and just keep the 3 Gig Swap "just in case" knowing that I'll likely never need it.

---

