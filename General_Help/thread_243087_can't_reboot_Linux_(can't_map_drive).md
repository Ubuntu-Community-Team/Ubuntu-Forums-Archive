---
title: "can't reboot Linux (can't map drive???)"
date: 2006-08-24
forum: General Help
---

### Post by worawutkk on 2006-08-24
Hi all,

I have a very big problem now. My Linux doesn't boot!! What happened is as follows, in step-wise manner.

1. I used Partition magic to creat partitions on my newly bought external harddrive.
2. I booted Linux(I have only one internal harddrive of 200GB, one portion is preserved for Linux: Ubuntu6.06). This time Linux doesn't boot up, with a message saying something like "can't find.... partitions"

Personally I think this is because the new partition in the External harddrive have taken the name formerly used by Linux, and obviously I didn't know that. Windows doesn't seem to see the existence of Linux, and vice versa!!

I tried changing the drive letters of my External harddrive to something like S, T, U which is far beyond D, E, F drive letters normally used, hoping that it might rescue the situation. To no avail, i didn't help.

Anybody help me please???? I would appreciate all the suggestions.


thanks a million
Worawutkk

---

### Post by Klaidas on 2006-08-25
I'm sorry I can help with your problem, but I think this is a wrong subforum - this one is for forum issues.

---

### Post by nalmeth on 2006-08-26
>  1. I used Partition magic to creat partitions on my newly bought external harddrive.
2. I booted Linux(I have only one internal harddrive of 200GB, one portion is preserved for Linux: Ubuntu6.06). This time Linux doesn't boot up, with a message saying something like "can't find.... partitions"

Personally I think this is because the new partition in the External harddrive have taken the name formerly used by Linux, and obviously I didn't know that. Windows doesn't seem to see the existence of Linux, and vice versa!!
?? Does this mean you can get into linux but can't see windows ??

Did you install linux at step 2? You don't *have* to create new partitions before hand, but since you did, how have you partitioned it? You have your NTFS/FAT32 windows, and Ubuntu's default filesystem is EXT3

Did you specify in the installer to install to the EXT3 you made, if you did create that FS?

Your post is confusing! :-s

---

### Post by Tomosaur on 2006-08-26
Altering drive letters in Windows will not help the situation, but just for the sake of clarity, could you try explaining your problem a bit more? It's pretty confusing :P

---

