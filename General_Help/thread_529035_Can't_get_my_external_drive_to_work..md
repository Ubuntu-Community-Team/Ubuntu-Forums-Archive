---
title: "Can't get my external drive to work."
date: 2007-08-18
forum: General Help
---

### Post by Sparky222B on 2007-08-18
Despite this line in my fstab:

```

/dev/sdk1       /media/HITACHI   vfat     umask=000,uid=sparky,gid=users 0 0 

```

and an fdisk -l out put of:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1      121601   976760001    c  W95 FAT32 (LBA)

```

for my only Fat32 hard drive, when I plug in the drive, Ubuntu says "You are not priviliged to mount the volume HITACHI".

What should I do?

---

### Post by taurus on 2007-08-18
What about?

```
sudo mount -a
df -h
```

---

### Post by Sparky222B on 2007-08-18
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              22G   19G  1.9G  91% /
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
procbususb            1.5G  184K  1.5G   1% /proc/bus/usb
udev                  1.5G  184K  1.5G   1% /dev
devshm                1.5G   16K  1.5G   1% /dev/shm
lrm                   1.5G   33M  1.5G   3% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             165G   69G   97G  42% /media/sda1
/dev/sdb5             187G  148G   39G  80% /media/sdb5
/dev/sdh1             153G  137G   17G  90% /media/External
/dev/scd0             3.7G  3.7G     0 100% /media/cdrom0
/dev/scd1             1.1G  1.1G     0 100% /media/cdrom1
/dev/sdg1             233G   91G  143G  39% /media/External 2
/dev/sdk1             932G   31G  901G   4% /media/HITACHI

```

---

### Post by Sparky222B on 2007-08-18
Ah, solved it!

Here's what I did:

I opened System -> Admin -> Storage Device Manager

Then I went to the partition (sdk -> sdk1 in my case) and hit Assistant

Then I just used the options there to set umask to 000 and config it how I liked

OK, Unmount, and Mount again

Voila!

---

### Post by Sparky222B on 2007-08-18
Update: Never mind. I rebooted and my HDD changed from sdk1 to sdc1. Is there any way to lock the drive to a specific name?

---

### Post by herdivet on 2008-04-30
This worked for me.  Not sure why this drive didn't want to pop up automatically, but this did the trick - Thanks!

---

