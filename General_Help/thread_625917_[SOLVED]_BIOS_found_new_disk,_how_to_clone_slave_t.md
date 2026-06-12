---
title: "[SOLVED] BIOS found new disk, how to clone slave to master"
date: 2007-11-28
forum: General Help
---

### Post by Mark_in_Hollywood on 2007-11-28
I have physically installed an unused 300 gig drive as on the cable as pri/master. The BIOS locates it. Up untill now, my Gutsy has been running (and quite well) as primary/slave (20 gig).

There are NO partitions on the 300 gig.

I want to clone the old drive's data over, and (can I use?) use GParted to resize the partitions to reflect the 300 gig's useable space.

Currently the 20 gig is partitioned as:

Partition        Filesystem          Mountpoint         Size             Used          Unused        Flags

/dev/sdb1 [locked[   ext3                 /             15.63GiB       5.2GiB         10.31GiB
/dev/sdb3        ext3                                         2.04GiB       2.04Gib       12.00KiB      boot
[down arrow]
/dev/sdb2 [locked] extended                         1004.06GiB      ---                ---
     /dev/sdb6    linux-swap                           164.67MiB      ---                  ---
    /dev/sdb5     linux-swap                          839.30Mib        ---                  ---

I don't quite understand what comes after "extended", this 20gig was Dapper and upgraded by Synaptic. It installed the extra partition at that time. Dapper didn't have the "extended". That doesn't matter. As long as I can "clone" the old drive to the new and resize the "main" partition.

Any recommendations about the size of the swap file? I have 10 gig for /
but can never figure out a good swap file size. Anyway I've altered swappiness from 60 to 10 as I have a gig of SDRAM. The 300 gig (technically 320gig) formats down to 290 gig. Room to spare for a while.

---

### Post by Irony on 2007-11-28
You can copy over your entire installation like this;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

Once you've done it make sure that your etc/fstab and boot/menu.lst are correct.

---

### Post by Cochise on 2007-11-28
check out ghost4lin its a live cd made for cloning hard drives

---

### Post by Mark_in_Hollywood on 2007-11-28
Ghostess was the Mostess. Now all I have to do  is make /dev/sda1 reflect the size of the available unused disk. Which I will do, in another post.

Thanks, community!

---

