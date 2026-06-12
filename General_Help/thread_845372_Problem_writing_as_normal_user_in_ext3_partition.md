---
title: "Problem writing as normal user in ext3 partition"
date: 2008-06-30
forum: General Help
---

### Post by Dr. Falken on 2008-06-30
Hi,

I'm having trouble to mount and use for R+W as normal user an ext3 partition (/dev/sda1) in my 8.04 i386 installation.

Here's a footprint about partitions:

```

root@wopr:~# fdisk -l /dev/sda

Disk /dev/sda: 145.9 GB, 145999527936 bytes
255 heads, 63 sectors/track, 17750 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+  83  Linux
/dev/sda2            2491        2988     4000185   82  Linux swap / Solaris
/dev/sda3            2989        5478    20000925   83  Linux
/dev/sda4            5479       17750    98574840   83  Linux

```

Their UUIDs:
```

root@wopr:~# blkid
/dev/sda1: UUID="c31004fa-e110-4ac3-8069-ff0131b2871c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="ceae1385-3423-453c-ae23-12a59bc67304" 
/dev/sda3: UUID="abcd54ee-87b6-4e9d-b523-ce6333ce272b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="399f48a6-3b43-4da8-a216-8fd77868c0eb" SEC_TYPE="ext2" TYPE="ext3" 

```

Here's the fstab status
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                            /proc          proc         defaults                      0  0  
# /dev/sda3
UUID=abcd54ee-87b6-4e9d-b523-ce6333ce272b       /              ext3         defaults,errors=remount-ro    0  1  
# /dev/sda4
UUID=399f48a6-3b43-4da8-a216-8fd77868c0eb       /home          ext3         defaults                      0  2  
# /dev/sda1
UUID=f36431f1-2e28-4b13-a1e1-df8152f4204e       /media/sda1    ext3         defaults                      0  2  
# /dev/sda2
UUID=ceae1385-3423-453c-ae23-12a59bc67304       none           swap         sw                            0  0  
/dev/scd0                                       /media/cdrom0  udf,iso9660  user,noauto,exec              0  0  
/dev/scd1                                       /media/cdrom1  udf,iso9660  user,noauto,exec              0  0  

```


And a footprint of my /media:
```

root@wopr:~# ls -l /media/
total 12
lrwxrwxrwx 1 root root    6 2008-01-07 17:45 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-01-07 17:45 cdrom0
drwxr-xr-x 2 root root 4096 2008-01-07 17:45 cdrom1
drwxr-xr-x 2 root root 4096 2008-06-30 15:00 sda1

```

And I also tried to change the Authorizations for users (see attached screenshot), but it doesn't helped, so, i rollbacked them to the defaults.

Using the authorizations and the Storage Device Manager (pysdm), i can only get to my normal user mount the drive, but the user doesn't have any Write access.

Any suggestions will be highly appreciated, and if you need additional data to this, ask for it. I'll try to post it ASAP.


Thanks in advance



Sergio

---

### Post by justleen on 2008-06-30
I would normally just change the owner/group, personally.

```
 chown -R username:username /media/sda1 
```

---

### Post by Dr. Falken on 2008-06-30
> **justleen said:**
> I would normally just change the owner/group, personally.

```
 chown -R username:username /media/sda1 
```

This worked, but i didn't want my normal user owns this directory. By the way, i skipped this because I've tried to do this from Nautilus (gksudo nautilus) without success.

by the way, thanks a lot!

---

### Post by vanadium on 2008-06-30
I would leave it to the root to manage mounts and own mount points. My policy to handle permanently mounted ext3 partitions:

* create a directory on the ext3 partition
* make a user owner of that directory
* create a symbolic link to that directory in the home dir of the user.

This way, the user does not have to worry about where the partition is mounted. He just can access the storage from within his home directory.

Added benefit: flexibility if you have multiple users. Just create another directory for another user. Or yet another directory for a group of users, etc.

---

### Post by chrisccoulson on 2008-06-30
I'm actually slightly confused about what is mounted under /media/sda1. The UUID in your /etc/fstab doesn't match any found by blkid. According to blkid, the UUID for /dev/sda1 is completely different.

---

### Post by vanadium on 2008-06-30
Thus it will probably be sufficient to update the UUID for sda1 in /etc/fstab with the correct uuid of sda1 to have the volume properly mounted.
```

# /dev/sda1
UUID=f36431f1-2e28-4b13-a1e1-df8152f4204e       /media/sda1    ext3         defaults                      0  2  

```

should be changed to

```

# /dev/sda1
UUID="c31004fa-e110-4ac3-8069-ff0131b2871c"       /media/sda1    ext3         defaults                      0  2  

```

Before you make the change, issue the command

```

sudo mount -a

```
This will probably give an error message about a partition that is not found. If /etc/fstab is correct, this command does not produce any output.

---

### Post by chrisccoulson on 2008-06-30
Before you make the change, just make sure that vol_id is the same as the output from blkid. Have a look at:
```
sudo vol_id /dev/sda1
```

---

