---
title: "second harddisk ubuntu server 12.04"
date: 2013-01-17
forum: General Help
---

### Post by Amfibee on 2013-01-17
Hey there everyone,

I'm pretty new in the world of Linux and just started with Ubuntu server 12.04.
I thought that during the installation proces of US 12.04,  the 2nd harddisk also was prepared for linux but I was wrong.
With the help of Google I was able to create a Linux formatted disk to /sdb1
But now my question; I want to use this disk as download storage for sabnzbdplus but I can't access /sdb1. For example; sabnzbd uses a nzb watch folder. I would like to create one on /sdb1 but access is not possible.
Is there a step by step procedure for preparing my second harddrive /sdb1 so that it is visible and useable, also in my network? Because I think that somewhere with the help of Google something went wrong. I'm a real noob with Linux so every tip is welcome.

Searching thru this forum is not an option because there are so many threads that I need at least a couple of days time to read. I'm sorry about that.

Grz mark

---

### Post by dannyboy79 on 2013-01-17
how are you mounting sdb1? open a terminal session and enter the following command and paste back the results.

```
mount
```

also, paste back the results of your /etc/fstab file by issuing the following command
```
cat /etc/fstab
```

---

### Post by Amfibee on 2013-01-17
Thx for the quick response!


> **> mount** /dev/sda1 on / type ext4 (rw,errors=remount-ro) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) none on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) cgroup on /sys/fs/cgroup type tmpfs (rw,relatime,mode=755) cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset) cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu) cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct) cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory) cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices) cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer) cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio) cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
```
**> cat /etc/fstab** # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda1 during installation UUID=e7dde52d-a7ff-4788-af7c-900a861b5ec7 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda5 during installation UUID=fbbb494b-8bba-498c-beed-dd59b72e0d5d none            swap    sw              0       0 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Amfibee on 2013-01-17
And now the correct code :p

```
**> mount** /dev/sda1 on / type ext4 (rw,errors=remount-ro) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) none on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) cgroup on /sys/fs/cgroup type tmpfs (rw,relatime,mode=755) cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset) cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu) cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct) cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory) cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices) cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer) cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio) cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
```


```
**> cat /etc/fstab** # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda1 during installation UUID=e7dde52d-a7ff-4788-af7c-900a861b5ec7 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda5 during installation UUID=fbbb494b-8bba-498c-beed-dd59b72e0d5d none            swap    sw              0       0 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by ARMac on 2013-01-17
I would advice against using /dev/sdx , use UUID instead.

paste the output of 

```
#sudo blkid
```

And you will get the UUID for the second hdd.
Then you will have to add the line to /etc/fstab

This is an example how it should look like
```
UUID="xxxxxxxxxxxxxxxxxxx" /mnt/mount-point fs-type defaults 0   0
```

---

### Post by dannyboy79 on 2013-01-17
you pasted them horribly hard to read BUT from what I can tell, your second hard drive isn't even mounted. So first you need to create a folder where you will mount it. I usually create a folder within either /media/ or /mnt/ BUT it's totally up to you.
if it's NOT in your users home directory, you'll need to use sudo. so for example
```
sudo mkdir /mnt/sabnzbdplus
```
once the folder is there, you'll need to change it's owner and group and what permissions you want it to have. so if your username is mark, then this is how you would change the folders username and group to mark
```
sudo chown mark:mark /mnt/sabnzbdplus
```
then to change it's permissions to read write execute for owner and group and just read/write for others it would be this
```
sudo chmod 776 /mnt/sabnzbdplus
```
then you want to mount the /dev/sdb1 partition to that folder, best way is to find out the partitions UUID, using the following
```
ls -la /dev/disk-by-uuid/
```
(i think that's the command, let me know what that returns.

---

### Post by Amfibee on 2013-01-17
Sorry about the bad pasting, its really a mess.
Even with that i'm a noob :) 

I will try yoyr advise dannyboy79, thx!

---

### Post by dannyboy79 on 2013-01-17
users coming from windows have trouble grasping the concept of directory structure and "mounting" partitions/hard drives. completely forget about C drives and D drives etc etc. 

so you basically "mount" a partition to a folder, which then makes that folder show the contents of that partition that is mounted there. so currently you have /dev/sda1/ mounted to the "root" location, which is /
the partitions UUID is e7dde52d-a7ff-4788-af7c-900a861b5ec7. so /dev/sda1 is a partition of data which has a bunch of folders in it, you can see them by issuing
```
ls -la /
```

and that will list all the contents of /dev/sda1, which there is obviously folders and files. So if you want to "mount" another partition or hard drive to be able to write to it, you need a folder to mount the partition/hard drive to. you do that with the /etc/fstab file. we'll do that after you tell me what the /dev/sdb1 UUID is and what filesystem you formatted it as. probably ext4? we'll give it mount options to allow it be accessed.
Good luck

---

### Post by Amfibee on 2013-01-17
Ok, here's the UUID of sdb1:

 ```
/dev/sdb1: UUID="a3f8f772-9f3e-4d9b-b3fb-2f95731910bb" SEC_TYPE="ext2" TYPE="ext3" 
```

---

### Post by Amfibee on 2013-01-17
I used the 
sudo blkid 
code to find the UUID as ARMAC described. Thx for that!

The code 
ls -la /dev/disk-by-uuid/ 
didn't work, the file or directory doen not excists

---

### Post by dannyboy79 on 2013-01-17
ok, did you do all the other steps with whatever folder you want to mount the partition to? if so, assuming you following my examples then edit your /etc/fstab file using the following
```
sudo nano /etc/fstab
```
then add a line like this
```
UUID=a3f8f772-9f3e-4d9b-b3fb-2f95731910bb               /mnt/sabnzbdplus                     ext3    defaults        1 1
```

then control and x to exit but read the bottom for saving the file. then issue the following so the system re-reads the fstab file
```
sudo mount -a
```

---

### Post by Amfibee on 2013-01-17
Ok I followed your steps in post #6 and your latest #11.
Should it work now?

---

### Post by dannyboy79 on 2013-01-17
> **Amfibee said:**
> Ok I followed your steps in post #6 and your latest #11.
Should it work now?
you can check by issuing the following command
```
df -h
```
and it will show each folder and how much space it has
also the mount command should now list /dev/sdb1 being mounted to /mnt/sabnzbdplus

---

### Post by Amfibee on 2013-01-17
Okay the 2nd disk is now mounted and I can see the sabnzbdplus folder also in sabnzbd! 

Great job and thanks a lot for your help Dannyboy79!!

---

### Post by dannyboy79 on 2013-01-17
glad you got it working, use the thread tools (upper right) to mark it as solved.

---

### Post by Amfibee on 2013-01-20
Nil

---

