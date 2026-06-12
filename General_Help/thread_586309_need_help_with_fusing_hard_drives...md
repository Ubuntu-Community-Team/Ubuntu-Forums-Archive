---
title: "need help with fusing hard drives.."
date: 2007-10-22
forum: General Help
---

### Post by Irti on 2007-10-22
hey... i am new to linux and after 2 months of dual booting windows and ubuntu..i finally decided to do away with xp.....so i had 3 partitions in my 180 gb hard drive......2 were the usual c and d drive in windows and one was the linux partition......the c partition was used by windows....i want to clean up this partition but in gparted it says that my c partition is the boot partition and it also has the bootmgr in it......Along with that there are other files i have no idea about which occupy around 10 gb of the c partition. Some one told me to just delete all of it....but i dont want to screw up my bootmgr and all that....i also wanted to fuse the c and d partition together.....but cant do it in gparted.... pls help...

---

### Post by bit4 on 2007-10-22
Standard warning:
Playing with partitions on a live system without backup can be disastrous, so be very careful and make sure you know what you are doing before jumping in.

Having said that, you need to know first how large each partition is and how much free space there is on it (or, rather, will be on it once you delete all the files you don't intend to have after you are done).

Normally, the Windows partitions (C and D in your case) do not contain anything that Ubuntu needs in order to boot. The boot sequence starts with reading sector 0 of the disk (the MBR), which in turn loads the next stage from the Ubuntu partition, so if you don't have any data files (or maybe Windows font files?) on C and D, you can safely delete everything on them. The fastest way to do this is by just deleting the partitions in gparted.

I never used this particular partition editor, so I am not familiar with its UI. If it refuses to delete partition C because it is a boot partition, you will need to first clear its 'boot' flag.

You will also need to instruct Grub (the boot loader) that you no longer have two boot options, and most likely also change the entry pointing to the Ubuntu partition, because once you delete the other partitions, the Ubuntu partition will have a different number. You can avoid this hassle if you don't delete C and D completely, but instead shrink them to almost zero size (format them or delete all the files on them, then use gparted to make them as small as it will allow).

---

