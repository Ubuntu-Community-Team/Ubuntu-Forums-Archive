---
title: "Dropbox syncing problem because of low disk space on Ubuntu"
date: 2013-02-05
forum: General Help
---

### Post by msk31 on 2013-02-05
Hi everyone! I have had this problem for a while in my workplace. In my workplace, we use Dropbox to sync files with all of the co-workers. Unfortunately, only one computer cannot get Dropbox to synce due to low disk space. The computer has Ubuntu on it, and when I run Disk Utility. I saw that the /home directory was only 3 GB and that is where the Dropbox and Documents folder is located. However, Dropbox needs at least 4.75 GB of free space. I cannot resize the partition, because Ubuntu was not able to locate the package gparted. On this computer, it has Ubuntu 10.10, which is really old. I emptied out the trash and tried to delete files that are taking up a lot of space. I was wondering if I can move to the Dropbox folder to another directory that has a lot of space. I tried to move to the folder to a location that had a lot of memory, but I could not, because it kept saying that the Target is a read-only folder. Here are the sizes of the partitions:
 
[LIST]
[*]/ (dev/sda1)= 25 GB
[*]/boot (dev/sda6)= 999 MB
[*]/home (dev/sda7)= 3 GB
[*]/tmp (dev/sda8)= 3 GB
[*]/usr (dev/sda9)= 3 GB
[*]/var (dev/sda10)= 3 GB
[*]free = 1.2 GB
[*]swap = 795 MB
[*]Extended (Logical Partitions) = 15 GB
[/LIST]I was hoping to just move the Dropbox folder to another location, and do not have to worry that I have to upgrade Ubuntu 10.10 to 11.04. I hope that someone can help me with this problem! I would really appreciate it!!

---

### Post by msk31 on 2013-02-08
I solved the problem. I just had to move it to a directory that had a lot of space and write the permissions for me to write into that directory. Then I had to point Dropbox to that location.

---

