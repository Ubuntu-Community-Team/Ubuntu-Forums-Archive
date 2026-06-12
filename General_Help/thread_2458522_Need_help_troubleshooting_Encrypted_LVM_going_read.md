---
title: "Need help troubleshooting Encrypted LVM going read-only"
date: 2021-02-26
forum: General Help
---

### Post by ndeubert on 2021-02-26
I followed these installation steps exactly using Xubuntu 20.04: [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019) on a Dell Precision 5550 - for the record I installed a second 500G NVME drive (it supports 2), only "zapped" that one, and installed Xubuntu on that one. Now my problem is after my laptop is booted for a few days the root filesystem will all of a sudden go read-only, and doesn't seem to be related any power actions (suspend). When it goes read-only as you can imagine everything just crashes and nothing works, not even shutdown and I have to press and hold the power button to reboot it. Everything I have read so far says this happens when the filesystem is getting corrupted and to run fsck on it, but I have done that twice from a live usb immediately after the problem occurs and neither time did it report any issues, so I am more suspicious it's some kind of issue with the encryption/lvm. The NVME I installed it on was working perfectly fine prior to this install on it, so I don't think it's a hardware issue with that.

Here is last thing in the syslog before the problem happened around 08:00:00. dmesg logs don't show anything after the first ~19 secs of boot, and I didn't see any other relevant logs, please let me know where else I can look for clues.
```
Feb 26 07:56:39 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-73 noise=9999 txrate=360000
Feb 26 07:56:46 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-60 noise=9999 txrate=360000
Feb 26 07:56:47 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-56 noise=9999 txrate=360000
Feb 26 07:58:21 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-67 noise=9999 txrate=162000
Feb 26 07:58:24 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-73 noise=9999 txrate=162000
Feb 26 07:58:31 koln obexd[1936]: disconnected: Transport got disconnected
Feb 26 07:58:31 koln acpid: input device has been disconnected, fd 21
Feb 26 07:58:31 koln bluetoothd[1012]: Unable to get io data for Headset Voice gateway: getpeername: Transport endpoint is not connected (107)
Feb 26 07:58:31 koln bluetoothd[1012]: Unable to get io data for Phone Book Access: getpeername: Transport endpoint is not connected (107)
Feb 26 07:58:33 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-80 noise=9999 txrate=81000
Feb 26 07:58:44 koln kernel: [385950.234020] input: Nick qc35 (AVRCP) as /devices/virtual/input/input47
Feb 26 07:58:44 koln obexd[1936]: CONNECT(0x0), <unknown>(0xff)
Feb 26 07:58:44 koln obexd[1936]: CONNECT(0x0), <unknown>(0x0)
Feb 26 07:58:44 koln obexd[1936]: SETPATH(0x5), <unknown>(0xff)
Feb 26 07:58:44 koln obexd[1936]: stat(/home/nd18548/phonebook/): No such file or directory (2) 
Feb 26 07:58:44 koln obexd[1936]: SETPATH(0x5), Not Found(0x44)
Feb 26 07:58:46 koln bluetoothd[1012]: /org/bluez/hci0/dev_04_52_C7_C2_FF_58/sep1/fd3: fd(53) ready
Feb 26 07:58:46 koln rtkit-daemon[1340]: Supervising 3 threads of 1 processes of 1 users.
Feb 26 07:58:46 koln rtkit-daemon[1340]: Successfully made thread 458926 of process 1630 owned by '18548' RT at priority 5.
Feb 26 07:58:46 koln rtkit-daemon[1340]: Supervising 4 threads of 1 processes of 1 users.
Feb 26 08:03:26 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-60 noise=9999 txrate=30000
Feb 26 08:03:27 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-56 noise=9999 txrate=30000
Feb 26 08:03:29 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-47 noise=9999 txrate=30000
Feb 26 08:03:36 koln xfce4-screensav[1748]: invalid uninstantiatable type '<unknown>' in cast to 'GSWindow'
Feb 26 08:03:36 koln xfce4-screensav[1748]: gdk_device_get_source: assertion 'GDK_IS_DEVICE (device)' failed
Feb 26 08:03:36 koln xfce4-screensav[1748]: message repeated 2 times: [ gdk_device_get_source: assertion 'GDK_IS_DEVICE (device)' failed]
Feb 26 08:03:36 koln xfce4-screensav[1748]: gdk_event_set_source_device: assertion 'GDK_IS_DEVICE (device)' failed
Feb 26 08:03:36 koln xfce4-screensav[1748]: gdk_device_get_source: assertion 'GDK_IS_DEVICE (device)' failed
Feb 26 08:03:36 koln xfce4-screensav[1748]: gdk_event_set_source_device: assertion 'GDK_IS_DEVICE (device)' failed
Feb 26 08:03:36 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-47 noise=9999 txrate=30000
Feb 26 08:03:39 koln wpa_supplicant[1058]: wlp0s20f3: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-45 noise=9999 txrate=30000
Feb 26 08:13:00 koln systemd-modules-load[661]: Inserted module 'lp'
Feb 26 08:13:00 koln systemd-modules-load[661]: Inserted module 'ppdev'
Feb 26 08:13:00 koln systemd-modules-load[661]: Inserted module 'parport_pc'
Feb 26 08:13:00 koln systemd-sysctl[678]: Not setting net/ipv4/conf/all/promote_secondaries (explicit setting exists).
Feb 26 08:13:00 koln systemd-sysctl[678]: Not setting net/ipv4/conf/default/promote_secondaries (explicit setting exists).
Feb 26 08:13:00 koln lvm[659]:   2 logical volume(s) in volume group "ubuntu-vg" monitored
Feb 26 08:13:00 koln systemd[1]: Starting Flush Journal to Persistent Storage...
Feb 26 08:13:00 koln systemd[1]: Finished udev Coldplug all Devices.
Feb 26 08:13:00 koln systemd[1]: Finished Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.
Feb 26 08:13:00 koln systemd[1]: Reached target Local File Systems (Pre).
Feb 26 08:13:00 koln systemd[1]: Starting Show Plymouth Boot Screen...
Feb 26 08:13:00 koln systemd[1]: plymouth-start.service: Succeeded.
Feb 26 08:13:00 koln systemd[1]: Started Show Plymouth Boot Screen.
Feb 26 08:13:00 koln systemd[1]: Condition check resulted in Dispatch Password Requests to Console Directory Watch being skipped.
Feb 26 08:13:00 koln systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Feb 26 08:13:00 koln systemd[1]: Finished Flush Journal to Persistent Storage.
Feb 26 08:13:00 koln systemd[1]: Starting Show Plymouth Boot Screen...
Feb 26 08:13:00 koln systemd[1]: Condition check resulted in Set Up Additional Binary Formats being skipped.
Feb 26 08:13:00 koln systemd[1]: Condition check resulted in File System Check on Root Device being skipped.
Feb 26 08:13:00 koln systemd[1]: Condition check resulted in Rebuild Hardware Database being skipped.
Feb 26 08:13:00 koln systemd[1]: Condition check resulted in Platform Persistent Storage Archival being skipped.
Feb 26 08:13:00 koln systemd[1]: plymouth-start.service: Succeeded.
Feb 26 08:13:00 koln systemd[1]: Started Show Plymouth Boot Screen.
Feb 26 08:13:00 koln systemd[1]: Condition check resulted in Dispatch Password Requests to Console Directory Watch being skipped.

```

Thanks for your time

---

### Post by TheFu on 2021-02-26
Seems you have a bad SSD.  I'd return it after running SMART tests to prove the problem.  Going read only happens under 2 situations that I've seen
[LIST]
[*]Corrupted file system
[*]Failing SSD / Disk
[/LIST]

What does SMART say about the problem device?

---

### Post by ndeubert on 2021-03-01
The SSD is not new, at least a few years old and I was previously using it in a different device (without any issues for years) and wiped it to do this install. Looking at the smart data shows it's 3% used so I don't think it's EOL yet.


```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-44-generic] (local build)                                                       
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)                                                       
                                                                                                                                  
=== START OF INFORMATION SECTION ===                                                                                              
Model Number:                       PM961 NVMe SAMSUNG 512GB                                                                      
Serial Number:                      S33YNB0J402048                                                                                
Firmware Version:                   CXY74D1Q                                                                                      
PCI Vendor/Subsystem ID:            0x144d                                                                                        
IEEE OUI Identifier:                0x002538                                                                                      
Total NVM Capacity:                 512,110,190,592 [512 GB]                                                                      
Unallocated NVM Capacity:           0                                                                                             
Controller ID:                      2
Number of Namespaces:               1
Namespace 1 Size/Capacity:          512,110,190,592 [512 GB]
Namespace 1 Utilization:            48,056,954,880 [48.0 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            002538 b471b41ead
Local Time is:                      Mon Mar  1 09:27:13 2021 EST
Firmware Updates (0x16):            3 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x001f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat
Warning  Comp. Temp. Threshold:     68 Celsius
Critical Comp. Temp. Threshold:     71 Celsius

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     7.60W       -        -    0  0  0  0        0       0
 1 +     5.00W       -        -    1  1  1  1        0       0
 2 +     3.60W       -        -    2  2  2  2        0       0
 3 -   0.0400W       -        -    3  3  3  3      210    1500
 4 -   0.0050W       -        -    4  4  4  4     2200    6000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        30 Celsius
Available Spare:                    100%
Available Spare Threshold:          50%
Percentage Used:                    3%
Data Units Read:                    55,708,446 [28.5 TB]
Data Units Written:                 28,159,994 [14.4 TB]
Host Read Commands:                 631,064,082
Host Write Commands:                357,291,237
Controller Busy Time:               1,961
Power Cycles:                       1,904
Power On Hours:                     1,861
Unsafe Shutdowns:                   319
Media and Data Integrity Errors:    0
Error Information Log Entries:      286
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               30 Celsius
Temperature Sensor 2:               31 Celsius

Error Information (NVMe Log 0x01, max 64 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0        286     0  0x0013  0x4016  0x004            0     1     -
  1        285     0  0x000f  0x4016  0x004            0     1     -
  2        284     0  0x0013  0x4016  0x004            0     1     -
  3        283     0  0x000f  0x4016  0x004            0     1     -
  4        282     0  0x0013  0x4016  0x004            0     1     -
  5        281     0  0x000f  0x4016  0x004            0     1     -
  6        280     0  0x000f  0x4016  0x004            0     1     -
  7        279     0  0x0013  0x4016  0x004            0     1     -
  8        278     0  0x000f  0x4016  0x004            0     1     -
  9        277     0  0x0013  0x4016  0x004            0     1     -
 10        276     0  0x000f  0x4016  0x004            0     1     -
 11        275     0  0x0013  0x4016  0x004            0     1     -
 12        274     0  0x000f  0x4016  0x004            0     1     -
 13        273     0  0x0013  0x4016  0x004            0     1     -
 14        272     0  0x000f  0x4016  0x004            0     1     -
 15        271     0  0x000f  0x4016  0x004            0     1     -
... (48 entries not shown)

```

---

### Post by TheFu on 2021-03-01
Were any tests run first?

Step 1: Run SMART Tests - *long* would be better than *short*
Step 2: Review SMART report

---

