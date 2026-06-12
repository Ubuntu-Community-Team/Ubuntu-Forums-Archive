---
title: "Ipod and banshee"
date: 2007-05-02
forum: General Help
---

### Post by kejar31 on 2007-05-02
I can not get banshee to recognize my ipod (30 gig 5G) within 7.04 (fresh install). After reviewing it on banshee's web site I checked for the raidbug by running a script.

here is the output of that script

any help would be awsome.

[[------------ Output of 'ipod --list' ------------]]

Path Info
   Device Path:      /dev/sda2
   Mount Point:      /media/JUSTIN'S IP
   Control Path:     /media/JUSTIN'S IP/iPod_Control/
   HAL ID:           /org/freedesktop/Hal/devices/volume_uuid_E1C7_27AE
Device Info
   Model Number:     A446
   Device Model:     Video (Black)
   iPod Generation:  Fifth (5)
   Adv. Capacity:    30 GB
   Is New:           YES
   Writable:         YES
   Serial Number:    8K7049CSV9M
   Firmware Version: (null)
   Manufacturer ID:  8K
   Production Year:  2007
   Production Week:  04
   Production Index: 10840
Volume Info
   Volume Size:      29907118080
   Volume Used:      15291983872
   Available         14615134208
   UUID:             E1C7-27AE
   Label             JUSTIN'S IP
User-Provided Info
   Device Name:      (null)
   User Name:        (null)
   Host Name:        (null)
Supported Artwork Formats
   Cover:            200x200
   Cover:            100x100
   Photo:            50x41
   Photo:            320x240
   Photo:            130x88
   Photo:            640x480



[[-------------------- HAL Dump -------------------]]

<---- iPod Device 1 ---->
udi = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'
  org.freedesktop.Hal.Device.Storage.method_execpaths = { 'hal-storage-eject', 'hal-storage-closetray' } (string list)
  org.freedesktop.Hal.Device.Storage.method_argnames = { 'extra_options', 'extra_options' } (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = { 'as', 'as' } (string list)
  org.freedesktop.Hal.Device.Storage.method_names = { 'Eject', 'CloseTray' } (string list)
  info.interfaces = { 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage' } (string list)
  info.addons = { 'hald-addon-storage' } (string list)
  portable_audio_player.output_formats = { 'audio/mpeg', 'audio/aac' } (string list)
  portable_audio_player.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'  (string)
  portable_audio_player.type = 'ipod'  (string)
  portable_audio_player.access_method = 'storage'  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable.media_size = 30005821440  (0x6fc7c8000)  (uint64)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = true  (bool)
  info.capabilities = { 'storage', 'block', 'portable_audio_player' } (string list)
  info.category = 'portable_audio_player'  (string)
  info.product = 'iPod'  (string)
  info.vendor = 'Apple'  (string)
  storage.size = 0  (0x0)  (uint64)
  storage.removable = true  (bool)
  storage.removable.media_available = true  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001509E9DB_if0'  (string)
  storage.lun = 0  (0x0)  (int)
  storage.firmware_version = '1.62'  (string)
  storage.serial = 'Apple_iPod_000A27001509E9DB-0:0'  (string)
  storage.vendor = 'Apple'  (string)
  storage.model = 'iPod'  (string)
  storage.drive_type = 'disk'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.no_partitions_hint = false  (bool)
  storage.bus = 'usb'  (string)
  block.is_volume = false  (bool)
  block.minor = 0  (0x0)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sda'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5ac_1209_000A27001509E9DB_if0_scsi_host_scsi_device_lun0'  (string)
  linux.sysfs_path_device = '/sys/block/sda'  (string)
  linux.sysfs_path = '/sys/block/sda'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part1_size_98574336'
  info.udi = '/org/freedesktop/Hal/devices/volume_part1_size_98574336'  (string)
  volume.partition.flags = {  } (string list)
  volume.partition.uuid = ''  (string)
  volume.partition.label = ''  (string)
  volume.partition.type = '0x00'  (string)
  volume.partition.scheme = 'mbr'  (string)
  info.product = 'Volume'  (string)
  volume.partition.media_size = 30005821440  (0x6fc7c8000)  (uint64)
  volume.partition.start = 129024  (0x1f800)  (uint64)
  volume.size = 98574336  (0x5e02000)  (uint64)
  volume.num_blocks = 192528  (0x2f010)  (int)
  volume.block_size = 2048  (0x800)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.linux.is_device_mapper = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = false  (bool)
  volume.mount_point = ''  (string)
  volume.label = ''  (string)
  volume.uuid = ''  (string)
  volume.fsversion = ''  (string)
  volume.fsusage = ''  (string)
  volume.fstype = ''  (string)
  storage.model = ''  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'  (string)
  block.is_volume = true  (bool)
  block.minor = 1  (0x1)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sda1'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'  (string)
  linux.sysfs_path_device = '/sys/block/sda/sda1'  (string)
  linux.sysfs_path = '/sys/block/sda/sda1'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_E1C7_27AE'
  info.ipod.serial_number = '8K7049CSV9M'  (string)
  info.callouts.add = { 'hal-ipod-info' } (string list)
  volume.unmount.valid_options = { 'lazy' } (string list)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid=' } (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject', 'hal-ipod-info' } (string list)
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' } (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as', 'as' } (string list)
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject', 'WriteIpodInfo' } (string list)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' } (string list)
  volume.ignore = false  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_E1C7_27AE'  (string)
  volume.partition.flags = {  } (string list)
  volume.partition.uuid = ''  (string)
  volume.partition.label = ''  (string)
  volume.partition.type = '0x0b'  (string)
  volume.partition.scheme = 'mbr'  (string)
  info.product = 'JUSTIN'S IP'  (string)
  volume.partition.media_size = 30005821440  (0x6fc7c8000)  (uint64)
  volume.partition.start = 98703360  (0x5e21800)  (uint64)
  volume.size = 29907118080  (0x6f69a6800)  (uint64)
  volume.num_blocks = 58412340  (0x37b4d34)  (int)
  volume.block_size = 2048  (0x800)  (int)
  volume.partition.number = 2  (0x2)  (int)
  info.capabilities = { 'volume', 'block' } (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.linux.is_device_mapper = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/JUSTIN'S IP'  (string)
  volume.label = 'JUSTIN'S IP'  (string)
  volume.uuid = 'E1C7-27AE'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'vfat'  (string)
  storage.model = ''  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'  (string)
  block.is_volume = true  (bool)
  block.minor = 2  (0x2)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sda2'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A27001509E9DB_0_0'  (string)
  linux.sysfs_path_device = '/sys/block/sda/sda2'  (string)
  linux.sysfs_path = '/sys/block/sda/sda2'  (string)

      ************************* WARNING *************************
      * This iPod suffers from the volume.fsusage=raid bug.     *
      * As such, it cannot be used in Banshee. This is not a    *
      * Banshee or gnome-volume-manager bug. And the issue is   *
      * very well known.                                        *
      *                                                         *
      * Please read the following web page for more information *
      * including possible fixes to the problem:                *
      *                                                         *
      * [http://banshee-project.org/Troubleshooting/iPod/RaidBug](http://banshee-project.org/Troubleshooting/iPod/RaidBug) *
      ***********************************************************

---

### Post by Spectre31337 on 2007-05-02
I am having the same problem. I have also tried GTKPod at the sugestion of some other posts and neither of them can talk to my 5G 30 Gig iPod Video :confused:

---

