---
title: "Newbie Needs Installation Help"
date: 2007-10-22
forum: General Help
---

### Post by keech on 2007-10-22
Hi All,

I wolud like to try out Ubuntu 'Gutsy' on my desktop. I am new to the Linux environment. I am presently using Win XP and want to migrate to Ubuntu eventually, knidly help me with installing Gutsy. 

Firstly let me give my sys breakup

AMD Athlon 64 X2 +4000, 
1GB RAM (128 MB shared for Graphics),
Single 160 GB Hard disk (Partition 40GB,40GB,80GB) Fully NTFS Formated by Win XP,
Gigabyte MB (GA-MA69VM-S2) with Integrated ATI&#8482; Radeon&#8482; X1200-based Graphics Engine
Other standard components

I want to know how I should go about my installation like when I try to install should I use Manual partion or guided

I want to dual boot and want to provide 20 GB and 2 GB Swap drive for Ubuntu from the 80 GB partition .

I just want to know how to go about the installation with this system and such Hard Disk allotment.

Also kindly tell me whether Compiz Fusion work on this system.

Thanks in Advance

Mohan :)

---

### Post by prince_niceguy on 2007-10-22
you can first get the partition of 80 GB resized using gparted.

gparted can be found under system --> administration when you are logged in using live cd. I would recommend the following

resize 80 GB to say 58 GB.

create a extended partition. this is important as you cannot create more than 4 primary partition.

now create a swap parition of 2 GB, another 8 GB partition for root and remaining for home. all your setting and other details reside in home partition so even if you have to delete root your setting/files would be still there when you reinstall the os or any other distro... that is one of the beauties of linux :-)..

now install and select manual partition and select 2 GB as swap, 8 GB as / and remaining 12 GB as /home.

i think compiz fusion should work... using xgl i think...

---

### Post by LanDan on 2007-10-22
i think all will go fine if you follow above,

2gb of swap is alot i think altough it will not hurd it won be usefull either.
you might as well make that 512MB since you will never use that

---

### Post by Sef on 2007-10-22
> now install and select manual partition and select 2 GB as swap, 8 GB as / and remaining 12 GB as /home.

Swap shouldn't be bigger than 1 GB.  If you need 2 GB swap, then get some more ram,

---

### Post by prince_niceguy on 2007-10-22
you will require more than the amount of your ram to enable hibernate... please correct me if i am wrong. and if you are like me running some servers/ ide then you will require lot of swap... it wont hurt to have more swap even if it remains unused as in case you host some application which require more swap then you will end up creating a swap file which is slower in access compared to a separate partition.

---

