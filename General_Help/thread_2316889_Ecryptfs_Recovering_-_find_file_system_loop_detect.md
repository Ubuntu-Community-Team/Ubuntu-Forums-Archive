---
title: "Ecryptfs Recovering - find: file system loop detected"
date: 2016-03-11
forum: General Help
---

### Post by dennker6 on 2016-03-11
Hello,

i'm running Ubuntu 14.04 with ecryptfs. Everything works fine; however as i would like to do a backup, i'm trying to mount the encrypted home on another computer with faster USB3.
I do have the password and passphrase, i am able to see the .private folders.

When i connect the HDD and run the ecryptfs-recover command, i get the following error:
```
ubuntu-mate@ubuntu-mate:~$ sudo ecryptfs-recover-private 
INFO: Searching for encrypted private directories (this might take a while)...
find: File system loop detected; `/sys/kernel/debug/pinctrl' is part of the same file system loop as `/sys/kernel/debug'.

```

This is my lsblk (sdc is the encrypted home HDD):

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   300M  0 part 
&#9500;&#9472;sda2   8:2    0    99M  0 part 
&#9500;&#9472;sda3   8:3    0   128M  0 part 
&#9492;&#9472;sda4   8:4    0 209.1G  0 part 
sdb      8:16   1   1.9G  0 disk 
&#9492;&#9472;sdb1   8:17   1   1.9G  0 part /cdrom
sdc      8:32   0 298.1G  0 disk 
&#9500;&#9472;sdc1   8:33   0 296.5G  0 part /media/ubuntu-mate/61acd881-6e9a-49ea-a862-6849
&#9500;&#9472;sdc2   8:34   0     1K  0 part 
&#9492;&#9472;sdc5   8:37   0   1.6G  0 part 
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0     1G  1 loop /rofs

```

Googling has lead to serveral posts telling other people to google, but i've been trying for days with no result. Anyone able to help me out? 

Thank you a lot in advance! :smile:

---

