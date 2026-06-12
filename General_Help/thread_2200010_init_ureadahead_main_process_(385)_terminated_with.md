---
title: "init: ureadahead main process (385) terminated with status 5"
date: 2014-01-17
forum: General Help
---

### Post by Azrael84 on 2014-01-17
I've noticed the following messages during boot up 

```

     EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
     init: ureadahead main process (385) terminated with status 5
     EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro

``` 

Upon googling this, I found people who had this error had separate "/var" partitions, however this is not the case for
me. I have only "/proc", "/dev/sdb6" (main root partition), "/boot/efi" and the swap partition. 

Is this something I should be worried about?

---

### Post by jeanjd63 on 2014-01-17
Hello

Could you post the contain of the file  /etc/fstab ?
and the return of the command :
**sudo  ls  -l  /dev/disk/by-uuid/**

Thanks

---

### Post by Azrael84 on 2014-01-17
Sure:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sdb6 during installation
UUID=fb9aa3cf-eb94-4298-b778-ac8fa2bd1368 /               ext4    errors=remount-ro 0       1

# /boot/efi was on /dev/sdb2 during installation
UUID=4659-4959    /boot/efi    vfat    defaults    0    1

# swap was on /dev/sdb5 during installation
/dev/mapper/cryptswap1 none swap sw 0 0


```

and

```


total 0
lrwxrwxrwx 1 root root 10 Jan 17 10:07 100E573C0E5719D4 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 17 10:07 4659-4959 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 17 10:07 56425C6B425C523B -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan 17 10:07 6218a138-b6d4-469e-bb06-ad09c0ba5075 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jan 17 10:07 fb9aa3cf-eb94-4298-b778-ac8fa2bd1368 -> ../../sda6


```

(sda1 is windows recovery, sda4 is windows)

---

### Post by jeanjd63 on 2014-01-17
All seems ok. May be swap ? 
You can edit file fstab :
sudo  gedit  /etc/fstab 
and try to comments this line :

# swap was on /dev/sdb5 during installation
# /dev/mapper/cryptswap1 none swap sw 0 0

and save and reboot, but i am not sure.

---

### Post by WinEunuchs2Unix on 2014-12-02
Hi 63.

On this system the same "error" in my /var/log/syslog.  Commenting out the swap in /etc/fstab made no difference.  The relevant log entries are:

```

Dec  2 20:00:14 Dell kernel: [    4.686346] enhanceio: module verification failed: signature and/or  required key missing - tainting kernel
Dec  2 20:00:14 Dell kernel: [    4.688356] register_policy: policy 2 added
Dec  2 20:00:14 Dell kernel: [    4.689194] register_policy: policy 1 added<5>[    4.789253] random: nonblocking pool is initialized
Dec  2 20:00:14 Dell kernel: [    5.349658] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Dec  2 20:00:14 Dell kernel: [    7.443760] init: ureadahead main process (418) terminated with status 5
Dec  2 20:00:14 Dell kernel: [    8.571679] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro

```

I noticed the OP was using device mapper and encrypted swap.  This system is using EnhanceIO which is a block level HDD to SSD caching utility.  ureadahead is redundant with HDD to SSD caching so it's not really a burning issue.  Was just a little curious & checking this issue whilst British version of House of Cards was running on Blu-Ray.

EDIT: EnhanceIO is obviously missing some Carriage Returns and Line Feeds whilst populating syslog.  Random cache policy is not preferable and the cache is actually defined with LRU (Least Recently Used) replacement policy.  A mute point since the Cache Size is 11GB and total Linux and Home size is 7.7 GB to date.  It's still a WIP after 6 weeks of speed enhancements of eio into initrd.img.

---

