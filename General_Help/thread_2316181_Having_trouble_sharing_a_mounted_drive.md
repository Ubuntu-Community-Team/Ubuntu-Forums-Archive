---
title: "Having trouble sharing a mounted drive"
date: 2016-03-05
forum: General Help
---

### Post by Tom_Lombaerts on 2016-03-05
So i have an ubuntu install on one drive,and i have a second, empty hard drive in my system.
What i'm trying to do is to create one giant share of that empty hard drive.
So i mounted the hard drive to a folder, like this: sudo mount /dev/sdb1 /media/Tom
The problem is now, that when i try to share it, it doesn't get persmission, i've tried mounting the drive to folders in my documents, but it straight up won't even detect those folders.

---

### Post by TheFu on 2016-03-06
Welcome to teh forums.

For storage that will be shared over the network, make certain that local file permissions are working the way you need first.  Also, I'd mount the storage using the /etc/fstab.  I suspect the permissions on the new storage are that you haven't opened up for non-root users.  Also, which file system does this new disk have?  Which **mkfs** command did you use?  Storage on a Linux machine should probably be ext4.

BTW, you didn't say how you wanted to share it - NFSv4, sshfs, something else? What OS are the client machines running?

---

