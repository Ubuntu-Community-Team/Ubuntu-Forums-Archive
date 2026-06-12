---
title: "Ubuntu filesystem"
date: 2017-05-25
forum: General Help
---

### Post by mwoosley on 2017-05-25
Hello everyone. I've been hitting the lessons hard and have gained significant ground in learning Linux, however, I have hit a small snag.

Right now, I'm working on trying to understand Linux file systems. I have Ubuntu Server 16.04 installed on a physical machine which is operating very smoothly with no issues. What I'm trying to figure out is the acquiring, setting up and using block storage devices. One of my issues that I haven't been able to locate a solution to is how to mount a multi-partition device. That device is currently a 128GB USB drive, partitioned with FDISK into 2 fairly equal partitions. The file system I formatted it with is the ext4 version. Before we go any further, I have not edited the fstab file to allow automatic mounting. I'm trying to manually mount these 2 partitions with the following commands... 
"sudo mount -o defaults /dev/sdd1 /mnt/data" for the 1st partition and 
"sudo mount -o defaults /dev/sdd2 /mnt/data" for the second partition.

Once I completed those commands, I went into command "df -h -x tmpfs -x devtmpfs" to test the mount commands. I was expecting to see...

Filesystem Size Used Avail Use% Mounted on
/dev/sda1 451G 2.8G 425G 1% /
/dev/sdd1 56G 45M 55G 1% /mnt/data # I am going to use this partition/block for my webServer depository
/dev/sdd2 57.7 52M 57.5G 1% /mnt/data # I am going to use this partition/block for my wordPress depositiory

but instead I see...

/dev/sda1 451G 2.8G 425G 1% /
/dev/sdd1 56G 45M 55G 1% /mnt/data

Why isn't the other partition (sdd2) mounted for use?

I appreciate any help or tips to figure this one out... but in the meantime I'm having a blast :p

Thanks in advance,
Mike

---

### Post by mook765 on 2017-05-25
The reason for this phenomenon is that you use the same mount-point (/mnt/data) to mount both partitions, only one partition can be mounted to a folder at a time!

---

### Post by Bucky Ball on 2017-05-26
> **mook765 said:**
> The reason for this phenomenon is that you use the same mount-point (/mnt/data) to mount both partitions, only one partition can be mounted to a folder at a time!

^^^
This. You need something like:

```
sudo mount -o defaults /dev/sdd1 /mnt/data/sdd1
sudo mount -o defaults /dev/sdd2 /mnt/data/sdd2
```

... which would mount the partitions in two mountpoints inside /data, or simpler:

```
sudo mount -o defaults /dev/sdd1 /mnt/data1
sudo mount -o defaults /dev/sdd2 /mnt/data2
```

... with the partitions mounted at /data1 and /data2. Be aware that you need to create the mountpoints in the first instance, for instance:

```
sudo mkdir /mnt/data1
```

... or whatever you're calling the new mountpoint.

The mountpoints in /data don't need to be ssd1 and ssd2. Call 'em what you like. You could also just issue:

```
sudo mount -a
```

... and that *may* mount things 'automagically' in /media/<username>/, where <username> is your username, under the partitions name, probably ssd1 or whatever you've labelled them, or a name of the system's choosing.

---

### Post by mwoosley on 2017-05-26
Thanks mook765!!  With all the studying and testing, it's quite refreshing to get a great answer to add to my notes.

---

### Post by mwoosley on 2017-05-26
Bucky Ball, thanks for tagging onto Mook765 with an example. You guys are great and I appreciate your help :)  In regards to the -a option to mount ALL the drives, this particular situation involved attempt/practice at "temporarily" mounting of drives.  If I'm understanding all this stuff correctly, I'm going to have to add the drives to the 'fstab' file in order to auto-mount at boot or simply using the -a switch to mount all of whenever needed.

Best to you!!

---

### Post by cuthead on 2017-05-26
tmpfs and devtmpfs is the mounted file system,x is exclude,if you want see mounted file system,simply use df to get mounted file system.

---

### Post by Bucky Ball on 2017-05-26
> **mwoosley said:**
> If I'm understanding all this stuff correctly, I'm going to have to add the drives to the 'fstab' file in order to auto-mount at boot or simply using the -a switch to mount all of whenever needed.

Correctly! :)

/etc/fstab to mount at boot, -a switch to mount everything when required. You can also mount an individual device, say sda5, manually to a mountpoint, say /mnt/data3, by a basic command like this one:

```
sudo mount /dev/sda5 /mnt/data3
```

Remember, and you probably know, you need to create the mountpoint /mnt/data3 before you can mount anything to it (see command in my last post). :)

Hope that helps a bit more ...

---

### Post by mook765 on 2017-05-26
Here the relevant information for  *mount -a* from *man mount*
```
-a, --all
              Mount all filesystems (of the given types)  mentioned  in  fstab
              (except  for those whose line contains the noauto keyword).  The
              filesystems are mounted following their order in fstab.
```

---

### Post by Bucky Ball on 2017-05-26
And there you go. That appears to state that mount -a will only mount whatever is in the fstab, so you will need to create those entries manually (although, whatever is in fstab should have been mounted at boot, so maybe I'm misinterpreting).

We can give you a hand with the fstab edit, but you will need to provide the exact details of what you want where if you need one. ;)

Here is an example from my fstab:

```
# /dev/sdb10 Data
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1 /mnt/storage    ext4    errors=remount-ro       0       1
```

This explains a lot. The first line beginning with # is a comment. It is not used by the system, just reminds me. Anything that has # in front is ignored by the system.

The UUID number is the number that equates to the /dev/ device. For instance, that UUID is for /dev/sdb10 in my system. You can find UUID numbers with this command.

```
sudo blkid
```

Find the UUID number of the device you want mounting at boot. In the above example, sdb10, as represented by the UUID number, is being mounted at /mount/storage. I hope that helps and makes some sense. :)

---

### Post by mwoosley on 2017-05-27
Yes, these answers and tips are very useful and allow me to update my notes/cheatsheet.

Thanks for everything ;-)

---

