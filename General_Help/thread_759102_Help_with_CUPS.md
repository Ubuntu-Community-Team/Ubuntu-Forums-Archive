---
title: "Help with CUPS??"
date: 2008-04-18
forum: General Help
---

### Post by ozweego5 on 2008-04-18
I have set up a cups server put when i log in to the terminal su to root and than execute the command
 root@dorin-desktop:/home/dorin# /etc/init.d/cups start
bash: /etc/init.d/cups: Permission denied

how do i change the permissions for this problem?? Thanks you to anyone who can post some linux knowledge!!!

---

### Post by keratos on 2008-04-18
post output of (logged in as root)
```

ls -l /etc/init.d
cat /etc/fstab
fdisk -l
id

```

---

### Post by ozweego5 on 2008-04-19
-rwSr--r-- 1 root root    0 2008-04-17 22:05 cups


how do i change this permission for cups??? i tried the command above but that just showed  my permissions than it talked about partitions?? I just need to change the permissions of this file so I can execute cups and stop getting bash shell command permission denied! ANYONE FOR SOME HELP

---

### Post by keratos on 2008-04-19
> **ozweego5 said:**
> -rwSr--r-- 1 root root    0 2008-04-17 22:05 cups


how do i change this permission for cups??? i tried the command above but that just showed  my permissions than it talked about partitions?? I just need to change the permissions of this file so I can execute cups and stop getting bash shell command permission denied! ANYONE FOR SOME HELP

help yourself and PROVIDE the information requested.

I dont think its the permissions. 

For the last time, PROVIDE the Information or I will go and help soneone else.

---

### Post by ozweego5 on 2008-04-19
ohh I am very sorry I miss understood what you wanted me to do here is the root post output of the commands you gave me, once again sorry for the miss-communication and thanks for your help

root@dorin-desktop:/# ls -l /etc/init.d
total 428
-rwxr-xr-x 1 root root 2701 2007-08-15 10:39 acpid
-rwxr-xr-x 1 root root  762 2007-08-30 22:48 acpi-support
-rwxr-xr-x 1 root root 9534 2007-09-03 22:52 alsa-utils
-rwxr-xr-x 1 root root 1084 2007-03-05 09:32 anacron
-rwxr-xr-x 1 root root 1460 2007-08-29 08:01 apcupsd
-rwxr-xr-x 1 root root 2793 2007-10-13 21:32 apparmor
-rwxr-xr-x 1 root root 3024 2007-05-14 02:28 apport
-rwxr-xr-x 1 root root  969 2007-02-20 09:05 atd
-rwxr-xr-x 1 root root 2460 2007-10-04 11:14 avahi-daemon
-rwxr-xr-x 1 root root 6557 2007-10-03 04:59 bluetooth
-rwxr-xr-x 1 root root 3597 2007-10-04 07:25 bootclean
-rwxr-xr-x 1 root root 2121 2007-10-04 07:25 bootlogd
-rwxr-xr-x 1 root root 1768 2007-10-04 07:25 bootmisc.sh
-rwxr-xr-x 1 root root 1383 2007-05-18 11:56 brltty
-rwxr-xr-x 1 root root 2887 2007-10-04 07:25 checkfs.sh
-rwxr-xr-x 1 root root 9875 2007-10-04 07:25 checkroot.sh
-rwxr-xr-x 1 root root 2941 2007-08-03 13:20 consolekit
-rwxr-xr-x 1 root root 6355 2007-05-30 08:29 console-screen.sh
-rwxr-xr-x 1 root root 1612 2007-05-02 07:41 console-setup
-rwxr-xr-x 1 root root 1761 2006-12-20 09:51 cron
-rwSr--r-- 1 root root    0 2008-04-17 22:05 cups
-rwxr-xr-x 1 root root 1937 2007-10-15 09:01 cupsys
-rwxr-xr-x 1 root root 4192 2007-10-05 09:27 dbus
-rwxr-xr-x 1 root root 1497 2007-06-12 10:57 dhcdbd
-rwxr-xr-x 1 root root 1223 2007-06-22 00:55 dns-clean
-rwxr-xr-x 1 root root 1567 2007-08-08 03:34 firestarter
-rwxr-xr-x 1 root root 3136 2007-10-15 07:09 gdm
-rwxr-xr-x 1 root root 6607 2007-09-30 19:51 glibc.sh
-rwxr-xr-x 1 root root 2294 2007-10-08 14:48 hal
-rwxr-xr-x 1 root root 1228 2007-10-04 07:25 halt
-rwxr-xr-x 1 root root 5137 2005-04-21 06:10 hdparm
-rwxr-xr-x 1 root root  909 2007-10-04 07:25 hostname.sh
-rwxr-xr-x 1 root root 3576 2007-09-29 20:43 hotkey-setup
-rwxr-xr-x 1 root root 4569 2007-10-03 00:27 hwclockfirst.sh
-rwxr-xr-x 1 root root 4568 2007-10-03 00:27 hwclock.sh
-rwxr-xr-x 1 root root 1304 2007-06-02 18:48 keyboard-setup
-rwxr-xr-x 1 root root  944 2007-10-04 07:25 killprocs
-rwxr-xr-x 1 root root 1752 2007-09-17 17:04 klogd
-rwxr-xr-x 1 root root 2285 2007-09-18 19:01 laptop-mode
-rwxr-xr-x 1 root root  632 2007-07-13 08:57 libpam-foreground
-rwxr-xr-x 1 root root  349 2007-10-15 07:33 linux-restricted-modules-common
-rwxr-xr-x 1 root root  748 2006-01-23 13:47 loopback
-rwxr-xr-x 1 root root 1050 2007-07-28 15:52 makedev
-rwxr-xr-x 1 root root 1399 2007-10-05 13:10 module-init-tools
-rwxr-xr-x 1 root root  596 2007-10-04 07:25 mountall-bootclean.sh
-rwxr-xr-x 1 root root 2430 2007-10-04 07:25 mountall.sh
-rwxr-xr-x 1 root root 1465 2007-10-04 07:25 mountdevsubfs.sh
-rwxr-xr-x 1 root root 1460 2007-10-04 07:25 mountkernfs.sh
-rwxr-xr-x 1 root root  594 2007-10-04 07:25 mountnfs-bootclean.sh
-rwxr-xr-x 1 root root 1244 2007-10-04 07:25 mountoverflowtmp
-rwxr-xr-x 1 root root 2689 2007-10-04 07:25 mtab.sh
-rwxr-xr-x 1 root root 1772 2007-05-08 06:33 networking
-rwxr-xr-x 1 root root 5467 2007-08-13 09:22 nfs-common
-rwxr-xr-x 1 root root 4388 2007-08-13 09:22 nfs-kernel-server
-rwxr-xr-x 1 root root  860 2005-10-28 22:48 nvidia-kernel
-rwxr-xr-x 1 root root 2351 2007-03-07 17:00 pcmciautils
-rwxr-xr-x 1 root root 1525 2007-08-23 22:22 portmap
-rwxr-xr-x 1 root root 4108 2006-12-18 19:37 powernowd
-rwxr-xr-x 1 root root  177 2006-12-18 19:37 powernowd.early
-rwxr-xr-x 1 root root  375 2007-10-04 16:47 pppd-dns
-rwxr-xr-x 1 root root 1208 2007-07-31 04:14 procps.sh
-rwxr-xr-x 1 root root 8191 2007-10-04 07:17 rc
-rwxr-xr-x 1 root root  522 2007-10-04 07:25 rc.local
-rwxr-xr-x 1 root root  117 2007-10-04 07:17 rcS
-rwxr-xr-x 1 root root 1492 2007-10-12 08:58 readahead
-rwxr-xr-x 1 root root 1957 2007-10-12 08:58 readahead-desktop
-rw-r--r-- 1 root root 1335 2007-10-04 07:17 README
-rwxr-xr-x 1 root root  692 2007-10-04 07:25 reboot
-rwxr-xr-x 1 root root 1000 2007-10-04 07:25 rmnologin
-rwxr-xr-x 1 root root 4945 2007-08-17 21:25 rsync
-rwxr-xr-x 1 root root 2426 2007-12-18 00:14 samba
-rwxr-xr-x 1 root root  714 2007-07-26 11:57 screen
-rwxr-xr-x 1 root root  975 2007-10-04 07:25 sendsigs
-rwxr-xr-x 1 root root  585 2007-10-04 07:25 single
-rwxr-xr-x 1 root root 4215 2007-10-04 07:25 skeleton
-rwxr-xr-x 1 root root  510 2007-10-04 07:25 stop-bootlogd
-rwxr-xr-x 1 root root  647 2007-10-04 07:25 stop-bootlogd-single
-rwxr-xr-x 1 root root  864 2007-10-12 08:58 stop-readahead
-rwxr-xr-x 1 root root 3369 2007-09-17 17:04 sysklogd
-rwxr-xr-x 1 root root 2471 2007-10-05 12:45 udev
-rwxr-xr-x 1 root root  706 2007-10-05 12:45 udev-finish
-rwxr-xr-x 1 root root 3511 2007-10-04 07:25 umountfs
-rwxr-xr-x 1 root root 1833 2007-10-04 07:25 umountnfs.sh
-rwxr-xr-x 1 root root 1439 2007-10-04 07:25 umountroot
lrwxrwxrwx 1 root root   22 2008-04-17 12:02 ups-monitor -> ../apcupsd/ups-monitor
-rwxr-xr-x 1 root root 1815 2007-10-04 07:25 urandom
-rwxr-xr-x 1 root root 2814 2007-10-15 05:20 usplash
-rwxr-xr-x 1 root root  820 2007-09-19 05:59 vbesave
-rwxr-xr-x 1 root root 1939 2007-10-04 07:25 waitnfs.sh
-rwxr-xr-x 1 root root 1626 2007-09-24 14:33 wpa-ifupdown
-rwxr-xr-x 1 root root 1843 2007-07-04 10:55 x11-common
-rwxr-xr-x 1 root root  503 2007-09-15 22:06 xserver-xorg-input-wacom
root@dorin-desktop:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a1b5e4c-2f72-4955-a4c1-6f9b8dddd407 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ad7f8078-4e17-45b4-a7b1-8f6bee22e3af none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
root@dorin-desktop:/# fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47559   382017636   83  Linux
/dev/sda2           47560       48641     8691165    5  Extended
/dev/sda5           47560       48641     8691133+  82  Linux swap / Solaris
root@dorin-desktop:/# id
uid=0(root) gid=0(root) groups=0(root)

---

### Post by keratos on 2008-04-20
chmod 755 /etc/init.d/cups

---

