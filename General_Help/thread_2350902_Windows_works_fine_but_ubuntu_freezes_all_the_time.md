---
title: "Windows works fine but ubuntu freezes all the time.."
date: 2017-01-28
forum: General Help
---

### Post by johnstefnds on 2017-01-28
Its like this: I have a dedicated hardisk which I use solely for ubuntu.
  I use ubuntu 16.10.
  The computer freezes seemingly randomly (it doesnt appear when running a certain/specific task nor around the same time).


  Some times it takes an hour to freeze some times a day but it WILL  freeze at some point within two days max even if I just leave it there  on the desktop without running any task at all. 


  By "freezing" I mean no keyboard response and the monitor stays on  but nothing moves not even the cursor and I have to shutdown the  computer by keeping the power button pushed down for a few seconds.


  What can I do to troubleshoot this and find what is at fault? like which logs to create(and how to create them) or check? 


  Thanks

---

### Post by ian-weisser on 2017-01-28
Start by noting the time of a freeze.

During a freeze, try CTRL+ALT+F1. If you reach a text login prompt, that means the X Sever has crashed. If nothing changes, then the entire kernel has crashed. Let us know which. It makes a big difference.

Stop holding down your power button. That causes other problems. It's like parking your car by gently crashing it into a curb every time.
Instead, do (hold)AltGr + (hold)Sysreq + (sequentially)E I U B
That will, among other things, terminate your processes and gracefully unmount your disk before rebooting. It's like parking your car by using the brakes.

After restarting, look in /var/log/syslog for the activity occurring before and at that time.

---

### Post by HereInOz on 2017-01-28
You could try installing GSmartControl and do a short, and if possible, an extended self test on your hard disk.  Check for, in particular, any read errors, write errors, and the reallocated sector count in the attributes tab.  This will give you indications as to whether the hard disk is failing or whether it appears to be OK.   If you are getting read or write errors, or the reallocated sector count is more than two or three, then that tends to indicate that the hard disk is on its way out. 

I tend to prefer R E I S U B as in ian-weisser's post.  That unmounts everything, shuts down the processes and reboots the computer.

---

### Post by johnstefnds on 2017-01-29
> **ian-weisser said:**
> Start by noting the time of a freeze.

During a freeze, try CTRL+ALT+F1. If you reach a text login prompt, that  means the X Sever has crashed. If nothing changes, then the entire  kernel has crashed. Let us know which. It makes a big difference.

Stop holding down your power button. That causes other problems. It's  like parking your car by gently crashing it into a curb every time.
Instead, do (hold)AltGr + (hold)Sysreq + (sequentially)E I U B
That will, among other things, terminate your processes and gracefully  unmount your disk before rebooting. It's like parking your car by using  the brakes.

After restarting, look in /var/log/syslog for the activity occurring before and at that time.





There is no alternative than to hold the power button as I mentioned keybord doesn't work either so CTRL+ALT+F1 or any other combination doesnt do anything at all.

---

### Post by ian-weisser on 2017-01-29
> **johnstefnds said:**
> There is no alternative than to hold the power button as I mentioned keybord doesn't work either so CTRL+ALT+F1 or any other combination doesnt do anything at all.

Yes, you said, "no keyboard response," which was vague. The tty and kernel reboot commands usually work even when the keyboard seems unresponsive in most other ways.

Are you saying that you tried both? And you are confirming a hard kernel crash? If so, what did syslog say?

---

### Post by johnstefnds on 2017-01-29
> **HereInOz said:**
> You could try installing GSmartControl and do a short, and if possible, an extended self test on your hard disk.  Check for, in particular, any read errors, write errors, and the reallocated sector count in the attributes tab.  This will give you indications as to whether the hard disk is failing or whether it appears to be OK.   If you are getting read or write errors, or the reallocated sector count is more than two or three, then that tends to indicate that the hard disk is on its way out. 

I tend to prefer R E I S U B as in ian-weisser's post.  That unmounts everything, shuts down the processes and reboots the computer.


This is the output of the extended test

```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.8.0-34-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SandForce Driven SSDs
Device Model:     ADATA SP900
Serial Number:    7E0320045323
LU WWN Device Id: 5 707c18 00002099a
Firmware Version: 5.0.7b
User Capacity:    128.035.676.160 bytes [128 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS, ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Jan 29 07:52:39 2017 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  48) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x0021)    SCT Status supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   120   120   050    Pre-fail  Always       -       0/0
  5 Retired_Block_Count     0x0033   100   100   003    Pre-fail  Always       -       2
  9 Power_On_Hours_and_Msec 0x0032   078   078   000    Old_age   Always       -       19287h+14m+32.990s
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       755
171 Program_Fail_Count      0x0032   000   000   000    Old_age   Always       -       1
172 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
174 Unexpect_Power_Loss_Ct  0x0030   000   000   000    Old_age   Offline      -       456
177 Wear_Range_Delta        0x0000   000   000   000    Old_age   Offline      -       10
181 Program_Fail_Count      0x0032   000   000   000    Old_age   Always       -       1
182 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   037   063   000    Old_age   Always       -       37 (Min/Max 14/63)
195 ECC_Uncorr_Error_Count  0x001c   100   100   000    Old_age   Offline      -       0/0
196 Reallocated_Event_Count 0x0033   100   100   003    Pre-fail  Always       -       2
201 Unc_Soft_Read_Err_Rate  0x001c   100   100   000    Old_age   Offline      -       0/0
204 Soft_ECC_Correct_Rate   0x001c   100   100   000    Old_age   Offline      -       0/0
230 Life_Curve_Status       0x0013   100   100   000    Pre-fail  Always       -       100
231 SSD_Life_Left           0x0013   096   096   010    Pre-fail  Always       -       0
233 SandForce_Internal      0x0000   000   000   000    Old_age   Offline      -       23924
234 SandForce_Internal      0x0032   000   000   000    Old_age   Always       -       16979
241 Lifetime_Writes_GiB     0x0032   000   000   000    Old_age   Always       -       16979
242 Lifetime_Reads_GiB      0x0032   000   000   000    Old_age   Always       -       11624

SMART Error Log not supported

SMART Self-test Log not supported

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

> **ian-weisser said:**
> Yes, you said, "no keyboard response," which was vague. The tty and kernel reboot commands usually work even when the keyboard seems unresponsive in most other ways.

Are you saying that you tried both? And you are confirming a hard kernel crash? If so, what did syslog say?

Nope I didnt try the last one (euib etc) cause I didnt know its existence..

But yes no console keybinds work and the keyboard doesnt work at all even the numlock /caps lock leds etc dont turn off or on (depends on their state prior to the freeze)

As for the sys log I cant make much sense of it but it doesnt record anything on the time the computer freezes there is a gap between around the time of the freeze and the time I reboot the system if it freezes again Ill post the sys log here... To post the current log now wouldnt make much sense I guess since for the last hours syslog has data the pc didnt freeze.

---

### Post by ian-weisser on 2017-01-29
If there's nothing unusual in syslog right before the freeze, then the crash is probably caused by hardware.
Most software crashes leave some kind of clue in the log.
If you're not sure, then post the 30-or-so lines before the freeze. (cut and paste, not screenshot please)

Total Guess: Some shoddy graphics cards crash the kernel due to poorly-written drivers. Do you have one of those? Search this forum for your graphic card model, and see if anyone else has had the same problem with the same model...

---

### Post by johnstefnds on 2017-01-30
> **ian-weisser said:**
> If there's nothing unusual in syslog right  before the freeze, then the crash is probably caused by hardware.
Most software crashes leave some kind of clue in the log.
If you're not sure, then post the 30-or-so lines before the freeze. (cut and paste, not screenshot please)

Total Guess: Some shoddy graphics cards crash the kernel due to  poorly-written drivers. Do you have one of those? Search this forum for  your graphic card model, and see if anyone else has had the same problem  with the same model...


The system froze while  switching between tabs in Firefox (and one of the tabs was a playing  video in youtube) at 8:00 AM (and some seconds) after almost a day of  continuous working without issue, I immediately pressed the power button  and restarted the computer. the log again stops at 7:45 and starts at  8:01...  everything on the log after 8:01 is about the boot process as  far as I can tell so because it was huge I only included a small part of  it. 


```
Jan 30 07:35:02 papajo-desktop anacron[23339]: Job `cron.daily' terminated
Jan 30 07:40:02 papajo-desktop anacron[23339]: Job `cron.weekly' started
Jan 30 07:40:02 papajo-desktop anacron[23928]: Updated timestamp for job `cron.weekly' to 2017-01-30
Jan  30 07:43:25 papajo-desktop compiz[2290]:  1485755005684#011addons.update-checker#011WARN#011Update manifest for  firefox@getpocket.com did not contain an updates property
Jan 30  07:43:25 papajo-desktop compiz[2290]:  1485755005705#011addons.update-checker#011WARN#011Update manifest for  webcompat@mozilla.org did not contain an updates property
Jan 30  07:43:25 papajo-desktop compiz[2290]:  1485755005740#011addons.update-checker#011WARN#011Update manifest for  aushelper@mozilla.org did not contain an updates property
Jan 30  07:43:25 papajo-desktop compiz[2290]:  1485755005777#011addons.update-checker#011WARN#011Update manifest for  e10srollout@mozilla.org did not contain an updates property
Jan 30  07:43:25 papajo-desktop compiz[2290]:  1485755005932#011addons.update-checker#011WARN#011Update manifest for  {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates  property
Jan 30 07:45:04 papajo-desktop anacron[23339]: Job `cron.weekly' terminated
Jan 30 07:45:04 papajo-desktop anacron[23339]: Normal exit (2 jobs run)
Jan 30 07:45:04 papajo-desktop systemd[1653]: Starting Notification regarding a new release of Ubuntu...
Jan  30 07:45:24 papajo-desktop check-new-release-gtk[24002]:  /usr/lib/ubuntu-release-upgrader/check-new-release-gtk:30: PyGIWarning:  Gtk was imported without specifying a version first. Use  gi.require_version('Gtk', '3.0') before import to ensure that the right  version gets loaded.
Jan 30 07:45:24 papajo-desktop check-new-release-gtk[24002]:   from gi.repository import Gtk
Jan 30 07:45:24 papajo-desktop check-new-release-gtk[24002]: WARNING:root:timeout reached, exiting
Jan 30 07:45:24 papajo-desktop systemd[1653]: Started Notification regarding a new release of Ubuntu.
Jan  30 07:45:38 papajo-desktop smartd[4862]: Device: /dev/sda [SAT], SMART  Usage Attribute: 194 Temperature_Celsius changed from 29 to 32
Jan 30  07:45:38 papajo-desktop smartd[4862]: Device: /dev/sdb [SAT], SMART  Usage Attribute: 190 Airflow_Temperature_Cel changed from 27 to 31
Jan  30 07:45:38 papajo-desktop smartd[4862]: Device: /dev/sdc [SAT], SMART  Usage Attribute: 194 Temperature_Celsius changed from 111 to 110
Jan  30 08:01:05 papajo-desktop rsyslogd: [origin software="rsyslogd"  swVersion="8.16.0" x-pid="1058" x-info="http://www.rsyslog.com"] start
Jan 30 08:01:05 papajo-desktop rsyslogd: rsyslogd's groupid changed to 108
Jan 30 08:01:05 papajo-desktop rsyslogd: rsyslogd's userid changed to 104
Jan 30 08:01:05 papajo-desktop systemd-modules-load[325]: Inserted module 'lp'
Jan 30 08:01:05 papajo-desktop systemd-modules-load[325]: Inserted module 'ppdev'
Jan 30 08:01:05 papajo-desktop keyboard-setup.sh[316]:  * Setting up keyboard layout...
Jan 30 08:01:05 papajo-desktop systemd-modules-load[325]: Inserted module 'parport_pc'
Jan 30 08:01:05 papajo-desktop systemd[1]: Started udev Kernel Device Manager.
Jan 30 08:01:05 papajo-desktop systemd[1]: Starting Remount Root and Kernel File Systems...
Jan 30 08:01:05 papajo-desktop systemd[1]: Started Remount Root and Kernel File Systems.
Jan 30 08:01:05 papajo-desktop systemd[1]: Starting udev Coldplug all Devices...
Jan 30 08:01:05 papajo-desktop systemd[1]: Starting Load/Save Random Seed...
Jan 30 08:01:05 papajo-desktop systemd[1]: Starting Flush Journal to Persistent Storage...
Jan 30 08:01:05 papajo-desktop systemd[1]: Started Load/Save Random Seed.
Jan 30 08:01:05 papajo-desktop systemd[1]: Started Flush Journal to Persistent Storage.
Jan 30 08:01:05 papajo-desktop keyboard-setup.sh[316]:    ...done.
Jan 30 08:01:05 papajo-desktop systemd[1]: Started Set the console keyboard layout.
Jan 30 08:01:05 papajo-desktop systemd[1]: Reached target Local File Systems (Pre).
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounting Mount unit for core...
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] Linux version  4.8.0-34-generic (buildd@lcy01-21) (gcc version 6.2.0 20161005 (Ubuntu  6.2.0-5ubuntu12) ) #36-Ubuntu SMP Wed Dec 21 17:24:18 UTC 2016 (Ubuntu  4.8.0-34.36-generic 4.8.11)
Jan 30 08:01:05 papajo-desktop kernel:  [    0.000000] Command line:  BOOT_IMAGE=/boot/vmlinuz-4.8.0-34-generic.efi.signed  root=UUID=46b19095-7f53-4e2e-aca9-17073adf965e ro quiet splash  vt.handoff=7
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounting Mount unit for htop...
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] KERNEL supported cpus:
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   Intel GenuineIntel
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounting Mount unit for sensors-unity...
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounting Mount unit for core...
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] x86/fpu: Enabled  xstate features 0x7, context size is 832 bytes, using 'standard' format.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] x86/fpu: Using 'eager' FPU context switches.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounted Mount unit for htop.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000de10ffff] usable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000de110000-0x00000000de4dffff] reserved
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounted Mount unit for core.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000de4e0000-0x00000000de8cdfff] ACPI NVS
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000de8ce000-0x00000000dee1efff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000dee1f000-0x00000000dee5cfff] type 20
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000dee5d000-0x00000000dee5dfff] usable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000dee5e000-0x00000000df063fff] ACPI NVS
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounted Mount unit for sensors-unity.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000df064000-0x00000000df462fff] usable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000df463000-0x00000000df7f2fff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000df7f3000-0x00000000df7fffff] usable
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounted Mount unit for core.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
Jan 30 08:01:05 papajo-desktop systemd[1]: Started udev Coldplug all Devices.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000041effffff] usable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 30 08:01:05 papajo-desktop systemd[1]: Starting Show Plymouth Boot Screen...
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] efi: EFI v2.31 by American Megatrends
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] efi:  ACPI=0xde8be000  ACPI 2.0=0xde8be000  SMBIOS=0xf04c0  MPS=0xfc080 
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] SMBIOS 2.7 present.
Jan 30 08:01:05 papajo-desktop systemd[1]: Started Show Plymouth Boot Screen.
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] DMI: To Be Filled By  O.E.M. To Be Filled By O.E.M./970 Pro3 R2.0, BIOS P2.80 05/31/2016
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan 30 08:01:05 papajo-desktop systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: No AGP bridge found
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] e820: last_pfn = 0x41f000 max_arch_pfn = 0x400000000
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] MTRR default type: uncachable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   00000-9FFFF write-back
Jan 30 08:01:05 papajo-desktop mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1.2"
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   A0000-BFFFF write-through
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   C0000-CFFFF write-protect
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   D0000-DFFFF uncachable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   E0000-FFFFF write-protect
Jan 30 08:01:05 papajo-desktop mtp-probe: checking bus 4, device 2: "/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2"
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
Jan 30 08:01:05 papajo-desktop mtp-probe: bus: 4, device: 2 was not an MTP device
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   3 base 0000DF800000 mask FFFFFF800000 uncachable
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   4 disabled
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   5 disabled
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   6 disabled
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   7 disabled
Jan 30 08:01:05 papajo-desktop mtp-probe: bus: 1, device: 4 was not an MTP device
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] TOM2: 000000041f000000 aka 16880M
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] total RAM covered: 3576M
Jan  30 08:01:05 papajo-desktop mtp-probe: checking bus 1, device 6:  "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1.4/1-1.4.2"
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Found optimal setting for mtrr clean up
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 3      lose cover RAM: 0G
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] e820: update [mem 0xdf800000-0xffffffff] usable ==> reserved
Jan 30 08:01:05 papajo-desktop mtp-probe: checking bus 7, device 2: "/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4"
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] found SMP MP-table at  [mem 0x000fc470-0x000fc47f] mapped at [ffff9cde000fc470]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Base memory trampoline at [ffff9cde00098000] 98000 size 24576
Jan 30 08:01:05 papajo-desktop mtp-probe: bus: 1, device: 6 was not an MTP device
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Using GB pages for direct mapping
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x5263c000, 0x5263cfff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x5263d000, 0x5263dfff] PGTABLE
Jan 30 08:01:05 papajo-desktop mtp-probe: bus: 7, device: 2 was not an MTP device
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x5263e000, 0x5263efff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x5263f000, 0x5263ffff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x52640000, 0x52640fff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x52641000, 0x52641fff] PGTABLE
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[418]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x52642000, 0x52642fff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x52643000, 0x52643fff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x52644000, 0x52644fff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x52645000, 0x52645fff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] BRK [0x52646000, 0x52646fff] PGTABLE
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] RAMDISK: [mem 0x3254a000-0x3529cfff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[434]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: RSDP 0x00000000DE8BE000 000024 (v02 ALASKA)
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: XSDT  0x00000000DE8BE078 00006C (v01 ALASKA A M I    01072009 AMI  00010013)
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: FACP  0x00000000DE8C4058 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI BIOS Warning  (bug): Optional FADT field Pm2ControlBlock has valid Length but zero  Address: 0x0000000000000000/0x1 (20160422/tbfadt-658)
Jan 30 08:01:05  papajo-desktop /usr/bin/snap[444]: cmd.go:101: DEBUG: not restarting  into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel:  [    0.000000] ACPI: DSDT 0x00000000DE8BE178 005EDF (v02 ALASKA A M I     00000000 INTL 20051117)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: FACS 0x00000000DE8C7080 000040
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: APIC  0x00000000DE8C4168 00009E (v03 ALASKA A M I    01072009 AMI  00010013)
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: FPDT  0x00000000DE8C4208 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: MCFG  0x00000000DE8C4250 00003C (v01 ALASKA A M I    01072009 MSFT 00010013)
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: AAFT  0x00000000DE8C4290 000062 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[500]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05  papajo-desktop kernel: [    0.000000] ACPI: HPET 0x00000000DE8C42F8  000038 (v01 ALASKA A M I    01072009 AMI  00000005)
Jan 30 08:01:05  papajo-desktop kernel: [    0.000000] ACPI: UEFI 0x00000000DE8C4330  000042 (v01 ALASKA A M I    01072009      00000000)
Jan 30 08:01:05  papajo-desktop kernel: [    0.000000] ACPI: BGRT 0x00000000DE8C4378  000038 (v00 ALASKA A M I    01072009 AMI  00010013)
Jan 30 08:01:05  papajo-desktop kernel: [    0.000000] ACPI: SSDT 0x00000000DE8C43B0  001714 (v01 AMD    POWERNOW 00000001 AMD  00000001)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[498]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] No NUMA configuration found
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000041effffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x41eff9000-0x41effdfff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Zone ranges:
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[499]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000041effffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   Device   empty
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Movable zone start for each node
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Early memory node ranges
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[495]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009ffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x00000000de10ffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   node   0: [mem 0x00000000dee5d000-0x00000000dee5dfff]
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[502]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   node   0: [mem 0x00000000df064000-0x00000000df462fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   node   0: [mem 0x00000000df7f3000-0x00000000df7fffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   node   0: [mem 0x0000000100001000-0x000000041effffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000041effffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] On node 0 totalpages: 4183227
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[496]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05  papajo-desktop /usr/bin/snap[504]: cmd.go:101: DEBUG: not restarting  into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[527]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[503]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[497]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[518]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[517]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[501]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[575]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[579]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[593]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[598]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[599]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop  /usr/bin/snap[609]: cmd.go:101: DEBUG: not restarting into  "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]): older than  "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   DMA zone: 25 pages reserved
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   DMA zone: 3999 pages, LIFO batch:0
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[600]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   DMA32 zone: 14165 pages used for memmap
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   DMA32 zone: 906525 pages, LIFO batch:31
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   Normal zone: 51136 pages used for memmap
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]   Normal zone: 3272703 pages, LIFO batch:31
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[610]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 9, version 33, address 0xfec00000, GSI 0-23
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] IOAPIC[1]: apic_id 10, version 33, address 0xfec20000, GSI 24-55
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[614]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[622]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[629]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xde110000-0xde4dffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xde4e0000-0xde8cdfff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xde8ce000-0xdee1efff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdee1f000-0xdee5cfff]
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[628]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdee5e000-0xdf063fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdf463000-0xdf7f2fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdf800000-0xfebfffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfec1ffff]
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[631]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec20000-0xfec20fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec21000-0xfecfffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[630]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeefffff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffffffff]
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[643]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] e820: [mem 0xdf800000-0xfebfffff] available for PCI devices
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] clocksource:  refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns:  7645519600211568 ns
Jan 30 08:01:05 papajo-desktop systemd[1]: Found device ADATA_SP900 EFI\x20System\x20Partition.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:8 nr_node_ids:1
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] percpu: Embedded 36  pages/cpu @ffff9ce21ec00000 s107864 r8192 d31400 u262144
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] pcpu-alloc: s107864 r8192 d31400 u262144 alloc=1*2097152
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Jan 30 08:01:05 papajo-desktop systemd[1]: Starting File System Check on /dev/disk/by-uuid/3671-1870...
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] Built 1 zonelists in  Node order, mobility grouping on.  Total pages: 4117837
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Policy zone: Normal
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-4.8.0-34-generic.efi.signed  root=UUID=46b19095-7f53-4e2e-aca9-17073adf965e ro quiet splash  vt.handoff=7
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan 30 08:01:05 papajo-desktop systemd[1]: Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: Checking aperture...
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: No AGP bridge found
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: Node 0: aperture [bus addr 0x6808000000-0x6809ffffff] (32MB)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
Jan 30 08:01:05 papajo-desktop systemd[1]: Found device ADATA_SP900 3.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: This costs you 64MB of RAM
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] AGP: Mapping aperture over RAM [mem 0xc8000000-0xcbffffff] (65536KB)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc8000000-0xcbffffff]
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] Memory:  16089672K/16732908K available (8836K kernel code, 1439K rwdata, 3812K  rodata, 1556K init, 1296K bss, 643236K reserved, 0K cma-reserved)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Jan 30 08:01:05 papajo-desktop systemd[1]: Found device ADATA_SP900 3.
Jan 30 08:01:05 papajo-desktop systemd[1]: Reached target Sound Card.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=512 to nr_cpu_ids=8.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] NR_IRQS:33024 nr_irqs:1032 16
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan 30 08:01:05 papajo-desktop systemd[1]: Started File System Check Daemon to report status.
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] Console: colour dummy device 80x25
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] console [tty0] enabled
Jan  30 08:01:05 papajo-desktop kernel: [    0.000000] clocksource: hpet:  mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484873504 ns
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] hpet clockevent registered
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jan 30 08:01:05 papajo-desktop systemd[1]: Activating swap Swap Partition...
Jan 30 08:01:05 papajo-desktop kernel: [    0.000000] tsc: Detected 3492.583 MHz processor
Jan 30 08:01:05 papajo-desktop swapon[678]: swapon: /dev/sda3: swapon failed: Invalid argument
Jan  30 08:01:05 papajo-desktop kernel: [    0.000019] Calibrating delay  loop (skipped), value calculated using timer frequency.. 6985.16  BogoMIPS (lpj=13970332)
Jan 30 08:01:05 papajo-desktop kernel: [    0.000021] pid_max: default: 32768 minimum: 301
Jan 30 08:01:05 papajo-desktop kernel: [    0.000031] ACPI: Core revision 20160422
Jan 30 08:01:05 papajo-desktop kernel: [    0.002696] ACPI: 2 ACPI AML tables successfully acquired and loaded
Jan 30 08:01:05 papajo-desktop systemd[1]: dev-sda3.swap: Swap process exited, code=exited status=255
Jan 30 08:01:05 papajo-desktop kernel: [    0.002698] 
Jan 30 08:01:05 papajo-desktop kernel: [    0.002946] Security Framework initialized
Jan 30 08:01:05 papajo-desktop systemd[1]: Failed to activate swap Swap Partition.
Jan 30 08:01:05 papajo-desktop kernel: [    0.002947] Yama: becoming mindful.
Jan 30 08:01:05 papajo-desktop kernel: [    0.002961] AppArmor: AppArmor initialized
Jan 30 08:01:05 papajo-desktop kernel: [    0.003809] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Jan 30 08:01:05 papajo-desktop kernel: [    0.007519] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jan 30 08:01:05 papajo-desktop kernel: [    0.009235] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
Jan 30 08:01:05 papajo-desktop systemd-fsck[659]: fsck.fat 4.0 (2016-05-06)
Jan 30 08:01:05 papajo-desktop kernel: [    0.009250] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
Jan 30 08:01:05 papajo-desktop kernel: [    0.009577] CPU: Physical Processor ID: 0
Jan 30 08:01:05 papajo-desktop kernel: [    0.009578] CPU: Processor Core ID: 0
Jan  30 08:01:05 papajo-desktop systemd-fsck[659]: 0x41: Dirty bit is set.  Fs was not properly unmounted and some data may be corrupt.
Jan 30 08:01:05 papajo-desktop kernel: [    0.009579] mce: CPU supports 7 MCE banks
Jan 30 08:01:05 papajo-desktop kernel: [    0.009585] LVT offset 1 assigned for vector 0xf9
Jan 30 08:01:05 papajo-desktop kernel: [    0.009590] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
Jan 30 08:01:05 papajo-desktop systemd-fsck[659]:  Automatically removing dirty bit.
Jan 30 08:01:05 papajo-desktop kernel: [    0.009591] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512, 1GB 0
Jan 30 08:01:05 papajo-desktop kernel: [    0.010114] Freeing SMP alternatives memory: 32K (ffffffffb9cee000 - ffffffffb9cf6000)
Jan 30 08:01:05 papajo-desktop kernel: [    0.020202] ftrace: allocating 33385 entries in 131 pages
Jan 30 08:01:05 papajo-desktop kernel: [    0.031541] smpboot: APIC(10) Converting physical 1 to logical package 0
Jan 30 08:01:05 papajo-desktop systemd-fsck[659]: Performing changes.
Jan 30 08:01:05 papajo-desktop kernel: [    0.031542] smpboot: Max logical packages: 2
Jan 30 08:01:05 papajo-desktop kernel: [    0.031890] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 30 08:01:05 papajo-desktop systemd-fsck[659]: /dev/sda1: 8 files, 915/130812 clusters
Jan  30 08:01:05 papajo-desktop kernel: [    0.175666] smpboot: CPU0: AMD  FX(tm)-8320 Eight-Core Processor (family: 0x15, model: 0x2, stepping:  0x0)
Jan 30 08:01:05 papajo-desktop kernel: [    0.175670] Performance Events: Fam15h core perfctr, AMD PMU driver.
Jan 30 08:01:05 papajo-desktop kernel: [    0.175673] ... version:                0
Jan 30 08:01:05 papajo-desktop kernel: [    0.175674] ... bit width:              48
Jan 30 08:01:05 papajo-desktop kernel: [    0.175674] ... generic registers:      6
Jan  30 08:01:05 papajo-desktop /usr/bin/snap[700]: cmd.go:101: DEBUG: not  restarting into "/snap/core/current/usr/bin/snap" ([VERSION=2.21 2.21]):  older than "/usr/bin/snap" (2.21+16.10)
Jan 30 08:01:05 papajo-desktop kernel: [    0.175675] ... value mask:             0000ffffffffffff
Jan 30 08:01:05 papajo-desktop kernel: [    0.175675] ... max period:             00007fffffffffff
Jan 30 08:01:05 papajo-desktop systemd[1]: dev-sda3.swap: Unit entered failed state.
Jan 30 08:01:05 papajo-desktop kernel: [    0.175676] ... fixed-purpose events:   0
Jan 30 08:01:05 papajo-desktop kernel: [    0.175676] ... event mask:             000000000000003f
Jan  30 08:01:05 papajo-desktop kernel: [    0.176384] NMI watchdog: enabled  on all CPUs, permanently consumes one hw-PMU counter.
Jan 30 08:01:05 papajo-desktop kernel: [    0.176475] x86: Booting SMP configuration:
Jan 30 08:01:05 papajo-desktop systemd[1]: Started File System Check on /dev/disk/by-uuid/3671-1870.
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounting /boot/efi...
Jan 30 08:01:05 papajo-desktop systemd[1]: Activating swap /dev/disk/by-uuid/11d19cb6-c572-4e1d-90c0-f175cd760208...
Jan 30 08:01:05 papajo-desktop swapon[730]: swapon: /dev/sda3: swapon failed: Invalid argument
Jan  30 08:01:05 papajo-desktop systemd[1]:  dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.swap:  Swap process exited, code=exited status=255
Jan 30 08:01:05 papajo-desktop kernel: [    0.176476] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
Jan  30 08:01:05 papajo-desktop rsyslogd-2039: Could not open output pipe  '/dev/xconsole':: No such file or directory [v8.16.0 try  http://www.rsyslog.com/e/2039 ]
Jan 30 08:01:05 papajo-desktop kernel: [    0.213053] x86: Booted up 1 node, 8 CPUs
Jan 30 08:01:05 papajo-desktop kernel: [    0.213055] smpboot: Total of 8 processors activated (55881.32 BogoMIPS)
Jan 30 08:01:05 papajo-desktop kernel: [    0.224725] devtmpfs: initialized
Jan 30 08:01:05 papajo-desktop kernel: [    0.224792] x86/mm: Memory block size: 128MB
Jan 30 08:01:05 papajo-desktop kernel: [    0.228780] evm: security.selinux
Jan  30 08:01:05 papajo-desktop rsyslogd-2007: action 'action 10' suspended,  next retry is Mon Jan 30 08:01:35 2017 [v8.16.0 try  http://www.rsyslog.com/e/2007 ]
Jan 30 08:01:05 papajo-desktop systemd[1]: Failed to activate swap /dev/disk/by-uuid/11d19cb6-c572-4e1d-90c0-f175cd760208.
Jan 30 08:01:05 papajo-desktop systemd[1]: Dependency failed for Swap.
Jan 30 08:01:05 papajo-desktop systemd[1]: swap.target: Job swap.target/start failed with result 'dependency'.
Jan  30 08:01:05 papajo-desktop systemd[1]:  dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.swap:  Unit entered failed state.
Jan 30 08:01:05 papajo-desktop systemd[1]: Mounted /boot/efi.
Jan 30 08:01:05 papajo-desktop systemd[1]: Reached target Local File Systems.
Jan 30 08:01:05 papajo-desktop kernel: [    0.228781] evm: security.SMACK64
Jan 30 08:01:05 papajo-desktop kernel: [    0.228781] evm: security.SMACK64EXEC
Jan 30 08:01:05 papajo-desktop kernel: [    0.228781] evm: security.SMACK64TRANSMUTE
Jan 30 08:01:05 papajo-desktop kernel: [    0.228782] evm: security.SMACK64MMAP
Jan 30 08:01:05 papajo-desktop kernel: [    0.228782] evm: security.ima
Jan 30 08:01:05 papajo-desktop kernel: [    0.228783] evm: security.capability
Jan  30 08:01:05 papajo-desktop kernel: [    0.228854] PM: Registering ACPI  NVS region [mem 0xde4e0000-0xde8cdfff] (4120576 bytes)
Jan 30  08:01:05 papajo-desktop kernel: [    0.228910] PM: Registering ACPI NVS  region [mem 0xdee5e000-0xdf063fff] (2121728 bytes)
Jan 30 08:01:05  papajo-desktop kernel: [    0.229005] clocksource: jiffies: mask:  0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Jan 30 08:01:05 papajo-desktop kernel: [    0.229054] pinctrl core: initialized pinctrl subsystem
Jan 30 08:01:05 papajo-desktop kernel: [    0.229152] RTC time:  6:01:00, date: 01/30/17
Jan 30 08:01:05 papajo-desktop kernel: [    0.229245] NET: Registered protocol family 16
Jan 30 08:01:05 papajo-desktop kernel: [    0.243665] cpuidle: using governor ladder
Jan 30 08:01:05 papajo-desktop kernel: [    0.259664] cpuidle: using governor menu
Jan 30 08:01:05 papajo-desktop kernel: [    0.259666] PCCT header not found.
Jan 30 08:01:05 papajo-desktop kernel: [    0.259735] ACPI: bus type PCI registered
Jan 30 08:01:05 papajo-desktop kernel: [    0.259736] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jan  30 08:01:05 papajo-desktop kernel: [    0.259796] PCI: MMCONFIG for  domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan 30 08:01:05 papajo-desktop kernel: [    0.259797] PCI: not using MMCONFIG
Jan 30 08:01:05 papajo-desktop kernel: [    0.259798] PCI: Using configuration type 1 for base access
Jan 30 08:01:05 papajo-desktop kernel: [    0.259799] PCI: Using configuration type 1 for extended access
Jan 30 08:01:05 papajo-desktop kernel: [    0.275847] HugeTLB registered 1 GB page size, pre-allocated 0 pages
Jan 30 08:01:05 papajo-desktop kernel: [    0.275848] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 30 08:01:05 papajo-desktop kernel: [    0.276168] ACPI: Added _OSI(Module Device)
Jan 30 08:01:05 papajo-desktop kernel: [    0.276168] ACPI: Added _OSI(Processor Device)
Jan 30 08:01:05 papajo-desktop kernel: [    0.276169] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan 30 08:01:05 papajo-desktop kernel: [    0.276169] ACPI: Added _OSI(Processor Aggregator Device)
Jan 30 08:01:05 papajo-desktop kernel: [    0.276347] ACPI: Executed 3 blocks of module-level executable AML code
Jan 30 08:01:05 papajo-desktop kernel: [    0.279184] ACPI: Interpreter enabled
Jan 30 08:01:05 papajo-desktop kernel: [    0.279198] ACPI: (supports S0 S3 S4 S5)
Jan 30 08:01:05 papajo-desktop kernel: [    0.279199] ACPI: Using IOAPIC for interrupt routing
Jan  30 08:01:05 papajo-desktop kernel: [    0.279319] PCI: MMCONFIG for  domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan  30 08:01:05 papajo-desktop kernel: [    0.279353] PCI: MMCONFIG at [mem  0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jan 30  08:01:05 papajo-desktop kernel: [    0.279356] pmd_set_huge: Cannot  satisfy [mem 0xe0000000-0xe0200000] with a huge-page mapping due to MTRR  override.
```

As for my graphics card I have a palit GTX 650 ti 2GB with the nvidia binary driver 367.57 (propreatery/tested) and couldnt find any particular issue on the interwebs yet. 

But as I said windows works normally so yea... i think my hardware is ok.

The rest of my specs are 16GB DDR3 memory at 2400Hz (but working at default frequency of the bios since I would have to OC my CPU in order to run the memory at 2400hz) 

I have an AMD FX 8320 (8 core @ 3.5 GHz) 

and 3 hard disks 2 are SSD (one that has the linux OS sda an other that I use just to save videos and data SDB and a normal HDD SDC)

It froze again a few minutes ago (about 10:04) while I was playing a game of chess online at lichess.org


```
Jan 30 10:04:14 papajo-desktop compiz[2406]: message repeated 3 times: [ WARN  2017-01-30 10:04:14 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it]
Jan 30 10:04:14 papajo-desktop gnome-session-binary[2255]: Entering running state
Jan 30 10:04:14 papajo-desktop nautilus[2732]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Jan 30 10:04:14 papajo-desktop nautilus[2732]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Jan 30 10:04:14 papajo-desktop dbus[1087]: [system] Successfully activated service 'org.freedesktop.locale1'
Jan 30 10:04:14 papajo-desktop systemd[1]: Started Locale Service.
Jan 30 10:04:14 papajo-desktop indicator-weather.desktop[2730]: /usr/bin/indicator-weather:28: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
Jan 30 10:04:14 papajo-desktop indicator-weather.desktop[2730]:   from gi.repository import AppIndicator3 as appIndicator
Jan 30 10:04:14 papajo-desktop dbus[1087]: [system] Activating service name='org.freedesktop.fwupd' (using servicehelper)
Jan 30 10:04:15 papajo-desktop fwupd[2771]: Failed to coldplug: UEFI firmware updating not supported
Jan 30 10:04:15 papajo-desktop dbus[1087]: [system] Successfully activated service 'org.freedesktop.fwupd'
Jan 30 10:04:17 papajo-desktop dbus-daemon[1700]: Activating service name='org.gnome.GConf'
Jan 30 10:04:17 papajo-desktop dbus-daemon[1700]: Successfully activated service 'org.gnome.GConf'
Jan 30 10:04:18 papajo-desktop unity-panel-ser[2425]: Already have a menu for window ID 52428825 with path /com/canonical/menu/3200019 from :1.123, unregistering that one
Jan 30 10:04:18 papajo-desktop compiz[2406]: console.error:
Jan 30 10:04:18 papajo-desktop compiz[2406]:   Corrupt session file (invalid JSON found)
Jan 30 10:04:18 papajo-desktop compiz[2406]:   Message: SyntaxError: JSON.parse: unexpected end of data at line 1 column 1 of the JSON data
Jan 30 10:04:18 papajo-desktop compiz[2406]:   Stack:
Jan 30 10:04:18 papajo-desktop compiz[2406]:     SessionFileInternal.read<@resource://app/modules/sessionstore/SessionFile.jsm:227:22
Jan 30 10:04:18 papajo-desktop compiz[2406]: TaskImpl_run@resource://gre/modules/Task.jsm:319:40
Jan 30 10:04:18 papajo-desktop compiz[2406]: Handler.prototype.process@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:937:23
Jan 30 10:04:18 papajo-desktop compiz[2406]: this.PromiseWalker.walkerLoop@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:816:7
Jan 30 10:04:18 papajo-desktop compiz[2406]: this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:750:11
Jan 30 10:04:18 papajo-desktop compiz[2406]:   SessionFileInternal.read<@resource://app/modules/sessionstore/SessionFile.jsm:227:22
Jan 30 10:04:18 papajo-desktop compiz[2406]: TaskImpl_run@resource://gre/modules/Task.jsm:319:40
Jan 30 10:04:18 papajo-desktop compiz[2406]: Handler.prototype.process@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:937:23
Jan 30 10:04:18 papajo-desktop compiz[2406]: this.PromiseWalker.walkerLoop@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:816:7
Jan 30 10:04:18 papajo-desktop compiz[2406]: this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:750:11
Jan 30 10:04:26 papajo-desktop pulseaudio[1561]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Jan 30 10:04:26 papajo-desktop pulseaudio[2444]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Jan 30 10:04:27 papajo-desktop systemd[1]: Stopping User Manager for UID 113...
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopped target Default.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopping D-Bus User Message Bus...
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopping Virtual filesystem service...
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopped D-Bus User Message Bus.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopped Virtual filesystem service.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopped target Basic System.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopped target Sockets.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopped target Paths.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Stopped target Timers.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Closed D-Bus User Message Bus Socket.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Reached target Shutdown.
Jan 30 10:04:27 papajo-desktop systemd[1360]: Starting Exit the Session...
Jan 30 10:04:27 papajo-desktop systemd[1360]: Received SIGRTMIN+24 from PID 2959 (kill).
Jan 30 10:04:27 papajo-desktop systemd[1]: Stopped User Manager for UID 113.
Jan 30 10:04:27 papajo-desktop systemd[1]: Removed slice User Slice of lightdm.
Jan 30 10:04:29 papajo-desktop systemd-timesyncd[860]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).
Jan 30 10:04:34 papajo-desktop dbus-daemon[1700]: Activating service name='org.gnome.zeitgeist.Engine'
Jan 30 10:04:34 papajo-desktop dbus-daemon[1700]: Activating service name='org.gnome.zeitgeist.SimpleIndexer'
Jan 30 10:04:34 papajo-desktop dbus-daemon[1700]: Successfully activated service 'org.gnome.zeitgeist.Engine'
Jan 30 10:04:34 papajo-desktop dbus-daemon[1700]: Successfully activated service 'org.gnome.zeitgeist.SimpleIndexer'
Jan 30 10:04:34 papajo-desktop zeitgeist-datah[2985]: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Jan 30 10:04:55 papajo-desktop systemd[1]: Starting Stop ureadahead data collection...
Jan 30 10:04:55 papajo-desktop systemd[1]: Started Stop ureadahead data collection.
Jan 30 10:05:16 papajo-desktop dbus-daemon[1700]: Activating service name='com.canonical.Unity.Scope.Home'
Jan 30 10:05:16 papajo-desktop dbus-daemon[1700]: Successfully activated service 'com.canonical.Unity.Scope.Home'
Jan 30 10:05:16 papajo-desktop dbus-daemon[1700]: Activating service name='com.canonical.Unity.Scope.Applications'
Jan 30 10:05:16 papajo-desktop dbus-daemon[1700]: Activating service name='com.canonical.Unity.Scope.LocalFiles'
Jan 30 10:05:16 papajo-desktop com.canonical.Unity.Scope.Applications[1700]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Jan 30 10:05:16 papajo-desktop unity-scope-loa[3086]: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Jan 30 10:05:16 papajo-desktop dbus-daemon[1700]: Successfully activated service 'com.canonical.Unity.Scope.LocalFiles'
Jan 30 10:05:16 papajo-desktop compiz[2406]: WARN  2017-01-30 10:05:16 unity.iconloader IconLoader.cpp:756 Unable to load icon file:///home/papajo at size -1x22: Error opening file /home/papajo: Is a directory
Jan 30 10:05:16 papajo-desktop dbus-daemon[1700]: Successfully activated service 'com.canonical.Unity.Scope.Applications'
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)' failed
Jan 30 10:05:21 papajo-desktop gnome-system-lo[3136]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL' failed


```

---

### Post by dragonfly41 on 2017-01-30
I can share my own experiences.  
It helps if you clarify your hardware in use.
You wrote ... > [COLOR=#000000]I have a dedicated hardisk which I use solely for ubuntu.[/COLOR][COLOR=#000000]
Is that an *external* USB hard disk with Ubuntu installed, and Windows is in your local drive?[/COLOR]

I have an old Dell Inspiron 1720 laptop which is dual boot configured (but I rarely use Windows so I can't say if I experience freezing in Windows mode). My daily use is Ubuntu 14.04 (32bits).

I experience freezes quite regularly, sometimes several times a day.  

I have learned to not use maximum memory (I have 3GB).  Tab management in browsers becomes important to avoid clocking up memory usage (particularly with Chromium Web Browser in use).   Chromium Web Browser add-ons such as OneTab allow open tabs to be saved and closed (thus releasing memory).

You can watch your usage of system resources by launching Applications > System Tools > System Monitor. Look at Resources tab.

In my own research for clues I have read that sometimes these freezes can be due to poor bedding of memory sticks.  
To pursue this theory, shut down the computer, remove power cable,  open up your PC or laptop and remove memory sticks one by one to be cleaned.

If you search for tutorials you will find different suggestions for cleaning memory sticks.

(a) use a cotton swab slightly moistened with rubbing fluid to clean the contact edges of each stick.  
or ...
(b) use a clean rubber (pencil rubber/eraser) to remove deposits on the contact edges.

Carefully replace sticks in same order as removal.  Avoid handling the sticks because of static discharge.  It helps if you have an anti-static wrist band but if not just hold the memory sticks lengthwise avoiding touching the contacts or components. 

On booting up you can start by running a memory test from the grub menu.

There is no guarantee that this will solve the freezing. It is only one point to check.

---

### Post by johnstefnds on 2017-01-30
No its an internal SSD (sda)  and I have 16GB of memory and +4GB of swap partition.

My system is surely overpowered for my usage (some office productivity videos and web surfing)

Ill try to clean the sticks though... since I dont know what else to do more other than that or praying :( 

[IMG]https://s3.amazonaws.com/lowres.cartoonstock.com/computers-computer_crash-fried_computers-lord-prays-prayers-jcon2913_low.jpg[/IMG]

---

### Post by dragonfly41 on 2017-01-30
I am envious of your system resources.  I've had a few crashes since I posted!
If you have 16GB memory you can try removing half (?) the sticks then running with reduced 8GB.
If no freezes after a test period try swapping with the removed 8 GB to see if you have a freeze.

---

### Post by johnstefnds on 2017-01-30
my sticks are fine I run a memtest and there were no issues there is something else wrong software wise... I dont want to return to windows but if those things keep happening I will be forced to...

---

### Post by dragonfly41 on 2017-01-30
I guess that this experiment tallies with the fact that there are no freezes when you run windows.
So the issue is to pin down the software root cause.
Can you try creating and running a separate user profile to see if this is profile related or other?

There is a very long shot you can try .. which is to install virtualbox in Windows and then install Ubuntu as a VM in virtualbox in Windows.
But that could be another fruitless experiment.

---

### Post by ian-weisser on 2017-01-30
Ubuntu does not have a "Freeze and Crash Without Warning Function" feature that can be mistakenly turned on. Years of work have squashed software bugs that cause that kind of behavior.
Web browsers, for example, themselves cannot freeze the system. There are whole layers of stack safeguards to prevent it...and this kind of freeze is not happening to millions of other browser users.

The second most common reason for the freezing you describe is a hardware driver bug. Linux and Windows use different drivers. Personally, I still think you have this (video card driver bug)...though you seem to have rejected the idea. I advise you to reconsider.
Either way, you are testing hardware, not software, to discover where the fault is. You must test your hardware methodically and deliberately. That will take time and careful recordkeeping.

We are willing to help you, as much as you are willing to be helped. But we cannot test your hardware for you.
Er, please don't disparage other OS. Some use Ubuntu by choice. Some use Windows by choice. Nobody is wrong. It's all a rich tapestry.

---

### Post by johnstefnds on 2017-01-30
well I can try later on creating a new profile.. but I dont have many hopes about that since this installation is very young I have only added VLC to it pychess and a weather program also a system monitor and thats it. 


As for installing a ubuntu vm in windows I dont know how that is going to be helpful

> **ian-weisser said:**
> Ubuntu does not have a "Freeze and Crash Without Warning Function" feature that can be mistakenly turned on. Years of work have squashed software bugs that cause that kind of behavior.

The most common reason for the freezing you describe, by far, is hardware. Linux is not Windows, and it uses hardware differently than Windows does. Until you really stress your hardware in both environments, you have not discounted that possibility.

The second most common reason for the freezing you describe is a hardware driver bug. Linux and Windows use different drivers. Personally, I still think you have this (video card driver bug)...though you seem to have rejected the idea without testing. Hey, it's your system and you know it best.

Either way, you are testing hardware, not software, to discover where the fault is. You must test your hardware methodically and deliberately. That will take time and careful recordkeeping.

Nobody here cares if you are 'forced' to return to Windows. We are not your vendor, and you are not our customer.
We are willing to help you, as much as you are willing to be helped. But we cannot test your hardware for you.

I dont know how you got the idea that I rejected something... tell me what to do and Ill do it... I dont know how to stress my graphics card in ubuntu...

---

### Post by ian-weisser on 2017-01-30
Try it the other way - remove the graphics card entirely. If the motherboard has graphics, use that for a couple days of normal use. If not, ssh into the system and put some load on it.

---

### Post by johnstefnds on 2017-01-30
The motherboard has no graphics unfortunately and the only other graphics card I have is a nvidia one too (9800 GX2 )

Ill try and run this ones and keep you posted if it crashes [https://fixmynix.com/gpu-benchmarking-and-stress-testing-in-linux/](https://fixmynix.com/gpu-benchmarking-and-stress-testing-in-linux/)

I run the first two for a few minutes and nothing happened but I have work to do now so I will run them more extensively later on

Also what do you mean by "ssh into the system and put some load into it" I dont know how to do that... I just know what ssh is but I dont know any command that will put some load on my system.

---

### Post by dragonfly41 on 2017-01-30
> [COLOR=#000000]As for installing a ubuntu vm in windows I dont know how that is going to be helpful

The logic is that if your VM Ubuntu does not freeze and your native Ubuntu does continue to freeze then this underlines the fact that you have some issue with native Ubuntu.

The other advantage of using virtualbox is that you can experiment with different distros.

But you could also install a second native Ubuntu on your SSD so that you can see some pattern of failure.

It is a process of elimination.  [/COLOR]https://en.wikiquote.org/wiki/Sherlock_Holmes

---

### Post by Perfect Storm on 2017-01-30
I had same experienced as you with my laptop with 16.04 current kernel. I fixed by updating to latest version of the kernel.
But it might be risky...

---

### Post by johnstefnds on 2017-01-31
Ok I run the afore mentioned GPU stress test for a day and nothing happened...

Today again while watching a video on youtube my system crushed at 12:44:14


I notice on the syslog that nothing comes up exactly or near that time... but again a SMART temp test is called and I see a kernel message about a tcp flooding or something like that... I dont know if thats significant or just an other thing that might happen while browsing for hours...

```
Jan 31 11:07:59 papajo-desktop anacron[1067]: Job `cron.daily' terminated
Jan 31 11:07:59 papajo-desktop anacron[1067]: Normal exit (1 job run)
Jan 31 11:13:08 papajo-desktop compiz[2510]: 1485853988578#011addons.update-checker#011WARN#011Update manifest for firefox@getpocket.com did not contain an updates property
Jan 31 11:13:08 papajo-desktop compiz[2510]: 1485853988586#011addons.update-checker#011WARN#011Update manifest for webcompat@mozilla.org did not contain an updates property
Jan 31 11:13:08 papajo-desktop compiz[2510]: 1485853988644#011addons.update-checker#011WARN#011Update manifest for aushelper@mozilla.org did not contain an updates property
Jan 31 11:13:08 papajo-desktop compiz[2510]: 1485853988662#011addons.update-checker#011WARN#011Update manifest for e10srollout@mozilla.org did not contain an updates property
Jan 31 11:13:08 papajo-desktop compiz[2510]: 1485853988830#011addons.update-checker#011WARN#011Update manifest for {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates property
Jan 31 11:15:33 papajo-desktop AptDaemon: INFO: Quitting due to inactivity
Jan 31 11:15:33 papajo-desktop AptDaemon: INFO: Quitting was requested
Jan 31 11:15:33 papajo-desktop org.debian.apt[1020]: 11:15:33 AptDaemon [INFO]: Quitting due to inactivity
Jan 31 11:15:33 papajo-desktop org.debian.apt[1020]: 11:15:33 AptDaemon [INFO]: Quitting was requested
Jan 31 11:17:01 papajo-desktop CRON[3965]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 31 11:18:01 papajo-desktop systemd[1]: Starting Cleanup of Temporary Directories...
Jan 31 11:18:01 papajo-desktop systemd-tmpfiles[3985]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jan 31 11:18:01 papajo-desktop systemd[1]: Started Cleanup of Temporary Directories.
Jan 31 11:32:58 papajo-desktop smartd[1066]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 18 to 26
Jan 31 11:32:58 papajo-desktop smartd[1066]: Device: /dev/sdb [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 18 to 24
Jan 31 11:32:58 papajo-desktop smartd[1066]: Device: /dev/sdc [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 125 to 113
Jan 31 11:35:21 papajo-desktop compiz[2510]: [aac @ 0x7fd51ec44800] Prediction is not allowed in AAC-LC.
Jan 31 11:35:21 papajo-desktop compiz[2510]: [aac @ 0x7fd51ec44800] channel element 3.2 is not allocated
Jan 31 11:35:21 papajo-desktop compiz[2510]: [aac @ 0x7fd51ec44800] Sample rate index in program config element does not match the sample rate index configured by the container.
Jan 31 11:35:21 papajo-desktop compiz[2510]: [aac @ 0x7fd51ec44800] Remapped id too large
Jan 31 11:35:21 papajo-desktop compiz[2510]: [aac @ 0x7fd51ec44800]  is not implemented. Update your FFmpeg version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
Jan 31 11:35:21 papajo-desktop compiz[2510]: [aac @ 0x7fd51ec44800] If you want to help, upload a sample of this file to ftp://upload.ffmpeg.org/incoming/ and contact the ffmpeg-devel mailing list. (ffmpeg-devel@ffmpeg.org)
Jan 31 11:35:21 papajo-desktop compiz[2510]: [aac @ 0x7fd51ec44800] channel element 3.4 is not allocated
Jan 31 11:37:13 papajo-desktop compiz[2510]: Vector smash protection is enabled.
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_set_accel_path: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_add_accelerator: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_set_accel_path: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_add_accelerator: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_set_accel_path: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_add_accelerator: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_set_accel_path: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_add_accelerator: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_set_accel_path: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 11:41:23 papajo-desktop unity-panel-ser[2526]: gtk_widget_add_accelerator: assertion 'GTK_IS_ACCEL_GROUP (accel_group)' failed
Jan 31 12:02:58 papajo-desktop smartd[1066]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 26 to 29
Jan 31 12:02:59 papajo-desktop smartd[1066]: Device: /dev/sdb [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 24 to 27
Jan 31 12:02:59 papajo-desktop smartd[1066]: Device: /dev/sdc [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 113 to 111
Jan 31 12:03:25 papajo-desktop evolution-sourc[2615]: secret_service_search_sync: must specify at least one attribute to match
Jan 31 12:14:47 papajo-desktop unity-panel-ser[2526]: menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed
Jan 31 12:17:01 papajo-desktop CRON[5185]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
**Jan 31 12:18:17 papajo-desktop kernel: [ 4525.185977] TCP: request_sock_TCP: Possible SYN flooding on port 8999. Sending cookies.  Check SNMP counters.**
Jan 31 12:32:58 papajo-desktop smartd[1066]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 29 to 31
Jan 31 12:32:58 papajo-desktop smartd[1066]: Device: /dev/sdb [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 27 to 29
Jan 31 12:32:58 papajo-desktop smartd[1066]: Device: /dev/sdc [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 111 to 110 
```


I would like to mention that when I opened the "Disks" program I noticed some weird directories? virtual drives? that I didnt create and dont know how they materialized into this installation are they native to 16.10? cause when I had 16.04LTS I didnt had those... 

[IMG]http://i64.tinypic.com/3163jpd.jpg[/IMG]

---

### Post by dragonfly41 on 2017-01-31
> [COLOR=#000000]Today again while watching a video on youtube my system crushed [sic] at 12:44:14

That is one clue I would focus on.

I've read quite a number of discussion threads on Ubuntu freezing symptoms and some common clues are "video" and "chrome".

Have you tried switching off hardware acceleration?
Have you tried running youtube with HTML5 option and flash player uninstalled?[/COLOR]

---

### Post by johnstefnds on 2017-01-31
> **dragonfly41 said:**
> That is one clue I would focus on.

I've read quite a number of discussion threads on Ubuntu freezing symptoms and some common clues are "video" and "chrome".

Have you tried switching off hardware acceleration?
Have you tried running youtube with HTML5 option and flash player uninstalled?[/COLOR]

I use firefox.

I have switched off hardware acceleration (although I wouldnt consider this a fix since if I have to turn down all the features of the system then why to use the system? :P but anyway as I said I have it off)

As for HTML5 I think its enabled by default on youtube, checking on this page [https://www.youtube.com/html5](https://www.youtube.com/html5) everything was ticket.


is there any way to contact ubuntu support or something like that? cause I think my issue needs a guy who really knows about linux and ubuntu...  I think I have done most of the "fixes" and tests a normal user would do.

---

### Post by ian-weisser on 2017-01-31
Ubuntu is community-supported.
That means us, sorry.

Some of the gurus passing through this thread have decades of experience with software and hardware. Many are IT professionals (and retired IT professionals) with plenty of Linux and Ubuntu knowledge.
You are, of course, welcome to look around for better help.
If you don't find it, you are welcome to keep trying with us. We like to help.

---

### Post by dragonfly41 on 2017-01-31
@johnstefnds
You are one of many puzzled by Ubuntu freezing symptoms.
There is no single solution or theory as to root cause.   There are so many variables. It could be hardware, software or a combination of factors.
If you followed earlier advice we would at least know if Ubuntu runs as a VM in Windows without problems.
Virtual Box uses different drivers, for example.
As I indicated you need to do detective work, looking for clues, so that others might help to pin down the root cause.
Here is yet another example of a user trying to solve the problem.

[http://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly](http://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly)

You can find these threads yourself by careful searching.
For example since you use firefox have you tried running this in safe mode, with no add-ons enabled?
If you find the solution, I will be interested to hear.
Good luck.

---

### Post by johnstefnds on 2017-02-01
> **dragonfly41 said:**
> @johnstefnds
You are one of many puzzled by Ubuntu freezing symptoms.
There is no single solution or theory as to root cause.   There are so many variables. It could be hardware, software or a combination of factors.
If you followed earlier advice we would at least know if Ubuntu runs as a VM in Windows without problems.
Virtual Box uses different drivers, for example.
As I indicated you need to do detective work, looking for clues, so that others might help to pin down the root cause.
Here is yet another example of a user trying to solve the problem.

[http://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly](http://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly)

You can find these threads yourself by careful searching.
For example since you use firefox have you tried running this in safe mode, with no add-ons enabled?
If you find the solution, I will be interested to hear.
Good luck.

I am following all the steps proposed to me I just didnt had any results 

The only step I didnt follow as of now is to run windows with ubuntu as a VM but thats cause currently its not easy for me to do that (I took the windows disk out of my system) but I will try that eventually to.

As for the link you provided I read this:

> However, this problem(where nothing but forced shutdown works to recover  from the freeze) may be related to the kernel and if kernel upgrading  cannot solve the problem, then an work-around could be [to add the statement **intel_idle.max_cstate=1** in the grub configuration file]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1511019/comments/8"): 

Which seems kinda promising but I have an AMD cpu is there a similar commant for AMD CPUs? or does this command work for AMD CPUs as well? I guess I could just type AMD instead of Intel in the line but I am not comfortable editing my grub without being sure that nothing bad will happen :P

---

### Post by dragonfly41 on 2017-02-01
I can't answer the question on AMD.
But following this line of investigation and searching around it seems that there are a number of threads where the grub has been tweaked to solve a freezing problem. So there is a pattern which seems promising.

[http://askubuntu.com/questions/749349/how-to-set-intel-idle-max-cstate-1](http://askubuntu.com/questions/749349/how-to-set-intel-idle-max-cstate-1)
[https://ask.fedoraproject.org/en/question/83930/how-to-intel_idlemax_cstate1/](https://ask.fedoraproject.org/en/question/83930/how-to-intel_idlemax_cstate1/)

One tip from the above second thread is to install Grub Customiser utility to edit grub.

Launch and go to General Settings > Advanced


edit GRUB_CMDLINE_LINUX_DEFAULT


If you are worried about corrupting grub I suggest that you have a bootable live Ubuntu USB on standby in case you have to dive in to manually edit the grub file which perhaps you should backup.


...

You could try alternative kernel


You should have at least two kernels to choos from to bootup


e.g. I have 
Linux 3.13.0-83-generic
Linux 3.13.0-79-generic

I would keep the VM experiment I suggested as a last resort. Stick with the native experiments.

---

### Post by johnstefnds on 2017-02-05
Well despite searching all over the web I still couldnt find what the grub line should be to change my AMD c state...


My system keeps freezing and I noticed that this zeitgeist error seems to come up more frequently in the sys log 

```
Feb  5 16:04:02 papajo-desktop dbus-daemon[1698]: Successfully activated service 'org.gnome.zeitgeist.SimpleIndexer'
Feb  5 16:04:02 papajo-desktop zeitgeist-datah[2944]: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Feb  5 16:04:22 papajo-desktop systemd[1]: Starting Stop ureadahead data collection...
Feb  5 16:04:22 papajo-desktop systemd[1]: Started Stop ureadahead data collection.
Feb  5 16:07:54 papajo-desktop dbus-daemon[1698]: Activating service name='com.canonical.Unity.Scope.Home' 
```

I also noticed that the system is more prone to freeze when I play on [www.lichess.org]("http://www.lichess.org") while watching a movie with VLC (I dont know if the use of VLC has any significance since I dont use any other player) 

I have deactivated hardware acceleration on both VLC and firefox (which I use to play on lichess).


Its gotten to a point where either I have to leave ubuntu and return to windows or find a fix like in the next days..... Its a fresh installation I dont know why this should happen really... I really would like someone like a mod to direct me on how to forward this to a place where some actual developer or something like that could see into this I notice on the web many people having the exact or similar issues... I know that its open source etc etc but its like the 16th major version of ubuntu and we are talking about up to date hardware so I dont understand why this should be acceptable even for an opensource OS... a brand new installation shouldnt freeze every half a day...

If you are reading this and know a guy that is really knowledgeable when it comes to linux/ubuntu even if he/she is just an online acquaintance please take a few minutes to PM/mail him forwarding this topic to him I would be grateful. Thanks.

---

### Post by ian-weisser on 2017-02-05
> **johnstefnds said:**
> Its gotten to a point where either I have to leave ubuntu and return to windows or find a fix like in the next days..... Its a fresh installation I dont know why this should happen really... I really would like someone like a mod to direct me on how to forward this to a place where some actual developer or something like that could see into this I notice on the web many people having the exact or similar issues... I know that its open source etc etc but its like the 16th major version of ubuntu and we are talking about up to date hardware so I dont understand why this should be acceptable even for an opensource OS... a brand new installation shouldnt freeze every half a day...

If you are reading this and know a guy that is really knowledgeable when it comes to linux/ubuntu even if he/she is just an online acquaintance please take a few minutes to PM/mail him forwarding this topic to him I would be grateful. Thanks.

See into what? None of us have the same problem you describe on our (many) systems.

If we did have the same problem you describe, we would have tracked it down and pushed a solution into Ubuntu long ago...just like we did with all the other issues that we did fix.

Keep doing the detective work, trying to find ways to duplicate the problem reliably, trying to isolate independent variables. When one of us can duplicate the problem from your instructions, we'll happliy help trace the source and debug it.
But we cannot trace a problem that we cannot see.

---

### Post by johnstefnds on 2017-02-05
> **ian-weisser said:**
> See into what? None of us have the same problem you describe on our (many) systems.

If we did have the same problem you describe, we would have tracked it down and pushed a solution into Ubuntu long ago...just like we did with all the other issues that we did fix.

Keep doing the detective work, trying to find ways to duplicate the problem reliably, trying to isolate independent variables. When one of us can duplicate the problem from your instructions, we'll happily help trace the source and debug it.
But we cannot trace a problem that we cannot see.

If you google ubuntu freezes youll find a few hundred similar problems with mine even one other user here posted that he faced the same problem and solved it by upgrading to a new kernel unfortunately I run already the newest kernel since I am on 16.10.


As for the detective work I do the best that I can do I am not a software engineer 

I show up the logs, I mention when it happens, I found also that zeitgeist error keeping popping up the time the system freezes I dont know if its relevant cause I dont know what zeigeist does...

I also dont know what else to do you told me to stress my GPU I did that using the programs I mentioned in a previous post I had them run for hours without any freeze.

I dont know what the next step should be like what I should look for. The only thing I have not done is run ubuntu as a VM in windows. Propose to me a next step to investigate and I will do it.

---

### Post by ian-weisser on 2017-02-05
Duplicating the freeze in a VM is a wise step. Try it.

---

### Post by dragonfly41 on 2017-02-05
I was reading your last post but while I was preparing this reply it seems to have gone / been deleted?.
I know that you are asking for expert opinion on this.

Since I often see freezes on my laptop I too would like to pin down the cause. 
That is why I continue with the search.
I ran yet another search and I found this thread which gives useful information.

[https://ubuntu-mate.community/t/screen-freezes-and-system-becomes-unresponsive/5610/24](https://ubuntu-mate.community/t/screen-freezes-and-system-becomes-unresponsive/5610/24)

From that thread I installed package ... inxi

ran command ... ```
inxi -ACDMNSG
```

If you collect the output from this command this will give readers of this thread something to work on.

Then I visited ...

[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)

You can search this and find 35 hits for "AMD".

I suggest that you create a summary report .. summarising salient facts .. and raise your question through that bug reporting thread which is dedicated to the issue of freezing.

The minimum information you need to list is
the output from running ... inxi -ACDMNSG

I don't think it would helpful to point to this Ubuntu discussion (as you suggested in the lost post) since there are a number of tests discussed which are not relevant.

You have confirmed that you have [COLOR=#000000]AMD FX 8320 (8 core @ 3.5 GHz) [/COLOR]
and “[COLOR=#000000]I run already the newest kernel since I am on 16.10[/COLOR]”.  But what is your actual kernel in use?

---

### Post by eduardoflsantos on 2017-02-05
Welcome to my daily nightmare. My luck is that the SSD start takes like 30 seconds, but it's still a pain. I've been dealing with this since November, or even before, with no solution whatsoever. I even wondered if I should go back to Windows, but it would just be a nightmare of a different kind, so I still here, waiting for... I don't know what.

I've spent so much time and money on this. I followed every theory and advice. Software and hardware related. People have told me it was a temperature problem, and graphic's card problem, a software problem... even a tech guy that I paid could not solve it.Made me buy a new cooler, a new gpu, a new PSU. Nothing worked. It's not Ubuntu's fault, thought, I believe. I've tried Mint and OpenSuse, same results. I tried older drivers from the repositories and brand new ones from nvidia website, but the results were the same.

---

### Post by johnstefnds on 2017-02-05
> **dragonfly41 said:**
> I was reading your last post but while I was preparing this reply it seems to have gone / been deleted?.
I know that you are asking for expert opinion on this.

Since I often see freezes on my laptop I too would like to pin down the cause. 
That is why I continue with the search.
I ran yet another search and I found this thread which gives useful information.

[https://ubuntu-mate.community/t/screen-freezes-and-system-becomes-unresponsive/5610/24](https://ubuntu-mate.community/t/screen-freezes-and-system-becomes-unresponsive/5610/24)

From that thread I installed package ... inxi

ran command ... ```
inxi -ACDMNSG
```

If you collect the output from this command this will give readers of this thread something to work on.

Then I visited ...

[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)

You can search this and find 35 hits for "AMD".

I suggest that you create a summary report .. summarising salient facts .. and raise your question through that bug reporting thread which is dedicated to the issue of freezing.

The minimum information you need to list is
the output from running ... inxi -ACDMNSG

I don't think it would helpful to point to this Ubuntu discussion (as you suggested in the lost post) since there are a number of tests discussed which are not relevant.

You have confirmed that you have [COLOR=#000000]AMD FX 8320 (8 core @ 3.5 GHz) [/COLOR]
and “[COLOR=#000000]I run already the newest kernel since I am on 16.10[/COLOR]”.  But what is your actual kernel in use?

I did run sudo inxi -ACDMNSG on the terminal and this was the output

```
System:    Host: papajo-desktop Kernel: 4.8.0-37-generic x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 16.10
Machine:   Device: desktop Mobo: ASRock model: 970 Pro3 R2.0
           UEFI: American Megatrends v: P2.80 date: 05/31/2016
CPU:       Quad core AMD FX-8320 Eight-Core (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 3500 MHz 1: 1700 MHz 2: 1400 MHz 3: 1400 MHz
           4: 1400 MHz 5: 1400 MHz 6: 2900 MHz 7: 1400 MHz 8: 1400 MHz
Graphics:  Card: NVIDIA GK106 [GeForce GTX 650 Ti]
           Display Server: X.org 1.18.4 drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           tty size: 80x24 Advanced Data: N/A for root
Audio:     Card-1 NVIDIA GK106 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Card-3 Logitech HD Pro Webcam C920 driver: USB Audio
           Card-4 Blue Microphones Yeti Stereo Microphone driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.8.0-37-generic
Network:   Card-1: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
           driver: ath5k
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 1108.2GB (2.7% used)
           ID-1: /dev/sda model: ADATA_SP900 size: 128.0GB
           ID-2: /dev/sdb model: INTEL_SSDSC2BW48 size: 480.1GB
           ID-3: /dev/sdc model: WDC_WD5000AAKS size: 500.1GB

 
```


My kernel version is  4.8.0-37-generic #39-Ubuntu SMP

I will create a report in the link you gave me later on this day or tomorrow thanks a lot for your answer.

---

### Post by johnstefnds on 2017-02-14
There must be a tool/program that makes more detailed log files than syslog... 

Consul seems like one of them but I dont know how to operate it..

Can anybody give me a better more detailed loging tool to monitor the system's background operations so that I could see what happenes at the time of freeze? 

Also tell me how to install and run it if its not like 1 command line or a click to do so or atleast point me at a webpage that has information on how to run it..

---

### Post by ian-weisser on 2017-02-14
Another application won't help.
Simply change the settings in the existing log daemon.

The settings are in /etc/rsyslog.d/
You must restart rsyslogd for the changes to take effect.
After you solve the problem, remember to change the setting back, lest your hard drive fill up with logs. It can happen.

---

### Post by HereInOz on 2017-02-15
I just had a look at the syslog output on page one, and noticed:
Temperature_Celsius changed from 111 to 110
in relation to /dev/sdc/

What is /dev/sdc used for.  That is a damnably high temperature for a disk drive.   I could be chasing phantoms but it does look a little wrong.

---

### Post by johnstefnds on 2017-02-23
Ok I tried the X.Org Nouveau drivers for my graphics card it crashes again all the same but it seems that with those drivers alt+sysrq+k seems to work (cant confirm that yet its the frist time it happened and may be a coincidence or the way the system responds with this driver when it crashes) 

Cause after like 2 minutes or so it displays the login screen without restarting that way I could get some more details (again im not an expert it may be a coinsidence those fails happened but its the first time I see a log with that many fails around the time of the crash)  that I hope would give someone a greater insight of what may happened:


```

Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#b22222]WARN[/COLOR]  2017-02-23 21:35:35 unity.dash.gsettingsscopereader GSettingsScopes.cpp:108 [COLOR=#ff0000]Error[/COLOR] fetching protocol metadata for scope: social.scope : Valid key file could not be found in search dirs
Feb 23 21:35:35 papajo-desktop systemd[1]: dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device: Job dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device/start timed out.
Feb 23 21:35:35 papajo-desktop systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device.
Feb 23 21:35:35 papajo-desktop systemd[1]: Dependency [COLOR=#ff0000]failed[/COLOR] for /dev/disk/by-uuid/11d19cb6-c572-4e1d-90c0-f175cd760208.
Feb 23 21:35:35 papajo-desktop systemd[1]: dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.swap: Job dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.swap/start [COLOR=#ff0000]failed[/COLOR] with result 'dependency'.
Feb 23 21:35:35 papajo-desktop systemd[1]: dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device: Job dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device/start [COLOR=#ff0000]failed[/COLOR] with result 'timeout'.
Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:35 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:35 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:35 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:35 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:35 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
Feb 23 21:35:35 papajo-desktop dbus-daemon[6028]: Activating service name='org.freedesktop.FileManager1'
Feb 23 21:35:35 papajo-desktop gnome-screensav[6520]: Lost the name, shutting down.
Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#ff0000]ERROR[/COLOR] 2017-02-23 21:35:35 unity.glib.dbus.server GLibDBusServer.cpp:538 DBus name lost 'org.gnome.Shell'
Feb 23 21:35:35 papajo-desktop compiz[6494]: [COLOR=#ff0000]ERROR[/COLOR] 2017-02-23 21:35:35 unity.glib.dbus.server GLibDBusServer.cpp:538 DBus name lost 'com.canonical.Unity'
Feb 23 21:35:36 papajo-desktop nautilus[6734]: Theme parsing [COLOR=#ff0000]error[/COLOR]: <broken file>:1:0: [COLOR=#ff0000]Failed[/COLOR] to import: The resource at '/org/gnome/libgd/tagged-entry/default.css' does not exist
Feb 23 21:35:36 papajo-desktop dbus-daemon[6028]: Successfully activated service 'org.freedesktop.FileManager1'
Feb 23 21:35:36 papajo-desktop dbus[5319]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Feb 23 21:35:36 papajo-desktop systemd[1]: Starting Hostname Service...
Feb 23 21:35:36 papajo-desktop unity-panel-ser[6511]: window_menu_model_new: assertion 'BAMF_IS_APPLICATION(app)' [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:36 papajo-desktop unity-panel-ser[6511]: track_menus: assertion 'IS_WINDOW_MENU(menus)' [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:36 papajo-desktop unity-panel-ser[6511]: window_menu_model_new: assertion 'BAMF_IS_APPLICATION(app)' [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:36 papajo-desktop unity-panel-ser[6511]: track_menus: assertion 'IS_WINDOW_MENU(menus)' [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:36 papajo-desktop dbus[5319]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb 23 21:35:36 papajo-desktop systemd[1]: Started Hostname Service.
Feb 23 21:35:36 papajo-desktop dbus-daemon[6028]: Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service'
Feb 23 21:35:36 papajo-desktop systemd[6020]: Starting Virtual filesystem metadata service...
Feb 23 21:35:36 papajo-desktop dbus-daemon[6028]: Successfully activated service 'org.gtk.vfs.Metadata'
Feb 23 21:35:36 papajo-desktop systemd[6020]: Started Virtual filesystem metadata service.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 8 threads of 2 processes of 2 users.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6766 of process 6538 (n/a) owned by '1000' RT at priority 5.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 9 threads of 2 processes of 2 users.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 9 threads of 2 processes of 2 users.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6767 of process 6538 (n/a) owned by '1000' RT at priority 5.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 10 threads of 2 processes of 2 users.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 10 threads of 2 processes of 2 users.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6768 of process 6538 (n/a) owned by '1000' RT at priority 5.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 11 threads of 2 processes of 2 users.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 11 threads of 2 processes of 2 users.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6769 of process 6538 (n/a) owned by '1000' RT at priority 5.
Feb 23 21:35:39 papajo-desktop rtkit-daemon[5937]: Supervising 12 threads of 2 processes of 2 users.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Supervising 12 threads of 2 processes of 2 users.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6770 of process 6538 (n/a) owned by '1000' RT at priority 5.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Supervising 13 threads of 2 processes of 2 users.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Supervising 13 threads of 2 processes of 2 users.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6771 of process 6538 (n/a) owned by '1000' RT at priority 5.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Supervising 14 threads of 2 processes of 2 users.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6775 of process 6775 (n/a) owned by '1000' high priority at nice level -11.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Supervising 15 threads of 3 processes of 2 users.
Feb 23 21:35:40 papajo-desktop pulseaudio[6775]: [pulseaudio] pid.c: Daemon already running.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Successfully made thread 6777 of process 6777 (n/a) owned by '1000' high priority at nice level -11.
Feb 23 21:35:40 papajo-desktop rtkit-daemon[5937]: Supervising 15 threads of 3 processes of 2 users.
Feb 23 21:35:40 papajo-desktop pulseaudio[6777]: [pulseaudio] pid.c: Daemon already running.
Feb 23 21:35:40 papajo-desktop dbus[5319]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Feb 23 21:35:40 papajo-desktop systemd[1]: Starting Locale Service...
Feb 23 21:35:40 papajo-desktop colord[5945]: [COLOR=#ff0000]failed[/COLOR] to get session [pid 6357]: No such device or address
Feb 23 21:35:40 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:40 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it
Feb 23 21:35:40 papajo-desktop indicator-appli[6784]: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Feb 23 21:35:40 papajo-desktop indicator-appli[6784]: Name Lost
Feb 23 21:35:40 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:40 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it
Feb 23 21:35:40 papajo-desktop compiz[6494]: message repeated 3 times: [ WARN  2017-02-23 21:35:40 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it]
Feb 23 21:35:40 papajo-desktop dbus-daemon[6028]: Activating service name='org.freedesktop.Notifications'
Feb 23 21:35:40 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:40 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it
Feb 23 21:35:40 papajo-desktop gnome-session-binary[6368]: Entering running state
Feb 23 21:35:40 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:40 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it
Feb 23 21:35:40 papajo-desktop compiz[6494]: message repeated 3 times: [ [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:40 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it]
Feb 23 21:35:40 papajo-desktop dbus[5319]: [system] Successfully activated service 'org.freedesktop.locale1'
Feb 23 21:35:40 papajo-desktop systemd[1]: Started Locale Service.
Feb 23 21:35:40 papajo-desktop nautilus[6800]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:40 papajo-desktop nautilus[6800]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:40 papajo-desktop pulseaudio[6538]: [pulseaudio] bluez5-util.c: GetManagedObjects() [COLOR=#ff0000]failed[/COLOR]: org.freedesktop.DBus.Error.TimedOut: [COLOR=#ff0000]Failed[/COLOR] to activate service 'org.bluez': timed out
Feb 23 21:35:40 papajo-desktop pulseaudio[5931]: [pulseaudio] bluez5-util.c: GetManagedObjects() [COLOR=#ff0000]failed[/COLOR]: org.freedesktop.DBus.Error.TimedOut: [COLOR=#ff0000]Failed[/COLOR] to activate service 'org.bluez': timed out
Feb 23 21:35:40 papajo-desktop dbus-daemon[6028]: Successfully activated service 'org.freedesktop.Notifications'
Feb 23 21:35:40 papajo-desktop dbus[5319]: [system] Activating service name='org.freedesktop.fwupd' (using servicehelper)
Feb 23 21:35:40 papajo-desktop indicator-weather.desktop[6799]: /usr/bin/indicator-weather:28: PyGI[COLOR=#ff0000]Warning[/COLOR]: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
Feb 23 21:35:40 papajo-desktop indicator-weather.desktop[6799]:   from gi.repository import AppIndicator3 as appIndicator
Feb 23 21:35:41 papajo-desktop fwupd[6842]: [COLOR=#ff0000]Failed[/COLOR] to coldplug: UEFI firmware updating not supported
Feb 23 21:35:41 papajo-desktop dbus[5319]: [system] Successfully activated service 'org.freedesktop.fwupd'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Activating service name='com.canonical.Unity.Scope.Home'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Successfully activated service 'com.canonical.Unity.Scope.Home'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Activating service name='com.canonical.Unity.Scope.Applications'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Activating service name='com.canonical.Unity.Scope.LocalFiles'
Feb 23 21:35:43 papajo-desktop com.canonical.Unity.Scope.Applications[6028]: [COLOR=#ff0000]Error[/COLOR] loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Feb 23 21:35:43 papajo-desktop unity-scope-loa[6886]: daemon.vala:144: [COLOR=#ff0000]Failed[/COLOR] to load Software Center index. 'Apps Available for Download' will not be listed
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Activating service name='org.gnome.zeitgeist.Engine'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Activating service name='org.gnome.zeitgeist.SimpleIndexer'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Successfully activated service 'org.gnome.zeitgeist.Engine'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Successfully activated service 'org.gnome.zeitgeist.SimpleIndexer'
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Successfully activated service 'com.canonical.Unity.Scope.LocalFiles'
Feb 23 21:35:43 papajo-desktop compiz[6494]: [COLOR=#ff0000]WARN[/COLOR]  2017-02-23 21:35:43 unity.iconloader IconLoader.cpp:756 Unable to load icon file:///home/papajo at size -1x22: [COLOR=#ff0000]Error[/COLOR] opening file /home/papajo: Is a directory
Feb 23 21:35:43 papajo-desktop dbus-daemon[6028]: Successfully activated service 'com.canonical.Unity.Scope.Applications'
Feb 23 21:35:52 papajo-desktop systemd[1]: Stopping User Manager for UID 113...
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopping D-Bus User Message Bus...
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopped target Default.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopping Virtual filesystem service...
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopped D-Bus User Message Bus.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopped Virtual filesystem service.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopped target Basic System.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopped target Timers.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopped target Sockets.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Closed D-Bus User Message Bus Socket.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Reached target Shutdown.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Starting Exit the Session...
Feb 23 21:35:52 papajo-desktop systemd[5751]: Stopped target Paths.
Feb 23 21:35:52 papajo-desktop systemd[5751]: Received SIGRTMIN+24 from PID 6952 (kill).
Feb 23 21:35:52 papajo-desktop systemd[1]: Stopped User Manager for UID 113.
Feb 23 21:35:52 papajo-desktop systemd[1]: Removed slice User Slice of lightdm.
Feb 23 21:35:56 papajo-desktop unity-panel-ser[6511]: window_menu_model_new: assertion 'BAMF_IS_APPLICATION(app)' [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:56 papajo-desktop unity-panel-ser[6511]: track_menus: assertion 'IS_WINDOW_MENU(menus)' failed
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)'  [COLOR=#ff0000]failed[/COLOR] 
  Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL'   [COLOR=#ff0000]failed[/COLOR]  
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)'     [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL'     [COLOR=#ff0000]failed[/COLOR]
   Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)'  [COLOR=#ff0000]failed[/COLOR]   
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL'    [COLOR=#ff0000]failed[/COLOR] 
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)'    [COLOR=#ff0000]failed[/COLOR] 
  Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL'  [COLOR=#ff0000]failed[/COLOR]   
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)'     [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL'     [COLOR=#ff0000]failed[/COLOR]
  Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)'   [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL'  [COLOR=#ff0000]failed[/COLOR] 
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: g_action_print_detailed_name: assertion 'g_action_name_is_valid (action_name)'  [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:35:56 papajo-desktop gnome-system-lo[6970]: gtk_application_set_accels_for_action: assertion 'detailed_action_name != NULL'   [COLOR=#ff0000]failed[/COLOR]
Feb 23 21:36:00 papajo-desktop zeitgeist-datah[6981]: zeitgeist-datahub.vala:229: [COLOR=#ff0000]Unable to get name[/COLOR] "org.gnome.zeitgeist.datahub" on the bus!
Feb 23 21:37:06 papajo-desktop systemd[1]: dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device: Job dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device/start timed out.
Feb 23 21:37:06 papajo-desktop systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device.
Feb 23 21:37:06 papajo-desktop systemd[1]: Dependency [COLOR=#ff0000]failed[/COLOR] for /dev/disk/by-uuid/11d19cb6-c572-4e1d-90c0-f175cd760208.
Feb 23 21:37:06 papajo-desktop systemd[1]: dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.swap: Job dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.swap/start failed with result 'dependency'.
Feb 23 21:37:06 papajo-desktop systemd[1]: dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device: Job dev-disk-by\x2duuid-11d19cb6\x2dc572\x2d4e1d\x2d90c0\x2df175cd760208.device/start failed with result 'timeout'.
Feb 23 21:39:42 papajo-desktop dbus-daemon[6028]: Activating service name='org.gnome.GConf'
Feb 23 21:39:42 papajo-desktop dbus-daemon[6028]: Successfully activated service 'org.gnome.GConf'
Feb 23 21:39:43 papajo-desktop unity-panel-ser[6511]: Already have a menu for window ID 62914585 with path /com/canonical/menu/3C00019 from :1.134, unregistering that one

```

---

### Post by daniell59 on 2017-02-23
Though I should be taking advice rather than giving it, I had a freezing problem with the first computer that I built. It turned out that the motherboard was not accurately setting the memory values. I reset everything manually. Never had a freezing problem again.

---

### Post by johnstefnds on 2017-02-24
you mean the CAS clocks?

---

### Post by daniell59 on 2017-02-24
> **johnstefnds said:**
> you mean the CAS clocks?

It has been a long time since I did it. I went into the BIOS and went through all of the specs. That included timing, voltage, etc.

---

