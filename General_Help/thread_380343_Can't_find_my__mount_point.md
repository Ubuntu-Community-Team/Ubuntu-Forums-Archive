---
title: "Can't find my / mount point"
date: 2007-03-09
forum: General Help
---

### Post by KLineD on 2007-03-09
Hello everybody!

I have my filesystem set up in the following way (or so I thought so)

/dev/sda1    /          10GB
/dev/sda2   swap   512MB
/dev/sda3   /home  80GB

However GParted shows an exclamation mark in /dev/sda1 and it doesn't report this partition as my root ( / ) mountpoint.

The contents of my fstab are not what I'm used to:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=0600-3F80 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=92029a57-223f-4b61-8d99-4ed54c34b7a5 /home ext3 defaults 0 2
# /dev/sda4 -- converted during upgrade to edgy
#UUID=6AC1A3382E9F3FCA /media/sda4 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda2       none swap sw 0 0
#UUID=5f92426f-94c0-4f6a-beaf-f2d12cddfe56 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I would think that the line UUID=0600-3F80 / ext3 defaults,errors=remount-ro 0 1 mounts the root partition, but why isn't the regular (/dev/sda1) way used? also mount reports the following:
> proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I can't see /dev/sda1 on / anywere! 

My main concern is in what device is the / mount point mounted? I would like it to be on /dev/sda1 obviously. How can I verify this?

Thanks a lot for your help.

---

### Post by Kateikyoushi on 2007-03-09
Since edgy ubuntu uses UUID and actually you can still find the old way commented in fstab.
For example: "# /dev/sda1 -- converted during upgrade to edgy" under this line can see it is mounted as / and ext3.

---

### Post by KLineD on 2007-03-09
If that's so, so how can I check how much free space is left in /dev/sda1 ( / ) ??

I used the command df to check this, but right now the output of df is:
> Filesystem           1K-blocks Used Available Use% Mounted on
varrun                  517108       200    516908   1% /var/run
varlock                 517108         4    517104   1% /var/lock
procbususb               10240       112     10128   2% /proc/bus/usb
udev                     10240       112     10128   2% /dev
devshm                  517108        20    517088   1% /dev/shm
lrm                     517108     17580    499528   4% /lib/modules/2.6.17-11-generic/volatile
/dev/sda3             85381500  32512708  51133936  39% /home

No /dev/sda1 or / in there... :confused:

---

