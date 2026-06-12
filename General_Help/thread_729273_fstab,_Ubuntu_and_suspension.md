---
title: "fstab, Ubuntu and suspension"
date: 2008-03-19
forum: General Help
---

### Post by federico92 on 2008-03-19
Hi :KS
I've set the /etc/fstab file (on Ubuntu) to mount my SDHC (/dev/sdb1) on /home. The problem is that when the pc wakes up after suspension, the SDHC isn't mounted and gdm freezes cause it doesn't find my home folder. How can I solve this?
Thank you and sorry for my bad English:oops:
:)

---

### Post by chrisccoulson on 2008-03-19
What interface does the SDHC use to connect to the computer (I assume you're referring to SD High Capacity card?)

---

### Post by federico92 on 2008-03-19
Sd High Capacity ;) connected by an internal card reader (USB 2.0)

---

### Post by chrisccoulson on 2008-03-19
Could you post the contents of your /etc/fstab?

I wonder if your problem is because it's on the USB interface?

---

### Post by federico92 on 2008-03-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=46aec5a6-d498-4c2a-b472-124db10c398f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=dbc8504e-3402-4337-8b41-4645f389353c none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1       /home           ext3            noatime,defaults,errors=remount-ro      0       2

That's my fstab file

---

### Post by chrisccoulson on 2008-03-19
Looks quite normally. One thing though - you can't always guarantee that your SDHC will get the same device identifier each time you boot (especially if you boot with something else plugged in to USB), so you should identify it in your fstab using the UUID really.

You can get the UUID by doing:
```
blkid /dev/sdb1
```
Replace '/dev/sdb1' in your fstab with 'UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx', using the UUID from the output of the blkid command, so it looks something like:
```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /home ext3 noatime,defaults,errors=remount-ro 0 2
```

---

### Post by federico92 on 2008-03-19
No, it doesn't work :confused:

---

### Post by chrisccoulson on 2008-03-19
No, what I suggested probably won't fix your problem. But it is a more robust way of mounting your /home partition

---

### Post by federico92 on 2008-03-19
[http://ubuntuforums.org/showthread.php?t=728331]("http://ubuntuforums.org/showthread.php?t=728331")
I read this thread, maybe it's my solution, but I really don't know how to create an udev rule... Could you help me?

---

### Post by chrisccoulson on 2008-03-19
I'm not really familiar with writing UDEV rules, and it's getting quite late here at the moment. I'll try and figure this out tomorrow and help you if that's ok (assuming nobody else offers their assistance first)

---

### Post by federico92 on 2008-03-20
ok, thanks :KS

---

### Post by chrisccoulson on 2008-03-20
Right, I've had a look through that stuff about writing UDEV rules, and I think I can help (although I can't guarantee it will work!)

First of all, you need to find unique attributes for the device exposed through sysfs, with which you can identify the device /dev/sdd1) and use as match keys for your UDEV rule. As I work through, I shall use an example (which will be my USB camera). With your SDHC card plugged in, type the following in to a terminal:
```
udevinfo -a -p /block/sdb
```
You should get attributes of the device displayed in the terminal. In my case, my camera is /dev/sdd and this is my output:
```
chr1s@chris-desktop:~$ udevinfo -a -p /block/sdd

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sdd':
    KERNEL=="sdd"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{capability}=="13"
    ATTR{stat}=="     124      323      678      644        0        0        0        0        0      552      644"
    ATTR{size}=="253696"
    ATTR{removable}=="1"
    ATTR{range}=="16"
    ATTR{dev}=="8:48"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb2/2-10/2-10:1.0/host4/target4:0:0/4:0:0:0':
    KERNELS=="4:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{iodone_cnt}=="0x8a"
    ATTRS{iorequest_cnt}=="0x8a"
    ATTRS{iocounterbits}=="32"
    ATTRS{timeout}=="30"
    ATTRS{state}=="running"
    ATTRS{rev}=="4.50"
    ATTRS{model}=="Sony DSC        "
    ATTRS{vendor}=="Sony    "
    ATTRS{scsi_level}=="0"
    ATTRS{type}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{queue_depth}=="1"
    ATTRS{device_blocked}=="0"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb2/2-10/2-10:1.0/host4/target4:0:0':
    KERNELS=="target4:0:0"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb2/2-10/2-10:1.0/host4':
    KERNELS=="host4"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb2/2-10/2-10:1.0':
    KERNELS=="2-10:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{modalias}=="usb:v054Cp0010d0450dc00dsc00dp00ic08iscFFip01"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb2/2-10':
    KERNELS=="2-10"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{product}=="Sony DSC"
    ATTRS{manufacturer}=="Sony"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="4"
    ATTRS{busnum}=="2"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0450"
    ATTRS{idProduct}=="0010"
    ATTRS{idVendor}=="054c"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:131"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:02.1"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-14-generic ehci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="10"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="2"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:128"

  looking at parent device '/devices/pci0000:00/0000:00:02.1':
    KERNELS=="0000:00:02.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{numa_node}=="0"
    ATTRS{modalias}=="pci:v000010DEd0000005Bsv00001043sd0000815Abc0Csc03i20"
    ATTRS{local_cpus}=="03"
    ATTRS{irq}=="23"
    ATTRS{class}=="0x0c0320"
    ATTRS{subsystem_device}=="0x815a"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{device}=="0x005b"
    ATTRS{vendor}=="0x10de"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

chr1s@chris-desktop:~$ 


```

Now, you need to pick one or more unique attributes. In the thread you linked to, the guy used a serial number, but I can't find one for my camera. I am going to use the following attributes to identify my camera:
```
SUBSYSTEMS=="scsi"
ATTRS{model}=="Sony DSC        "
DRIVERS=="sd"
ATTRS{modalias}=="scsi:t-0x00"

```
These will form the match keys for my rule. You have to make sure that your attributes are unique to /dev/sdb1, and not common between /dev/sdb (which we aren't interested in) and /dev/sdb1. For me, it was guess-work, but there may be a more scientific way of doing it.

Next, we need to create the UDEV rule. We are going to create it in /etc/udev/rules.d/10-local.rules, which probably won't exist yet. In a terminal, open up the nano text editor:
```
sudo nano /etc/udev/rules.d/10-local.rules
```
Then add your rule, including match keys and assignment keys. All keys are comma separated. Match keys use a '==' equality operator, whilst assignmnet keys use '=' assignment operator. In my case, it will look something like (remember, the rule CANNOT span multiple lines:
```
SUBSYSTEMS=="scsi", ATTRS{model}=="Sony DSC        ", DRIVERS=="sd", ATTRS{modalias}=="scsi:t-0x00", MODE="0666", OPTIONS+="last_rule", RUN+="/bin/mount /home"
```
Obviously, your rule will contain your unique match keys.

Save the file and exit nano.

Give that a try and see what happens. If you want any help picking attributes to identify your device, please post the output of:
```
udevinfo -a -p /block/sdb
```
If you have any problems, please post the output of:
```
udevtest /block/sdb
```

---

### Post by federico92 on 2008-03-20
I triet but when I get to the login screen, it says my home folder doesn't exist, so I've deleted the rule.

udevinfo -a -p /block/sdb:
```
Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{capability}=="13"
    ATTR{stat}=="    1015      811    25646     5400      315      846     9280    68852        0    15284    74252"
    ATTR{size}=="32313344"
    ATTR{removable}=="1"
    ATTR{range}=="16"
    ATTR{dev}=="8:16"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host2/target2:0:0/2:0:0:0':
    KERNELS=="2:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{ioerr_cnt}=="0x2"
    ATTRS{iodone_cnt}=="0x5d1"
    ATTRS{iorequest_cnt}=="0x5d1"
    ATTRS{iocounterbits}=="32"
    ATTRS{timeout}=="30"
    ATTRS{state}=="running"
    ATTRS{rev}=="0100"
    ATTRS{model}=="CardReader SD0  "
    ATTRS{vendor}=="USB2.0  "
    ATTRS{scsi_level}=="0"
    ATTRS{type}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{queue_depth}=="1"
    ATTRS{device_blocked}=="0"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host2/target2:0:0':
    KERNELS=="target2:0:0"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host2':
    KERNELS=="host2"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0':
    KERNELS=="5-5:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{modalias}=="usb:v0951p1606d0100dc00dsc00dp00ic08isc06ip50"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5/5-5':
    KERNELS=="5-5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="146030377350"
    ATTRS{product}=="UB6225"
    ATTRS{manufacturer}=="ENE"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="2"
    ATTRS{busnum}=="5"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0100"
    ATTRS{idProduct}=="1606"
    ATTRS{idVendor}=="0951"
    ATTRS{bMaxPower}=="498mA"
    ATTRS{bmAttributes}=="80"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:513"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb5':
    KERNELS=="usb5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-14-generic ehci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="8"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="5"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:512"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00008086d0000265Csv00001043sd000082D8bc0Csc03i20"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="19"
    ATTRS{class}=="0x0c0320"
    ATTRS{subsystem_device}=="0x82d8"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{device}=="0x265c"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

```

udevtest /block/sdb
```
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/00-init.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libgphoto2.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libsane.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-libpisock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/99-udevmonitor.rules' as rules file
parse_file: reading '/etc/udev/rules.d/libmtp.rules' as rules file
main: looking at device '/block/sdb' from subsystem 'block'
match_rule: set ENV 'DEVTYPE=disk'
run_program: 'usb_id --export /block/sdb'
run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR=USB2.0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL=CardReader_SD0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_REVISION=0100'
run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL=USB2.0_CardReader_SD0_146030377350-0:0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL_SHORT=146030377350'
run_program: '/lib/udev/usb_id' (stdout) 'ID_TYPE=disk'
run_program: '/lib/udev/usb_id' (stdout) 'ID_INSTANCE=0:0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_BUS=usb'
run_program: '/lib/udev/usb_id' returned with status 0
udev_rules_get_name: add symlink 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0'
run_program: 'path_id /block/sdb'
run_program: '/lib/udev/path_id' (stdout) 'ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
run_program: '/lib/udev/path_id' returned with status 0
udev_rules_get_name: add symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
udev_node_mknod: atomically replace '/dev/.tmp-8-16'
udev_node_mknod: mknod(/dev/.tmp-8-16.udev-tmp, 060600, 8, 16) failed: Permission denied
run_program: 'vol_id --export /dev/.tmp-8-16'
run_program: '/lib/udev/vol_id' (stderr) '/dev/.tmp-8-16: error opening volume'
run_program: '/lib/udev/vol_id' returned with status 2
run_program: 'edd_id --export /dev/.tmp-8-16'
run_program: '/lib/udev/edd_id' (stderr) 'no kernel EDD support'
run_program: '/lib/udev/edd_id' returned with status 2
udev_rules_get_name: no node name set, will use kernel name 'sdb'
unlink_secure: chown(/dev/.tmp-8-16, 0, 0) failed: No such file or directory
unlink_secure: chmod(/dev/.tmp-8-16, 0000) failed: No such file or directory
udev_device_event: device '/block/sdb' already in database, cleanup
udev_node_add: creating device node '/dev/sdb', major=8, minor=16, mode=0660, uid=0, gid=46
udev_node_update_symlinks: update symlink 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0' of '/block/sdb'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-id\x2fusb-USB2.0_CardReader_SD0_146030377350-0:0'
update_link: found 1 devices with name 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0'
update_link: found '/block/sdb' for 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0'
update_link: compare (our own) priority of '/block/sdb' 0 >= 0
update_link: 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0' with target 'sdb' has the highest priority 0, create it
udev_node_update_symlinks: update symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0' of '/block/sdb'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-path\x2fpci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: found 1 devices with name 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: found '/block/sdb' for 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: compare (our own) priority of '/block/sdb' 0 >= 0
update_link: 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0' with target 'sdb' has the highest priority 0, create it
main: run: 'socket:/org/freedesktop/hal/udev_event'
main: run: 'socket:/org/kernel/udev/monitor'

```

---

### Post by chrisccoulson on 2008-03-20
Can you show the rule that you added? The output from udevtest is no good without the rule anyway

---

### Post by federico92 on 2008-03-20
```
SUBSYSTEMS=="scsi", ATTRS{model}=="CardReader SD0  ", DRIVERS=="sd", ATTRS{modalias}=="scsi:t-0x00", MODE="0666", OPTIONS+="last_rule", RUN+="/bin/mount /home"
```

---

### Post by chrisccoulson on 2008-03-20
Did you change your fstab to identify the disk by UUID instead of device node? I think that might cause it not to work, because we specified the last_rule option in the UDEV rule - this will mean no further udev rules are processed. We'll try giving it a persistent name instead. Try:
```
SUBSYSTEMS=="scsi", ATTRS{model}=="CardReader SD0  ", DRIVERS=="sd", ATTRS{modalias}=="scsi:t-0x00", MODE="0666", SYMLINK+=home, OPTIONS+="last_rule", RUN+="/bin/mount /home"
```
Edit your fstab to identify the volume using /dev/home (instead of using the UUID or /dev/sdb1).

If that works, we could make some alterations to your rule. First of all, you are assigning your raw disk with 0666 permissions - this is bad as it means that any normal user on the system can write to the raw disk without using sudo, which will really screw everything up. Try this modified rule instead (once you have the one above working):
```
SUBSYSTEMS=="scsi", ATTRS{model}=="CardReader SD0  ", DRIVERS=="sd", ATTRS{modalias}=="scsi:t-0x00", OWNER="root", GROUP="disk", MODE="0666", SYMLINK+=home, OPTIONS+="last_rule", RUN+="/bin/mount /home"
```

---

### Post by federico92 on 2008-03-20
> **chrisccoulson said:**
> Edit your fstab to identify the volume using /dev/home (instead of using the UUID or /dev/sdb1).

Do you mean I'm going to edit /etc/sdb1 to /etc/home in fstab?

---

### Post by chrisccoulson on 2008-03-20
What is currently in your fstab?

---

### Post by federico92 on 2008-03-20
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=46aec5a6-d498-4c2a-b472-124db10c398f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=dbc8504e-3402-4337-8b41-4645f389353c none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/sdb1	/home		ext3		noatime,defaults,errors=remount-ro	0	2
UUID=f21e3731-787f-44ba-bc32-256e2269d713	/home	ext3	noatime,defaults,errors=remount-ro	0	2
```

---

### Post by chrisccoulson on 2008-03-20
Yes, the problem is with the UUID now. Replace 'UUID=f21e3731-787f-44ba-bc32-256e2269d713' with '/dev/home' (only when you have the UDEV rule present - without the rule, /dev/home never exists), so it looks like:
```
/dev/home	/home	ext3	noatime,defaults,errors=remount-ro	0	2
```

---

### Post by federico92 on 2008-03-20
During the boot, it says "Device /dev/home doesn't exist", even with the rule activated,

---

### Post by chrisccoulson on 2008-03-20
Thats because it should be /**dev**/home

---

### Post by federico92 on 2008-03-20
> **chrisccoulson said:**
> Thats because it should be /**dev**/home

my fault, in fstab it's /dev/home :oops:

---

### Post by chrisccoulson on 2008-03-20
It could be that udev isn't matching your drive to the rule. I could do with the output of 'udevtest /dev/sdb1' with the rule in place really (but this means you'll have no /home mounted, so you might have to do it from a root shell in recovery mode instead)

---

### Post by federico92 on 2008-03-20
```
root@Fedeee:/# sudo udevtest /dev/sdb1
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/00-init.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/10-local.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libgphoto2.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libsane.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-libpisock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/99-udevmonitor.rules' as rules file
parse_file: reading '/etc/udev/rules.d/libmtp.rules' as rules file
unable to open device '/dev/sdb1'

```

---

### Post by chrisccoulson on 2008-03-20
Sorry, I mean:
```
udevtest /block/sdb
```

---

### Post by federico92 on 2008-03-20
```
federico@Fedeee:~$ sudo udevtest /block/sdb
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/00-init.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/10-local.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libgphoto2.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libsane.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-libpisock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/99-udevmonitor.rules' as rules file
parse_file: reading '/etc/udev/rules.d/libmtp.rules' as rules file
main: looking at device '/block/sdb' from subsystem 'block'
match_rule: set ENV 'DEVTYPE=disk'
run_program: 'usb_id --export /block/sdb'
run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR=USB2.0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL=CardReader_SD0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_REVISION=0100'
run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL=USB2.0_CardReader_SD0_146030377350-0:0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL_SHORT=146030377350'
run_program: '/lib/udev/usb_id' (stdout) 'ID_TYPE=disk'
run_program: '/lib/udev/usb_id' (stdout) 'ID_INSTANCE=0:0'
run_program: '/lib/udev/usb_id' (stdout) 'ID_BUS=usb'
run_program: '/lib/udev/usb_id' returned with status 0
udev_rules_get_name: add symlink 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0'
run_program: 'path_id /block/sdb'
run_program: '/lib/udev/path_id' (stdout) 'ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
run_program: '/lib/udev/path_id' returned with status 0
udev_rules_get_name: add symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
run_program: 'vol_id --export /dev/.tmp-8-16'
run_program: '/lib/udev/vol_id' (stderr) '/dev/.tmp-8-16: unknown volume type'
run_program: '/lib/udev/vol_id' returned with status 4
run_program: 'edd_id --export /dev/.tmp-8-16'
run_program: '/lib/udev/edd_id' (stderr) 'no kernel EDD support'
run_program: '/lib/udev/edd_id' returned with status 2
udev_rules_get_name: no node name set, will use kernel name 'sdb'
udev_device_event: device '/block/sdb' already in database, cleanup
udev_node_add: creating device node '/dev/sdb', major=8, minor=16, mode=0666, uid=0, gid=46
udev_node_update_symlinks: update symlink 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0' of '/block/sdb'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-id\x2fusb-USB2.0_CardReader_SD0_146030377350-0:0'
update_link: found 1 devices with name 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0'
update_link: found '/block/sdb' for 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0'
update_link: compare (our own) priority of '/block/sdb' 0 >= 0
update_link: 'disk/by-id/usb-USB2.0_CardReader_SD0_146030377350-0:0' with target 'sdb' has the highest priority 0, create it
udev_node_update_symlinks: update symlink 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0' of '/block/sdb'
udev_db_get_devices_by_name: found index directory '/dev/.udev/names/disk\x2fby-path\x2fpci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: found 1 devices with name 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: found '/block/sdb' for 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0'
update_link: compare (our own) priority of '/block/sdb' 0 >= 0
update_link: 'disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0' with target 'sdb' has the highest priority 0, create it
main: run: 'socket:/org/freedesktop/hal/udev_event'
main: run: 'socket:/org/kernel/udev/monitor'

```

---

### Post by chrisccoulson on 2008-03-20
It doesn't look like it is being matched by the rule that you've added. Not sure what else to suggest really!

---

### Post by chrisccoulson on 2008-03-20
Ah, my bad! There is a typo in the rule I gave you. The symlink assignment should look like:
```
SYMLINK+="home"
```
Note the double quotes around 'home' now, which I didn't specify before.

---

### Post by federico92 on 2008-03-21
now it mounts /dev/home correctly, but during the boot it says "fsck died with exit status 8". However I can make it continue (CTRL+D) and then it works well (suspension not tried yet).

---

