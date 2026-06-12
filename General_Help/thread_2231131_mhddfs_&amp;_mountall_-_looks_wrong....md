---
title: "mhddfs &amp; mountall - looks wrong..."
date: 2014-06-23
forum: General Help
---

### Post by IanUK on 2014-06-23
I have installed Ubuntu 14.04 on an SSD, and want to setup my /tmp using mhddfs to join a small tmpfs and an HDD partition.
I have managed to get the /etc/fstab looking ok, and the boot runs ok (no mount errors to skip), and the directories appear to look as if this is working -

Prior to boot the / mount points are (seen as mounted to another ubuntu image) -[INDENT][FONT=courier new]drwxrwxrwt   2 root root  4096 Jun 23 16:39 tmp
drwxrwxrwt   2 root root  4096 Jun 23 15:45 tmp-hdd
drwxrwxrwt   2 root root  4096 Jun 19 16:06 tmp-ram[/FONT]
[/INDENT]

These are all empty.
There is a separate HDD partition that gets mounted to /tmp-hdd, this contains -[INDENT][FONT=courier new]drwxrwxrwt 3 root root 4096 Jun 23 15:44 .
drwxr-xr-x 9 root root 4096 Jun 23 17:36 ..
drwxrwxrwx 2 root root 4096 Jun 23 12:51 Firefox-cache[/FONT]
[/INDENT]

/etc/fstab looks like this -[INDENT][FONT=courier new]# /tmp on ram+hdd :
#   * hdd => Cap1-hdd1
UUID=221181b3-f65c-4382-92a8-d5f88ca50854     /tmp-hdd        ext4    showthrough,bootwait 0 2
#   * ram =>
tmpfs /tmp-ram tmpfs defaults,noatime,size=200M,mode=1777,showthrough,bootwait 0 0
#   * unionfs =>
mhddfs#/tmp-ram,/tmp-hdd /tmp fuse defaults,allow_other,mlimit=100M,nonempty,showthrough,bootwait 0 0
#
# / was on /dev/sdc1 during installation
UUID=58f05a4a-8647-46be-96f3-5b44080abf72     /               ext4    noatime,errors=remount-ro,bootwait     0 1
[/FONT][/INDENT]

I have done this with showthrough etc, as /tmp seemed sensitive to being mounted after / - things seem to start to use /tmp very early on...

When booted up, /tmp looks like this -[INDENT][FONT=courier new]total 24
drwxrwxrwt  5 root root  180 Jun 23 17:47 .
drwxr-xr-x 26 root root 4096 Jun 23 16:38 ..
drwxrwxrwx  2 root root 4096 Jun 23 12:51 Firefox-cache
-rw-------  1 ian  ian  8192 Jun 23 17:46 .fuse_hidden000000210000000a
drwxrwxrwt  2 root root   60 Jun 23 17:46 .ICE-unix
drwx------  2 ian  ian    60 Jun 23 17:46 ssh-xxxxxxxxxxxx
-rw-r--r--  1 ian  ian     0 Jun 23 17:46 unity_support_test.0
-rw-r--r--  1 nut  nut   101 Jun 23 17:45 UPS_STATE.log
-r--r--r--  1 root root   11 Jun 23 17:45 .X0-lock
drwxrwxrwt  2 root root   60 Jun 23 17:45 .X11-unix[/FONT]
[/INDENT]

Most of this is in /tmp-ram -[INDENT][FONT=courier new]total 20
drwxrwxrwt  5 root root  180 Jun 23 17:47 .
drwxr-xr-x 26 root root 4096 Jun 23 16:38 ..
-rw-------  1 ian  ian  8192 Jun 23 17:46 .fuse_hidden000000210000000a
drwxrwxrwt  2 root root   60 Jun 23 17:46 .ICE-unix
drwx------  2 ian  ian    60 Jun 23 17:46 ssh-xxxxxxxxxxxx
-rw-r--r--  1 ian  ian     0 Jun 23 17:46 unity_support_test.0
-rw-r--r--  1 nut  nut   101 Jun 23 17:45 UPS_STATE.log
-r--r--r--  1 root root   11 Jun 23 17:45 .X0-lock
drwxrwxrwt  2 root root   60 Jun 23 17:45 .X11-unix[/FONT]
[/INDENT]

and /tmp-hdd has -[INDENT][FONT=courier new]total 12
drwxrwxrwt  3 root root 4096 Jun 23 15:44 .
drwxr-xr-x 26 root root 4096 Jun 23 16:38 ..
drwxrwxrwx  2 root root 4096 Jun 23 12:51 Firefox-cache[/FONT]
[/INDENT]

THAT ALL LOOKS GOOD TO ME, BUT THIS LOOKS ODD -

/var/log/upstart/mountall.log conains and error - "mountall: mount /tmp [411] terminated with status 255" -[INDENT][FONT=courier new]fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
mhddfs: directory '/tmp-ram' added to list
mhddfs: directory '/tmp-hdd' added to list
mhddfs: mount to: /tmp
mhddfs: move size limit 104857600 bytes
/dev/sdc1: clean, 249353/3301376 files, 1588452/13187988 blocks

Multi-hdd FUSE filesystem
 Copyright (C) 2008, Dmitry E. Oboukhov <dimka@avanto.org>

Usage:
 mhddfs dir1,dir2.. mountpoint [ -o OPTIONS ]

OPTIONS:
  mlimit=xxx - limit of the disk free space (if the disk
          has the free space more than specified - it is
          considered as the empty one).  Default is  4Gb,
          but 100Mb at least.
  logfile=/path/to/file  -  path to a file where the logs
          will be stored.
  loglevel=x - level for log-messages:
                0 - debug
                1 - info
                2 - default messages

 see fusermount(1) for information about other options
**[COLOR=#ff0000]mountall: mount /tmp [411] terminated with status 255[/COLOR]**
var-log: clean, 124/1281120 files, 127101/5120000 blocks
Cap1-hdd1: clean, 11/15933440 files, 1047876/63730944 blocks[/FONT]
[/INDENT]

AND I do not see /tmp mentioned in the output of mount -[INDENT][FONT=courier new]/dev/sdc1 on / type ext4 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
tmpfs on /tmp-ram type tmpfs (rw,noatime,size=200M,mode=1777)
/dev/sda7 on /var/log type ext4 (rw,errors=remount-ro)
/dev/sda8 on /tmp-hdd type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ian)
gvfsd-fuse on /root/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)[/FONT]
[/INDENT]

It seems to be working - but I don't like to see error messages from mountall that could indicate all is NOT well...

Edit: I have tried adding a "logfile=xxx" option to /etc/fstab, but everything is read-only at that stage, so the mount for /tmp fails totally...

---

