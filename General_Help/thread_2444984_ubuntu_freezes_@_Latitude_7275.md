---
title: "ubuntu freezes @ Latitude 7275"
date: 2020-06-07
forum: General Help
---

### Post by asgard2 on 2020-06-07
Hi,

I installed ubuntu on a Latitude 7275.
Before installation, I upgraded the bios version.

Ubuntu is freezing every time or very slow and it seems to get worse, the smartmoontools package installation took an around hour ... ](*,)

I tried to run a self-test, but the test is interrupted any time.  [https://pastebin.com/3t4FjsME](https://pastebin.com/3t4FjsME)

The errors in the smart log, should only appear after the Ubuntu installation & bios upgrade:
By reading smart values? 
```
9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       428
```
```
Error 386 occurred at disk power-on lifetime: 417 hours (17 days + 9 hours)

   When the command that caused the error occurred, the device was active or idle.
  
   After command completion occurred, registers were:
   ER ST SC SN CL CH DH
   -- -- -- -- -- -- --
   10 51 00 00 4f c2 e0  Error: IDNF
  
   Commands leading to the command that caused the error were:
   CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
   -- -- -- -- -- -- -- --  ----------------  --------------------
   b0 d5 01 e0 4f c2 00 00      01:05:37.730  SMART READ LOG
   b0 d0 01 00 4f c2 00 00      01:05:28.900  SMART READ DATA
   b0 d5 01 e0 4f c2 00 00      01:05:28.890  SMART READ LOG
   b0 d0 01 00 4f c2 00 00      01:05:23.850  SMART READ DATA
   b0 d5 01 e0 4f c2 00 00      01:05:23.840  SMART READ LOG
```


It is a 2in1 Tablet with Intel(R) Core(TM) m7-6Y75 CPU @ 1.20GHz .

The lshw output: [https://pastebin.com/Lks7T01m](https://pastebin.com/Lks7T01m)

On shutdown was an error with
> ata1:SError: PHYRdyChg CommWake
ata1 failed command: READ DMA
...
ata1 status: DRDY
blk_update_request i/o error dev, sda, sector
...

But the DELL device test returns "All tests passed." :-k

Anything I can try?

---

### Post by asgard2 on 2020-06-08
Maybe, that the device (scsi ?) controller is dying? :confused:

---

### Post by oldfred on 2020-06-08
Is drive in AHCI mode, not RAID, nor Intel RST?

Is install UEFI or BIOS?

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by asgard2 on 2020-06-08
It is installed in UEFI mode, secure boot is disabled.

AHCI - I can not find it in the bios options. Normaly it is unter *System Configuartion* - *SATA Operation @* Dell
But the options *Integrated NIC*, *SATA Operation, Drives *and* SMART Reporting *are not available at this device.

The boot repair is for devices with lost OS access?

After the shutdown error in the first post, booting was unavailable and the disk was not even listed at boot options. Now the OS is starting again, like nothing happened. It seems the freezes are getting worse after time ... at [#1]("https://ubuntuforums.org/showthread.php?t=2444984&p=13963540#post13963540"), the device was a few hours on.

---

### Post by oldfred on 2020-06-08
Some systems require you to see an UEFI password to open more settings. Never lose that password or else you may never get back into it. Some reset to blank after making changes.

Do log files show any issue?

Does top or htop (you may have to install htop) show heavy use of cpu, drives, some runaway apt?

Not all systems will show temps, but could be overheating?

---

### Post by asgard2 on 2020-06-09
From the dmesg log file, i only noticed:
> [    5.649898] kernel: Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-11-5.ddc
[    5.653563] kernel: Bluetooth: hci0: Applying Intel DDC parameters completed
[    6.588023] kernel: ACPI: Invalid package element [0]: got number, expecting [R]
[    6.588025] kernel: _ART package 0 is invalid, ignored
[    6.588055] kernel: ACPI: Invalid package element [0]: got number, expecting [R]
[    6.588056] kernel: _ART package 0 is invalid, ignored
[    6.598452] kernel: ACPI: Invalid package element [0]: got number, expecting [R]
[    6.598454] kernel: _ART package 0 is invalid, ignored
[    6.598479] kernel: ACPI: Invalid package element [0]: got number, expecting [R]
[    6.598480] kernel: _ART package 0 is invalid, ignored

But it seems to be incomplete.

The 20.04 on this device has only dmesg logs. My notebook with 18.04 has kern + syslog, but no dmesg. 
Something changed here with the new ubuntu release?

It is hard too reach a terminal. The the freeze comes, I can open a terminal, but the no response message appears. unable to quit the app or open a tty terminal, they are just black.

Update ...
> **oldfred said:**
> 
Do log files show any issue?
I found the errors, similar to the shutdown error message:
[https://pastebin.com/dtqydwJi](https://pastebin.com/dtqydwJi)

@oldfred could you  take a look at the error messages

As far as I can see, the temperature is in normal range (checked with lm-sensors) and no processes with heavy use. But there are some "temperature above threshold" messages too.

thx

---

### Post by oldfred on 2020-06-10
It looks like some errors on sda?
And I see "frozen" then lots of errors.

See what this says:
Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sda
Use hdparm to unfreeze
[http://ubuntuforums.org/showthread.php?t=2317805](http://ubuntuforums.org/showthread.php?t=2317805)
Info on freeze
[https://partedmagic.com/secure-erase/](https://partedmagic.com/secure-erase/)

---

### Post by asgard2 on 2020-06-11
@oldfred
you are right, the ssd is frozen

> Security: 
        Master password revision code = 49047
                supported
        not   enabled
        not   locked
                frozen
        not   expired: security count
                supported: enhanced erase
        Security level high
        2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT.

Could the I/O errors and smart data errors come from a frozen state?

dmesg:>  blk_update_request: I/O error, dev sda, sector 365854272 op 0x0:(READ) flags 0x80700 phys_seg 3 prio class 0
smart:>  Error: IDNF
No hdd password is set in the bios and a suspend is not unfreezing the ssd.

The Dell Bios "Data Wipe" with secure erase is not unfreezing it too.


It seems that it is not way around, I need to try the hot-swapping with pm?

---

### Post by asgard2 on 2020-06-14
@ oldfred
pm is stuck at boot, maybe this ubcd version is too old.

The frozen state seems actually be normal on some bios versions, but it should not affect the linux installation ... ?
I did a successful secure wipe over bios options, so it should be ok.

Here are some hints: [https://askubuntu.com/questions/133946/are-these-sata-errors-dangerous](https://askubuntu.com/questions/133946/are-these-sata-errors-dangerous)
FTR:
```
[Mi Jun 10 01:46:58 2020] mce: CPU1: **Core temperature above threshold**, cpu clock throttled (total events = 9)
 [Mi Jun 10 01:46:58 2020] mce: CPU3: Core temperature above threshold, cpu clock throttled (total events = 9)
 [Mi Jun 10 01:46:58 2020] mce: CPU1: Package temperature above threshold, cpu clock throttled (total events = 23)
 [Mi Jun 10 01:46:58 2020] mce: CPU3: Package temperature above threshold, cpu clock throttled (total events = 23)
 [Mi Jun 10 01:46:58 2020] mce: CPU2: Package temperature above threshold, cpu clock throttled (total events = 23)
 [Mi Jun 10 01:46:58 2020] mce: CPU0: Package temperature above threshold, cpu clock throttled (total events = 23)
 [Mi Jun 10 01:46:58 2020] mce: CPU1: Core temperature/speed normal
 [Mi Jun 10 01:46:58 2020] mce: CPU3: Core temperature/speed normal
 [Mi Jun 10 01:46:58 2020] mce: CPU1: Package temperature/speed normal
 [Mi Jun 10 01:46:58 2020] mce: CPU3: Package temperature/speed normal
 [Mi Jun 10 01:46:58 2020] mce: CPU0: Package temperature/speed normal
 [Mi Jun 10 01:46:58 2020] mce: CPU2: Package temperature/speed normal
 [Mi Jun 10 01:50:26 2020]** ata1.00: exception Emask 0x0 SAct 0x78 SErr 0x50000 action 0x6 frozen**
 [Mi Jun 10 01:50:26 2020] ata1: SError: { PHYRdyChg CommWake }
 [Mi Jun 10 01:50:26 2020] ata1.00: failed command: READ FPDMA QUEUED
 [Mi Jun 10 01:50:26 2020] ata1.00: cmd 60/00:18:40:7e:ce/01:00:15:00:00/40 tag 3 ncq dma 131072 in
                                    res 40/00:00:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
 [Mi Jun 10 01:50:26 2020] ata1.00: status: { DRDY }
 [Mi Jun 10 01:50:26 2020] ata1.00: failed command: READ FPDMA QUEUED
 [Mi Jun 10 01:50:26 2020] ata1.00: cmd 60/00:20:40:7f:ce/01:00:15:00:00/40 tag 4 ncq dma 131072 in
                                    res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 [Mi Jun 10 01:50:26 2020] ata1.00: status: { DRDY }
 [Mi Jun 10 01:50:26 2020] ata1.00: failed command: WRITE FPDMA QUEUED
 [Mi Jun 10 01:50:26 2020] ata1.00: cmd 61/08:28:c0:ca:af/00:00:15:00:00/40 tag 5 ncq dma 4096 out
                                    res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 [Mi Jun 10 01:50:26 2020] ata1.00: status: { DRDY }
 [Mi Jun 10 01:50:26 2020] ata1.00: failed command: READ FPDMA QUEUED
 [Mi Jun 10 01:50:26 2020] ata1.00: cmd 60/08:30:70:09:d1/00:00:15:00:00/40 tag 6 ncq dma 4096 in
                                    res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 [Mi Jun 10 01:50:26 2020] ata1.00: status: { DRDY }
 [Mi Jun 10 01:50:26 2020] ata1: hard resetting link
 [Mi Jun 10 01:50:26 2020] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 [Mi Jun 10 01:50:26 2020] ata1.00: configured for UDMA/133
 [Mi Jun 10 01:50:26 2020] ata1.00: device reported invalid CHS sector 0
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#3 Sense Key : Illegal Request [current] 
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#3 Add. Sense: Unaligned write command
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#3 CDB: Read(10) 28 00 15 ce 7e 40 00 01 00 00
 [Mi Jun 10 01:50:26 2020]** blk_update_request: I/O  error, dev sda, sector 365854272 op 0x0:(READ) flags 0x80700 phys_seg 3  prio class 0**
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#4 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#4 Sense Key : Illegal Request [current] 
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#4 Add. Sense: Unaligned write command
 [Mi Jun 10 01:50:26 2020] sd 0:0:0:0: [sda] tag#4 CDB: Read(10) 28 00 15 ce 7f 40 00 01 00 00
```

After the dmesg log, the temerature could be a problem, but this device has no fan ...

---

### Post by oldfred on 2020-06-14
That is saying ata1 is overtemp or your drive? So that may be why frozen?
Can you download & run Tools from vendor for SSD?
I have Samsung and they have their own tools.

---

### Post by asgard2 on 2020-06-14
The CPU temperature seems to be above threshold multiple times.

After the ssd wipe from the bios, i reinstalled ubuntu, at least the ssd was working yesterday.
Today it only booted to busybox because of filesystem errors and the same error messages with frozen ... are in the log.


It seems that I need to reinstall windows for ssd test software from this manufacturer.

---

### Post by asgard2 on 2020-06-16
@ 				 				 					 						 	[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711") The tool from the ssd vendor is not helping at all. But I updated the ssd firmware.

It is just saying anything is ok, but the extended self-test from a life linux was successful. No errors found.

On Windows at the beginning, anything worked, but then ... the same problems. 
The self-test from the vendor froze windows and the ssd test. On a live ubuntu I saw the test was stuck at some percent. I needed to power off, to cancel it, the -X option was not working.

Maybe the device is using some standby setting for the ssd interface and  this is messing anything up ... that would explain the delay.
Or some defective hardware on the mainboard board ? 

I do not know, it is strange. :(

---

### Post by oldfred on 2020-06-16
If vendors self test fails, then I would suspect hardware issues.
Does self test show anything in the way of errors.

Also in Ubuntu's Disks and upper right corner is Smart Data. Or you can download a terminal version of smart data and run tests. All I know is good/bad as total. 

See this from TheFu on SSD and Smartdata info:
[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)

---

### Post by asgard2 on 2020-06-18
Shouldn't it be the same self-test at smartmoontools and at the vendor software? The extended test in smartmoontools completed with no error.

The test from the vendor is not starting (or not finishing, because of the frozen test state I can find in linux). There is not error from the vendor software and no log from an interrupted selftest in the smart data. The vendor test was running the hole day, the device was just very hot, no result at all.

I updated the Link with the ssd smart data (old log below): [https://pastebin.com/3t4FjsME](https://pastebin.com/3t4FjsME)

---

