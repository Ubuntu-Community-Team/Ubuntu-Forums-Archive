---
title: "ZFS problem, need help!"
date: 2017-04-21
forum: General Help
---

### Post by coolit2 on 2017-04-21
Hey Guys,

I need your help, I have 2 ZFS array(s)
Array 1 (4 disks without a spare)
Array 2 (raidz, 2 disks with 1 spare)
+ an ssd for my OS ( Ubuntu 16.04)
Yesterday my computer crashed the 3rd disk in the second array died. 
I didn't know what was going on so I rebooted.
Now the computer can only find the first array. the second (the raidz one) is gone.
PC says there is no such pool. First array has no problem.

My question:
Can I still recover the data from the raidz array?
Is there any way I can force the pc to detect it?
If not, can I recover the data in any way?
I don't care about the disk(s) I just want to boot it once to copy the data to an external drive.

Thx allot in advance.

---

### Post by Autodave on 2017-04-21
If you are sure which disk is failed, you can try connecting it to any PC with a USB cable (available most everywhere) and see if any data is available. Short of that, youmay be able to get professional recovery services to get most / some/ now data back off of the disc. This will NOT be cheap.

---

### Post by coolit2 on 2017-04-21
HiAutodave, thx for the reply.
I don't think you understood me...
There is parity available on this array. so 2 disks should be enough to retain all the data. 
My question is: can I let zfs scan the 2 working drives (should contain all the data) and boot them temporarily to copy the data to an external drive.
If I typ: "sudo zfs status" it cant find the zfs pool. Any way to force detection?[[COLOR=#000000][URL="https://ubuntuforums.org/member.php?u=917298"][COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=917298")[/COLOR][/URL]

---

