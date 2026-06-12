---
title: "Merging partitions."
date: 2014-08-21
forum: General Help
---

### Post by filip-milic94 on 2014-08-21
[B]Hi guys, i have installed Lubuntu 14.04 not so long ago, and today i  have tried to install Elementary OS alongside it. Since the dualboot  didn't work, i've deleted the partition which had Elementary OS  installed. I've done this from Lubuntu using GParted.
And now i'm left with this unallocated space (30.94GB). What i want to  do now is merge unallocated space with my Lubuntu partition which is  sda1 (ext4).
How do i do this in a simple way, without losing any data, especially on sda5 (ntfs), because i have my personal files in there?
[COLOR=#ff0000]Here's a screenshot:[/COLOR][/B] [http://i57.tinypic.com/2i03l3m.png](http://i57.tinypic.com/2i03l3m.png)

---

### Post by Bashing-om on 2014-08-21
filip-milic94; Hi ! Welcome to the forum;

Though doable, there is a high degree of risk in moving the partitions about - back up all your data !

A better thought might be to make that "unallocated" space into a 'shared' partition (??)

But to answer your request:
From the liveDVD (partitions unmounted, make sure swap is also turned off in GParted);
As that "unallocated" space resides in the 'container" called an extended partition; one has to first shrink that container (sda2), and turn off swap so that the partition is not in use - ( can not operate on a partition that is in use !) once shrunk, one may then expand 'sda1' in the now available space.

exercise care and consideration
[INDENT][INDENT][INDENT][INDENT]good luck
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-08-21
There never are any guarantees with major changes like editing partitions, so good backups are required.
But you should be able to use a live installer and gparted. The little key say partitions are mounted and you cannot edit mounted partitions. Live version of gparted will probably mount swap and you have to click on it, to unmount swap and release extended partition from it in effect from being mounted.
Then you should be able to move extended partition right, which in effect moves unallocated out of extended partition and into space next to sda1. 
Then you can expand sda1 into unallocated.

Should not change any UUIDs are you are not editing partitions and since start of sda1 is not changing, you should not have to reinstall grub. But again have working live installer handy just in case.

There seems to be a rule. If you have good backups and a emergency disk, you will not need them. But the one time you are in a hurry and skip those steps is the one time everything goes awry.

---

### Post by ajgreeny on 2014-08-21
Just a warning that expanding that partition will take a very long time, maybe a few hours, and you **MUST NOT INTERRUPT OR CANCEL  ** the expansion or you will probably lose everything, so if this is a laptop, make sure that it is plugged in to an external power source.

---

### Post by filip-milic94 on 2014-08-21
Hey guys, i've sorted my problem with guys on Ubuntu IRC channel. (I was impatient) Anyway, thank you guys for quick replies, and all the help, you are the best. :D

---

### Post by Bashing-om on 2014-08-21
filip-milic94; Outstanding !

The guys on IRC are the best too ! // We all do what we can.

As this situation is now at an end:
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

