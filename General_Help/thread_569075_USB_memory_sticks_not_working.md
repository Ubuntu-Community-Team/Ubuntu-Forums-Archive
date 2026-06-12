---
title: "USB memory sticks not working"
date: 2007-10-06
forum: General Help
---

### Post by Dark Aspect on 2007-10-06
Hi I appear to have a problem with my USB memory sticks.It worked fine a few days ago but now my USB seems completely broken when I try to access memory on a device.It works on other Linux systems and windows.I can't access external hard drives or my PSP now.

I am using Ubuntu 7.04 and I have had my memory sticks working before with my computer.Any ideas?

---

### Post by Dark Aspect on 2007-10-06
Bump......

Okay I have made things worse now...........

The default Disk Usage Analyzer tool completely crashes when I click on it and I have no text in my /etc/fstab file.I am actually pretty surprised I can boot at all,my computer thinks there is 3 hard drives.

I think I might wanna just backup my data and do a clean install.

---

### Post by tgalati4 on 2007-10-07
Post the output of the following:

>dmesg | tail -n 50

---

### Post by Dark Aspect on 2007-10-07
> **tgalati4 said:**
> Post the output of the following:

>dmesg | tail -n 50

Okay heres the whole output:

[   52.615578] bridge-eth1: attached
[   61.015724] eth1: no IPv6 routers present
[   94.160498] eth1: no IPv6 routers present
[  108.759605] usb 2-10: new high speed USB device using ehci_hcd and address 4
[  108.892493] usb 2-10: configuration #1 chosen from 1 choice
[  108.995510] usbcore: registered new interface driver libusual
[  109.017367] Initializing USB Mass Storage driver...
[  109.017421] scsi4 : SCSI emulation for USB Mass Storage devices
[  109.017464] usbcore: registered new interface driver usb-storage
[  109.017467] USB Mass Storage support registered.
[  109.017574] usb-storage: device found at 4
[  109.017576] usb-storage: waiting for device to settle before scanning
[  114.018880] usb-storage: device scan complete
[  114.020007] scsi 4:0:0:0: Direct-Access     USB007   mini-USB2BU      0.00 PQ: 0 ANSI: 2
[  114.022237] SCSI device sdb: 1024000 512-byte hdwr sectors (524 MB)
[  114.023860] sdb: Write Protect is off
[  114.023863] sdb: Mode Sense: 00 00 00 00
[  114.023865] sdb: assuming drive cache: write through
[  114.027232] SCSI device sdb: 1024000 512-byte hdwr sectors (524 MB)
[  114.028858] sdb: Write Protect is off
[  114.028860] sdb: Mode Sense: 00 00 00 00
[  114.028862] sdb: assuming drive cache: write through
[  114.028864]  sdb: sdb1
[  114.101271] sd 4:0:0:0: Attached scsi removable disk sdb
[  114.101304] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 2740.379546] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 2740.841156] usb 2-2: configuration #1 chosen from 1 choice
[ 2740.841647] scsi5 : SCSI emulation for USB Mass Storage devices
[ 2740.841689] usb-storage: device found at 5
[ 2740.841690] usb-storage: waiting for device to settle before scanning
[ 2745.841970] usb-storage: device scan complete
[ 2745.844051] scsi 5:0:0:0: Direct-Access     Rave-MP  Dig Audio Player 0100 PQ: 0 ANSI: 4
[ 2745.845727] scsi 5:0:0:1: Direct-Access     Rave-MP  Dig Audio Player 0100 PQ: 0 ANSI: 4
[ 2745.856061] SCSI device sdc: 507904 512-byte hdwr sectors (260 MB)
[ 2745.857938] sdc: Write Protect is off
[ 2745.857941] sdc: Mode Sense: 03 00 00 00
[ 2745.857943] sdc: assuming drive cache: write through
[ 2745.863309] SCSI device sdc: 507904 512-byte hdwr sectors (260 MB)
[ 2745.864182] sdc: Write Protect is off
[ 2745.864185] sdc: Mode Sense: 03 00 00 00
[ 2745.864187] sdc: assuming drive cache: write through
[ 2745.864191]  sdc: sdc1
[ 2745.866391] sd 5:0:0:0: Attached scsi removable disk sdc
[ 2745.866434] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 2745.868358] sd 5:0:0:1: Attached scsi removable disk sdd
[ 2745.868392] sd 5:0:0:1: Attached scsi generic sg3 type 0
[ 2750.968012] usb 2-2: USB disconnect, address 5
[ 5022.809368] SoftMAC: Open Authentication completed with 00:11:50:43:ea:f9
[ 5387.547152] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 5387.548361] VMBlock warning: DentryOpRevalidate: invalid args from kernel

Any ideas would be helpful but its no big deal if it can't be fixed because I'll just reinstall Ubuntu if I can't fix it.That fixes almost everything software related so.

---

### Post by tgalati4 on 2007-10-07
Check Places-->Computer and see if you have USB_disk icons and click on them to mount.  Your dmesg is not showing errors (except for the last 2, I'm not sure what VMBlock is for--some sort of networking?

Post the output of:

/etc/fstab

and

/etc/mtab

You want to find the problem before reinstalling.  Linux is not Windows, so reinstalling will sometimes show the exact same problem.  With Windows, when the registry gets screwed up, you sometimes have to reinstall to get a fresh start.  With Ubuntu, hardware problems sometimes appear to be software problems.  Software problems usually show up in log files (/var/log) and are quick to trace.  Hardware problems are more difficult.

---

### Post by Dark Aspect on 2007-10-07
Great well maybe Ubuntu 7.10 will fix the problem when I update to it.

> **tgalati4 said:**
> 
Post the output of:

/etc/fstab

and

/etc/mtab.

Okay For /etc/fstab I have nothing.The file is there just nothing in it,this might be a huge part of the problem.I have for /etc/mtab. this:

proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
none /proc/fs/vmblock/mountPoint vmblock rw 0 0

---

