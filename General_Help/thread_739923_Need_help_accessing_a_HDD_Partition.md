---
title: "Need help accessing a HDD Partition"
date: 2008-03-30
forum: General Help
---

### Post by 3pinner on 2008-03-30
I partitioned some unallocated space on a hard disk using gparted.
formatted as ext3
mounted it using pysdm.
I can see the mounted drive on my desktop, but cannot copy files to it.
It is a permissions issue. 
Properties shows:
owner: root  create and delete files
group: root  Access files
others: access files

How do I change some of those permissions so I can write to this disk?
It will be used to store system backups.


Thanks!

---

### Post by odiseo77 on 2008-03-30
The easy way (not sure if it'll work 100% because I don't do it this way): Open the partition's mount point as root with ***gksu gnome-open /path/to/the/mount/point***, or simply with ***gksu nautilus***, then, right click on the directory for the mount point and change its permissions under "properties" (**be sure to change the permissions of this partition and not other directory!!**)

The other way: Edit /etc/fstab and add a line like the following at the end of it:

```
/dev/sdXN /mnt/data ext3 defaults,auto,uid=your_username   0      0
```

In the above line, you must change at least three things: 

.- "/dev/sdXN" for yor real partition's device.
.-"/mnt/data" for your partition's mount point
.-"uid=your_username" for your real user name

After you've added that line to your fstab file, remount the partition, and it should work.

---

### Post by 3pinner on 2008-03-30
Thank you for the help.

Here is a copy of this partition from the fstab file

/dev/sdb3      /media/sdb3     ext3         defaults                    0  0  

This partition is on an internal second hard drive.
I did not specifically create a directory as a mountpoint for this partition.
Do I need to correct this?

If I follow the instructions above, should the line from fstab read:
/dev/sdb3     /media/sdb3     ext3    defaults,   auto, my_username   0  0

I have two user accounts, one that I set up when I installed the OS (I assume that is my admin account) and my regular user account.
Which user name should I put under "my_username" and will that allow me to access this drive no matter which account I am logged into?

Finally, what sequence of steps should I have taken to avoid this in the first place??

Thanks for the help!!

---

### Post by 3pinner on 2008-03-30
Sorry to bump.
I'd just like to get this fixed (and maybe learn something from you as well!)

---

### Post by odiseo77 on 2008-03-30
If the directory /media/sdb3 exists, then you don't have to worry about the mount point. The line for this partition on /etc/fstab should be something like this:

```
/dev/sdb3 /media/sdb3 ext3 defaults,rw,user   0      0
```

Note that there aren't spaces between the comma separated values (only commas). Also note that by mounting the partition with these fstab options, any user will have read and write access to it.

---

### Post by 3pinner on 2008-03-30
Wellllllllllllllll........
I'm still having issues.
I edited the fstab file just as you suggested:

/dev/sdb3 /media/sdb3 ext3 defaults,rw,user   0      0

rebooted, the drive appeared on the desktop (mounted) and I still cannot copy files to it.
Permissions denied.
The properties still list permissions as

owner: root create and delete files
group: root Access files
others: access files

Here is the output of the ls-l command for /dev/sdb3:

brw-rw---- 1 root disk 8, 19 2008-03-30 13:09 /dev/sdb3

I guess what I need is help in using chmod (which I havent used before) to change the permissions to this disk.


Sorry to have to post again!

---

### Post by odiseo77 on 2008-03-30
Well, now with the partition mounted, you can change the permissions inside it from the GUI as root; simply open /media with a file manager as root and change the permissions of /media/sdb3 to your like. Being an ext3 partition, the permissions should stick there.

To open the directory as root, open a terminal and type ***gksu gnome-open /media*** and then right click on /media/sdb3 , go to the "properties" tab and change its permissions to your need (or if you're on kde, you must type ***kdesu konqueror /media***).

Greetings.

---

### Post by 3pinner on 2008-03-30
OK!
that's what I was looking for.
As for changing the permissions (I was just looking for infomation on this) What is the best general policy for allowing  access 
What group should I allow?  (plgdev?? users??)
what setting for "others" should I allow? (create and delete files / read and write??)

---

### Post by odiseo77 on 2008-03-30
It depends on what you want, but since you want your two users to have access to this partition, you can set the group to *users* (with read and write access, or with read only access, depending on what you need), and in the "others" field, you could either leave it as it is by default (read only), or you could even set the permission to "none" (so only root and your two users have access to the partition). Oh, and don't forget to press the "Apply permissions to the files inside" button (or something like that; the button at the bottom of the permissions properties window); this will set the permissions recursively to the files and folders inside.

Greetings.

---

### Post by 3pinner on 2008-03-30
Thanks for the help.
I had set up the permissions similar to your suggestions before you replied, and was able to copy my backup to the new partition.
thanks for your patience!

---

