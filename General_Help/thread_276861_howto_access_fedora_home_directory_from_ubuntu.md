---
title: "howto access fedora home directory from ubuntu"
date: 2006-10-13
forum: General Help
---

### Post by ubuntwo on 2006-10-13
I have two hardisks one IDE and another SATA. I dual boot from the SATA drive with XP and ubuntu (dapper). The IDE drive has Fedora FC5. FC5 doesnt boot after I changed my motherboard. I need to backup the data in fedora home directory onto the SATA drive. 

After booting ubuntu I was able to mount the Fedora partition with "sudo mount -t ext3 -w /dev/hda9 /mnt/fc5/". After that I am not able to cd to my home directory. I see a "permission denied" message.

The directory permissions are as below

raja@mane:/mnt/fc5$ ls -ld /mnt/fc5/home/
drwxr-xr-x 3 root root 4096 2006-04-24 00:18 /mnt/fc5/home/
raja@mane:/mnt/fc5$ ls -ld /mnt/fc5/home/raja/
drwx------ 56 500 500 4096 2006-07-24 23:38 /mnt/fc5/home/raja/

This is my first posting . Please excuse me if I am in the wrong forum or asking a question already answered (although I googled a lot). Thanks

---

### Post by skierkegaard on 2006-10-13
You need some more permissions for your home folder.

sudo chmod 755 -R /mnt/fc5/home/raja/

---

### Post by ubuntwo on 2006-10-13
yippie:D . It works. Thanks a ton !!!!

---

