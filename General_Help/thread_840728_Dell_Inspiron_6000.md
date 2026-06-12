---
title: "Dell Inspiron 6000"
date: 2008-06-25
forum: General Help
---

### Post by NoFear63 on 2008-06-25
Hey. Im new to the world of linux.
I tried running linux from the live CD so i could determine if i wanted to install it and everything seemed in order.
My sound was working,wireless was working,all the stuff that i needed was there. 
My only issue was that it seemed really slow. I am assuming this is because i was running it from the live C.D. but am not completely sure.

I was wondering based on my specs if i should go through with linux because im not sure if my laptop will make linux slow like i experienced on the live c.d

Dell Inspiron 6000
60 GB hdd. (partitioned 4 ways;one for windows(main partition).
then dell took 2 partitions totaling about 4 gb. and then there is some unpartitioned space. On the windows partition that i am on right now has a total of 52 gb with 38.5 free.
1.6 GHz Intel Pentium M Processor
504 MB of Ram
Mobile Intel 915GM/GMS,910GML Express Video Card. 128 MB
SigmaTel C-Major Audio

Im not sure if i should include anything else. If I do just let me know. 

Also if you have any tips for me on installing ubuntu that would be greatly appreciated.

---

### Post by overdrank on 2008-06-25
> **NoFear63 said:**
> Hey. Im new to the world of linux.
I tried running linux from the live CD so i could determine if i wanted to install it and everything seemed in order.
My sound was working,wireless was working,all the stuff that i needed was there. 
My only issue was that it seemed really slow. I am assuming this is because i was running it from the live C.D. but am not completely sure.

I was wondering based on my specs if i should go through with linux because im not sure if my laptop will make linux slow like i experienced on the live c.d

Dell Inspiron 6000
60 GB hdd. (partitioned 4 ways;one for windows(main partition).
then dell took 2 partitions totaling about 4 gb. and then there is some unpartitioned space. On the windows partition that i am on right now has a total of 52 gb with 38.5 free.
1.6 GHz Intel Pentium M Processor
504 MB of Ram
Mobile Intel 915GM/GMS,910GML Express Video Card. 128 MB
SigmaTel C-Major Audio

Im not sure if i should include anything else. If I do just let me know. 

Also if you have any tips for me on installing ubuntu that would be greatly appreciated.

HI and welcome. The live cd it a little slower than the actual install. The system specs should run ubuntu just fine. When you choose to install it should let you resize windows partition for the space needed to install ubuntu.

---

### Post by NoFear63 on 2008-06-25
Thanks for your reply. Although it leads me to another question.
Will i be able to make my hdd into two partitions one being windows and the other linux? Because as i stated i have 4 partitions and i only want two. I need windows for games thats the only reason im keeping   I look on partition magic and it says that i have the main partition being like 50 somthing gb and another with unallocated space and the other two being something that dell put on it to like restore the OS or something like that. I prob just realy confused you but i hope i didn't

---

### Post by overdrank on 2008-06-25
> **NoFear63 said:**
> Thanks for your reply. Although it leads me to another question.
Will i be able to make my hdd into two partitions one being windows and the other linux? Because as i stated i have 4 partitions and i only want two. I need windows for games thats the only reason im keeping   I look on partition magic and it says that i have the main partition being like 50 somthing gb and another with unallocated space and the other two being something that dell put on it to like restore the OS or something like that. I prob just realy confused you but i hope i didn't

Hi and yes those are restore partitions from dell. So I would not recommend deleting those partitions. You can have up to 4 primary partition on a drive unless you create a extended partition, then you may have more partitions. So if you keep those restore partitions then you would need to resize the windows partition for free space for ubuntu. Then create a extended partition for the ones needed for ubuntu and swap.  This link may help with the partitioning
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by NoFear63 on 2008-06-25
thanks for the link. It was very helpful

---

