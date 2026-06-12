---
title: "&quot;failure writing sector to hd0&quot; and (related?) keyboard errors"
date: 2017-01-18
forum: General Help
---

### Post by chestervonwinchester on 2017-01-18
On startup of my Samsung 900x laptop (Ubuntu 16.04), I experienced the error

```

failure writing sector (some hex code) to hd0
press any key to continue ...

```

I reached the login screen and was able to type my password, but upon logging in, I lost the keyboard and cursor! [Once in a while my keyboard doesn't work on startup]("http://askubuntu.com/questions/769419/keyboard-randomly-doesnt-work-on-startup"), but I've never experienced a `failure writing to sector` error along with it. Furthormore, I've never experienced losing the keyboard *after* login.


When I lose keyboard control, my only option to reboot is to force a power down (i.e., press and hold the power button). Could it be possible that when I'm forced to do this, that it causes disk errors?

`dmesg` seems to indicate many errors:

```

    [    1.949908] ata1.00: exception Emask 0x10 SAct 0x7f8000ff SErr 0x400100 action 0x6 frozen
    [    1.949915] ata1.00: irq_stat 0x08000000, interface fatal error
    [    1.949919] ata1: SError: { UnrecovData Handshk }
    [    1.949924] ata1.00: failed command: WRITE FPDMA QUEUED
    [    1.949940] ata1.00: cmd 61/08:00:08:08:10/00:00:06:00:00/40 tag 0 ncq 4096 out
                            res 40/00:e4:10:28:10/00:00:00:00:00/40 Emask 0x10 (ATA bus error)

```


Here is the full `dmesg` print out: [http://pastebin.com/raw/tBgBDpvV](http://pastebin.com/raw/tBgBDpvV)

**My questions**:

[LIST=1]
[*] Is it possible that "hard shutdown" (i.e., power-button power-down) can cause disk errors?
[*] If yes, how should I proceed in finding and fixing the (seemingly random) loss of keyboard control and the existing disk errors? If no, how should I proceed in fixing the disk errors above?
[/LIST]

---

### Post by laurent85 on 2017-01-18
The logs report an drive hardware failure, backup your data, hard disk may die soon.

Check current SMART drive's health,

install smartmontools:
```
sudo apt install smartmontools --no-install-recommends
```

generate and post back the report:
```
sudo smartctl -iHA --log=error /dev/sda
```

---

### Post by chestervonwinchester on 2017-01-18
Here is the result of `smartctl`:

```

smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-59-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     LITEONIT LMT-256M3M
Serial Number:    002240129533
LU WWN Device Id: 5 000000 000000000
Firmware Version: VZJ4
User Capacity:    256,060,514,304 bytes [256 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS, ATA/ATAPI-7 T13/1532D revision 4a
SATA Version is:  SATA 3.0, 6.0 Gb/s
Local Time is:    Wed Jan 18 09:23:26 2017 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0003   100   100   070    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0003   100   100   000    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0002   100   100   000    Old_age   Always       -       10090
 12 Power_Cycle_Count       0x0002   100   100   000    Old_age   Always       -       2917
171 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
173 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       69
174 Unknown_Attribute       0x0030   000   000   000    Old_age   Offline      -       80
178 Used_Rsvd_Blk_Cnt_Chip  0x0003   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0002   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0003   100   100   000    Pre-fail  Always       -       80
230 Unknown_SSD_Attribute   0x0032   100   100   000    Old_age   Always       -       142588
232 Available_Reservd_Space 0x0003   100   100   010    Pre-fail  Always       -       2848
241 Total_LBAs_Written      0x0003   100   100   000    Pre-fail  Always       -       383014
242 Total_LBAs_Read         0x0003   100   100   000    Pre-fail  Always       -       227344


SMART Error Log Version: 0
No Errors Logged

```

---

### Post by laurent85 on 2017-01-18
This hard disk is not in smartctl database so some hard disk attributes are unknown. Looking at the logs it seems the system could reset the sata link as no more errors are reported after resetting. So keyboard issue probably not related.

---

### Post by chestervonwinchester on 2017-01-18
> **laurent85 said:**
> This hard disk is not in smartctl database so some hard disk attributes are unknown. Looking at the logs it seems the system could reset the sata link as no more errors are reported after resetting. So keyboard issue probably not related.

Hmm. The following situation repeated about 3 or 4 times before I booted successfully:


[LIST=1]
[*]I boot up and encounter the `**failure writing sector to hd0**` message.
[*]I reach the login screen and type my password. Upon logging in, keyboard and mouse do not work.
[*]I force shutdown.
[/LIST]

So clearly the keyboard is related, but maybe only as collateral damage?

---

### Post by laurent85 on 2017-01-18
Check booting a usb live session keyboard and mouse are worling properly. If so, installed system is corrupted somehow.

---

### Post by chestervonwinchester on 2017-01-18
It looks like I will have to do that. I'll update this afterwards.

---

### Post by chestervonwinchester on 2017-01-18
**Update**:

I created a boot disc and found that there were no problems when I booted to that. I did a clean reinstall, and there's no longer any error messages in the output of `dmesg`, sooo ... problem solved? :(
[B]
Second update:

[/B]It's been through a few power on/off cycles now, and things still look good:

```

dmesg | less | grep ata1

[    1.570352] ata1: SATA max UDMA/133 abar m2048@0xf0708000 port 0xf0708100 irq 29
[    1.891641] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.891938] ata1.00: ATA-8: LITEONIT LMT-256M3M, VZJ4, max UDMA/133
[    1.891943] ata1.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.892304] ata1.00: configured for UDMA/133

```

Retrospectively, on the previous install, I ran some random terminal magic that I did not understand in order to get the keyboard backlight working. This could've played a part in the keyboard. I do not know why the hard disk became corrupted, and I am still puzzled as to why the two seemed related.

---

