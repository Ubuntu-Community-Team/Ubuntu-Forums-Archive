---
title: "Problem with Software RAID"
date: 2007-08-24
forum: General Help
---

### Post by mlinsgomes on 2007-08-24
Hi everybody,

I have here a software RAID5 built with mdadm for storage purposes, but a few days ago, one of 4 HD's present some problem and i've marked it as faulty, and now, i can't mount the special device. Let me show you the output:

root@server:~# mount /home
mount: /dev/md0: can't read superblock

root@server:~# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sdb1[0] sdc1[2] sdd1[1]
      1465151808 blocks
       
unused devices: <none>

I'm thinking in try to use:

mdadm --assemble --update

to update superblocks, but i don't know if there is a possibility of data loss. Someone can help me about this?

Thanks in advance, and sorry for my bad english.

---

### Post by fjgaude on 2007-08-25
Are you sure you marked the correct disk faulty? How did you know which is which? There is a chance you took out the wrong disk, one that has good data. Put it back and see what happens.

After you took the so-called bad drive out you no longer had an array, right? Put it back in and see if the array shows. I wouldn't try assembling it just yet.

What does sudo mdadm -D /dev/md0 show?

frank

---

