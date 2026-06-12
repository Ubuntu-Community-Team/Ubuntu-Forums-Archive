---
title: "Unable to boot."
date: 2007-09-15
forum: General Help
---

### Post by The Exorcist on 2007-09-15
Hi, my Kubuntu, which was installed via Wubi is no longer booting. It is hanging at the Grub stage with a flashing cursor and this message above -

 Ubuntu, kernel 2.6.20-16-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash

...I copied that from menu.lst

The last time Kubuntu was used was just before my hols, here are the log outputs :

+ PREREQ=
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
+ . /conf/param.conf
+ ROOT=/media/host/wubi/disks/system.virtual.disk
+ ROOTFLAGS=-o loop
+ ROOTFSTYPE=ext3
+ ISOMNT=/cdrom
+ ROOTMNT=/root
+ HOSTFOLDER=/media/host/wubi
+ SUITE=
+ SETUPISO=
+ HOSTMNT=/media/host
+ ROOTDEV=/media/host/wubi/disks/system.virtual.disk
+ HOMEDEV=/media/host/wubi/disks/home.virtual.disk
+ SWAPDEV=/media/host/wubi/disks/swap.virtual.disk
+ EXTRADEV=
+ PAUSEFORDEBUG=n
+ pause_for_debug Lupin Start
+ cd /
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /media/host/wubi ]
+ [ -e /media/host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /media/host/wubi/logs

******

+ PREREQ=
+ ROOTMNT=/root
+ HOSTMNT=/media/host
+ HOSTFOLDER=
+ ISOMNT=/cdrom
+ HOSTKEY=
+ SUITE=
+ DEFAULTSUITE=feisty dapper unstable testing stable
+ SETUP_INIT=busybox init
+ SETUPISO=
+ ROOTIMG=system.virtual.disk
+ HOMEIMG=home.virtual.disk
+ SWAPIMG=swap.virtual.disk
+ EXTRAIMG=extra.virtual.disk
+ USRIMG=programs.virtual.disk
+ DUMMYIMG=install.virtual.disk
+ ROOTDEV=
+ HOMEDEV=
+ SWAPDEV=
+ EXTRADEV=
+ USRDEV=
+ DUMMYDEV=
+ USEFREESPACE=
+ PAUSEFORDEBUG=n
+ cat /proc/cmdline
+ HOSTKEY=/wubi/boot/linux
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
+ [ -n /wubi/boot/linux ]
+ find_host_folder
+ wait_for_devs
+ log_begin_msg ...waiting for devs...
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT ...waiting for devs...
+ _log_msg Begin: ...waiting for devs... ...
+ echo Begin: ...waiting for devs... ...
Begin: ...waiting for devs... ...
+ udevtrigger --subsystem-match=block
+ udevsettle
+ log_end_msg ...devs loaded...
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write SUCCESS ok
+ _log_msg Done.
+ echo Done.
Done.
+ update_progress
+ [ -d /dev/.initramfs ]
+ [ -z 1 ]
+ PROGRESS_STATE=2
+ echo PROGRESS_STATE=2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 2
+ [ -n /wubi/boot/linux ]
+ log_begin_msg Loking for /wubi/boot/linux
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Loking for /wubi/boot/linux
+ _log_msg Begin: Loking for /wubi/boot/linux ...
+ echo Begin: Loking for /wubi/boot/linux ...
Begin: Loking for /wubi/boot/linux ...
+ fast_scan
+ log_begin_msg Fast scan
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Fast scan
+ _log_msg Begin: Fast scan ...
+ echo Begin: Fast scan ...
Begin: Fast scan ...
+ list_devices
+ ALLDEVICES=
+ check_fs /dev/sda1
+ dev=/dev/sda1
+ get_fs /dev/sda1
+ [ -n  ]
+ [ vfat = unknown ]
+ [ vfat = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1
+ check_fs /dev/sda2
+ dev=/dev/sda2
+ get_fs /dev/sda2
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda2
+ check_fs /dev/sda
+ dev=/dev/sda
+ get_fs /dev/sda
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ check_fs /dev/mapper/*RAID[0123456789]
+ dev=/dev/mapper/*RAID[0123456789]
+ get_fs /dev/mapper/*RAID[0123456789]
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ scan_devices /dev/sda1 /dev/sda2
+ devs=/dev/sda1 /dev/sda2
+ is_host_device /dev/sda1
+ dev=/dev/sda1
+ log_begin_msg Testing device /dev/sda1
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/sda1
+ _log_msg Begin: Testing device /dev/sda1 ...
+ echo Begin: Testing device /dev/sda1 ...
Begin: Testing device /dev/sda1 ...
+ safe_mount /dev/sda1 /media/host
+ dev=/dev/sda1
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ mkdir -p /media/host
+ umount /media/host
+ get_fs /dev/sda1
+ dev=/dev/sda1
+ FSTYPE=unknown
+ [ ! -b /dev/sda1 ]
+ /lib/udev/vol_id -t /dev/sda1
+ FSTYPE=vfat
+ [ -z vfat ]
+ mount -t auto /dev/sda1 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg Host not found
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write SUCCESS ok
+ _log_msg Done.
+ echo Done.
Done.
+ update_progress
+ [ -d /dev/.initramfs ]
+ [ -z 2 ]
+ PROGRESS_STATE=3
+ echo PROGRESS_STATE=3
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 3
+ return 5
+ is_host_device /dev/sda2
+ dev=/dev/sda2
+ log_begin_msg Testing device /dev/sda2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/sda2
+ _log_msg Begin: Testing device /dev/sda2 ...
+ echo Begin: Testing device /dev/sda2 ...
Begin: Testing device /dev/sda2 ...
+ safe_mount /dev/sda2 /media/host
+ dev=/dev/sda2
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/sda2
+ dev=/dev/sda2
+ FSTYPE=unknown
+ [ ! -b /dev/sda2 ]
+ /lib/udev/vol_id -t /dev/sda2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/sda2 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg !!!!Found host device /dev/sda2!!!!
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write SUCCESS ok
+ _log_msg Done.
+ echo Done.
Done.
+ update_progress
+ [ -d /dev/.initramfs ]
+ [ -z 3 ]
+ PROGRESS_STATE=4
+ echo PROGRESS_STATE=4
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 4
+ return 0
+ return 0
+ log_end_msg
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write SUCCESS ok
+ _log_msg Done.
+ echo Done.
Done.
+ update_progress
+ [ -d /dev/.initramfs ]
+ [ -z 4 ]
+ PROGRESS_STATE=5
+ echo PROGRESS_STATE=5
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 5
+ return 0
+ mount_host_dev /dev/sda2
+ hostdev=/dev/sda2
+ log_begin_msg Mounting /dev/sda2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting /dev/sda2
+ _log_msg Begin: Mounting /dev/sda2 ...
+ echo Begin: Mounting /dev/sda2 ...
Begin: Mounting /dev/sda2 ...
+ safe_mount /dev/sda2 /media/host rw
+ dev=/dev/sda2
+ mntpoint=/media/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/sda2
+ dev=/dev/sda2
+ FSTYPE=unknown
+ [ ! -b /dev/sda2 ]
+ /lib/udev/vol_id -t /dev/sda2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g -o rw /dev/sda2 /media/host
+ HOSTFOLDER=/wubi/boot
+ HOSTFOLDER=/wubi
+ [ /wubi = / ]
+ HOSTFOLDER=/media/host/wubi
+ return 0
+ rm_logs
+ [ -e /media/host/wubi/logs ]
+ rm /media/host/wubi/logs/lupin.log /media/host/wubi/logs/zenigata.log
+ get_target_devices
+ [  = y ]
+ [ -f /media/host/wubi/disks/system.virtual.disk ]
+ ROOTDEV=/media/host/wubi/disks/system.virtual.disk
+ [ -f /media/host/wubi/disks/swap.virtual.disk ]
+ SWAPDEV=/media/host/wubi/disks/swap.virtual.disk
+ [ -f /media/host/wubi/disks/home.virtual.disk ]
+ HOMEDEV=/media/host/wubi/disks/home.virtual.disk
+ [ -f /media/host/wubi/disks/extra.virtual.disk ]
+ [ -f /media/host/wubi/disks/programs.virtual.disk ]
+ return 0
+ [ -n /media/host/wubi/disks/system.virtual.disk ]
+ check_fs /media/host/wubi/disks/system.virtual.disk
+ dev=/media/host/wubi/disks/system.virtual.disk
+ get_fs /media/host/wubi/disks/system.virtual.disk
+ [ -n  ]
+ [ ext3 = unknown ]
+ [ ext3 = swap ]
+ return 0
+ ROOT=/media/host/wubi/disks/system.virtual.disk
+ [ -n  ]
+ ROOTFLAGS=-o loop
+ echo ROOT=/media/host/wubi/disks/system.virtual.disk
+ echo ROOTFLAGS='-o loop'
+ echo ROOTFSTYPE=ext3
+ echo ISOMNT=/cdrom
+ echo ROOTMNT=/root
+ echo HOSTFOLDER=/media/host/wubi
+ echo SUITE=
+ echo SETUPISO=
+ echo HOSTMNT=/media/host
+ echo ROOTDEV=/media/host/wubi/disks/system.virtual.disk
+ echo HOMEDEV=/media/host/wubi/disks/home.virtual.disk
+ echo SWAPDEV=/media/host/wubi/disks/swap.virtual.disk
+ echo EXTRADEV=
+ echo PAUSEFORDEBUG=n
+ [ -f /media/host/wubi/boot/lupin ]
+ pause_for_debug Zenigata End
+ cd /
+ cp_logs
+ [ -e /logs ]
+ mkdir /logs
+ cp /tmp/zenigata.log /logs/
+ [ -e /media/host/wubi ]
+ [ -e /media/host/wubi/logs ]
+ cp /tmp/zenigata.log /media/host/wubi/logs
+ [ n = y ]
+ return 0

*****

Please advise. :)

---

### Post by ago on 2007-09-17
try chkdsk /r from windows and defragmenting, also remove "quiet spalsh" from menu.lst in the wubi folder

---

### Post by The Exorcist on 2007-09-17
> **ago said:**
> try chkdsk /r from windows and defragmenting, also remove "quiet spalsh" from menu.lst in the wubi folder
Thanks, I had already done a ChkDsk and defragged.

The problem is now solved. It was caused by (over) compressing the NTFS C Drive, which was the only major Windows change that I had done to that drive between Kubuntu boots. I uncompressed the drive using this guide [http://pubs.logicalexpressions.com/Pub0009/LPMArticle.asp?ID=648](http://pubs.logicalexpressions.com/Pub0009/LPMArticle.asp?ID=648)

...ran ChkDsk and defragged again and now all is fine again.

Will not make that mistake again. :)

---

