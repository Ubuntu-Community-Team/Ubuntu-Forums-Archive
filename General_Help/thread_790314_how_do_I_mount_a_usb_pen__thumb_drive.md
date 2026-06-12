---
title: "how do I mount a usb pen / thumb drive?"
date: 2008-05-11
forum: General Help
---

### Post by hurtstotalktoyou on 2008-05-11
Hi, all.

This should be a simple thing, but for some reason I can't find any online instructions--none I can understand, anyway.  I have a 1GB USB flash drive.  I plugged it into my Ubuntu 8.04 system.  Nothing happens, and I can't find it anywhere in my Places/Computer menus.

How do I access the drive to read/write files?

Thanks!

---

### Post by metiosarius on 2008-05-11
> **hurtstotalktoyou said:**
> Hi, all.

This should be a simple thing, but for some reason I can't find any online instructions--none I can understand, anyway.  I have a 1GB USB flash drive.  I plugged it into my Ubuntu 8.04 system.  Nothing happens, and I can't find it anywhere in my Places/Computer menus.

How do I access the drive to read/write files?

Thanks!

Odd - Generally just plugging it in will open a file manager...
Post the contents of /etc/fstab and the output of the command: mount

---

### Post by happyisland on 2008-07-09
I am having the same issues with my music player (which is supposed to connect as a USB mass storage device - AND it works fine on other OSes (apple, windows, even xandros linux)). My fstab is as follows. The output of mount is below that. Any help would be MUCH appreciated!!! 
:smile:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dae8be2e-a454-4781-ba04-a4d6b591be25 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e8e71b1a-a20f-429e-ae90-538c744c01ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#entered for extra internal sata disk
/dev/sdb1	/media/scsidisk-1  ext3	defaults	0	0


mount

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/scsidisk-1 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by Skukfas on 2008-07-17
same problem here.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4d95d3fd-7f95-4746-b02c-d8e6f543501a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=963141b7-0fe8-4162-9bbc-9b0a6fbc4f45 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
                  

 mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/skukfas/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=skukfas)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


dmesg | grep usb
> [   17.354800] usbcore: registered new interface driver usbfs
[   17.354835] usbcore: registered new interface driver hub
[   17.373502] usbcore: registered new device driver usb
[   18.351214] usb usb1: configuration #1 chosen from 1 choice
[   18.510935] usb usb2: configuration #1 chosen from 1 choice
[   18.670664] usb usb3: configuration #1 chosen from 1 choice
[   18.784548] usb usb4: configuration #1 chosen from 1 choice
[ 2793.708657] usb 4-1: new high speed USB device using ehci_hcd and address 2
[ 2793.844269] usb 4-1: configuration #1 chosen from 1 choice
[ 2794.910181] usbcore: registered new interface driver libusual
[ 2794.999309] usbcore: registered new interface driver usb-storage
[ 2794.999889] usb-storage: device found at 2
[ 2794.999894] usb-storage: waiting for device to settle before scanning
[ 2799.990740] usb-storage: device scan complete
[ 2800.477585] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2815.564912] usb 4-1: device descriptor read/64, error -110
[ 2830.756050] usb 4-1: device descriptor read/64, error -110
[ 2830.971699] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2846.059017] usb 4-1: device descriptor read/64, error -110
[ 2861.250165] usb 4-1: device descriptor read/64, error -110
[ 2861.465809] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2871.856811] usb 4-1: device not accepting address 2, error -110
[ 2871.968628] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2882.359627] usb 4-1: device not accepting address 2, error -110
[ 2882.359791] usb 4-1: USB disconnect, address 2
[ 2882.471467] usb 4-1: new high speed USB device using ehci_hcd and address 3
[ 2897.558783] usb 4-1: device descriptor read/64, error -110
[ 2912.749942] usb 4-1: device descriptor read/64, error -110
[ 2912.965569] usb 4-1: new high speed USB device using ehci_hcd and address 4
[ 2928.053008] usb 4-1: device descriptor read/64, error -110
[ 2943.244027] usb 4-1: device descriptor read/64, error -110
[ 2943.459683] usb 4-1: new high speed USB device using ehci_hcd and address 5
[ 2953.850689] usb 4-1: device not accepting address 5, error -110
[ 2953.962491] usb 4-1: new high speed USB device using ehci_hcd and address 6
[ 2964.353521] usb 4-1: device not accepting address 6, error -110


---

### Post by marioitalo on 2008-10-01
I found a solution to that problem (apparently this is about the time needed to the device wake-up):
At /etc/modprobe.d/options I added the line:
options scsi_mod inq_timeout=20
Then I tried to unload and load the module(scsi_mod), but didn't work, because this option was in initrd file. So I reinstalled the package linux-image-* what forced the system to make a new initrd file and use the new configuration (of course there is a better way to do that but I didn't want to search how to), then, after a reboot, voilá, the pen drive was back to life.:popcorn:
I hope this help someone.

---

