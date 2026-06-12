---
title: "serious errors were found while checking the disk drive for /MEDIA2"
date: 2013-10-08
forum: General Help
---

### Post by mahalos on 2013-10-08
serious errors were found while checking the disk drive for /MEDIA2 (/dev/sdc3)

im getting this error a lot when booting into my minimal ubuntu xbmc install (ubuntu 13.04)

if i drop into to the recovery console and try to run fsck on the partition it tells me the partition is already mounted.

```
fsck from util-linux 2.20.1
/dev/sdc3 is mounted.
```

typing in "mount" it shows the partition as unmounted

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdc2 on /media/usbhd-sdc2 type ext4 (rw,relatime,data=ordered)
/dev/sdb1 on /MEDIA type ext4 (rw)

```


trying umount /dev/sdc3 tells me the partition isn't mounted

it appears the partition has mounted in /media/usbhd-sdc3 not sure why?

i can successfully umount the partition from /media/usbhd-sdc3 and then run fsck on it and it pulls up no errors

does anybody have any ideas on this one.....it's got me kinda stuck.

here's the boot.log from the recovery console..

```
xbmc@xbmc:~$ cat boot.log 
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sdc3 is in use.
e2fsck: Cannot continue, aborting.


mountall: fsck /MEDIA2 [326] terminated with status 8
mountall: Unrecoverable fsck error: /MEDIA2
New_Volume: clean, 102414/3915216 files, 1831174/15630336 blocks
lircd-0.9.0[776]: lircd(default) ready, using /var/run/lirc/lircd
WDRED: clean, 9506/183148544 files, 573458628/732566272 blocks
Ignoring errors with /MEDIA2 at user request
/etc/rcS.d/S37apparmor: 35: .: Can't open /lib/apparmor/functions
Loading the saved-state of the serial devices... 
 * Setting sensors limits        * Starting NetBIOS name server                                                                                        [ OK ]
                                                                                                                                                   [ OK ]
 * Loading LIRC modules                                                                                                                                [ OK ]
 * Stopping System V initialisation compatibility                                                                                                      [ OK ]
 * Starting System V runlevel compatibility                                                                                                            [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting ACPI daemon                                                                                                                                [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting save kernel messages                                                                                                                       [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting regular background program processing daemon                                                                                               [ OK ]
 * Starting CPU interrupts balancing daemon                                                                                                            [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                                                            [ OK ]
 * Stopping save kernel messages                                                                                                                       [ OK ]
Starting Sick Beard
Starting XBMC
 * Starting SABnzbd+ binary newsgrabber                                                                                                                [ OK ]
 * Checking battery state...                                                                                                                           [ OK ]
 * Stopping System V runlevel compatibility                                                                                                            [ OK ]
 * Starting                                            
```

and here's the one after exiting and booting up successfully..

```
xbmc@xbmc:~$ cat /var/log/boot.log 
fsck from util-linux 2.20.1
/dev/sdc3: clean, 18703/119349248 files, 287562124/477377851 blocks
swapon: /dev/disk/by-uuid/ac801b6f-ed4a-4f21-bf86-40e8ce8ed2c2: swapon failed: Device       or resource busy
mountall: swapon /dev/disk/by-uuid/ac801b6f-ed4a-4f21-bf86-40e8ce8ed2c2 [943]  terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/ac801b6f-ed4a-4f21-bf86-40e8ce8ed2c2
/etc/rcS.d/S37apparmor: 35: .: Can't open /lib/apparmor/functions
Loading the saved-state of the serial devices... 
 * Starting system logging daemon                                                                                                                          [ OK ]
 * Setting sensors limits                                                                                                                              [ OK ]
 * Stopping System V initialisation compatibility                                                                                                      [ OK ]
 * Starting System V runlevel compatibility                                                                                                            [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting regular background program processing daemon                                                                                               [ OK ]
 * Starting ACPI daemon                                                                                                                                [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting save kernel messages                                                                                                                       [ OK ]
 * Starting                                                                                                                                            [ OK ]
 * Starting CPU interrupts balancing daemon                                                                                                            [ OK ]
 * Loading LIRC modules                                                                                                                                [ OK ]
 * Stopping save kernel messages                                                                                                                       [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                                                            [ OK ]
Starting Sick Beard
Starting XBMC
 * Starting SABnzbd+ binary newsgrabber                                                                                                                [ OK ]
 * Checking battery state...                                                                                                                           [ OK ]
 * Stopping System V runlevel compatibility                                                                                                            [ OK ]
 * Starting                                                                                                                                            [ OK ]
```

It seems the swap partition failed to mount.....i believe it's because it was mounted in /media/usbhd-sdc2

i have no idea where these mount points have come from..!!!

it seems all my mechanical hdds partitions have been listed in the /media

```
xbmc@xbmc:/media$ ls
usbhd-sdc1  usbhd-sdc2  usbhd-sdc3  WDRED
```

here's my fstab..

```
xbmc@xbmc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f7767ada-f636-4983-9888-9491484ec5c4 /               ext4    errors=remount-ro 0       1
# /MEDIA was on /dev/sdb1 during installation
UUID=b52ed08d-2eca-425f-ac80-3fcfd781b0f8 /MEDIA          ext4    defaults        0       2
# /MEDIA2 was on /dev/sdc3 during installation
UUID=34dc11ad-bf6d-4874-8ae6-6aaa5eade523 /MEDIA2         ext4    defaults        0       2
# swap was on /dev/sdc1 during installation
UUID=ac801b6f-ed4a-4f21-bf86-40e8ce8ed2c2 none            swap    sw              0       0
```


Any help or suggestions would be greatly appreciated...

---

