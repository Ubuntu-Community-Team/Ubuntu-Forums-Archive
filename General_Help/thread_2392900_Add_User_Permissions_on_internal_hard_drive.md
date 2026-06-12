---
title: "Add User Permissions on internal hard drive"
date: 2018-05-26
forum: General Help
---

### Post by heroquestelf on 2018-05-26
I know this has probably been answered a thousand times, but I can't seem to find the answer. I am trying to modify the read/write permissions on a second hard drive.

First off, I am running Ubuntu MATE 18.04 LTS. I have a Intel Core i5-4460 CPU @ 3.2 GHz. 

That all done... I have two internal hard drives in my computer. When **I **log into the system I can see the hard drive fine. However, my wife also has a personal login to the computer, and when she logs in, the icon for the second hard drive appears on her desktop, but she cannot access the drive. 

It's listed as /dev/sdb5, and it's UUID is A0A03F80A03F5C4A

> Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 67CC4DAE-1FE7-41BB-BB73-82DC4A5E36EA

Device       Start        End    Sectors   Size Type
/dev/sdb5  2906112 1936320511 1933414400 921.9G Microsoft basic data



My wife needs full read/write permissions for this drive. (Also, my 8 year old son also has a basic user login to the machine, and while I would not mind giving him **read** privileges, I don't want to give him **write** privileges, so I can't make a blanket change to ownership of the drive.)

---

### Post by TheFu on 2018-05-27
You'll need to learn and understand group permissions for this to work.  Work through a permissions tutorial, then spend about 45 minutes with a few terminals open in a set of play-area directories under /tmp/somewhere. Each terminal should have different userids and a mix-match of shared and unshared groups. Play around with permissions. See who can and cannot read,  edit, delete files.  Do the same with directories.  Try all the permissions from 0-7 for each part of the files/directories.  

There is a simple solution and there are more complete solutions that take a little more to setup.
The simple solution is to give each userid their own storage directories on the drive and give them full ownership.  If you want, you can setup quotas, so your son can't use more than XX GB on  that partition.

For full sharing, just follow the normal Unix workgroup techniques. From my training slides:

```
Working Together

1.   Put everyone into the same group.
2.   Create a directory where they can share files.
3.   Make the group on that empty directory have rws permissions

               $ sudo gpasswd -M  user1,user2,user3  ourgroup
               $ mkdir -p /tmp/Workspace
               $ chmod g=rwxs Workspace
               $ ls -l Workspace
                  drwxrws---   owner    group    Workspace/ 
               $ chgrp ourgroup Workspace
               $ ls -l Workspace
                  drwxrws---   owner    ourgroup    Workspace/
```
Your son would not be added to ourgroup if you don't want him to have "write" access. Then just change the directory permissions to be o+rw.

Clear as mud?   Spending the time playing around really does work.  Things should "click" and you'll never have permissions issues again - well - not that you can't fix. On a multi-user system, permissions are very important.

---

### Post by Morbius1 on 2018-05-27
Just some random observations:

>  It's listed as /dev/sdb5, and it's UUID is A0A03F80A03F5C4A
That is the UUID of an NTFS partition so the traditional chown / chmod will not work.

> I have two internal hard drives in my computer. When **I **log into  the system I can see the hard drive fine. However, my wife also has a  personal login to the computer, and when she logs in, the icon for the  second hard drive appears on her desktop, but she cannot access the  drive. 

We also don't know if there is an entry in /etc/fstab that mounts this  partition automatically and where the mount point is located.

If it's mounted at /media/heroquestelf/LABEL Mrs. heroquestelf will never get to LABEL regardless of the filesystem or it's permissions.

---

### Post by yancek on 2018-05-27
The UUID you posted indicates that is a windows ntfs partition so you will likely need to set umask options as indicated in the above post.  Check to see if there is an entry in the /etc/fstab or /etc/mtab files for that partition.  Using umask and other options is explained at the link below.

 [https://askubuntu.com/questions/223016/setting-permission-for-ntfs-partition](https://askubuntu.com/questions/223016/setting-permission-for-ntfs-partition)

---

### Post by TheFu on 2018-05-27
But with the simple needs for 1 group having rwx access to the disk and "everyone else" having read-only access, the  NTFS mount options can be used.  As soon as any other sorts of permissions are needed, it won't work.  NTFS permissions are set for the entire partition, at mount and can't be dynamically changed (easily).

Or reformat the disk to any Linux file system before too much stuff gets put onto it.   Time to check the backups.

I would reformat to ext4.

---

### Post by heroquestelf on 2018-06-10
> Or reformat the disk to any Linux file system before too much stuff gets put onto it.   Time to check the backups.

I would reformat to ext4.

That was actually going to be my next question. I have enough backup space right now that I can wipe and reformat that drive over to a Linux format if that would make the process easier. This hard drive is a hold-over to when the machine was using Windoze Tin.

---

