---
title: "2nd Partition on USB mounted as root not my userID"
date: 2014-02-02
forum: General Help
---

### Post by karl9 on 2014-02-02
Hi All,

I have two partitions on a USB drive, one has a FAT32 filesystem that other is EXT4. 

The problem is that when it is auto-mounted the FAT32 is mounted at /media/karl/SEAGATEWIN and owned by user karl (This is what I want  so I can add files etc) 

[B]BUT the EXT4 partition is mounted at /media/karl/SEAGATEEXT4 but owned by root

How can I get it to mount and be owned by my user automatically too?[/B]

```

root@box:~# gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.7


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 1953525167 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3CBDBA94-B533-4E20-933B-6733533D03F7
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525133
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        41945087   20.0 GiB    0700  Microsoft basic data
   2        41945088      1953525133   911.5 GiB   8300  Linux filesystem

```

```

root@box:~# ls -ld /media/karl/SEAGATEWIN/drwx------ 7 karl karl 16384 Jan  1  1970 /media/karl/SEAGATEWIN/
root@box:~# ls -ld /media/karl/SEAGATEEXT4/
drwxr-xr-x 3 root root 4096 Feb  3 11:26 /media/karl/SEAGATEEXT4/

```

Cheers

Karl

---

### Post by tfrue on 2014-02-03
I would say you would have to edit the *fstab* file to allow users to mount, then we would have to override the default entries.

Here is a great site for editing the fstab file:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

In short, we would want something that looks like,
```

/dev/sdb2 /media/karl/SEAGATEEXT4 ext4 user,exec,suid,dev,rw, 0 0

```
This will mount /dev/sdb2 at /media/karl/SEAGATEEXT4 with the FS as ext4 with the options of **user**(To allow any user to mount this), **exex**(To allow execution of binaries),**suid**(To allow suid and sgid bits),**dev**(To allow Interpret character or block special devices on the file system),**rw**(To allow Read Write) with a dump and pass of 0.

Hope that helps!
Chris

---

### Post by karl9 on 2014-02-03
HI Chris, thanks for the response I'll try that soon, (when I've stopped working :-) 

The thing that confuses me though is why do I not have to have such a similar entry for /dev/sdb1 which automatically mounts and is owned by me? 

Is there something clever happening in the udev or something?

Any ideas?

Cheers
Karl

---

### Post by tfrue on 2014-02-03
We we mount a FS in linux, we have to be the super user, so that means when the command '*sudo mount /dev/sdb1 /media/blah/blah*' the user *root* is actually mounting the drive. There are such things as *pmount* that will allow a normal user to mount, but I would stay away from that. 

We edit the *fstab* file to allow users to mount the drive so you can mount the drive as a normal user.

You might be able to type:
```

sudo chown karl.karl /media/karl/SEAGATEEXT4
```
After the drive is mounted to see if you can change ownership to you, and I'm not really sure why you are able to mount the WIN mount and have the user.group as karl...

Will you post the commands you used to mount the drives?

Thanks,
Chris

---

### Post by oldfred on 2014-02-03
Usually you do not automount external drives with fstab as external may not be there when rebooting. It still should boot but may give errors.

Best to set ownership & permissions for your data partition.
 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not copy or type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data


 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by karl9 on 2014-02-03
Hi Chris and Oldfred,

OK maybe I used the wrong word when I said "Automount", and I'm not running any commands, what I mean is that when I plug the external USB disk into my PC the Ubuntu File browser pops up showing me the contents of the two partitions.

If I run mount, I can see that both partitions are mounted at

/media/<userid>/<volname>

I can also see that the first partition is owned by my userid, but the second partition is owned by root. I'm guessing that the hotplug deamon, or whatever is used in ubuntu is chown'ing the mount point of the first partition automatically afer it mounts it, but not the second partition... perhaps there is a udev rule whose regex only spots the first partition?

I'm afraid I don't know enough about Ubuntu to start looking in the right place, but it is annoying, currently I have created a directory in the second partition as root and chowned it to my user, so I can store stuff on that partition.

Any suggestions of where to look?

Thanks

---

### Post by oldfred on 2014-02-03
NTFS partition may show they are owned by root. But permissions & ownership are set as defaults when mounted.

If it is the ext4 partition, you should just mount it and reset ownership & permissions as above.

---

### Post by tfrue on 2014-02-04
I second Oldfred.

---

