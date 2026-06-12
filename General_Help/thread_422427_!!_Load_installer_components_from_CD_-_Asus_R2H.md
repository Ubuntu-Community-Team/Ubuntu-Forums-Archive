---
title: "!! Load installer components from CD - Asus R2H"
date: 2007-04-25
forum: General Help
---

### Post by dhns on 2007-04-25
Hi,

I am trying to install wubi/Ubuntu from the network on an Asus R2H with WinXP using the minefield2 installer.

It perfectly loads the files, prepared everything and starts GRUB and booting. After some installation steps it shows a red screen with these messages:

!! Load installer components from CD
Installation step failed
An installation step failed. You can try to run the failing item
again from the menu, or skip it and choose something else. The
failing step is: Load installer components from CD

<Continue>

The previous step "Detect and mount CD-ROM" apparently works for the iso image on my HDD.

So, what could be the reason? What could I try or do differently?

Nikolaus

---

### Post by ecology2007 on 2007-04-25
If you are sure ubuntu 7.04 is supposed to work on it, and if the actual installation started (semi gui screens) :
1-post the files you find in wubi/logs
2-save the iso file in wubi/install next to wubi.exe, so you won t have to download it again.
3-you have to fully uninstall wubi after each failed install attempt using using windows add/remove, running wubi again, or uninstall.exe in wubi folder.
4-If another try does not solve the issue, search or post in the general forum for this asus r2h known issues with ubuntu 7.04.

---

### Post by ldm1979 on 2007-04-25
Got the same thing With Windows 2000

---

### Post by dhns on 2007-04-26
> **ecology2007 said:**
> If you are sure ubuntu 7.04 is supposed to work on it, and if the actual
Well, how should I know before isuccessfully installing?> 
 installation started (semi gui screens) :
1-post the files you find in wubi/logs

Zenigata:
> 
+ PREREQ=
+ ROOTMNT=/root
+ HOSTMNT=/host
+ HOSTFOLDER=
+ ISOMNT=/cdrom
+ HOSTKEY=
+ SUITE=
+ DEFAULTSUITE=feisty dapper unstable testing stable
+ SETUP_INIT=busybox init
+ SETUPISO=
+ ROOTIMG=root.img
+ HOMEIMG=home.img
+ SWAPIMG=swap.img
+ EXTRAIMG=extra.img
+ ROOTDEV=/dev/loop7
+ HOMEDEV=/dev/loop6
+ SWAPDEV=/dev/loop5
+ EXTRADEV=/dev/loop4
+ USEFREESPACE=
+ PAUSEFORDEBUG=n
+ cat /proc/cmdline
+ HOSTKEY=/wubi/linux
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_LOOP_ROOT=6
+ ERR_LOOP_HOME=7
+ ERR_LOOP_SWAP=8
+ ERR_LOOP_EXTRA=9
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_LOOP_ISO=13
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
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
+ [ -n /wubi/linux ]
+ log_begin_msg Loking for /wubi/linux
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Loking for /wubi/linux
+ _log_msg Begin: Loking for /wubi/linux ...
+ echo Begin: Loking for /wubi/linux ...
Begin: Loking for /wubi/linux ...
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
+ [ vfat = unknown ]
+ [ vfat = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda2
+ check_fs /dev/sda3
+ dev=/dev/sda3
+ get_fs /dev/sda3
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ check_fs /dev/sda5
+ dev=/dev/sda5
+ get_fs /dev/sda5
+ [ -n  ]
+ [ vfat = unknown ]
+ [ vfat = swap ]
+ return 0
+ ALLDEVICES=/dev/sda1 /dev/sda2 /dev/sda5
+ check_fs /dev/sda
+ dev=/dev/sda
+ get_fs /dev/sda
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ scan_devices /dev/sda1 /dev/sda2 /dev/sda5
+ devs=/dev/sda1 /dev/sda2 /dev/sda5
+ is_host_device /dev/sda1
+ dev=/dev/sda1
+ log_begin_msg Testing device /dev/sda1
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Testing device /dev/sda1
+ _log_msg Begin: Testing device /dev/sda1 ...
+ echo Begin: Testing device /dev/sda1 ...
Begin: Testing device /dev/sda1 ...
+ safe_mount /dev/sda1 /host
+ dev=/dev/sda1
+ mntpoint=/host
+ options=
+ [ -n  ]
+ check_mountpoint /host
+ mntpoint=/host
+ [ -d /host ]
+ mkdir -p /host
+ umount /host
+ get_fs /dev/sda1
+ dev=/dev/sda1
+ FSTYPE=
+ FSSIZE=
+ [ ! -b /dev/sda1 ]
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ -z unknown ]
+ [ unknown = unknown ]
+ [ -x /lib/udev/vol_id ]
+ /lib/udev/vol_id -t /dev/sda1
+ FSTYPE=vfat
+ [ -z vfat ]
+ [ vfat = unknown ]
+ [ -z vfat ]
+ mount -t auto /dev/sda1 /host
+ [ -n /wubi/linux ]
+ [ -f /host/wubi/linux ]
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
+ safe_mount /dev/sda2 /host
+ dev=/dev/sda2
+ mntpoint=/host
+ options=
+ [ -n  ]
+ check_mountpoint /host
+ mntpoint=/host
+ [ -d /host ]
+ umount /host
+ get_fs /dev/sda2
+ dev=/dev/sda2
+ FSTYPE=
+ FSSIZE=
+ [ ! -b /dev/sda2 ]
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ -z unknown ]
+ [ unknown = unknown ]
+ [ -x /lib/udev/vol_id ]
+ /lib/udev/vol_id -t /dev/sda2
+ FSTYPE=vfat
+ [ -z vfat ]
+ [ vfat = unknown ]
+ [ -z vfat ]
+ mount -t auto /dev/sda2 /host
+ [ -n /wubi/linux ]
+ [ -f /host/wubi/linux ]
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
+ safe_mount /dev/sda2 /host rw
+ dev=/dev/sda2
+ mntpoint=/host
+ options=rw
+ [ -n rw ]
+ options=-o rw
+ check_mountpoint /host
+ mntpoint=/host
+ [ -d /host ]
+ umount /host
+ get_fs /dev/sda2
+ dev=/dev/sda2
+ FSTYPE=
+ FSSIZE=
+ [ ! -b /dev/sda2 ]
+ fstype
+ eval FSTYPE=unknown FSSIZE=0
+ FSTYPE=unknown FSSIZE=0
+ [ -z unknown ]
+ [ unknown = unknown ]
+ [ -x /lib/udev/vol_id ]
+ /lib/udev/vol_id -t /dev/sda2
+ FSTYPE=vfat
+ [ -z vfat ]
+ [ vfat = unknown ]
+ [ -z vfat ]
+ mount -t auto -o rw /dev/sda2 /host
+ HOSTFOLDER=/wubi
+ [ /wubi = / ]
+ HOSTFOLDER=/host/wubi
+ return 0
+ rm_logs
+ [ -e /host/wubi/logs ]
+ get_target_devices
+ make_loop_devs
+ [ -b /dev/loop7 ]
+ return 0
+ [  = y ]
+ [ -f /host/wubi/disks/root.img ]
+ losetup /dev/loop7 /host/wubi/disks/root.img
+ [ -f /host/wubi/disks/swap.img ]
+ losetup /dev/loop5 /host/wubi/disks/swap.img
+ [ -f /host/wubi/disks/home.img ]
+ losetup /dev/loop6 /host/wubi/disks/home.img
+ [ -f /host/wubi/disks/extra.img ]
+ return 0
+ ROOTFSTYPE=ext3
+ echo ROOT=/dev/loop7
+ echo ROOTFSTYPE=ext3
+ echo ROOTDEV=/dev/loop7
+ echo ISOMNT=/cdrom
+ echo ROOTMNT=/root
+ echo HOSTFOLDER=/host/wubi
+ echo SUITE=
+ echo SETUPISO=
+ echo HOSTMNT=/host
+ echo ROOTDEV=/dev/loop7
+ echo HOMEDEV=/dev/loop6
+ echo SWAPDEV=/dev/loop5
+ echo EXTRADEV=/dev/loop4
+ echo PAUSEFORDEBUG=n
+ [ -f /host/wubi/boot/lupin ]


lupin:
> 
+ PREREQ=
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_LOOP_ROOT=6
+ ERR_LOOP_HOME=7
+ ERR_LOOP_SWAP=8
+ ERR_LOOP_EXTRA=9
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_LOOP_ISO=13
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
+ . /conf/param.conf
+ ROOT=/dev/loop7
+ ROOTFSTYPE=ext3
+ ROOTDEV=/dev/loop7
+ ISOMNT=/cdrom
+ ROOTMNT=/root
+ HOSTFOLDER=/host/wubi
+ SUITE=
+ SETUPISO=
+ HOSTMNT=/host
+ ROOTDEV=/dev/loop7
+ HOMEDEV=/dev/loop6
+ SWAPDEV=/dev/loop5
+ EXTRADEV=/dev/loop4
+ PAUSEFORDEBUG=n
+ pause_for_debug
+ cd /
+ cp_logs
+ [ -e /logs ]
+ mkdir /logs
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ mkdir /host/wubi/logs
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs
+ [ n = y ]
+ return 0
+ grep -q /dev/loop7 /proc/mounts
+ check_fs /dev/loop7
+ dev=/dev/loop7
+ get_fs /dev/loop7
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ get_iso
+ [ -n  ]
+ log_warning_msg No Setup-ISO specified, looking for one
+ _log_msg Warning: No Setup-ISO specified, looking for one
+ echo Warning: No Setup-ISO specified, looking for one
Warning: No Setup-ISO specified, looking for one
+ [ -f /host/wubi/install/preseed.cfg ]
+ [ -f /host/wubi/install/preseed.cfg.template ]
+ [ -f /host/wubi/install/ubuntu-7.04-alternate-i386.iso ]
+ is_setup_iso /host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ isodev=/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ safe_mount /host/wubi/install/ubuntu-7.04-alternate-i386.iso /cdrom
+ dev=/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ mntpoint=/cdrom
+ options=
+ [ -n  ]
+ check_mountpoint /cdrom
+ mntpoint=/cdrom
+ [ -d /cdrom ]
+ mkdir -p /cdrom
+ umount /cdrom
+ get_fs /host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ dev=/host/wubi/install/ubuntu-7.04-alternate-i386.iso
+ FSTYPE=
+ FSSIZE=
+ [ ! -b /host/wubi/install/ubuntu-7.04-alternate-i386.iso ]
+ [ ! -f /host/wubi/install/ubuntu-7.04-alternate-i386.iso ]
+ fstype
+ eval FSTYPE=iso9660 FSSIZE=0
+ FSTYPE=iso9660 FSSIZE=0
+ [ -z iso9660 ]
+ [ iso9660 = unknown ]
+ [ -z iso9660 ]
+ [ iso9660 = unknown ]
+ [ -z iso9660 ]
+ mount -t iso9660 /host/wubi/install/ubuntu-7.04-alternate-i386.iso /cdrom
+ [ -e /cdrom/.disk/info ]
+ uname -r
+ [ -e /cdrom/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-15-generic_2.6.20-15.27_i386.deb ]
+ get_allowed_suites
+ [ ! -n  ]
+ [ -f /host/wubi/install/preseed.cfg ]
+ SUITE=feisty
+ [ -n feisty ]
+ [ -e /cdrom/dists/feisty/Release ]
+ return 0
+ return 0
+ [ -e /cdrom/casper/filesystem.squashfs ]
+ [ -e /cdrom/install/initrd.gz ]
+ mount_alternate_iso
+ log_begin_msg Mounting alternate iso
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write TEXT Mounting alternate iso
+ _log_msg Begin: Mounting alternate iso ...
+ echo Begin: Mounting alternate iso ...
Begin: Mounting alternate iso ...
+ check_mountpoint /root
+ mntpoint=/root
+ [ -d /root ]
+ umount /root
+ true
+ mount -t ramfs none /root
+ cd /root
+ gunzip -cd /cdrom/install/initrd.gz
+ cpio -i -d -H newc --no-absolute-filenames
28227 blocks
+ overlay_iso alternate-iso /root
+ overlay_name=alternate-iso
+ target=/root
+ [ -f /host/wubi/install/preseed.cfg ]
+ cp /host/wubi/install/preseed.cfg /root/
+ rm /host/wubi/install/preseed.cfg
+ fix_preseed /root/preseed.cfg
+ preseed=/root/preseed.cfg
+ [ -e /root/preseed.cfg ]
+ sed -i s/.$// /root/preseed.cfg
+ grep multiselect
+ cat /cdrom/preseed/ubuntu.seed
+ desktop=tasksel	tasksel/first	multiselect ubuntu-desktop
+ desktop=ubuntu-desktop
+ sed -i s/ ubuntu-desktop/ ubuntu-desktop/g /root/preseed.cfg
+ [ -d /root/conf ]
+ mkdir /root/conf
+ cp /conf/param.conf /root/conf/
+ cd /root
+ [ -f /alternate-iso.cpio ]
+ [ -f /host/wubi/install/alternate-iso.cpio ]
+ [ -d /alternate-iso ]
+ cp -af /alternate-iso/initramfs-tools /alternate-iso/packages /alternate-iso/sbin /alternate-iso/var /root/
+ cd /
+ log_end_msg
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
+ cd /root
+ check_mountpoint /root/cdrom
+ mntpoint=/root/cdrom
+ [ -d /root/cdrom ]
+ mkdir -p /root/cdrom
+ umount /root/cdrom
+ true
+ mount -n -o move /cdrom /root/cdrom
+ cp /tmp/lupin.log /tmp/zenigata.log /root/var/log
+ quit_usplash
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 100
+ /sbin/usplash_write SUCCESS ok
+ /sbin/usplash_write QUIT
+ pause_for_debug
+ cd /
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs

Hope this is enough indication.
> 
2-save the iso file in wubi/install next to wubi.exe, so you won t have to download it again.already done> 
3-you have to fully uninstall wubi after each failed install attempt using using windows add/remove, running wubi again, or uninstall.exe in wubi folder.done several times in different order without any change> 
4-If another try does not solve the issue, search or post in the general forum for this asus r2h known issues with ubuntu 7.04.Nothing found... Except an interestinh hint that some hackers even managed to install MacOS X on this device.

Many thanks for any hint...

Nikolaus

---

### Post by myoldryn on 2007-04-26
This page maybe can help you -> [http://www.xs4all.nl/~sozonko/asus_r2h_howto/](http://www.xs4all.nl/~sozonko/asus_r2h_howto/)

---

### Post by dhns on 2007-04-26
> **myoldryn said:**
> This page maybe can help you -> [http://www.xs4all.nl/~sozonko/asus_r2h_howto/](http://www.xs4all.nl/~sozonko/asus_r2h_howto/)

Many thanks. I know this page - and unfortunately it does neither help with Ubuntu nor wubi...

Nikolaus

---

### Post by ago on 2007-04-27
When you have the red page press Alt+F4 and see if there is any useful error. If you need to see older messages, press Alt+F2 and at the prompt execute:

nano /var/log/syslog

---

### Post by dhns on 2007-04-27
> **ago said:**
> When you have the red page press Alt+F4 and see if there is any useful error. If you need to see older messages, press Alt+F2 and at the prompt execute:

nano /var/log/syslog
I uninstalled wubi and did a fresh install.

After rebooting, I again got the red screen with installer components issues. This time I had shortly seen a message about some loop7 device that could not be mounted.

Pressing Alt-F4 at the red page made the installer step selection list reappear. I could not even select "Execute a shell" - gave a different red screen. Strange... When selecting a second time it worked (without having the keyboard layout set correctly).

Alt-F2 gave a screen with a list of additional installer components. E.g. choose-mirror, eject-udeb, iso-scan, etc.

Looking into syslog by your proposed nano command shows:
* several messages about resolver (libc6) and resolver (libnewt0.52): package doesn't exist
(this came before a message BEGIN LOOP INSTALL)
* after doing something with ROOT=/dev/loop7 like
  Mounting /dev/loop7 on /target
* these 5 messages from the kernel appear:
(all prefixed with Apr 27 11:39:20 kernel: [  250.140000])
  XFS: bad magic number
  XFS: SB validate failed
  attempt to access beyond end of device
  loop7: rw=0, want=258, limit=256
  isofs_fill_super: bread failed, dev=loop
 * finally: Unable to mount loop device

mount says (I hope I have copied the most important lines):

fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /host type vfat
/dev/loop0 on /cdrom type iso9660 (ro)
none on  / type ramfs (rw)

Nikolaus

---

### Post by ago on 2007-04-27
Make sure that the img files are strictly smaller than 4GB, larger files are not supported by vfat. Reinstall via wubi, then before rebooting, copy any other file of 3-4Gb over root.img. See if that fixes it.

---

### Post by dhns on 2007-04-27
> **ago said:**
> Make sure that the img files are strictly smaller than 4GB, larger files are not supported by vfat. Reinstall via wubi, then before rebooting, copy any other file of 3-4Gb over root.img. See if that fixes it.
Ok!

Firstly, I checked the files that Wubi installer has created before rebooting (i.e. while it was showing its final question for reboot).

ubuntu-7.04-alternate-i386.iso is 712 MB
C:\wubi\disks\home.img is 2048 MB 
C:\wubi\disks\root.img is 129 kB     <- appears to be too small :(
C:\wubi\disks\swap.img is 770 MB

Then, I **removed the root.img and made a copy of home.img that I renamed to root.img**.

And it finally installs and works (just the keyboard layout was not initialized but that is easy to change)!!!

Many thanks,
Nikolaus

---

### Post by ago on 2007-04-27
Not sure how you ended up with such a small root.img file. New version has a different size algorithm.

---

### Post by k386 on 2007-06-19
Was just wondering what the end result of this was? 

How was the support? I'm not expecting the GPS to work, mainly curious about any issues you ran into beyond whats outlined here.

Odd question - considering the somewhat limited horsepower of the machine - but any change you tried to get Beryl going? Seems possible as apparently Vista can run on this.

Any info would be awesome. I'm waiting on delivery of my R2H and would love to get Ubuntu up and running on it.

thanks in advance

---

### Post by freaksterr6676 on 2007-07-21
The GPS works, you need to enable it with the asus-laptop kernel module.  I've used gpsdrive, although I can't scale the window to fit the size of the display.  I've also used the gps with windows apps via wine.

Beryl worked straight out of the box without a problem.

I'm having a few weird issues though:
*   The mac address of the ethernet nic switches between two different numbers.  Only one of which works.  I have to boot into windows first, then reboot for it to work properly.
*   Can't get alsa running properly.  The volume out of the speaker is way too low and if I use the headphones, it's pretty distorted.  I've put the following in /etc/modprobe.d/alsa-base: options snd_hda_intel model=3stack position_fix=1

---

### Post by hans12345 on 2007-08-05
I have the same failure in installation - Load installer components from CD

Standard desktop PC Athlon 2400, 512 M RAM, runs Win XP pro, 17 GB of HD available for Wubi to install Ubuntu.

I looked at the earlier post 
quote
ubuntu-7.04-alternate-i386.iso is 712 MB
C:\wubi\disks\home.img is 2048 MB
C:\wubi\disks\root.img is 129 kB <- appears to be too small
C:\wubi\disks\swap.img is 770 MB
unquote

I decided to check my img files

I HAVE NO IMAGE FILES ANYWHERE!

In my R:\wubi\disks directory, I have 3 files, home, swap and system virtual disks.

There is one special thing about this PC - there is no C drive

Help!

---

### Post by tuxcantfly on 2007-08-05
I decided to check my img files

I HAVE NO IMAGE FILES ANYWHERE!

In my R:\wubi\disks directory, I have 3 files, home, swap and system virtual disks.> 

The virtual disks are the image files.

---

### Post by hans12345 on 2007-08-05
The lupin.log looks bad, here it is:

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

---

### Post by hans12345 on 2007-08-05
My virtual disk sizes are:

home.virtual.disk : 977 MB
swap.virtual.disk : 499 MB
system.virtual.disk : 0 MB

Nothing esle

---

### Post by tuxcantfly on 2007-08-05
> My virtual disk sizes are:

home.virtual.disk : 977 MB
swap.virtual.disk : 499 MB
system.virtual.disk : 0 MB

Nothing esle

Sounds way too small... perhaps try reinstalling Wubi, and before you reboot, try downloading and running this file: [http://cutlersoftware.com/ubuntusetup/devel/scripts/vdisks10g.exe](http://cutlersoftware.com/ubuntusetup/devel/scripts/vdisks10g.exe) and it will create larger virtual disks for you, just move them into C:\wubi\disks and replace the ones you have, then reboot, and it should work.

---

### Post by hans12345 on 2007-08-05
Problem fixed. 

I read the other posts and found someone with a similar problem.

He finally reran his install allowing only 4 GB to Wubi  and I tried the same (earlier I had allowed Wubi to take 10 GB), and, like magic, it worked.

Wubi developers - this is a silly bug.

My advice to everyone who sees this:

        system.virtual.disk : 0 MB

just set your default size in the Wubi install screen to 4 GB

---

