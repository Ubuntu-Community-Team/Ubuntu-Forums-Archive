---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-09-04
forum: General Help
---

### Post by ahuemmer3 on 2014-09-04
When I try to install anything or update anything I get this return

libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/local.conf line 2: ignoring bad line starting with 'drm_kms_helper'

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-35-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.13.0-34-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

someone please help

---

### Post by TheFu on 2014-09-04
Please post output from:
```
df -i
df -h
```

Did you install with LVM or encryption?

---

### Post by ahuemmer3 on 2014-09-05
I'm not sure. I'm new to this stuff and don't fully know what I'm doing

ahuemmer12@ahuemmer12-Inspiron-N5110:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 45383680 441437 44942243    1% /
none                          752013      2   752011    1% /sys/fs/cgroup
udev                          748184    527   747657    1% /dev
tmpfs                         752013    560   751453    1% /run
none                          752013      4   752009    1% /run/lock
none                          752013     12   752001    1% /run/shm
none                          752013     29   751984    1% /run/user
/dev/sda1                      62248    327    61921    1% /boot


ahuemmer12@ahuemmer12-Inspiron-N5110:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  682G  9.9G  638G   2% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         2.9G  4.0K  2.9G   1% /dev
tmpfs                        588M  1.2M  587M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         2.9G  204K  2.9G   1% /run/shm
none                         100M   48K  100M   1% /run/user
/dev/sda1                    236M  233M     0 100% /boot

---

### Post by TheFu on 2014-09-05
So - you ARE using LVM - this forced /boot to be on a partition all alone.  It is full.  That means you won't be able to have any updated kernels until this problem is solved.

Oh - and please edit the post above and use "**code tags**" so things line up properly.
```
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 236M 233M 0 100% /boot 
```

This will be a re-occurring issue with a /boot that small.  You are in a precarious situation.  It is some work to clean this stuff up. It is much easier (though more compute time) to just reinstall the OS and be careful about how large the partitions are.  1-2G would be a better size for /boot - assuming you want LVM.  If you don't know what LVM is - avoid it.

So - there are at least 5 threads here with the exact same issue in the last 2 months. Find those and follow the long, cumbersome instructions to clean up some old kernel packages using dpkg (not apt-get) - only removing old kernels will clean up /boot. Nothing else will help.

How to prevent this in the future - clean up old kernels before there are too many. There are other things that must be performed to maintain a Linux desktop. [http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) was republished by lifehacker. Sadly, it won't help you today or to clean up the old kernels when there isn't any space left already. Sorry.

---

