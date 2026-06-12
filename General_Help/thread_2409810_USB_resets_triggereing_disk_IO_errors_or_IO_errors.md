---
title: "USB resets triggereing disk I/O errors or I/O errors triggering USB resets?"
date: 2019-01-07
forum: General Help
---

### Post by CharlesA on 2019-01-07
Hello,

I have been running into a bit of a puzzling situation - I am trying to restore data from backups stored on external USB 3.0 hard drives and I keep running into dmesg being flooded with these messages:

```

[83492.100280] sd 9:0:0:0: [sdl] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[83492.101876] sd 9:0:0:0: [sdl] Very big device. Trying to use READ CAPACITY(16).
[83492.123116] sd 9:0:0:0: [sdl] Very big device. Trying to use READ CAPACITY(16).
[83492.124330] sd 9:0:0:0: [sdl] Attached SCSI disk
[83550.022925] sd 9:0:0:0: [sdl] Very big device. Trying to use READ CAPACITY(16).
[85150.111759] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[85150.137032] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[85150.137038] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 00 c3 ee 73 c8 00 00 08 00 00 00
[85150.137041] print_req_error: I/O error, dev sdl, sector 3287184328
[86689.607608] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[86689.632889] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[86689.632892] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 00 07 d5 e7 28 00 00 01 00 00 00
[86689.632893] print_req_error: I/O error, dev sdl, sector 131458856
[86710.979573] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[86711.004782] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[86711.004788] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 01 2b c3 26 f0 00 00 01 00 00 00
[86711.004791] print_req_error: I/O error, dev sdl, sector 5029177072
[88185.900530] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[88185.925829] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[88185.925834] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 00 a2 1e 1a e0 00 00 01 00 00 00
[88185.925837] print_req_error: I/O error, dev sdl, sector 2719881952
[89656.852062] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[89656.877324] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[89656.877330] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 01 d2 d6 5e 70 00 00 01 00 00 00
[89656.877333] print_req_error: I/O error, dev sdl, sector 7832231536
[89820.099051] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[89820.124312] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[89820.124317] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 00 8f 8b 76 a8 00 00 01 00 00 00
[89820.124320] print_req_error: I/O error, dev sdl, sector 2408281768
[89967.437774] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[89967.463256] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[89967.463259] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 00 8f e4 bf 98 00 00 01 00 00 00
[89967.463260] print_req_error: I/O error, dev sdl, sector 2414133144
[90306.571110] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[90306.596162] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[90306.596164] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 01 76 36 4f b0 00 00 01 00 00 00
[90306.596166] print_req_error: I/O error, dev sdl, sector 6278238128
[90375.526407] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[90375.551670] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[90375.551676] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 01 76 b8 f8 58 00 00 08 00 00 00
[90375.551678] print_req_error: I/O error, dev sdl, sector 6286800984
[90608.936458] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[90608.961641] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[90608.961647] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 00 ad 7c da e8 00 00 01 00 00 00
[90608.961650] print_req_error: I/O error, dev sdl, sector 2910640872
[91352.890363] usb 6-1: reset SuperSpeed USB device number 3 using xhci_hcd
[91352.915572] sd 9:0:0:0: [sdl] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[91352.915575] sd 9:0:0:0: [sdl] tag#0 CDB: Read(16) 88 00 00 00 00 01 7e 25 2a a0 00 00 01 00 00 00
[91352.915576] print_req_error: I/O error, dev sdl, sector 6411332256

```

Now, I've had the same behavior with three or four different drives. Two brand new 10TB WD Easystores and a 5TB Toshiba are the latest.

Here's the smart error log data from the Toshiba drive.

```

smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.18-9-pve] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 3.5" MD04ACA... Enterprise HDD
Device Model:     TOSHIBA MD04ACA500
Serial Number:    <redacted>
LU WWN Device Id: 5 000039 68ba80e5a
Firmware Version: FP2A
User Capacity:    5,000,981,078,016 bytes [5.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sun Jan  6 23:00:26 2019 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART Status not supported: Incomplete response, ATA output registers missing
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       8550
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       41203
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   079   079   000    Old_age   Always       -       8667
 10 Spin_Retry_Count        0x0033   253   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       41202
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       142
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       65
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       41433
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       60 (Min/Max 17/71)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
**199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       20**
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   079   079   000    Old_age   Always       -       8564
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       204
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 20 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 20 occurred at disk power-on lifetime: 8666 hours (361 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 c0 90 4a 08 40  Error: ICRC, ABRT 192 sectors at LBA = 0x00084a90 = 543376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 50 4a 08 40 00      02:41:45.552  READ DMA EXT
  25 00 00 50 49 08 40 00      02:41:45.551  READ DMA EXT
  25 00 00 50 48 08 40 00      02:41:45.550  READ DMA EXT
  25 00 00 50 47 08 40 00      02:41:45.550  READ DMA EXT
  25 00 00 50 46 08 40 00      02:41:45.549  READ DMA EXT

Error 19 occurred at disk power-on lifetime: 8134 hours (338 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 20 98 03 ba 40  Error: ICRC, ABRT 32 sectors at LBA = 0x00ba0398 = 12190616

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 b8 02 ba 40 00      01:19:22.719  READ DMA EXT
  25 00 00 b8 fd b9 40 00      01:19:22.716  READ DMA EXT
  25 00 00 b8 fc b9 40 00      01:19:22.715  READ DMA EXT
  25 00 00 b8 fb b9 40 00      01:19:22.715  READ DMA EXT
  25 00 00 b8 fa b9 40 00      01:19:22.714  READ DMA EXT

Error 18 occurred at disk power-on lifetime: 8043 hours (335 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 d0 f0 46 35 40  Error: ICRC, ABRT 208 sectors at LBA = 0x003546f0 = 3491568

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 c0 46 35 40 00      01:15:11.713  READ DMA EXT
  25 00 00 c0 45 35 40 00      01:15:11.713  READ DMA EXT
  25 00 00 c0 44 35 40 00      01:15:11.712  READ DMA EXT
  25 00 00 c0 43 35 40 00      01:15:11.712  READ DMA EXT
  25 00 00 c0 42 35 40 00      01:15:11.711  READ DMA EXT

Error 17 occurred at disk power-on lifetime: 7774 hours (323 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 10 e8 06 66 40  Error: ICRC, ABRT 16 sectors at LBA = 0x006606e8 = 6686440

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 f8 05 66 40 00      02:10:41.377  READ DMA EXT
  25 00 00 f8 04 66 40 00      02:10:41.377  READ DMA EXT
  25 00 00 f8 03 66 40 00      02:10:41.376  READ DMA EXT
  25 00 00 f8 02 66 40 00      02:10:41.375  READ DMA EXT
  25 00 00 f8 01 66 40 00      02:10:41.375  READ DMA EXT

Error 16 occurred at disk power-on lifetime: 7773 hours (323 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 e0 68 bd 6c 40  Error: ICRC, ABRT 224 sectors at LBA = 0x006cbd68 = 7126376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 48 bd 6c 40 00      01:00:19.324  READ DMA EXT
  25 00 00 48 bc 6c 40 00      01:00:19.323  READ DMA EXT
  25 00 00 48 bb 6c 40 00      01:00:19.322  READ DMA EXT
  25 00 00 48 ba 6c 40 00      01:00:19.322  READ DMA EXT
  25 00 00 48 b9 6c 40 00      01:00:19.321  READ DMA EXT

```

When this issue occurs, zfs will detect the errors and put the pool into a degraded state but the files are still being copied. I have cancelled the copy and restored the files from a different backup medium (backup server, vs USB drive).

```
The number of checksum errors associated with a ZFS device
exceeded acceptable levels. ZFS has marked the device as
degraded.
```

I just want to figure out what the deal is since it doesn't make sense that several new drives and a couple old drives would freak out in the same fashion. All the affected drives are LUKS encrypted and have their own single ZFS pools. They have also recently had a scrub performed on them which found zero errors.

Most of the info I found online said to just ignore the USB resets, but if they are causing zfs to think the pool is degraded due to errors, and I see I/O errors in dmesg, I would not think they are safe to ignore.

The really strange part of this whole thing is if I remove the drive from the external enclosure and connect it via SATA.. ZFS scrubs it OK and shows no errors detected. Dmesg is also clean. I haven't tried copying the files over yet to see if I get the same behavior, but I have a feeling the files will copy fine when connected via SATA.

I've seen this problem on two different systems, both with onboard USB3 and expansion cards for USB3 support.

Any idea where to start to try to troubleshoot this? I could get around it be removing the drives from their enclosures and connecting via SATA, but that's a bit of a pain and I shouldn't have to do that.

I'm running kernel 4.9.0-8-amd64, currently.

---

### Post by QIII on 2019-01-07
Do any of the enclosures have e-SATA connections?  Can you rule out the enclosures or the expansion cards as the point(s) of failure?

---

### Post by CharlesA on 2019-01-07
> **QIII said:**
> Do any of the enclosures have e-SATA connections?  Can you rule out the enclosures or the expansion cards as the point(s) of failure?

They only have USB, unfortunately. I can try using a different USB cable, maybe.

I checked the status of the scrub I kicked off earlier and the pool is still degraded and I have more of the USB reset errors in dmesg... 

```

  pool: dvd_movies
 state: DEGRADED
status: One or more devices has experienced an unrecoverable error.  An
        attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
        using 'zpool clear' or replace the device with 'zpool replace'.
   see: http://zfsonlinux.org/msg/ZFS-8000-9P
  **scan: scrub repaired 0B in 5h40m with 0 errors on Mon Jan  7 04:10:32 2019**
config:

        NAME                STATE     READ WRITE CKSUM
        dvd_movies          DEGRADED     0     0     0
          crypt_dvd_movies  DEGRADED     0     0     0  too many errors

errors: No known data errors


```

I've added 3 new entries to the UDAM_CRC_ERROR_COUNT value:
```
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       23
```

I also noticed that these externals apparently hit 60C while under load, but I wouldn't have thought that heat would cause data errors.

Just for the heck of it, I think I will hook the drive up to the USB2 port and see if I get the same behavior of not with the same cable I am using now and see what happens.

---

### Post by CharlesA on 2019-01-08
> **CharlesA said:**
> Just for the heck of it, I think I will hook the drive up to the USB2 port and see if I get the same behavior of not with the same cable I am using now and see what happens.

The scrub crawled along at 30MB/sec rather than 100MB/sec, but it completed without errors and no I/O errors appeared in dmesg when I had it connected to a USB2 port. I used the same cable and same power adapter too.

This leads me to believe that the drives are OK and that somehow the USB3 interface isn't playing nice.

---

### Post by QIII on 2019-01-08
Were you using USB3 on your expansion card?

It would be nice to know if the hiccup is on the enclosure side or not.

---

### Post by CharlesA on 2019-01-08
> **QIII said:**
> Were you using USB3 on your expansion card?

It would be nice to know if the hiccup is on the enclosure side or not.

I was using USB3 both onboard and on the expansion card.

I had one enclosure (same model as the other one) perform fine when I was copying via rsync.. no errors on that one - either USB resets or I/O errors.

The problem seems random, and if I take the drives out of the enclosures and connect them via SATA they are fine. I just don't really want to have to do that.

---

### Post by QIII on 2019-01-08
Sounds like an excuse to buy all new stuffs?

---

### Post by QIII on 2019-01-08
Firmware versions different, maybe?

Refusing to work with Linux and expecting Windows?

---

### Post by CharlesA on 2019-01-08
> **QIII said:**
> Sounds like an excuse to buy all new stuffs?

Meh, I was close to buying 5 more drives and expanding the storage on the whole box. Then throw the old drives into the back up server and do the backups that way. No need for USB 3 when you transfer stuff over the network.

But that costs money... :(

> **QIII said:**
> Firmware versions different, maybe?

Refusing to work with Linux and expecting Windows?

I dunno. I think it might be a kernel thing because I remember running into the same type of thing with a USB 3.0 dock I bought a couple years ago. I shelved it cuz I thought it was the problem, but maybe it wasn't the problem after all.

What a pain in the butt, though, especially since I am out of ideas.

---

