---
title: "USB has stopped working once I upgraded to 7.04"
date: 2007-07-06
forum: General Help
---

### Post by monocongo on 2007-07-06
I have recently upgraded from 6.10 to 7.04.  I was able to get USB devices to be recognized before by adding irqpoll to the default options in /boot/grub/menu.lst.  That file hasn't changed, but now my system no longer recognizes USB devices when they're plugged in.  Can someone suggest where I can look to find the problem?  I'd really like to have the use of my external hard drives again.  No problems at all when I boot into Windows XP so I assume there's nothing wrong with USB on this computer.

Thanks in advance.

--James

---

### Post by PgR on 2007-07-06
> **monocongo said:**
> Can someone suggest where I can look to find the problem?

The syslog.

```
tail /var/log/syslog -f
```

plug the device in, and see what it says. It's unlikely to say "Ah, you need to xxx" but it'll give you a starting point.

---

### Post by monocongo on 2007-07-06
Thanks PgR.

When I removed the USB cable I see this:
```
Jul  6 06:54:48 freethink kernel: [ 2801.753010] usb 1-1: USB disconnect, address 2
Jul  6 06:54:48 freethink NetworkManager: <debug info>^I[1183726488.967778] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0_scsi_device_lun0_scsi_generic').
Jul  6 06:54:48 freethink NetworkManager: <debug info>^I[1183726488.973616] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_CAE0999AE0998D77').
Jul  6 06:54:48 freethink NetworkManager: <debug info>^I[1183726488.978179] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0_scsi_device_lun0').
Jul  6 06:54:48 freethink NetworkManager: <debug info>^I[1183726488.980220] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0_scsi_host').
Jul  6 06:54:48 freethink NetworkManager: <debug info>^I[1183726488.984778] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_usbraw').
Jul  6 06:54:48 freethink NetworkManager: <debug info>^I[1183726488.988332] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0').
Jul  6 06:54:48 freethink NetworkManager: <debug info>^I[1183726488.990635] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740').
Jul  6 06:54:49 freethink NetworkManager: <debug info>^I[1183726489.026031] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ST332062_0AS_4BCDEF0000003740_0_0').
Jul  6 06:54:50 freethink kernel: [ 2803.717528] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01). Trying to recover by ending request.
```

When I plugged it back in I saw this:```
Jul  6 06:55:23 freethink kernel: [ 2836.263595] usb 1-1: new high speed USB device using ehci_hcd and address 5
Jul  6 06:55:23 freethink kernel: [ 2836.398796] usb 1-1: configuration #1 chosen from 1 choice
Jul  6 06:55:23 freethink kernel: [ 2836.399918] scsi6 : SCSI emulation for USB Mass Storage devices
Jul  6 06:55:23 freethink kernel: [ 2836.399962] usb-storage: device found at 5
Jul  6 06:55:23 freethink kernel: [ 2836.399963] usb-storage: waiting for device to settle before scanning
Jul  6 06:55:23 freethink NetworkManager: <debug info>^I[1183726523.687032] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740').
Jul  6 06:55:23 freethink NetworkManager: <debug info>^I[1183726523.764424] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0').
Jul  6 06:55:23 freethink NetworkManager: <debug info>^I[1183726523.785919] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0_scsi_host').
Jul  6 06:55:23 freethink NetworkManager: <debug info>^I[1183726523.817923] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_usbraw').
Jul  6 06:55:28 freethink kernel: [ 2841.390815] usb-storage: device scan complete
Jul  6 06:55:28 freethink kernel: [ 2841.391436] scsi 6:0:0:0: Direct-Access     ST332062 0AS              3.AA PQ: 0 ANSI: 4
Jul  6 06:55:28 freethink kernel: [ 2841.409020] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
Jul  6 06:55:28 freethink kernel: [ 2841.409516] sdb: Write Protect is off
Jul  6 06:55:28 freethink kernel: [ 2841.409519] sdb: Mode Sense: 11 00 00 00
Jul  6 06:55:28 freethink kernel: [ 2841.409521] sdb: assuming drive cache: write through
Jul  6 06:55:28 freethink kernel: [ 2841.410765] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
Jul  6 06:55:28 freethink kernel: [ 2841.411260] sdb: Write Protect is off
Jul  6 06:55:28 freethink kernel: [ 2841.411263] sdb: Mode Sense: 11 00 00 00
Jul  6 06:55:28 freethink kernel: [ 2841.411264] sdb: assuming drive cache: write through
Jul  6 06:55:28 freethink kernel: [ 2841.411267]  sdb: sdb1
Jul  6 06:55:28 freethink kernel: [ 2841.418557] sd 6:0:0:0: Attached scsi disk sdb
Jul  6 06:55:28 freethink kernel: [ 2841.418589] sd 6:0:0:0: Attached scsi generic sg1 type 0
Jul  6 06:55:28 freethink NetworkManager: <debug info>^I[1183726528.724825] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0_scsi_host_scsi_device_lun0').
Jul  6 06:55:28 freethink NetworkManager: <debug info>^I[1183726528.757969] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_2_4BCDEF0000003740_if0_scsi_host_scsi_device_lun0_scsi_generic').
Jul  6 06:55:28 freethink NetworkManager: <debug info>^I[1183726528.826339] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ST332062_0AS_4BCDEF0000003740_0_0').
Jul  6 06:55:28 freethink NetworkManager: <debug info>^I[1183726528.928929] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_CAE0999AE0998D77').
```

The above is mostly gibberish to me.  If someone can make sense of it for me I'll certainly appreciate the help.

--James

---

### Post by rikersmailbox on 2007-07-06
I have a similar problem with my laptop and I'd love to see someone come up with a solution...

---

### Post by PgR on 2007-07-09
Well it certainly seems to be seeing the drive OK.

What's it say in /etc/fstab? Mine has ```
/dev/sdc1       /media/sdc1 vfat defaults,rw,user,noauto 0 0
``` I would anticipate yours having a similar line (but refering to /dev/sdb1) The /media/sdc1 refers to the "mount point" which may be different to yours.

If there's no mention, then add that line to fstab (remembering to use sdb1) and make sure the mount point directory exists, then 

```
sudo mount /dev/sdb1
```

And see whether you can mount it manually.

---

### Post by monocongo on 2007-07-11
I added the following line to my /etc/fstab:

```
/dev/sdb1 /media/external1 ntfs-3g defaults,rw,user,noauto 0 0
```

Then I ran the mount command:

```
sudo mount /dev/sdb1
```  

It croaked with the following message:

```
fusermount: failed to access mountpoint /media/external1: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (Seagate320)
```

BTW Seagate320 is the name of the drive when it's mounted on Windows XP.

--James

---

### Post by monocongo on 2007-07-11
I just created the directory /media/external1 and tried the mount command again and now it works.

I have three external USB drives.  If I have all of them plugged in and have entries in /etc/fstab for each, will I be guaranteed to have them all mounted at the same spot each time, or is it a random selection?  In other words how can I be sure that Seagate320 will always be mounted onto /dev/sdb1 and WesternDigital250 will always be mounted on /dev/sdc?  Do the /dev/* files map to specific USB ports?

--James

---

### Post by PgR on 2007-07-11
Glad you've got that bit working.
Sorry - should have been more explicit about the directory having to exist, but you found it.

As for mounting them in the same place each time... I believe that it will assign /dev/sdb1 to the first drive it sees, /dev/sdc1 to the next, and so on.

With fixed disks you can give the UUID of a partition, rather than use /dev /.... to specify a mount point. Don't know if you can do that with USB (and I don't have any USB disks handy, just a flash drive)- but it would be worth a try.

To discover the UUID of the partition use```
sudo vol_id -u /dev/sdb1
``` then replace the "/dev/sdb1" reference in /etc/fstab with UUID=<whatever-it-came-up-with>

I'd be interested to know how you get on, 'cos then I can learn for next time.

---

### Post by PgR on 2007-07-11
> **monocongo said:**
> Do the /dev/* files map to specific USB ports?

No. Be helpful if they did, though, wouldn't it.

---

### Post by orb9220 on 2007-07-11
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

