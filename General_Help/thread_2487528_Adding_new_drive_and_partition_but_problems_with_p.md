---
title: "Adding new drive and partition but problems with permissions"
date: 2023-06-07
forum: General Help
---

### Post by mason64 on 2023-06-07
Hi 

I have added a new drive to my rasberry pi running ubuntu 23.04 server

i have managed to delete old partitions, create a new partition with gdisk, format disk and mount SDA1 disk to /mnt/ssd1 

It works fine but i have to sudo to do anything in that partition is this down to permissions?

 drwxr-xr-x  3 root root 4096 Jun  7 15:40 ssd1/

i am running as a user called username, username part of the sudo group. do i need to make username part of the root group? i will only ever have 2 maybe 3 users on this server that will need to access that hard drive. 

Thanks and sorry if its a n00b question 

Thanks

---

### Post by Holger_Gehrke on 2023-06-07
Yes, its due to permissions. Lets take a look:

drwxr-xr-x  3 root root 4096 Jun  7 15:40 ssd1/

That's file type d for directory. The first group of the characters after that (rwx) means that the owning user is allowed to read, write, and execute (execute ? not really. For directories the 'x' means 'is allowed to set this directory as current working directory). The next three show the permissions for group: read and execute. Everyone else (not the owner or the group) can read and execute. There are three hard links (aka names) for this directory. It's owned by root and associated with the group root. Date of last change and name of the file follow.

Now you can either change the permissions and allow everyone to write ('sudo chmod o+w /mnt/ssd1'; not a good idea for security reasons) or transfer ownership ('sudo chown username /mnt/ssd1'). If you are alone on that machine that would be it.

But since you said there will be 2 or 3 users, it's probably best to create a new group ('sudo addgroup allowedonssd1'; you can give the group any name you want ...), add yourself and those users to the group ('sudo usermod -a -G allowedonssd1 username' for each username), change the group for the directory ('sudo chgrp allowedonssd1 /mnt/ssd1') and allow the group to write ('sudo chmod g+w /mnt/ssd1').

Holger

---

### Post by mason64 on 2023-06-07
brillant 

Thank you i thought that was the case but didnt want to break anything if i was wrong. 

Thank you very much Holger for the help.

Asked 2 questions in two days now and both have been answered perfectly. Great forum! and great users.

o also just an edit -

thought it wasnt working but i had to log out and back in after adding myself to the group is that normal practice?

Thanks
Dave

---

### Post by TheFu on 2023-06-07
For new storage that is mounted and has a Linux file system (not NTFS/exFAT/fat32), then changing the owner and/or group would be required almost always.  After all, new storage usually isn't only to be used by root, right?  This is normal, standard, permissions stuff on every Unix-like system in the world.

Of course, if you mount the file system someplace specific to the OS, then the user+group and permissions will need to make sense for that specific location.
Remember, storage has these layers, at a minimum:
```
file system
   partition
       disk
```
We mount file systems, not partitions and definitely not disks.

With more advanced volume management, file systems can become more abstract than a partition.  Still, we mount the file system, not the abstract thing where the file system is places (which can be any "file", BTW).

---

### Post by mason64 on 2023-06-08
Thanks to both for the help.

---

