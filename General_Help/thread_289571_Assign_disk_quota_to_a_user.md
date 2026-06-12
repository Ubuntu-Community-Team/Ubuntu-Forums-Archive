---
title: "Assign disk quota to a user?"
date: 2006-10-31
forum: General Help
---

### Post by Johnsie on 2006-10-31
Hi, I would like to assign 30gb to user "johnsie" so that he can only have 30gb of stuff to the disk. I've heard you can do this using a package called quota. Can anyone out there tell me in detail how to do this using quota or any other program? 

Thanks alot in advance, 
Johnsie

---

### Post by Swab on 2006-10-31
try this...

```
sudo apt-get install quota
```

then edit your /etc/fstab .. find the partition you want to put quotas on and add in ursquota and grpquota .. for example

```
/dev/hda3       /home           ext3    defaults,usrquota,grpquota        0       2
```

reboot.. then assuming the partition is hda3

```
sudo edquota -u johnsie -f /dev/hda3
```

make it look like this

```

Disk quotas for user johnsie (uid 100):
  Filesystem                   blocks       soft       hard     inodes     soft     hard
  /dev/hda3                         0     31457280     31457280          0        0        0
```

home my calculations are correct :)

OK, save that file... now do

```
sudo edquota -t -f /dev/hda3
```

set grace periods to 0 seconds like this

```
Grace period before enforcing soft limits for users:
Time units may be: days, hours, minutes, or seconds
  Filesystem             Block grace period     Inode grace period
  /dev/hda3                  0seconds               0seconds
```

again, save the file... and finally

```
quotaoff -a
```
and..
```
quotaon /dev/hda3
```

Hope this helps!

---

