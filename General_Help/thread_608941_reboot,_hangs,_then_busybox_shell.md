---
title: "reboot, hangs, then busybox shell"
date: 2007-11-10
forum: General Help
---

### Post by s9am_me on 2007-11-10
trying to install ubuntu studio on my computer.  Install went fine I think, I left it on over night.  Then I reboot my comp to boot into ubuntu.  I get a splash screen but it hangs after about 10 seconds then it brings me to a shell prompt where it says "can't access tty job control" or something along those lines.  I tried doing a chkdsk /f on both of my partitions and still the same problem.  Drive C: is my windows xp partition, and drive D: is all my personal files which I have installed Wubi on.

Opteron 2.6Ghz
2GB RAM
two 500GB hard drives in RAID 0
two dvd drives
ATI x1800xt video card

here are my logs if you guys can make some sense into them:

lupin.log
```
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

```

zenigata.log
```
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
+ [ -b /dev/mapper/nvidia_cffebffg ]
+ check_fs /dev/mapper/nvidia_cffebffg
+ dev=/dev/mapper/nvidia_cffebffg
+ get_fs /dev/mapper/nvidia_cffebffg
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/mapper/nvidia_cffebffg1 ]
+ check_fs /dev/mapper/nvidia_cffebffg1
+ dev=/dev/mapper/nvidia_cffebffg1
+ get_fs /dev/mapper/nvidia_cffebffg1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1
+ [ -b /dev/mapper/nvidia_cffebffg2 ]
+ check_fs /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ get_fs /dev/mapper/nvidia_cffebffg2
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2
+ [ -b /dev/sdb1 ]
+ check_fs /dev/sdb1
+ dev=/dev/sdb1
+ get_fs /dev/sdb1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1
+ [ -b /dev/sdb2 ]
+ check_fs /dev/sdb2
+ dev=/dev/sdb2
+ get_fs /dev/sdb2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hda ]
+ check_fs /dev/hda
+ dev=/dev/hda
+ get_fs /dev/hda
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hdb ]
+ check_fs /dev/hdb
+ dev=/dev/hdb
+ get_fs /dev/hdb
+ [ -n  ]
+ [ iso9660 = unknown ]
+ [ iso9660 = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hdb
+ [ -b /dev/sda ]
+ check_fs /dev/sda
+ dev=/dev/sda
+ get_fs /dev/sda
+ [ -n  ]
+ [ nvidia_raid_member = unknown ]
+ [ nvidia_raid_member = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hdb /dev/sda
+ [ -b /dev/sdb ]
+ check_fs /dev/sdb
+ dev=/dev/sdb
+ get_fs /dev/sdb
+ [ -n  ]
+ [ nvidia_raid_member = unknown ]
+ [ nvidia_raid_member = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hdb /dev/sda /dev/sdb
+ dev=/sys/block/sdb/sdb1
+ dev=/dev/sdb1
+ [ -b /dev/sdb1 ]
+ check_fs /dev/sdb1
+ dev=/dev/sdb1
+ get_fs /dev/sdb1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hdb /dev/sda /dev/sdb /dev/sdb1
+ dev=/sys/block/sdb/sdb2
+ dev=/dev/sdb2
+ [ -b /dev/sdb2 ]
+ check_fs /dev/sdb2
+ dev=/dev/sdb2
+ get_fs /dev/sdb2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ scan_devices /dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hdb /dev/sda /dev/sdb /dev/sdb1
+ devs=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hdb /dev/sda /dev/sdb /dev/sdb1
+ is_host_device /dev/mapper/nvidia_cffebffg1
+ dev=/dev/mapper/nvidia_cffebffg1
+ log_begin_msg Testing device /dev/mapper/nvidia_cffebffg1
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/nvidia_cffebffg1
+ _log_msg Begin: Testing device /dev/mapper/nvidia_cffebffg1 ...
+ echo Begin: Testing device /dev/mapper/nvidia_cffebffg1 ...
Begin: Testing device /dev/mapper/nvidia_cffebffg1 ...
+ safe_mount /dev/mapper/nvidia_cffebffg1 /media/host
+ dev=/dev/mapper/nvidia_cffebffg1
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ mkdir -p /media/host
+ umount /media/host
+ get_fs /dev/mapper/nvidia_cffebffg1
+ dev=/dev/mapper/nvidia_cffebffg1
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/nvidia_cffebffg1 ]
+ /lib/udev/vol_id -t /dev/mapper/nvidia_cffebffg1
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/nvidia_cffebffg1 /media/host
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
+ is_host_device /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ log_begin_msg Testing device /dev/mapper/nvidia_cffebffg2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/nvidia_cffebffg2
+ _log_msg Begin: Testing device /dev/mapper/nvidia_cffebffg2 ...
+ echo Begin: Testing device /dev/mapper/nvidia_cffebffg2 ...
Begin: Testing device /dev/mapper/nvidia_cffebffg2 ...
+ safe_mount /dev/mapper/nvidia_cffebffg2 /media/host
+ dev=/dev/mapper/nvidia_cffebffg2
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/nvidia_cffebffg2 ]
+ /lib/udev/vol_id -t /dev/mapper/nvidia_cffebffg2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/nvidia_cffebffg2 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg !!!!Found host device /dev/mapper/nvidia_cffebffg2!!!!
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
+ mount_host_dev /dev/mapper/nvidia_cffebffg2
+ hostdev=/dev/mapper/nvidia_cffebffg2
+ log_begin_msg Mounting /dev/mapper/nvidia_cffebffg2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting /dev/mapper/nvidia_cffebffg2
+ _log_msg Begin: Mounting /dev/mapper/nvidia_cffebffg2 ...
+ echo Begin: Mounting /dev/mapper/nvidia_cffebffg2 ...
Begin: Mounting /dev/mapper/nvidia_cffebffg2 ...
+ safe_mount /dev/mapper/nvidia_cffebffg2 /media/host rw
+ dev=/dev/mapper/nvidia_cffebffg2
+ mntpoint=/media/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/nvidia_cffebffg2 ]
+ /lib/udev/vol_id -t /dev/mapper/nvidia_cffebffg2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g -o rw /dev/mapper/nvidia_cffebffg2 /media/host
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

```

thanks for the help!

---

### Post by s9am_me on 2007-11-13
any ideas?  I'm starting to think its my RAID set up.  Tried Wubi on an old Dell computer and worked just fine.

---

### Post by ago on 2007-11-13
Can you try 7.10 with regular ubuntu?

---

### Post by s9am_me on 2007-11-15
> **ago said:**
> Can you try 7.10 with regular ubuntu?

i'll try that tonight

---

### Post by iNeedHelp3 on 2007-11-16
I have The same problem, I tried to install Kubuntu on my D: drive, and everything seems to install ok.
after the first reboot (to start the iso of the Live-CD) everything installs ok, but after the second Reboot (after Kubuntu is completely installed) I get a splash screen, and it falls back to the Busybox shell
with the prompt: (initramfs)
I have tried build 384 and 386, both with the same problem.
I don't have a raid configuration  (although my Motherboard supports Raid), so I don't think this could be the problem, but I am trying to install on my D: drive

Athlon 2000+
two HD 80GB each 
Nvidea Geforce4 Ti4200

---

### Post by s9am_me on 2007-11-17
ok I tried regular Ubuntu and it still doing the same thing.  Exactly as described by Ineedhelp3.  Here are my logs

lupin.log
```
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

```

zenigata.log
```
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
+ [ -b /dev/mapper/nvidia_cffebffg ]
+ check_fs /dev/mapper/nvidia_cffebffg
+ dev=/dev/mapper/nvidia_cffebffg
+ get_fs /dev/mapper/nvidia_cffebffg
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/mapper/nvidia_cffebffg1 ]
+ check_fs /dev/mapper/nvidia_cffebffg1
+ dev=/dev/mapper/nvidia_cffebffg1
+ get_fs /dev/mapper/nvidia_cffebffg1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1
+ [ -b /dev/mapper/nvidia_cffebffg2 ]
+ check_fs /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ get_fs /dev/mapper/nvidia_cffebffg2
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2
+ [ -b /dev/sdb1 ]
+ check_fs /dev/sdb1
+ dev=/dev/sdb1
+ get_fs /dev/sdb1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1
+ [ -b /dev/sdb2 ]
+ check_fs /dev/sdb2
+ dev=/dev/sdb2
+ get_fs /dev/sdb2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ [ -b /dev/hda ]
+ check_fs /dev/hda
+ dev=/dev/hda
+ get_fs /dev/hda
+ [ -n  ]
+ [ udf = unknown ]
+ [ udf = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hda
+ [ -b /dev/hdb ]
+ check_fs /dev/hdb
+ dev=/dev/hdb
+ get_fs /dev/hdb
+ [ -n  ]
+ [ udf = unknown ]
+ [ udf = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hda /dev/hdb
+ [ -b /dev/sda ]
+ check_fs /dev/sda
+ dev=/dev/sda
+ get_fs /dev/sda
+ [ -n  ]
+ [ nvidia_raid_member = unknown ]
+ [ nvidia_raid_member = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hda /dev/hdb /dev/sda
+ [ -b /dev/sdb ]
+ check_fs /dev/sdb
+ dev=/dev/sdb
+ get_fs /dev/sdb
+ [ -n  ]
+ [ nvidia_raid_member = unknown ]
+ [ nvidia_raid_member = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hda /dev/hdb /dev/sda /dev/sdb
+ dev=/sys/block/sdb/sdb1
+ dev=/dev/sdb1
+ [ -b /dev/sdb1 ]
+ check_fs /dev/sdb1
+ dev=/dev/sdb1
+ get_fs /dev/sdb1
+ [ -n  ]
+ [ ntfs = unknown ]
+ [ ntfs = swap ]
+ return 0
+ ALLDEVICES=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hda /dev/hdb /dev/sda /dev/sdb /dev/sdb1
+ dev=/sys/block/sdb/sdb2
+ dev=/dev/sdb2
+ [ -b /dev/sdb2 ]
+ check_fs /dev/sdb2
+ dev=/dev/sdb2
+ get_fs /dev/sdb2
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ scan_devices /dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hda /dev/hdb /dev/sda /dev/sdb /dev/sdb1
+ devs=/dev/mapper/nvidia_cffebffg1 /dev/mapper/nvidia_cffebffg2 /dev/sdb1 /dev/hda /dev/hdb /dev/sda /dev/sdb /dev/sdb1
+ is_host_device /dev/mapper/nvidia_cffebffg1
+ dev=/dev/mapper/nvidia_cffebffg1
+ log_begin_msg Testing device /dev/mapper/nvidia_cffebffg1
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/nvidia_cffebffg1
+ _log_msg Begin: Testing device /dev/mapper/nvidia_cffebffg1 ...
+ echo Begin: Testing device /dev/mapper/nvidia_cffebffg1 ...
Begin: Testing device /dev/mapper/nvidia_cffebffg1 ...
+ safe_mount /dev/mapper/nvidia_cffebffg1 /media/host
+ dev=/dev/mapper/nvidia_cffebffg1
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ mkdir -p /media/host
+ umount /media/host
+ get_fs /dev/mapper/nvidia_cffebffg1
+ dev=/dev/mapper/nvidia_cffebffg1
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/nvidia_cffebffg1 ]
+ /lib/udev/vol_id -t /dev/mapper/nvidia_cffebffg1
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/nvidia_cffebffg1 /media/host
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
+ is_host_device /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ log_begin_msg Testing device /dev/mapper/nvidia_cffebffg2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/mapper/nvidia_cffebffg2
+ _log_msg Begin: Testing device /dev/mapper/nvidia_cffebffg2 ...
+ echo Begin: Testing device /dev/mapper/nvidia_cffebffg2 ...
Begin: Testing device /dev/mapper/nvidia_cffebffg2 ...
+ safe_mount /dev/mapper/nvidia_cffebffg2 /media/host
+ dev=/dev/mapper/nvidia_cffebffg2
+ mntpoint=/media/host
+ options=
+ [ -n  ]
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/nvidia_cffebffg2 ]
+ /lib/udev/vol_id -t /dev/mapper/nvidia_cffebffg2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g /dev/mapper/nvidia_cffebffg2 /media/host
+ [ -n /wubi/boot/linux ]
+ [ -f /media/host/wubi/boot/linux ]
+ log_end_msg !!!!Found host device /dev/mapper/nvidia_cffebffg2!!!!
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
+ mount_host_dev /dev/mapper/nvidia_cffebffg2
+ hostdev=/dev/mapper/nvidia_cffebffg2
+ log_begin_msg Mounting /dev/mapper/nvidia_cffebffg2
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting /dev/mapper/nvidia_cffebffg2
+ _log_msg Begin: Mounting /dev/mapper/nvidia_cffebffg2 ...
+ echo Begin: Mounting /dev/mapper/nvidia_cffebffg2 ...
Begin: Mounting /dev/mapper/nvidia_cffebffg2 ...
+ safe_mount /dev/mapper/nvidia_cffebffg2 /media/host rw
+ dev=/dev/mapper/nvidia_cffebffg2
+ mntpoint=/media/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /media/host
+ mntpoint=/media/host
+ [ -d /media/host ]
+ umount /media/host
+ get_fs /dev/mapper/nvidia_cffebffg2
+ dev=/dev/mapper/nvidia_cffebffg2
+ FSTYPE=unknown
+ [ ! -b /dev/mapper/nvidia_cffebffg2 ]
+ /lib/udev/vol_id -t /dev/mapper/nvidia_cffebffg2
+ FSTYPE=ntfs
+ [ -z ntfs ]
+ ntfs-3g -o rw /dev/mapper/nvidia_cffebffg2 /media/host
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

```

---

### Post by ago on 2007-11-19
7.10 is here [http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

---

### Post by s9am_me on 2007-11-20
ok I tried 7.10.  Ran the installer and after downloading the iso file I rebooted.  Upon reboot it showed the ubuntu splash screen then I got the busybox shell prompt about 5 secs later.  It doesn't even install like 7.04

---

### Post by ago on 2007-11-20
cat /casper.log
and report any error msg

---

### Post by Alef Auman on 2007-12-25
I've the same error.
The output of the log is:
stdin: I/O error
Unable to find a medium containing a live file system

---

### Post by Momule on 2007-12-25
Similar problem for me. might want to check out this thread:

7.10 on old bios HD limited system

busybox with hangup at boot

hope helps you guys too...

---

### Post by David_91 on 2008-01-07
i have the exact same problem, i dunno what this is (total newb) so im stuck.

any actual help?

---

### Post by s.jesudasan on 2008-01-08
i too get the same shell with 
my harddisk unable to mount message

---

### Post by ago on 2008-01-08
At the countdown press esc
Select the verbose mode
At the prompt type:

cat /tmp/initramfs*

post here any relevant error message

---

### Post by David_91 on 2008-01-10
what do you mean at the Countdown?

the Ubuntu loading bar?

---

### Post by ago on 2008-01-10
Before that there should be a 3 sec countdown, 3...2...1...

---

### Post by hibajugala on 2008-01-12
i feel like im adding to spam, but I also have the same error.

Ive tried ubuntu studio as well as 7.10 and it does the same thing

---

