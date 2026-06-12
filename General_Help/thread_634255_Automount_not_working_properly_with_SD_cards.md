---
title: "Automount not working properly with SD cards"
date: 2007-12-07
forum: General Help
---

### Post by dreikin on 2007-12-07
SEE THIRD POST FOR SOLUTION

[note: just realized I'd posted this in the wrong thread.  Since I no longer know where the thread I *meant* to post it in is, here it be:]

So..

I have two SD cards that automount correctly, but one that doesn't.

Info is for the one that doesn't.

dmesg on insert:

> [ 5980.260000] mmcblk0: mmc0:e624 SD02G 1985024KiB 
[ 5980.260000]  mmcblk0: p1

it's recognized in hal-device-manager.

after insert, hal-device | grep mmc:

> 0: udi = '/org/freedesktop/Hal/devices/volume_uuid_1769_6A29'
  block.minor = 1  (0x1)  (int)
  volume.label = 'CANON_DC'  (string)
  volume.ignore = true  (bool)
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' } (string list)
  info.capabilities = { 'volume', 'block' } (string list)
  volume.partition.flags = {  } (string list)
  volume.is_partition = true  (bool)
  volume.mount_point = ''  (string)
  info.category = 'volume'  (string)
  info.product = 'CANON_DC'  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.partition.type = '0x06'  (string)
  block.is_volume = true  (bool)
  volume.linux.is_device_mapper = false  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_0x206bb243'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_0x206bb243'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  volume.num_blocks = 3969799  (0x3c9307)  (int)
  volume.fsversion = 'FAT16'  (string)
  block.device = '/dev/mmcblk0p1'  (string)
  volume.uuid = '1769-6A29'  (string)
  volume.partition.label = ''  (string)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.media_size = 2032664576  (0x79280000)  (uint64)
  linux.fstab.mountpoint = '/media/mmcblk0p1'  (string)
  volume.partition.uuid = ''  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.is_mounted_read_only = false  (bool)
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' } (string list)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' } (string list)
  storage.model = ''  (string)
  volume.size = 2032537088  (0x79260e00)  (uint64)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_1769_6A29'  (string)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid=', 'flush', 'usefree' } (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' } (string list)
  block.major = 179  (0xb3)  (int)
  volume.fstype = 'vfat'  (string)
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' } (string list)
  volume.unmount.valid_options = { 'lazy' } (string list)
  linux.hotplug_type = 3  (0x3)  (int)
  volume.partition.start = 127488  (0x1f200)  (uint64)
  linux.sysfs_path = '/sys/block/mmcblk0/mmcblk0p1'  (string)
  linux.fstab.options = 'defaults,utf8,umask=007,gid=46'  (string)

and 

> 2: udi = '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host_mmc_card_rca58916'
  mmc.serial = 543928899  (0x206bb243)  (int)
  info.bus = 'mmc'  (string)
  mmc.oem = 'Unknown (21316)'  (string)
  mmc.date = '05/2007'  (string)
  mmc.cid = '035344534430324780206bb243007500'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host_mmc_card_rca58916'  (string)
  mmc.vendor = 'Unknown (3)'  (string)
  linux.subsystem = 'mmc'  (string)
  mmc.csd = '002600325f5a83c93efbcfff92804000'  (string)
  mmc.scr = '0225000000000000'  (string)
  info.vendor = 'Unknown (3)'  (string)
  info.subsystem = 'mmc'  (string)
  mmc.rca = 58916  (0xe624)  (int)
  info.product = 'SD02G'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.sysfs_path = '/sys/class/mmc_host/mmc0/mmc0:e624'  (string)
  mmc.hwrev = 8  (0x8)  (int)
  mmc.fwrev = 0  (0x0)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'  (string)
  info.linux.driver = 'mmcblk'  (string)

So hal's getting it,

Next, sudo udevmonitor, showing one removal and addition of the card:

> UEVENT[1196995763.354021] remove   /block/mmcblk0/mmcblk0p1 (block)
UEVENT[1196995763.354129] remove   /block/mmcblk0 (block)
UEVENT[1196995763.354152] remove   /class/mmc_host/mmc0/mmc0:e624 (mmc)
UDEV  [1196995763.365765] remove   /block/mmcblk0/mmcblk0p1 (block)
UDEV  [1196995763.365805] remove   /class/mmc_host/mmc0/mmc0:e624 (mmc)
UDEV  [1196995763.365826] remove   /block/mmcblk0 (block)
UEVENT[1196995765.486338] add      /class/mmc_host/mmc0/mmc0:e624 (mmc)
UEVENT[1196995765.487569] add      /block/mmcblk0 (block)
UEVENT[1196995765.487600] add      /block/mmcblk0/mmcblk0p1 (block)
UDEV  [1196995765.510374] add      /class/mmc_host/mmc0/mmc0:e624 (mmc)
UDEV  [1196995765.588606] add      /block/mmcblk0 (block)
UDEV  [1196995765.686968] add      /block/mmcblk0/mmcblk0p1 (block)

dbus-monitor --system (on add):

> signal sender=:1.3 -> dest=(null destination) path=/org/freedesktop/Hal/Manager; interface=org.freedesktop.Hal.Manager; member=DeviceAdded
   string "/org/freedesktop/Hal/devices/pci_1180_822_mmc_host_mmc_card_rca58916"
signal sender=:1.3 -> dest=(null destination) path=/org/freedesktop/Hal/Manager; interface=org.freedesktop.Hal.Manager; member=DeviceAdded
   string "/org/freedesktop/Hal/devices/storage_serial_0x206bb243"
signal sender=:1.3 -> dest=(null destination) path=/org/freedesktop/Hal/Manager; interface=org.freedesktop.Hal.Manager; member=DeviceAdded
   string "/org/freedesktop/Hal/devices/volume_uuid_1769_6A29"

..which are all the items man gnome-volume-manager says it uses..

also, there is no /usr/share/hal/fdi/policy/gparted-disable-automount.fdi to worry about either.

So, since neither my google-fu or forum search is being successful, any ideas?

---

### Post by dreikin on 2007-12-07
Two posts, one for some more information, and then the solution

For the same card, I could find it EVERYWHERE playing around on the command line.  System logs, udev, hal, /dev.  It was definitely detected by the system.

However, even
```
mount -t [auto,vfat] /dev/mmcblk0p1 /media/mmcblk0p1
```
failed, saying either I had to specify the file system (auto), or that it was the wrong one [vfat].  I used vfat before because it was the same one all the other cards showed up as.

So, moving over to the windows partition, I checked to make sure the card actually was working and such.

Yep.  No different than the others.

Struck luck on a google search though..

---

### Post by dreikin on 2007-12-07
Apparently, linux doesn't like SD 2.0 cards (the others were SD 1.x) with FAT filesystems != FAT32, and won't play nicely with them (at least on ubuntu).

So, quick copy of data, reformat as FAT32, copy back, and reboot..

and voila, it works.

So where should the bug report go, hmm?

(note: source of that bit of info: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96870](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96870) )

---

### Post by kwacka on 2008-01-19
error

---

