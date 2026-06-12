---
title: "unable to mount volume"
date: 2007-01-08
forum: General Help
---

### Post by styven on 2007-01-08
Hi all,

As of this morning i cannot mount anything that plugs in via usb, card reader, external hard drive etc.

Above the folder media (filesystems/media) there is a red box with a cross in it.

It seems i no longer have permission and i am not aware i have done anything to change my settings, all was fine last night.

Help :confused: 

Can someone help me get my permissions back [-o< 

Steve

---

### Post by laidback on 2007-01-08
Have you tried Computer>(right click on the device icon)>mount.

---

### Post by gaebriel on 2007-01-08
Have you read the /var/log/messages file to see if it can point you in the right direction?

---

### Post by styven on 2007-01-09
I have just had a look at /var/log messages, nothing jumping out at me, but then not sure what I am looking for.

Here is a sample from yesterday

Jan  8 19:53:15 styvens syslogd 1.4.1#18ubuntu6: restart.
Jan  8 19:53:44 styvens kernel: [17180023.528000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:54:04 styvens kernel: [17180043.968000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:54:31 styvens kernel: [17180070.596000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:54:37 styvens kernel: [17180077.076000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:54:40 styvens kernel: [17180079.600000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:55:25 styvens kernel: [17180124.392000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:56:27 styvens kernel: [17180187.024000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:56:50 styvens exiting on signal 15
Jan  8 19:56:51 styvens syslogd 1.4.1#18ubuntu6: restart.
Jan  8 19:58:10 styvens kernel: [17180289.964000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:58:27 styvens kernel: [17180306.252000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:58:41 styvens kernel: [17180320.792000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 19:59:22 styvens kernel: [17180361.448000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:01:11 styvens kernel: [17180470.244000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:01:11 styvens kernel: [17180470.416000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:01:31 styvens kernel: [17180490.764000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:01:58 styvens kernel: [17180517.324000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:02:53 styvens kernel: [17180572.104000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:03:59 styvens kernel: [17180638.672000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:04:26 styvens kernel: [17180665.208000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:05:12 styvens kernel: [17180711.920000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:05:17 styvens kernel: [17180716.352000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:06:00 styvens kernel: [17180759.116000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:06:14 styvens kernel: [17180773.568000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:07:09 styvens kernel: [17180828.364000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:07:31 styvens kernel: [17180850.816000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:08:06 styvens kernel: [17180885.468000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:09:05 styvens kernel: [17180944.212000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:09:11 styvens kernel: [17180950.536000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:10:12 styvens kernel: [17181011.412000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:10:28 styvens kernel: [17181027.804000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:10:55 styvens kernel: [17181054.380000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:10:57 styvens kernel: [17181056.868000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:11:16 styvens kernel: [17181075.496000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:11:22 styvens kernel: [17181081.988000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:12:35 styvens kernel: [17181154.928000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:13:00 styvens kernel: [17181179.316000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:13:02 styvens kernel: [17181181.768000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:13:25 styvens kernel: [17181204.428000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:13:45 styvens kernel: [17181224.956000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:13:48 styvens kernel: [17181227.452000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:14:07 styvens kernel: [17181246.084000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:14:11 styvens kernel: [17181250.568000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:14:28 styvens kernel: [17181267.180000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:16:21 styvens kernel: [17181380.248000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:16:37 styvens kernel: [17181396.476000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:17:12 styvens kernel: [17181431.172000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:17:14 styvens kernel: [17181433.576000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:17:33 styvens kernel: [17181452.388000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:18:58 styvens kernel: [17181537.344000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:19:22 styvens kernel: [17181561.680000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:20:15 styvens kernel: [17181614.436000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:20:41 styvens kernel: [17181640.912000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:21:06 styvens kernel: [17181665.488000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:21:28 styvens kernel: [17181688.016000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:21:55 styvens kernel: [17181714.652000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:23:00 styvens kernel: [17181779.468000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:23:04 styvens kernel: [17181783.764000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:23:53 styvens kernel: [17181832.564000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:23:57 styvens kernel: [17181836.928000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:25:04 styvens kernel: [17181903.840000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:25:51 styvens kernel: [17181950.388000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:25:53 styvens kernel: [17181952.740000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:27:33 styvens kernel: [17182052.032000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:27:49 styvens kernel: [17182068.292000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:28:09 styvens kernel: [17182088.848000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:28:12 styvens kernel: [17182091.316000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:29:05 styvens kernel: [17182144.060000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:29:55 styvens kernel: [17182194.684000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:30:02 styvens kernel: [17182201.148000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:31:04 styvens kernel: [17182263.904000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:32:07 styvens kernel: [17182326.680000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:32:36 styvens kernel: [17182355.136000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:32:36 styvens kernel: [17182355.304000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:32:50 styvens kernel: [17182369.612000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:33:47 styvens kernel: [17182426.448000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:33:59 styvens kernel: [17182438.832000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:34:10 styvens kernel: [17182449.372000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:35:03 styvens kernel: [17182502.172000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:35:15 styvens kernel: [17182514.572000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:35:44 styvens kernel: [17182543.224000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:36:49 styvens kernel: [17182608.024000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:36:55 styvens kernel: [17182614.336000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:37:36 styvens kernel: [17182655.084000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:37:50 styvens kernel: [17182669.540000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:38:59 styvens kernel: [17182738.428000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:40:20 styvens kernel: [17182819.168000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:41:14 styvens kernel: [17182873.704000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:42:17 styvens kernel: [17182936.396000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:42:43 styvens kernel: [17182962.832000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:42:48 styvens kernel: [17182967.284000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:44:37 styvens kernel: [17183076.444000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:44:40 styvens kernel: [17183079.092000] SCSI device sdc: 498176 512-byte hdwr sectors (255 MB)
Jan  8 20:44:40 styvens kernel: [17183079.092000] sdc: Write Protect is off
Jan  8 20:44:48 styvens kernel: [17183087.732000] SCSI device sdc: 498176 512-byte hdwr sectors (255 MB)
Jan  8 20:44:48 styvens kernel: [17183087.732000] sdc: Write Protect is off
Jan  8 20:44:55 styvens kernel: [17183094.288000] SCSI device sdc: 498176 512-byte hdwr sectors (255 MB)
Jan  8 20:44:55 styvens kernel: [17183094.288000] sdc: Write Protect is off
Jan  8 20:45:10 styvens kernel: [17183109.224000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:45:15 styvens kernel: [17183114.876000] SCSI device sdc: 498176 512-byte hdwr sectors (255 MB)
Jan  8 20:45:15 styvens kernel: [17183114.880000] sdc: Write Protect is off
Jan  8 20:45:48 styvens kernel: [17183147.556000] SCSI device sdc: 498176 512-byte hdwr sectors (255 MB)
Jan  8 20:45:48 styvens kernel: [17183147.556000] sdc: Write Protect is off
Jan  8 20:45:50 styvens kernel: [17183149.024000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:46:13 styvens kernel: [17183172.216000] usb 5-3.1: reset high speed USB device using ehci_hcd and address 3
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde : READ CAPACITY failed.
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde : status=0, message=00, host=7, driver=00 
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde : sense not available. 
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde: Write Protect is off
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde : READ CAPACITY failed.
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde : status=0, message=00, host=7, driver=00 
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde : sense not available. 
Jan  8 20:46:30 styvens kernel: [17183189.204000] sde: Write Protect is off
Jan  8 20:46:30 styvens kernel: [17183189.204000]  sde:<3>Buffer I/O error on device sde, logical block 0
Jan  8 20:46:30 styvens kernel: [17183189.204000]  unable to read partition table
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde : READ CAPACITY failed.
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde : status=0, message=00, host=7, driver=00 
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde : sense not available. 
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde: Write Protect is off
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde : READ CAPACITY failed.
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde : status=0, message=00, host=7, driver=00 
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde : sense not available. 
Jan  8 20:46:30 styvens kernel: [17183189.256000] sde: Write Protect is off
Jan  8 20:46:30 styvens kernel: [17183189.256000]  sde:<3>Buffer I/O error on device sde, logical block 0
Jan  8 20:46:30 styvens kernel: [17183189.272000]  unable to read partition table
Jan  8 20:46:30 styvens kernel: [17183189.320000] usb 5-3: USB disconnect, address 2
Jan  8 20:46:30 styvens kernel: [17183189.320000] usb 5-3.1: USB disconnect, address 3
Jan  8 20:46:30 styvens kernel: [17183189.320000] usb 5-3.2: USB disconnect, address 4
Jan  8 20:46:30 styvens kernel: [17183189.320000] usb 5-3.3: USB disconnect, address 5
Jan  8 20:46:30 styvens kernel: [17183189.320000] drivers/usb/class/usblp.c: usblp0: removed
Jan  8 20:46:30 styvens kernel: [17183189.320000] usb 5-3.4: USB disconnect, address 6
Jan  8 20:46:43 styvens kernel: [17183202.412000] usb 5-4: new high speed USB device using ehci_hcd and address 7
Jan  8 20:46:43 styvens kernel: [17183202.544000] usb 5-4: configuration #1 chosen from 1 choice
Jan  8 20:46:43 styvens kernel: [17183202.544000] hub 5-4:1.0: USB hub found
Jan  8 20:46:43 styvens kernel: [17183202.544000] hub 5-4:1.0: 4 ports detected
Jan  8 20:46:43 styvens kernel: [17183202.848000] usb 5-4.1: new high speed USB device using ehci_hcd and address 8
Jan  8 20:46:44 styvens kernel: [17183202.940000] usb 5-4.1: configuration #1 chosen from 1 choice
Jan  8 20:46:44 styvens kernel: [17183202.940000] scsi6 : SCSI emulation for USB Mass Storage devices
Jan  8 20:46:44 styvens kernel: [17183203.140000] usb 5-4.2: new high speed USB device using ehci_hcd and address 9
Jan  8 20:46:44 styvens kernel: [17183203.248000] usb 5-4.2: configuration #1 chosen from 1 choice
Jan  8 20:46:44 styvens kernel: [17183203.248000] scsi7 : SCSI emulation for USB Mass Storage devices
Jan  8 20:46:44 styvens kernel: [17183203.452000] usb 5-4.3: new full speed USB device using ehci_hcd and address 10
Jan  8 20:46:44 styvens kernel: [17183203.572000] usb 5-4.3: configuration #1 chosen from 1 choice
Jan  8 20:46:44 styvens kernel: [17183203.572000] drivers/usb/class/usblp.c: Disabling reads from problem bidirectional printer on usblp0
Jan  8 20:46:44 styvens kernel: [17183203.588000] drivers/usb/class/usblp.c: usblp0: USB Unidirectional printer dev 10 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0604
Jan  8 20:46:45 styvens kernel: [17183203.792000] usb 5-4.4: new low speed USB device using ehci_hcd and address 11
Jan  8 20:46:45 styvens kernel: [17183203.892000] usb 5-4.4: configuration #1 chosen from 1 choice
Jan  8 20:46:45 styvens kernel: [17183203.896000] input: Acrox USB & PS/2 Mouse as /class/input/input4
Jan  8 20:46:45 styvens kernel: [17183203.896000] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:1d.7-4.4
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
Jan  8 20:46:49 styvens kernel: [17183207.940000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:46:49 styvens kernel: [17183208.472000] SCSI device sdb: 498176 512-byte hdwr sectors (255 MB)
Jan  8 20:46:49 styvens kernel: [17183208.476000] sdb: Write Protect is off
Jan  8 20:46:49 styvens kernel: [17183208.476000] SCSI device sdb: 498176 512-byte hdwr sectors (255 MB)
Jan  8 20:46:49 styvens kernel: [17183208.476000] sdb: Write Protect is off
Jan  8 20:46:49 styvens kernel: [17183208.476000]  sdb: sdb1
Jan  8 20:46:49 styvens kernel: [17183208.480000] sd 6:0:0:0: Attached scsi removable disk sdb
Jan  8 20:46:49 styvens kernel: [17183208.480000] sd 6:0:0:0: Attached scsi generic sg1 type 0
Jan  8 20:46:49 styvens kernel: [17183208.484000] sd 6:0:0:1: Attached scsi removable disk sdc
Jan  8 20:46:49 styvens kernel: [17183208.484000] sd 6:0:0:1: Attached scsi generic sg2 type 0
Jan  8 20:46:49 styvens kernel: [17183208.484000] sd 6:0:0:2: Attached scsi removable disk sdd
Jan  8 20:46:49 styvens kernel: [17183208.484000] sd 6:0:0:2: Attached scsi generic sg3 type 0
Jan  8 20:46:49 styvens kernel: [17183208.488000] sd 6:0:0:3: Attached scsi removable disk sde
Jan  8 20:46:49 styvens kernel: [17183208.488000] sd 6:0:0:3: Attached scsi generic sg4 type 0
Jan  8 20:46:50 styvens kernel: [17183209.120000]   Vendor: Maxtor    Model: 3200              Rev: 0341
Jan  8 20:46:50 styvens kernel: [17183209.120000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Jan  8 20:46:50 styvens kernel: [17183209.140000] SCSI device sdf: 195813072 512-byte hdwr sectors (100256 MB)
Jan  8 20:46:50 styvens kernel: [17183209.140000] sdf: Write Protect is off
Jan  8 20:46:50 styvens kernel: [17183209.144000] SCSI device sdf: 195813072 512-byte hdwr sectors (100256 MB)
Jan  8 20:46:50 styvens kernel: [17183209.144000] sdf: Write Protect is off
Jan  8 20:46:50 styvens kernel: [17183209.144000]  sdf: sdf1
Jan  8 20:46:50 styvens kernel: [17183209.168000] sd 7:0:0:0: Attached scsi disk sdf
Jan  8 20:46:50 styvens kernel: [17183209.168000] sd 7:0:0:0: Attached scsi generic sg5 type 0
Jan  8 20:48:18 styvens kernel: [17183297.196000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 8
Jan  8 20:49:15 styvens kernel: [17183353.928000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 8
Jan  8 20:53:24 styvens kernel: [17183602.920000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 8
Jan  8 20:54:06 styvens kernel: [17183645.624000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 8
Jan  8 20:54:42 styvens kernel: [17183681.224000] usb 5-4: USB disconnect, address 7
Jan  8 20:54:42 styvens kernel: [17183681.224000] usb 5-4.1: USB disconnect, address 8
Jan  8 20:54:42 styvens kernel: [17183681.224000] usb 5-4.2: USB disconnect, address 9
Jan  8 20:54:42 styvens kernel: [17183681.224000] usb 5-4.3: USB disconnect, address 10
Jan  8 20:54:42 styvens kernel: [17183681.224000] drivers/usb/class/usblp.c: usblp0: removed
Jan  8 20:54:42 styvens kernel: [17183681.224000] usb 5-4.4: USB disconnect, address 11
Jan  8 20:54:47 styvens kernel: [17183686.252000] usb 5-4: new high speed USB device using ehci_hcd and address 12
Jan  8 20:54:47 styvens kernel: [17183686.384000] usb 5-4: configuration #1 chosen from 1 choice
Jan  8 20:54:47 styvens kernel: [17183686.384000] hub 5-4:1.0: USB hub found
Jan  8 20:54:47 styvens kernel: [17183686.384000] hub 5-4:1.0: 4 ports detected
Jan  8 20:54:47 styvens kernel: [17183686.688000] usb 5-4.1: new high speed USB device using ehci_hcd and address 13
Jan  8 20:54:48 styvens kernel: [17183686.780000] usb 5-4.1: configuration #1 chosen from 1 choice
Jan  8 20:54:48 styvens kernel: [17183686.780000] scsi8 : SCSI emulation for USB Mass Storage devices
Jan  8 20:54:48 styvens kernel: [17183686.980000] usb 5-4.2: new high speed USB device using ehci_hcd and address 14
Jan  8 20:54:48 styvens kernel: [17183687.088000] usb 5-4.2: configuration #1 chosen from 1 choice
Jan  8 20:54:48 styvens kernel: [17183687.088000] scsi9 : SCSI emulation for USB Mass Storage devices
Jan  8 20:54:48 styvens kernel: [17183687.292000] usb 5-4.3: new full speed USB device using ehci_hcd and address 15
Jan  8 20:54:48 styvens kernel: [17183687.420000] usb 5-4.3: configuration #1 chosen from 1 choice
Jan  8 20:54:48 styvens kernel: [17183687.420000] drivers/usb/class/usblp.c: Disabling reads from problem bidirectional printer on usblp0
Jan  8 20:54:48 styvens kernel: [17183687.436000] drivers/usb/class/usblp.c: usblp0: USB Unidirectional printer dev 15 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0604
Jan  8 20:54:48 styvens kernel: [17183687.636000] usb 5-4.4: new low speed USB device using ehci_hcd and address 16
Jan  8 20:54:48 styvens kernel: [17183687.732000] usb 5-4.4: configuration #1 chosen from 1 choice
Jan  8 20:54:48 styvens kernel: [17183687.736000] input: Acrox USB & PS/2 Mouse as /class/input/input5
Jan  8 20:54:48 styvens kernel: [17183687.736000] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:1d.7-4.4
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
Jan  8 20:54:52 styvens kernel: [17183691.780000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  8 20:54:52 styvens kernel: [17183691.784000] sd 8:0:0:0: Attached scsi removable disk sdb
Jan  8 20:54:52 styvens kernel: [17183691.784000] sd 8:0:0:0: Attached scsi generic sg1 type 0
Jan  8 20:54:52 styvens kernel: [17183691.788000] sd 8:0:0:1: Attached scsi removable disk sdc
Jan  8 20:54:52 styvens kernel: [17183691.788000] sd 8:0:0:1: Attached scsi generic sg2 type 0
Jan  8 20:54:52 styvens kernel: [17183691.788000] sd 8:0:0:2: Attached scsi removable disk sdd
Jan  8 20:54:52 styvens kernel: [17183691.788000] sd 8:0:0:2: Attached scsi generic sg3 type 0
Jan  8 20:54:52 styvens kernel: [17183691.792000] sd 8:0:0:3: Attached scsi removable disk sde
Jan  8 20:54:52 styvens kernel: [17183691.792000] sd 8:0:0:3: Attached scsi generic sg4 type 0
Jan  8 20:54:54 styvens kernel: [17183692.960000]   Vendor: Maxtor    Model: 3200              Rev: 0341
Jan  8 20:54:54 styvens kernel: [17183692.960000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Jan  8 20:54:54 styvens kernel: [17183692.960000] SCSI device sdf: 195813072 512-byte hdwr sectors (100256 MB)
Jan  8 20:54:54 styvens kernel: [17183692.960000] sdf: Write Protect is off
Jan  8 20:54:54 styvens kernel: [17183692.960000] SCSI device sdf: 195813072 512-byte hdwr sectors (100256 MB)
Jan  8 20:54:54 styvens kernel: [17183692.964000] sdf: Write Protect is off
Jan  8 20:54:54 styvens kernel: [17183692.964000]  sdf: sdf1
Jan  8 20:54:54 styvens kernel: [17183692.984000] sd 9:0:0:0: Attached scsi disk sdf
Jan  8 20:54:54 styvens kernel: [17183692.984000] sd 9:0:0:0: Attached scsi generic sg5 type 0
Jan  8 20:55:27 styvens kernel: [17183726.292000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:04:21 styvens kernel: [17184260.208000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:16:10 styvens kernel: [17184969.680000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:17:37 styvens kernel: [17185056.024000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:19:18 styvens kernel: [17185157.780000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:19:37 styvens kernel: [17185176.472000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:22:02 styvens kernel: [17185321.044000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:23:28 styvens kernel: [17185407.388000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:26:31 styvens kernel: [17185589.936000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:26:35 styvens kernel: [17185593.936000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:28:32 styvens kernel: [17185711.192000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:29:00 styvens kernel: [17185739.420000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:30:12 styvens kernel: [17185811.732000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:36:34 styvens kernel: [17186193.636000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:38:50 styvens kernel: [17186329.100000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:42:22 styvens kernel: [17186540.944000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:48:36 styvens kernel: [17186915.108000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:50:50 styvens kernel: [17187049.544000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:51:47 styvens kernel: [17187106.296000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:53:40 styvens kernel: [17187219.208000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 21:55:29 styvens gconfd (styven-4643): Failed to send buffer
Jan  8 21:58:21 styvens kernel: [17187500.008000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:01:20 styvens kernel: [17187679.128000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:05:13 styvens kernel: [17187911.796000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:06:47 styvens kernel: [17188006.340000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:07:44 styvens kernel: [17188063.448000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:09:42 styvens kernel: [17188181.168000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:12:47 styvens kernel: [17188366.224000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:13:40 styvens kernel: [17188419.380000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:15:11 styvens kernel: [17188510.328000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:16:32 styvens kernel: [17188590.816000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:18:06 styvens kernel: [17188685.356000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:18:14 styvens kernel: [17188693.540000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:22:17 styvens kernel: [17188936.496000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:25:03 styvens kernel: [17189101.660000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:26:41 styvens kernel: [17189199.860000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:27:55 styvens kernel: [17189274.284000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:33:56 styvens kernel: [17189634.904000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:35:59 styvens kernel: [17189757.564000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:36:19 styvens kernel: [17189777.956000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:38:04 styvens kernel: [17189882.544000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:38:28 styvens kernel: [17189906.804000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:41:16 styvens kernel: [17190075.324000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:44:23 styvens kernel: [17190261.908000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:46:48 styvens kernel: [17190407.304000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:47:05 styvens kernel: [17190424.016000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:48:11 styvens gconfd (styven-4643): Exiting
Jan  8 22:48:21 styvens kernel: [17190500.372000] usb 5-4.1: reset high speed USB device using ehci_hcd and address 13
Jan  8 22:48:26 styvens exiting on signal 15
Jan  9 19:01:32 styvens syslogd 1.4.1#18ubuntu6: restart.

Steve

---

### Post by Geir_Holst on 2007-01-11
> **gaebriel said:**
> Have you read the /var/log/messages file to see if it can point you in the right direction?

](*,) 
I am sharing your problem, seems my computer dont validate me loging  on as a root user any more.

This seems to be partialy my problem but why I do not know.
I &#314;l quote you soon as I figure it out.

---

### Post by gaebriel on 2007-01-14
You need to determine if it's a hardware problem or a permissions problem. Does the device function correctly on another computer? Have you tried mounting the device with sudo? i.e. ```
sudo mount /dev/sdf1 /media/usbdisk
```. From your log it looks like a USB drive is being recognized by the system at /dev/sdf, and /dev/sd[b-e] are media readers on your printer, but you'll need to replace the /dev/sdf1 in that command above to the appropriate device.

---

### Post by styven on 2007-01-14
Thanks for your input.

I would be suprised if it was a hardware problem, this means that all my media reading devices have stopped working at the same time, i can't access my cd rom either.

I think it is a permissions issue.

I have the follwing setup on my laptop.

1 x 4port usb hub
Connected to the hub is a usb multi card reader, hp printer, 100gb maxtor external hdd.

I can use my printer via the hub, but cannot mount anything else, even if i bypass the hub.

As you can see in my screenshots, the laptop can see all the drives i can't get onto them.

I really don't want to do another reinstall.

Steve.

---

### Post by styven on 2007-01-14
Not least because i can't back up my home folder ](*,)

---

### Post by styven on 2007-01-15
Hi,

Can anyone help, is there not a chmod 777 type command?

At this stage i would be happy to get access to my external hardrive.

Steve

---

### Post by styven on 2007-01-15
Hi again,

the issue seems to be that my media file is "red crossed" I can't change anythingas it is all greyed out.

See piccy.....

Steve

---

### Post by styven on 2007-01-15
sorry here's the pic..........

I did manage to get access by running "sudo chmod 777 -R /media"

This only let me access once, I need to have continuous access.


Steve

---

### Post by styven on 2007-01-16
Hi all,

Don't mean to go on, but i am getting desperate here:( 

I am running out of disk space on my laptop and really need to back up to my external drive so I can clear some space.

I have photos on memory cards, work files etc that i can't do anything with, please help!

Steve

---

### Post by gaebriel on 2007-01-23
If you just need to backup the data once, can't you just use sudo to make it happen? i.e. `sudo cp -pruv [source folder] [destination external disk mounted folder]`

---

