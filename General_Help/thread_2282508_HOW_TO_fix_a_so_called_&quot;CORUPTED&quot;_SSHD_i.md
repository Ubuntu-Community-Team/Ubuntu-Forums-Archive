---
title: "HOW TO fix a so called &quot;CORUPTED&quot; SSHD internal storage disk ????"
date: 2015-06-14
forum: General Help
---

### Post by Mads_Unneberg on 2015-06-14
When I`am formatting a disk for a new instalment on a OS I like to use another software than the formatting in the OS I`am installing.  
I do this because I can see that the disk is getting formatted, deleted and so on.... 
I now use "Darik`s Boot and Nuke" and it works weary well for me.
BUT....
In the software I have there is no way to pick out one disk. This software ERASE`S ANY DISK YOU HAVE CONNECTED.
And for half a second it had started it`s formatting AND I TURNED THE COMPUTER OFF.
And now I`w being told that my other disk`s are corrupted and can`t be mounted ore opened in Ubuntu 15.04 


 - SO IS THERE A SOFTWARE THAT CAN FIX THIS PROBLEM ???  

Regards
M.

---

### Post by Steve_Horan on 2015-06-14
You should use Gparted manually format disks in the future. Recovering data after Boot and Nuke is pretty hard to do. Not usually something as simple as running a program and getting your data back.

---

### Post by yetimon_64 on 2015-06-15
Darik's boot and nuke (DBN) can do a heck of a lot of damage in even "half a second". If it has only wiped the first meg or two you may get lucky and be able to rebuild using "testdisk". If it has gotten too far into the drive, even testdisk won't be much help to you. DBN is pretty nasty in what it does, it overwrites actual data not just the drive formatting.

I'd recommend you install testdisk from the ubuntu repos and give it a try.
A step by step guide : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I really don't know how likely or possible recovering the system is in this case. Though testdisk is worth a try in my opinion.

---

### Post by Mads_Unneberg on 2015-06-26
This took a waile....
But THANK`s to both **Steve_Horan** and **yetimon_64 ):P):P**
It all ended up in freshly formatted disk`s and I`ll carry the loss.
Regards
MU.

---

