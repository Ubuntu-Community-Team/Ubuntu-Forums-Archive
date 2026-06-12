---
title: "Can't unmount device: umount: /mnt/Windows: device is busy"
date: 2007-07-09
forum: General Help
---

### Post by miLl3niUm on 2007-07-09
To mount my ntfs drive I type:
```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/Windows
```

But now I can't unmount it:
```
alter@millenium:~$ sudo umount /mnt/Windows
Password:
umount: /mnt/Windows: device is busy
umount: /mnt/Windows: device is busy

```

---

### Post by eggdeng on 2007-07-09
Have you tried ```
sudo umount /dev/sdb1
```

---

### Post by miLl3niUm on 2007-07-09
It shows the same thing (device busy)

---

### Post by smoker on 2007-07-09
hi, if the partition won't unmount, maybe you have a file relating to that partition still open, or a read / write cycle is still ongoing. if you are sure this is not the case, you could to try to force umount by apending -f after the mount command, though bear in mind you may lose data if  the partition is still being used!

---

### Post by eggdeng on 2007-07-09
Try ```
ps -A
``` to see if you can identify what process might be using the NTFS partition. Then kill <pid> to stop it.

---

### Post by miLl3niUm on 2007-07-09
Is it possible to be VirtualBox?

---

### Post by eggdeng on 2007-07-09
Kill it and see. If you can't exit it normally, either use the kill command with the process id shown by ```
ps -A
``` or do ```
killall virtualbox
``` The worst that can happen is nothing at all.

---

### Post by miLl3niUm on 2007-07-09
I use Xfce 4 Task Manager. I'll do it tomorrow and tell you what happened, thank you.

---

### Post by Mr. C. on 2007-07-09
This isn't Windows - don't try random approaches or killing random processes.   Use the tools that help you.

Run:

```
lsof | grep '/mnt/Windows'
```

to see a list of processes that have an open file or directory within that file system.

Any processes that :

[LIST]
[*]started with a working directory in that file system
[*]  have open files in that file system
[*]  have a working directory in that file system
[/LIST]

are possibilities.  Usually, it is just your shell, because you have **cd**'d into one of the file systems subdirectories.

MrC

---

### Post by miLl3niUm on 2007-07-10
Problem solved. Thank you Mr. C. :)

---

### Post by sparklejess on 2008-02-10
Thanks Mr C!  That's just solved a problem I had with a CD that was refusing to unmount.

---

### Post by Nakarti on 2008-03-15
My situation once your suggestions gave me more thoughts:
Services running dependent on the filesystem such as NFS and SaMBa
Files mounted loopback from within the filesystem(like an install CD image)

---

### Post by _Jo_ on 2008-03-27
> **Mr. C. said:**
> ... are possibilities.  Usually, it is just your shell, because you have **cd**'d into one of the file systems subdirectories. 

Argh. Thanks Mr. C. 
I must be having a slow morning.

---

