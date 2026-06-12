---
title: "How to create partitions. QTParted for LFS system"
date: 2006-09-13
forum: General Help
---

### Post by linux_help_vampire on 2006-09-13
I am currently trying to make a LFS system (Linux From Scratch) with my installation of Dapper. I cannot however create partitions on my hard drive using QTParted. I am trying to make a 3gb partition on the hard drive on my machine. I have two hard drives in my PC. One Windows, the other Ubuntu. The Ubuntu drive is set to cable select, because i dont have the slave jumper for it. Hope thats enough information for the diagnosis of my problem. 

If any of you have had past experience with LFS systems, any help or tips would be really appreciated.

Thanks in advance

---

### Post by pravuil on 2006-09-13
Couple of questions to get this thread going.

1) Does QTparted recognize the second hard drive at all? (Just to clarify)

2) Are you running QTparted through LiveCD or do you have Ubuntu already installed and are using qtparted within it?

3) Are you trying to edit an active partition?

4) Have you used other distributions (such as Knoppix) to edit the partitions?

5) Do you have you hard drive write protected? (Doubt you'll have to worry about this, just posting for eventuallity)

BTW, have fun building from source. I understand the thrill of it but I don't envy you one bit. Just one word of advice, it would be better if you installed Ubuntu through the installer but if your going to do it against that advice make sure your Windows partition has been backed up, not to mention your MBR. 

```
dd if=/dev/XXX of=mbr.backup bs=512 count=1
```
XXX being the designation for your harddrive (hda, sda, etc.) Should only work if Ubuntu has already been installed. Not sure if it would work through the LiveCD.

---

### Post by linux_help_vampire on 2006-09-14
Ok here are the answers

1 Yes QTParted does indeed recognise the hard drive. It shows it to me as being the right size with all the proper information 

2 I already have Ubuntu installed on the hard drive

3 Yes i think so

4 Yes I have tried Knoppix to edir the partitions, but to no avail

5 I dont know

Hope this is enough information.

Thanks in advance

---

