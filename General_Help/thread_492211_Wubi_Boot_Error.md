---
title: "Wubi Boot Error"
date: 2007-07-04
forum: General Help
---

### Post by TimmWubi on 2007-07-04
I'm a very new user of linux/ubuntu. 
I've tried to install Ubuntu with Wubi. After the installation i boot ubuntu, but it froze in. 
After 20minutes waiting i get this error:  /bin/sh: can't access tty: job control turned off
i don't know what that means, maybe someone can help me.

---

### Post by ago on 2007-07-04
Try to run chkdisk or equivalent from windows and try again. Wubi does not work if the ntfs partition is marked as dirty.

---

### Post by TimmWubi on 2007-07-05
I did this, but nothing happend. Maybe someone has an other idea, what i can do.

---

### Post by ago on 2007-07-05
can you provide me with the files in /tmp? there should be a couple of log files. You might also see them from windows under c:/wubi/logs (depends when the error occurs).

---

### Post by TimmWubi on 2007-07-06
i found these two log files:



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
+ ROOT=/media/host/wubi/install/install.virtual.disk
+ ROOTFLAGS=-o loop
+ ROOTFSTYPE=ext2
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
+ [ n = y ]
+ return 0
+ [ -n /media/host/wubi/disks/system.virtual.disk ]
+ [ /media/host/wubi/install/install.virtual.disk = /media/host/wubi/disks/system.virtual.disk ]
+ check_fs /media/host/wubi/disks/system.virtual.disk
+ dev=/media/host/wubi/disks/system.virtual.disk
+ get_fs /media/host/wubi/disks/system.virtual.disk
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ get_iso
+ [ -n  ]
+ log_warning_msg No Setup-ISO specified, looking for one
+ _log_msg Warning: No Setup-ISO specified, looking for one
+ echo Warning: No Setup-ISO specified, looking for one
Warning: No Setup-ISO specified, looking for one
+ [ -f /media/host/wubi/install/install.virtual.disk ]
+ [ -f /media/host/wubi/install/kubuntu-7.04-alternate-amd64.iso.metalink ]
+ [ -f /media/host/wubi/install/kubuntu-7.04-alternate-i386.iso.metalink ]
+ [ -f /media/host/wubi/install/lupin-devel-amd64.tar.bz2.metalink ]
+ [ -f /media/host/wubi/install/lupin-devel-amd64.zip.metalink ]
+ [ -f /media/host/wubi/install/preseed.cfg ]
+ [ -f /media/host/wubi/install/preseed.cfg.template ]
+ [ -f /media/host/wubi/install/ubuntu-7.04-alternate-amd64.iso.metalink ]
+ [ -f /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso ]
+ is_setup_iso /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ isodev=/media/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ safe_mount /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso /cdrom
+ dev=/media/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ mntpoint=/cdrom
+ options=
+ [ -n  ]
+ check_mountpoint /cdrom
+ mntpoint=/cdrom
+ [ -d /cdrom ]
+ mkdir -p /cdrom
+ umount /cdrom
+ get_fs /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ dev=/media/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ FSTYPE=unknown
+ [ ! -b /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso ]
+ [ ! -f /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso ]
+ /lib/udev/vol_id -t /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ FSTYPE=iso9660
+ [ -z iso9660 ]
+ mount -t iso9660 /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso /cdrom
+ [ -e /cdrom/.disk/info ]
+ [ -e /cdrom/install/vmlinuz ]
+ uname -r
+ grep -q 2.6.20-15-generic /cdrom/install/vmlinuz
+ return 0
+ pause_for_debug Live ISO
+ cd /
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /media/host/wubi ]
+ [ -e /media/host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /media/host/wubi/logs
+ [ n = y ]
+ return 0
+ [ -e /cdrom/casper/filesystem.squashfs ]
+ [ -e /cdrom/install/initrd.gz ]
+ pause_for_debug Alternate ISO
+ cd /
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /media/host/wubi ]
+ [ -e /media/host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /media/host/wubi/logs







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
+ [ -b /dev/sda1 ]
+ check_fs /dev/sda1
+ dev=/dev/sda1
+ get_fs /dev/sda1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1
+ [ -b /dev/sda2 ]
+ check_fs /dev/sda2
+ dev=/dev/sda2
+ get_fs /dev/sda2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/sda ]
+ check_fs /dev/sda
+ dev=/dev/sda
+ get_fs /dev/sda
+ [ -n  ]
+ [ isw_raid_member = unknown ]
+ [ isw_raid_member = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda
+ [ -b /dev/sdb ]
+ check_fs /dev/sdb
+ dev=/dev/sdb
+ get_fs /dev/sdb
+ [ -n  ]
+ [ isw_raid_member = unknown ]
+ [ isw_raid_member = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda /dev/sdb
+ [ -b /dev/mapper/isw_digaffgdce_RAID_Volume0 ]
+ check_fs /dev/mapper/isw_digaffgdce_RAID_Volume0
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume0
+ get_fs /dev/mapper/isw_digaffgdce_RAID_Volume0
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/mapper/isw_digaffgdce_RAID_Volume01 ]
+ check_fs /dev/mapper/isw_digaffgdce_RAID_Volume01
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume01
+ get_fs /dev/mapper/isw_digaffgdce_RAID_Volume01
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda /dev/sdb /dev/mapper/isw_digaffgdce_RAID_Volume01
+ [ -b /dev/mapper/isw_digaffgdce_RAID_Volume05 ]
+ check_fs /dev/mapper/isw_digaffgdce_RAID_Volume05
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume05
+ get_fs /dev/mapper/isw_digaffgdce_RAID_Volume05
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda /dev/sdb /dev/mapper/isw_digaffgdce_RAID_Volume01 /dev/mapper/isw_digaffgdce_RAID_Volume05
+ [ -b /dev/mapper/isw_digaffgdce_RAID_Volume06 ]
+ check_fs /dev/mapper/isw_digaffgdce_RAID_Volume06
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume06
+ get_fs /dev/mapper/isw_digaffgdce_RAID_Volume06
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda /dev/sdb /dev/mapper/isw_digaffgdce_RAID_Volume01 /dev/mapper/isw_digaffgdce_RAID_Volume05 /dev/mapper/isw_digaffgdce_RAID_Volume06
+ dev=/sys/block/sda/sda1
+ dev=/dev/sda1
+ [ -b /dev/sda1 ]
+ check_fs /dev/sda1
+ dev=/dev/sda1
+ get_fs /dev/sda1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda /dev/sdb /dev/mapper/isw_digaffgdce_RAID_Volume01 /dev/mapper/isw_digaffgdce_RAID_Volume05 /dev/mapper/isw_digaffgdce_RAID_Volume06 /dev/sda1
+ dev=/sys/block/sda/sda2
+ dev=/dev/sda2
+ [ -b /dev/sda2 ]
+ check_fs /dev/sda2
+ dev=/dev/sda2
+ get_fs /dev/sda2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ scan_devices /dev/sda1 /dev/sda /dev/sdb /dev/mapper/isw_digaffgdce_RAID_Volume01 /dev/mapper/isw_digaffgdce_RAID_Volume05 /dev/mapper/isw_digaffgdce_RAID_Volume06 /dev/sda1
+ devs=/dev/sda1 /dev/sda /dev/sdb /dev/mapper/isw_digaffgdce_RAID_Volume01 /dev/mapper/isw_digaffgdce_RAID_Volume05 /dev/mapper/isw_digaffgdce_RAID_Volume06 /dev/sda1
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
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/sda1 /media/host
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.
+ return 16
+ return 4
+ is_host_device /dev/sda
+ dev=/dev/sda
+ log_begin_msg Testing device /dev/sda
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/sda
+ _log_msg Begin: Testing device /dev/sda ...
+ echo Begin: Testing device /dev/sda ...
Begin: Testing device /dev/sda ...
+ safe_mount /dev/sda /media/host
+ dev=/dev/sda
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/sda
+ dev=/dev/sda
+ FSTYPE=unknown
+ [ ! -b /dev/sda ]
+ /lib/udev/vol_id -t /dev/sda
+ FSTYPE=isw_raid_member
+ [ -z isw_raid_member ]
+ mount -t auto /dev/sda /media/host
mount: Mounting /dev/sda on /media/host failed: Device or resource busy
+ return 16
+ return 4
+ is_host_device /dev/sdb
+ dev=/dev/sdb
+ log_begin_msg Testing device /dev/sdb
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/sdb
+ _log_msg Begin: Testing device /dev/sdb ...
+ echo Begin: Testing device /dev/sdb ...
Begin: Testing device /dev/sdb ...
+ safe_mount /dev/sdb /media/host
+ dev=/dev/sdb
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/sdb
+ dev=/dev/sdb
+ FSTYPE=unknown
+ [ ! -b /dev/sdb ]
+ /lib/udev/vol_id -t /dev/sdb
+ FSTYPE=isw_raid_member
+ [ -z isw_raid_member ]
+ mount -t auto /dev/sdb /media/host
mount: Mounting /dev/sdb on /media/host failed: Device or resource busy
+ return 16
+ return 4
+ is_host_device /dev/mapper/isw_digaffgdce_RAID_Volume01
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume01
+ log_begin_msg Testing device /dev/mapper/isw_digaffgdce_RAID_Volume01
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/isw_digaffgdce_RAID_Volume01
+ _log_msg Begin: Testing device /dev/mapper/isw_digaffgdce_RAID_Volume01 ...
+ echo Begin: Testing device /dev/mapper/isw_digaffgdce_RAID_Volume01 ...
Begin: Testing device /dev/mapper/isw_digaffgdce_RAID_Volume01 ...
+ safe_mount /dev/mapper/isw_digaffgdce_RAID_Volume01 /media/host
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume01
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/isw_digaffgdce_RAID_Volume01
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume01
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/isw_digaffgdce_RAID_Volume01 ]
+ /lib/udev/vol_id -t /dev/mapper/isw_digaffgdce_RAID_Volume01
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/isw_digaffgdce_RAID_Volume01 /media/host
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
+ is_host_device /dev/mapper/isw_digaffgdce_RAID_Volume05
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume05
+ log_begin_msg Testing device /dev/mapper/isw_digaffgdce_RAID_Volume05
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/isw_digaffgdce_RAID_Volume05
+ _log_msg Begin: Testing device /dev/mapper/isw_digaffgdce_RAID_Volume05 ...
+ echo Begin: Testing device /dev/mapper/isw_digaffgdce_RAID_Volume05 ...
Begin: Testing device /dev/mapper/isw_digaffgdce_RAID_Volume05 ...
+ safe_mount /dev/mapper/isw_digaffgdce_RAID_Volume05 /media/host
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume05
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/isw_digaffgdce_RAID_Volume05
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume05
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/isw_digaffgdce_RAID_Volume05 ]
+ /lib/udev/vol_id -t /dev/mapper/isw_digaffgdce_RAID_Volume05
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/isw_digaffgdce_RAID_Volume05 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg !!!!Found host device /dev/mapper/isw_digaffgdce_RAID_Volume05!!!!
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
+ mount_host_dev /dev/mapper/isw_digaffgdce_RAID_Volume05
+ hostdev=/dev/mapper/isw_digaffgdce_RAID_Volume05
+ log_begin_msg Mounting /dev/mapper/isw_digaffgdce_RAID_Volume05
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting /dev/mapper/isw_digaffgdce_RAID_Volume05
+ _log_msg Begin: Mounting /dev/mapper/isw_digaffgdce_RAID_Volume05 ...
+ echo Begin: Mounting /dev/mapper/isw_digaffgdce_RAID_Volume05 ...
Begin: Mounting /dev/mapper/isw_digaffgdce_RAID_Volume05 ...
+ safe_mount /dev/mapper/isw_digaffgdce_RAID_Volume05 /media/host rw
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume05
+ mntpoint=/media/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/isw_digaffgdce_RAID_Volume05
+ dev=/dev/mapper/isw_digaffgdce_RAID_Volume05
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/isw_digaffgdce_RAID_Volume05 ]
+ /lib/udev/vol_id -t /dev/mapper/isw_digaffgdce_RAID_Volume05
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g -o rw /dev/mapper/isw_digaffgdce_RAID_Volume05 /media/host
+ HOSTFOLDER=/wubi/boot
+ HOSTFOLDER=/wubi
+ [ /wubi = / ]
+ HOSTFOLDER=/media/host/wubi
+ grep /media/host /proc/mounts
+ grep -q rw
+ 
+ return 0
+ rm_logs
+ [ -e /media/host/wubi/logs ]
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
+ [ unknown = unknown ]
+ return 19
+ ROOT=/media/host/wubi/install/install.virtual.disk
+ FSTYPE=ext2
+ [ -n  ]
+ ROOTFLAGS=-o loop
+ echo ROOT=/media/host/wubi/install/install.virtual.disk
+ echo ROOTFLAGS='-o loop'
+ echo ROOTFSTYPE=ext2
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
+ mkdir -p /media/host/wubi/logs
+ cp /tmp/zenigata.log /media/host/wubi/logs
+ [ n = y ]
+ return 0













But i don't understand them!

---

### Post by ago on 2007-07-06
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

---

### Post by TimmWubi on 2007-07-06
" This volume is used by an other porcess . should it be checked when the system boots?
Type Yes oder No"

when i type yes, nothing happens.

---

### Post by mikewhatever on 2007-07-06
> should it be checked when the system boots?
Obviously, you have to reboot.

---

### Post by ago on 2007-07-06
If it still does not work can you also provide lupin.log?

---

### Post by TimmWubi on 2007-07-06
ok, now did this. windows checked the system. after reboot, i booted ubuntu and get the same error:
"/bin/sh: can't access tty: job control turned off"

---

### Post by TimmWubi on 2007-07-06
i just notices that the computer only checks partiton c:, but wubi is on partition d:
is this a problem?

---

### Post by szaka on 2007-07-06
> **ago said:**
> NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.
This is part of WUBI's NTFS volume autodetection. Mount failed because only a strip was tested, not the full RAID device. NTFS was mounted fine later on when the RAID was setup properly, as I can see it.

The ntfs-3g error message is misleading. Typically open(2) returns ENODEV for RAID strips but here the kernel RAID driver allowed to open the device, sadly. I don't know how ntfs-3g could detect the incorrect mount usage and warn the user to mount the proper device under /dev/mapper, not the incorrect /dev/sdaX strips in such cases. This is an unfortunate kernel, isw device driver bug. I can only add to the ntfs-3g error message that the user may have RAID and needs to mount a different device.

---

### Post by ago on 2007-07-06
> **szaka said:**
> This is part of WUBI's NTFS volume autodetection. Mount failed because only a strip was tested, not the full RAID device. NTFS was mounted fine later on when the RAID was setup properly, as I can see it.

The ntfs-3g error message is misleading. Typically open(2) returns ENODEV for RAID strips but here the kernel RAID driver allowed to open the device, sadly. I don't know how ntfs-3g could detect the incorrect mount usage and warn the user to mount the proper device under /dev/mapper, not the incorrect /dev/sdaX strips in such cases. This is an unfortunate kernel, isw device driver bug. I can only add to the ntfs-3g error message that the user may have RAID and needs to mount a different device.

I can test /dev/mapper/XYZ before /dev/sdaX. Will it help?

---

### Post by szaka on 2007-07-07
> **ago said:**
> I can test /dev/mapper/XYZ before /dev/sdaX. Will it help?
Sounds like a good idea. 

It would be also nice to know what devices /dev/mapper/XYZ uses.

---

### Post by ago on 2007-07-08
> **szaka said:**
> Sounds like a good idea. 

It would be also nice to know what devices /dev/mapper/XYZ uses.

I have a simple algorithm: for each device in the folders I pass, it checks whether it is a block device, then whether there appears to be a filesystem on it, then it tries to mount it and runs the required tests. I'll change the order so that /dev/mapper/* is tested upfront. Thanks for the tip.

---

