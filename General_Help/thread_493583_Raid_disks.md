---
title: "Raid disks?"
date: 2007-07-05
forum: General Help
---

### Post by kkei08 on 2007-07-05
I used to get the error 17 message, but now I get to a point where it says loading...please wait for a few seconds then displays

"no RAID disks"

I can't find any solution online.

I ran chkdsk, too.

edit-after i let it idle for a while with the raid message, i got this:
"BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

/bin/shi can't access tty; job control turned off"

---

### Post by oxalá on 2007-07-05
yeah, i'm at the exact same point.

---

### Post by kkei08 on 2007-07-06
> **oxalá said:**
> yeah, i'm at the exact same point.

Surprising that I come across another person with the exact same problem so quickly, yet I can't find a comprehensive solution. 
Perhaps someone will come across us...let me know if you find anything.

---

### Post by ago on 2007-07-06
There are 2 log files /tmp/zenigata.log and /tmp/lupin.log. I'd need them both to understand what is the reason.

---

### Post by kkei08 on 2007-07-06
Where would I find those log files? A windows search didn't turn up anything.

---

### Post by ago on 2007-07-06
Do a fresh install.
If the error occurs late in the process, the programs are available under c:\wubi\logs. If you get a command prompt in linux, you can see the logs in the /tmp/ folder

---

### Post by kkei08 on 2007-07-06
It happens early in the install, so nothing appears in C:\wubi\logs

Is there a way to save the logs to that directory if they don't automatically store there, or will I have to transcribe the log contents by hand?

---

### Post by Baneat on 2007-08-25
Lupin.Log

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
+ SETUPISO=ubuntu-7.04-alternate-i386.iso
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
+ [ -n ubuntu-7.04-alternate-i386.iso ]
+ isodev=/media/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ [ -e /media/host/wubi/install/ubuntu-7.04-alternate-i386.iso ]
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

Zenigata.Log

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
+ SETUPISO=ubuntu-7.04-alternate-i386.iso
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
+ [ -b /dev/hda1 ]
+ check_fs /dev/hda1
+ dev=/dev/hda1
+ get_fs /dev/hda1
+ [ -n  ]
+ [ vfat = unknown ]
+ [ vfat = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1
+ [ -b /dev/hda2 ]
+ check_fs /dev/hda2
+ dev=/dev/hda2
+ get_fs /dev/hda2
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1 /dev/hda2
+ [ -b /dev/hda3 ]
+ check_fs /dev/hda3
+ dev=/dev/hda3
+ get_fs /dev/hda3
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hda5 ]
+ check_fs /dev/hda5
+ dev=/dev/hda5
+ get_fs /dev/hda5
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1 /dev/hda2 /dev/hda5
+ [ -b /dev/hda ]
+ check_fs /dev/hda
+ dev=/dev/hda
+ get_fs /dev/hda
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdc ]
+ check_fs /dev/hdc
+ dev=/dev/hdc
+ get_fs /dev/hdc
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ dev=/sys/block/hda/hda1
+ dev=/dev/hda1
+ [ -b /dev/hda1 ]
+ check_fs /dev/hda1
+ dev=/dev/hda1
+ get_fs /dev/hda1
+ [ -n  ]
+ [ vfat = unknown ]
+ [ vfat = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1 /dev/hda2 /dev/hda5 /dev/hda1
+ dev=/sys/block/hda/hda2
+ dev=/dev/hda2
+ [ -b /dev/hda2 ]
+ check_fs /dev/hda2
+ dev=/dev/hda2
+ get_fs /dev/hda2
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1 /dev/hda2 /dev/hda5 /dev/hda1 /dev/hda2
+ dev=/sys/block/hda/hda3
+ dev=/dev/hda3
+ [ -b /dev/hda3 ]
+ check_fs /dev/hda3
+ dev=/dev/hda3
+ get_fs /dev/hda3
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ dev=/sys/block/hda/hda5
+ dev=/dev/hda5
+ [ -b /dev/hda5 ]
+ check_fs /dev/hda5
+ dev=/dev/hda5
+ get_fs /dev/hda5
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/hda1 /dev/hda2 /dev/hda5 /dev/hda1 /dev/hda2 /dev/hda5
+ scan_devices /dev/hda1 /dev/hda2 /dev/hda5 /dev/hda1 /dev/hda2 /dev/hda5
+ devs=/dev/hda1 /dev/hda2 /dev/hda5 /dev/hda1 /dev/hda2 /dev/hda5
+ is_host_device /dev/hda1
+ dev=/dev/hda1
+ log_begin_msg Testing device /dev/hda1
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/hda1
+ _log_msg Begin: Testing device /dev/hda1 ...
+ echo Begin: Testing device /dev/hda1 ...
Begin: Testing device /dev/hda1 ...
+ safe_mount /dev/hda1 /media/host
+ dev=/dev/hda1
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ mkdir -p /media/host
+ umount /media/host
+ get_fs /dev/hda1
+ dev=/dev/hda1
+ FSTYPE=unknown
+ [ ! -b /dev/hda1 ]
+ /lib/udev/vol_id -t /dev/hda1
+ FSTYPE=vfat
+ [ -z vfat ]
+ mount -t auto /dev/hda1 /media/host
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
+ is_host_device /dev/hda2
+ dev=/dev/hda2
+ log_begin_msg Testing device /dev/hda2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/hda2
+ _log_msg Begin: Testing device /dev/hda2 ...
+ echo Begin: Testing device /dev/hda2 ...
Begin: Testing device /dev/hda2 ...
+ safe_mount /dev/hda2 /media/host
+ dev=/dev/hda2
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/hda2
+ dev=/dev/hda2
+ FSTYPE=unknown
+ [ ! -b /dev/hda2 ]
+ /lib/udev/vol_id -t /dev/hda2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/hda2 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg !!!!Found host device /dev/hda2!!!!
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
+ mount_host_dev /dev/hda2
+ hostdev=/dev/hda2
+ log_begin_msg Mounting /dev/hda2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting /dev/hda2
+ _log_msg Begin: Mounting /dev/hda2 ...
+ echo Begin: Mounting /dev/hda2 ...
Begin: Mounting /dev/hda2 ...
+ safe_mount /dev/hda2 /media/host rw
+ dev=/dev/hda2
+ mntpoint=/media/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/hda2
+ dev=/dev/hda2
+ FSTYPE=unknown
+ [ ! -b /dev/hda2 ]
+ /lib/udev/vol_id -t /dev/hda2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g -o rw /dev/hda2 /media/host
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
+ echo SETUPISO=ubuntu-7.04-alternate-i386.iso
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

I don't know whether this will help at all but i cant use Wubi and i get a similar message at some point but it does something else but then it  shows me a blank blue screen with a black bar. (Alt+F4 and things dont ever get any further than something about an eth0 not being wireless)

---

