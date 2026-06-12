---
title: "RAID problems"
date: 2006-12-07
forum: General Help
---

### Post by randomphrase on 2006-12-07
OK, so I'm new to Ubuntu. Like what I see so far.

But I'm having problems with Software RAID. Yesterday I got it working, now I've rebooted and nothing is working right. All I can say is mdadm is still installed!

I encountered a problem yesterday with /dev/md0 not being created. I ended up creating it manually using mknod. Today I seem to be having other problems:

```
alastair@pierre:~$ sudo insmod raid1
insmod: can't read 'raid1': No such file or directory
alastair@pierre:~$ cat /proc/mdstat 
Personalities : 
unused devices: <none>
alastair@pierre:~$ ls /dev/md0
ls: /dev/md0: No such file or directory
alastair@pierre:~$ sudo insmod md
insmod: can't read 'md': No such file or directory
alastair@pierre:~$ sudo mknod /dev/md0 b 9 1
alastair@pierre:~$ sudo insmod md
insmod: can't read 'md': No such file or directory
alastair@pierre:~$ cat /proc/mdstat 
Personalities : 
unused devices: <none>
alastair@pierre:~$ sudo insmod raid1
insmod: can't read 'raid1': No such file or directory

```

In a word: HELP! Thanks

---

