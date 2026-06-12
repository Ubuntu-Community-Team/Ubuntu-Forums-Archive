---
title: "Recovering jfs /home"
date: 2013-04-28
forum: General Help
---

### Post by gupti on 2013-04-28
Hello all,

I've recently tweaked my computer by overclocking, and I have updated to 13.04. The PC started acting strange, giving me a recursion error on every second boot, and the last time my computer worked, syslog and kern.log were over 20GB in size. I deleted them, scheduled a fsck and rebooted, only to find I was sent into grub rescue. That problem was fixed with boot repair, but now it said that there were serious issues with my /home, so I began manual recovery.

Unfortunately, fsck.jfs is having problems recovering /home, stating that a buffer overflow was detected, and it exits with signal 6. Not sure if it's a problem caused by the 13.04 update or overclocking, I conducted stress tests on Windows for ~15 minutes and played TF2 on Linux for a few hours yesterday and everything seemed fine. Any suggestions?

---

### Post by gupti on 2013-04-28
Here's the gparted log from a Live USB:
```
GParted 0.12.1 --enable-libparted-dmraid
 Libparted 2.3
 [TABLE]
 [TR]
 [TD="colspan: 2"] **Check and repair file system (jfs) on /dev/sda1**  00:00:48    ( ERROR ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] calibrate /dev/sda1  00:00:00    ( SUCCESS ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] [I]path: /dev/sda1
start: 2,048
end: 1,953,523,711
size: 1,953,521,664 (931.51 GiB)[/I] [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [TABLE]
 [TR]
 [TD="colspan: 2"] check file system on /dev/sda1 for errors and (if possible) fix them  00:00:48    ( ERROR ) [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] ***jfs_fsck -f /dev/sda1*** [/TD]
 [/TR]
 [TR]
 [TD]    [/TD]
 [TD] [TABLE]
 [TR]
 [TD="colspan: 2"] [I]jfs_fsck version 1.1.15, 04-Mar-2011
processing started: 4/28/2013 19:13:16
The current device is:  /dev/sda1
Block size in bytes:  4096
Filesystem size in blocks:  244190208
**Phase 0 - Replay Journal Log
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
Incorrect link counts have been detected. Will correct.
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
File system object FF263 is linked as: ECRYPTFS_FNEK_ENCRYPTED.FWbdkerFWzeYXUSS3BQrhey.Lcc8q52Fbvph5jfnpCLdNXIVa25WVDJgEE--
cannot repair the data format error(s) in this file.
cannot repair FF263.  Will release.
File  system object DF479785 is linked as:  /.ecryptfs/paul/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWbdkerFWzeYXUSS3BQrhey.Lcc8q52FbvphN8V5F1I08bkC8YnRSQtBTk--/ECRYPTFS_FNEK_ENCRYPTED.FWbdkerFWzeYXUSS3BQrhey.Lcc8q52Fbvphn15YOTARAbuJ7l9TZzE9xU--/ECRYPTFS_FNEK_ENCRYPTED.FXbdkerFWzeYXUSS3BQrhey.Lcc8q52FbvphfXMsHRUeBbIQfo2HZ4tEe8E6K5zOfT10QYNOa3IJFpk-/ECRYPTFS_FNEK_ENCRYPTED.FXbdkerFWzeYXUSS3BQrhey.Lcc8q52FbvphEWLflpXGunFtC2dIVX6jQVkyT0sgzz.SiBd5XH5Mgo2-/ECRYPTFS_FNEK_ENCRYPTED.FWbdkerFWzeYXUSS3BQrhey.Lcc8q52Fbvph
[/I] [/TD]
 [/TR]
 [/TABLE]
 [TABLE]
 [TR]
 [TD="colspan: 2"] [I]*** buffer overflow detected ***: jfs_fsck terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x5c)[0x7fd2d0de582c]
/lib/x86_64-linux-gnu/libc.so.6(+0x109700)[0x7fd2d0de4700]
/lib/x86_64-linux-gnu/libc.so.6(__strncpy_chk+0x0)[0x7fd2d0de3880]
jfs_fsck[0x423f8a]
jfs_fsck[0x410b0a]
jfs_fsck[0x4112e4]
jfs_fsck[0x42182a]
jfs_fsck[0x42240d]
jfs_fsck[0x401d16]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7fd2d0cfc76d]
jfs_fsck[0x401f59]
======= Memory map: ========
00400000-00435000 r-xp 00000000 07:00 24017                              /sbin/jfs_fsck
00634000-00635000 r--p 00034000 07:00 24017                              /sbin/jfs_fsck
00635000-00663000 rw-p 00035000 07:00 24017                              /sbin/jfs_fsck
00663000-006fb000 rw-p 00000000 00:00 0 
019c5000-01bf7000 rw-p 00000000 00:00 0                                  [heap]
7fd2d0ac5000-7fd2d0ada000 r-xp 00000000 07:00 28030                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fd2d0ada000-7fd2d0cd9000 ---p 00015000 07:00 28030                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fd2d0cd9000-7fd2d0cda000 r--p 00014000 07:00 28030                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fd2d0cda000-7fd2d0cdb000 rw-p 00015000 07:00 28030                      /lib/x86_64-linux-gnu/libgcc_s.so.1
7fd2d0cdb000-7fd2d0e90000 r-xp 00000000 07:00 27932                      /lib/x86_64-linux-gnu/libc-2.15.so
7fd2d0e90000-7fd2d108f000 ---p 001b5000 07:00 27932                      /lib/x86_64-linux-gnu/libc-2.15.so
7fd2d108f000-7fd2d1093000 r--p 001b4000 07:00 27932                      /lib/x86_64-linux-gnu/libc-2.15.so
7fd2d1093000-7fd2d1095000 rw-p 001b8000 07:00 27932                      /lib/x86_64-linux-gnu/libc-2.15.so
7fd2d1095000-7fd2d109a000 rw-p 00000000 00:00 0 
7fd2d109a000-7fd2d109e000 r-xp 00000000 07:00 28117                      /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fd2d109e000-7fd2d129d000 ---p 00004000 07:00 28117                      /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fd2d129d000-7fd2d129e000 r--p 00003000 07:00 28117                      /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fd2d129e000-7fd2d129f000 rw-p 00004000 07:00 28117                      /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fd2d129f000-7fd2d12c1000 r-xp 00000000 07:00 28060                      /lib/x86_64-linux-gnu/ld-2.15.so
7fd2d148a000-7fd2d14ae000 rw-p 00000000 00:00 0 
7fd2d14bc000-7fd2d14c1000 rw-p 00000000 00:00 0 
7fd2d14c1000-7fd2d14c2000 r--p 00022000 07:00 28060                      /lib/x86_64-linux-gnu/ld-2.15.so
7fd2d14c2000-7fd2d14c4000 rw-p 00023000 07:00 28060                      /lib/x86_64-linux-gnu/ld-2.15.so
7fff69bfa000-7fff69c1b000 rw-p 00000000 00:00 0                          [stack]
7fff69d44000-7fff69d45000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted (core dumped)
[/I] [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 [/TD]
 [/TR]
 [/TABLE]
 ========================================


```

---

### Post by dabl on 2013-04-28
What operating system is on the Live USB stick?  The problem has nothing to do with the OS installed on the hard drive.  Also, what is the "ENCRYPTFS_xxxxxx" all about -- are we talking about an encrypted partition here?

---

### Post by gupti on 2013-04-28
Yes, it's an encrypted /home on its own separate hard drive. The Live USB is 12.10. If I don't find a solution, I'll just have to do a re-install (possibly with Arch Linux this time), and restore most of my data through an older back-up.

---

### Post by dabl on 2013-04-30
The version of GParted in Ubuntu 12.10 is 0.12.1.  On my Parted Magic USB stick, the version is 0.14.1.  I do not know whether the newer version could handle that jfs error, or not.  If it were me, I would (1) back up my data securely and completely, (2) try a Parted Magic Live CD or USB stick, and try again to check/fix the filesystem, and if that does not resolve it, then I would remake the filesystem as an ext4 filesystem, and restore my data.  If the OS is not on that partition, then there is not need to install a different OS -- you can just mount the partition with an appropriate line in /etc/fstab.  Note that the jfs filesystem is not a "feature" of any OS, including Ubuntu -- it is an independent project, and it is _not_ the recommended filesystem for *buntu installations.

---

