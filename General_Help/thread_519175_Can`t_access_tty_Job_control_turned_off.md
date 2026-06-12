---
title: "Can`t access tty: Job control turned off"
date: 2007-08-06
forum: General Help
---

### Post by acehzo on 2007-08-06
Hi

First of all, I would like to say Thx for the great work on Wubi! Great idea, and it worked on my first laptop install with no problems. (IBM X41)  :KS

Now for the question... I have tried installing Ubuntu via Wubi but get the "Cant access tty: Job control turned off" or something like that after startup of Ubuntu... I have read most of the threads, but it does not seem like there is a answer that can solve the problem!
I am running a Sony Vaio VGN-AR21S Full HD Laptop, 200Gb HDD, Core 2 Duo 2Ghz, 2Gb Ram, Blue ray drive and NVidia Geforce go 7600(256MB dedicated gfx). :confused:

[B]Any help will be appreciated!  
[/B]
I have attached the log files content!

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
+ [ -f /media/host/wubi/install/edubuntu-7.04-server-i386.iso.metalink ]
+ [ -f /media/host/wubi/install/install.virtual.disk ]
+ [ -f /media/host/wubi/install/kubuntu-7.04-alternate-amd64.iso.metalink ]
+ [ -f /media/host/wubi/install/kubuntu-7.04-alternate-i386.iso.metalink ]
+ [ -f /media/host/wubi/install/lupin-devel-amd64.tar.bz2.metalink ]
+ [ -f /media/host/wubi/install/lupin-devel-amd64.zip.metalink ]
+ [ -f /media/host/wubi/install/preseed.cfg ]
+ [ -f /media/host/wubi/install/preseed.cfg.template ]
+ [ -f /media/host/wubi/install/ubuntu-7.04-alternate-amd64.iso.metalink ]
+ [ -f /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso.metalink ]
+ [ -f /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso ]
+ is_setup_iso /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso
+ isodev=/media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso
+ safe_mount /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso /cdrom
+ dev=/media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso
+ mntpoint=/cdrom
+ options=
+ [ -n  ]
+ check_mountpoint /cdrom
+ mntpoint=/cdrom
+ [ -d /cdrom ]
+ mkdir -p /cdrom
+ umount /cdrom
+ get_fs /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso
+ dev=/media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso
+ FSTYPE=unknown
+ [ ! -b /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso ]
+ [ ! -f /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso ]
+ /lib/udev/vol_id -t /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso
+ FSTYPE=iso9660
+ [ -z iso9660 ]
+ mount -t iso9660 /media/host/wubi/install/ubuntustudio-7.04-alternate-i386.iso /cdrom
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


-----------------------------------------------------
zenigata.log

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
+ [ -b /dev/mapper/control ]
+ [ -b /dev/mapper/isw_dbhfcidfcf_Volume0 ]
+ check_fs /dev/mapper/isw_dbhfcidfcf_Volume0
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume0
+ get_fs /dev/mapper/isw_dbhfcidfcf_Volume0
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/mapper/isw_dbhfcidfcf_Volume01 ]
+ check_fs /dev/mapper/isw_dbhfcidfcf_Volume01
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume01
+ get_fs /dev/mapper/isw_dbhfcidfcf_Volume01
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/isw_dbhfcidfcf_Volume01
+ [ -b /dev/mapper/isw_dbhfcidfcf_Volume02 ]
+ check_fs /dev/mapper/isw_dbhfcidfcf_Volume02
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume02
+ get_fs /dev/mapper/isw_dbhfcidfcf_Volume02
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02
+ [ -b /dev/mapper/isw_dbhfcidfcf_Volume05 ]
+ check_fs /dev/mapper/isw_dbhfcidfcf_Volume05
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume05
+ get_fs /dev/mapper/isw_dbhfcidfcf_Volume05
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02 /dev/mapper/isw_dbhfcidfcf_Volume05
+ [ -b /dev/sda1 ]
+ check_fs /dev/sda1
+ dev=/dev/sda1
+ get_fs /dev/sda1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02 /dev/mapper/isw_dbhfcidfcf_Volume05 /dev/sda1
+ [ -b /dev/sda2 ]
+ check_fs /dev/sda2
+ dev=/dev/sda2
+ get_fs /dev/sda2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/sda3 ]
+ check_fs /dev/sda3
+ dev=/dev/sda3
+ get_fs /dev/sda3
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
+ ALLDEVICES=/dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02 /dev/mapper/isw_dbhfcidfcf_Volume05 /dev/sda1 /dev/sda
+ [ -b /dev/sdb ]
+ check_fs /dev/sdb
+ dev=/dev/sdb
+ get_fs /dev/sdb
+ [ -n  ]
+ [ isw_raid_member = unknown ]
+ [ isw_raid_member = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02 /dev/mapper/isw_dbhfcidfcf_Volume05 /dev/sda1 /dev/sda /dev/sdb
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
+ ALLDEVICES=/dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02 /dev/mapper/isw_dbhfcidfcf_Volume05 /dev/sda1 /dev/sda /dev/sdb /dev/sda1
+ dev=/sys/block/sda/sda2
+ dev=/dev/sda2
+ [ -b /dev/sda2 ]
+ check_fs /dev/sda2
+ dev=/dev/sda2
+ get_fs /dev/sda2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ dev=/sys/block/sda/sda3
+ dev=/dev/sda3
+ [ -b /dev/sda3 ]
+ check_fs /dev/sda3
+ dev=/dev/sda3
+ get_fs /dev/sda3
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ scan_devices /dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02 /dev/mapper/isw_dbhfcidfcf_Volume05 /dev/sda1 /dev/sda /dev/sdb /dev/sda1
+ devs=/dev/mapper/isw_dbhfcidfcf_Volume01 /dev/mapper/isw_dbhfcidfcf_Volume02 /dev/mapper/isw_dbhfcidfcf_Volume05 /dev/sda1 /dev/sda /dev/sdb /dev/sda1
+ is_host_device /dev/mapper/isw_dbhfcidfcf_Volume01
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume01
+ log_begin_msg Testing device /dev/mapper/isw_dbhfcidfcf_Volume01
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/isw_dbhfcidfcf_Volume01
+ _log_msg Begin: Testing device /dev/mapper/isw_dbhfcidfcf_Volume01 ...
+ echo Begin: Testing device /dev/mapper/isw_dbhfcidfcf_Volume01 ...
Begin: Testing device /dev/mapper/isw_dbhfcidfcf_Volume01 ...
+ safe_mount /dev/mapper/isw_dbhfcidfcf_Volume01 /media/host
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume01
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ mkdir -p /media/host
+ umount /media/host
+ get_fs /dev/mapper/isw_dbhfcidfcf_Volume01
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume01
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/isw_dbhfcidfcf_Volume01 ]
+ /lib/udev/vol_id -t /dev/mapper/isw_dbhfcidfcf_Volume01
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/isw_dbhfcidfcf_Volume01 /media/host
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
+ is_host_device /dev/mapper/isw_dbhfcidfcf_Volume02
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume02
+ log_begin_msg Testing device /dev/mapper/isw_dbhfcidfcf_Volume02
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/isw_dbhfcidfcf_Volume02
+ _log_msg Begin: Testing device /dev/mapper/isw_dbhfcidfcf_Volume02 ...
+ echo Begin: Testing device /dev/mapper/isw_dbhfcidfcf_Volume02 ...
Begin: Testing device /dev/mapper/isw_dbhfcidfcf_Volume02 ...
+ safe_mount /dev/mapper/isw_dbhfcidfcf_Volume02 /media/host
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume02
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/isw_dbhfcidfcf_Volume02
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume02
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/isw_dbhfcidfcf_Volume02 ]
+ /lib/udev/vol_id -t /dev/mapper/isw_dbhfcidfcf_Volume02
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/isw_dbhfcidfcf_Volume02 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg !!!!Found host device /dev/mapper/isw_dbhfcidfcf_Volume02!!!!
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
+ mount_host_dev /dev/mapper/isw_dbhfcidfcf_Volume02
+ hostdev=/dev/mapper/isw_dbhfcidfcf_Volume02
+ log_begin_msg Mounting /dev/mapper/isw_dbhfcidfcf_Volume02
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting /dev/mapper/isw_dbhfcidfcf_Volume02
+ _log_msg Begin: Mounting /dev/mapper/isw_dbhfcidfcf_Volume02 ...
+ echo Begin: Mounting /dev/mapper/isw_dbhfcidfcf_Volume02 ...
Begin: Mounting /dev/mapper/isw_dbhfcidfcf_Volume02 ...
+ safe_mount /dev/mapper/isw_dbhfcidfcf_Volume02 /media/host rw
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume02
+ mntpoint=/media/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/isw_dbhfcidfcf_Volume02
+ dev=/dev/mapper/isw_dbhfcidfcf_Volume02
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/isw_dbhfcidfcf_Volume02 ]
+ /lib/udev/vol_id -t /dev/mapper/isw_dbhfcidfcf_Volume02
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g -o rw /dev/mapper/isw_dbhfcidfcf_Volume02 /media/host
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

---

### Post by acehzo on 2007-08-06
Doh! 

Forgot to mention that I am trying Ubuntu Studio... I have tried normal Ubuntu twice already with the same result!

Thx again!

---

### Post by ago on 2007-08-07
There should be another bit of lupin.log, the relevant part is the one that is missing. You need to look into the log in the tmp folder not the one in the logs folder, do a fresh installation and then when it stops run the command:

more /tmp/lupin.log

I have noticed though that you have some raid setup, so that might be the issue, you may want to try to install on a standard partition

---

