---
title: "Understanding of commands to increase use of RAM"
date: 2013-11-25
forum: General Help
---

### Post by joan_carles2 on 2013-11-25
I've just found a post that explains how to maximize use of RAM. The way to do it is write next commands in /etc/fstab:

tmpfs  /dev/shm  tmpfs  defaults           0  0
tmpfs  /var/log    tmpfs  noexec,nosuid  0  0
tmpfs  /tmp         tmpfs  noexec,nosuid  0  0
tmpfs  /var/tmp   tmpfs  noexec,nosuid  0  0

Seems that this commands store all the content of (/dec/shm, /var/log, /tmp, var/tmp) to the RAM memory.

So some of the adavande that you have is increase the speed and enlarge the life of your hard disk.

Doesn anyone know the meaning of the commands introduced in the fstab. There are many command like tmpfs, noexec, nosuid that I don't have any idea what they do.

---

### Post by ajgreeny on 2013-11-25
Here's the fstab info you want.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I think those extra lines put hose temporary files into ram rather than into /tmp and /var etc etc.

---

### Post by joan_carles2 on 2013-11-26
Thks. So the idea is:

[Device]: tmpfs    (**We normaly put Position that starts the mounting point... So what means tmpfs??** )
[Mount Point]  /dev/shm
[File System Type] tmpfs  (**I don't understand it because we normally should put ext4, ntfs, swap ,etc.. What is the meaning of tmpfs**)
[Options] defaults
Dump 0
Pass 0

and 

[Device]: tmfs
[Mount Point]  /var/log
[File System Type] tmpfs
[Options] noexec,nosuid 
dump 0
PAss 0

Thks

---

### Post by ajgreeny on 2013-11-26
tmpfs means "temporary file system", hat is to say, a filesystem that is made at boot and disappears when you shutdown therefore losing all the files that were in it.

---

### Post by efflandt on 2013-11-26
You likely do NOT want to use tmpfs for /var/log, because then if you have a hang, crash, or other problem, once you shutdown or reboot any logs written to tmpfs (in RAM) will not exist.

Although, tmpfs for /tmp is the default for live/install iso on USB memory and possibly a good idea if using SSD (to minimize writes), if you do anything that uses a large amount of /tmp (like rip DVD, making an iso, etc.) you may want to use actual disk space for /tmp at that time. Although, if you have enough swap it may use that if it needs it for too much tmpfs.

---

### Post by joan_carles2 on 2013-11-27
So

The mounting point is a temporary file system. And this temporary file system is the RAM memory,
Then second command we indicate what we want to mount in the temporary file system (for example /var/tmp)
and the file system type is tmpfs i guess because if you store in the ram it isn't neither ext2, ext3 nor ext4

I will appreciate if you can confirm this data. Then I can start testing if works. I really think that the performance will be the same but I want to test what happens.

---

