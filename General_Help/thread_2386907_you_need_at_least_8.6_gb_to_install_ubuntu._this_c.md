---
title: "you need at least 8.6 gb to install ubuntu. this computer has only 0.0b"
date: 2018-03-12
forum: General Help
---

### Post by auroraofdawn on 2018-03-12
Hello, I recently installed Ubuntu and it was working fine but decided I wanted to change my computer name. 

Figuring it was a fresh install it would be easier to just reinstall Ubuntu and rename that way.

 My second installation came back with "you need at least 8.6 gb to install ubuntu. this computer has only 0.0b" 

I am running a gateway with 
Memory 3.7
 Processor intel Pentium (r) cpu b960 @2.20ghz x 2
Os type 64 bit
Disk 2.0 Gb (though 488 originally)

Try Ubuntu works fine.

Thanks in advance.:confused::confused:

---

### Post by speartip on 2018-03-12
Looking at the specs you have posted, your disk is only 2.0GB (though 488 originally)??? No operating system will install on a space that small.

---

### Post by yancek on 2018-03-12
Which installation option did you use?  Is Ubuntu the only OS and is it using the entire disk?  Boot up and Try Ubuntu and at the Desktop, open a terminal and run the command

```
sudo fdisk -l
```

Lower Case letter L in the command, post the output here as it will show drive/partition information.

---

### Post by auroraofdawn on 2018-03-12
I installed ubuntu only on the first and second installation. The first installation was fine. I wanted to change the compute name, I should have just changed the computer name but thought it easier just to reinstall, I was very wrong.:mad:

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.5 GiB, 1564921856 bytes, 3056488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ubuntu@ubuntu:~$

---

