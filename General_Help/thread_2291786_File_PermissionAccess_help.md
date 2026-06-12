---
title: "File Permission/Access help"
date: 2015-08-22
forum: General Help
---

### Post by james139 on 2015-08-22
I've created a partition called 'Shared'. I have no permissions on it as yet and want to set it so all users can read/write to it as they wish, but don't really know where to start. I tried chmod 777, but I'm doing something wrong; I'm the only one who can access it.

---

### Post by XBNCPRk on 2015-08-22
Are these local or remote users? 

How is your fstab mounting it, or are you attempting to use something like udisks or a script to mount the partition?

---

### Post by james139 on 2015-08-22
Sorry, local users. I edited fstab to mount it permanently/on startup.

---

### Post by yancek on 2015-08-22
Is your Shared partition a Linux filesystem?
You didn't post your fstab entry so there is no way anyone can advise you on its accuracy.
Usually, you would add the users you want to a group then give that group write permissions.  Doing a chmod 777 is a bad idea as anyone then has the ability to delete anything on the partition.

---

### Post by james139 on 2015-08-23
Hi yancek, Yes the file system is ext4. This is what I added to fstab:

> UUID=e12bb62a-17f7-4fdd-b8ee-932470e2ca9c /media/james/Shared ext4 defaults  0     2

---

### Post by Morbius1 on 2015-08-23
> UUID=e12bb62a-17f7-4fdd-b8ee-932470e2ca9c /media/james/Shared ext4 defaults  0     2
*** Create a new mount point at /media/Shared.

*** Unmount the partition:
```
sudo umount /media/james/Shared
```
*** Change the fstab line to reflect this new mount point:
```
UUID=e12bb62a-17f7-4fdd-b8ee-932470e2ca9c /media/Shared ext4 defaults  0     2                      

     
 

```
Remount with this:
```
sudo mount -a
```

The /media/$USER folder ( /media/james in your case ) is under the control of an Access Control List ( acl ) imposed by the system that prevents anyone other than $USER ( james ) from gaining access to anything under it - regardless of what permissions are set. Moving the mount point one level higher gets you away from the acl.

---

### Post by james139 on 2015-08-23
Thanks Morbius, worked a treat :)

---

### Post by james139 on 2015-08-23
So with that in mind, if I want to create any personal partitions for other users, I can just create a mount point under the username and they'll be unaccessible to all other users?

---

### Post by Morbius1 on 2015-08-23
You could but "best practice" is to never permanently mount anything under /media/$USER. That is where the system automounts external devices and you may end up in a situation where there is a conflict between that and a defined mount.

It would be better to create the mount point in one's home directory for example and then change permissions after the mount that would prevent access from everyone else.

So you would create say ... /home/morbius/mountpoint
Mount the partition to that mount point.
Then change permissins to prevent anyone else access:
```
chmod 0770 /home/morbius/mountpoint
```

---

### Post by james139 on 2015-08-23
Brilliant thanks, just done another partition like that, worked first time :)

 In the fstab UUID line, what do the 'default' and '0' and '2' signify exactly?

---

### Post by Morbius1 on 2015-08-23
You need to get acquainted with what will become your BFF - the man command:
```
man mount
```
From that you will see that defaults:
> defaults
              Use default options: rw, suid, dev, exec, auto, nouser, and async.
And from:
```
man fstab:
```
> The fifth field (fs_freq).
              This field is used for these filesystems by the dump(8) command to determine which filesystems need to be dumped.  If
              the fifth field is not present, a value of zero is returned and dump will assume that the filesystem does not need to
              be dumped.

       The sixth field (fs_passno).
              This  field is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time.
              The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a  fs_passno  of  2.
              Filesystems  within  a drive will be checked sequentially, but filesystems on different drives will be checked at the
              same time to utilize parallelism available in the hardware.  If the sixth field is not present or zero,  a  value  of
              zero is returned and fsck will assume that the filesystem does not need to be checked.



---

### Post by james139 on 2015-08-31
So if I changed the 2nd  0 to 1 on sda3 (my home partition), it would be checked on startup?

---

### Post by Morbius1 on 2015-08-31
A "1" is usually reserved for the root partition where your OS is installed. A "2" is usually used for all other partitions formatted to a linux filesystem.

Either one will cause the system to do a fsck on boot. Not necessarily the very next boot and certainly not on every boot.

---

