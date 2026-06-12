---
title: "Samsung N210/12.04 Won't Wake After Suspend"
date: 2013-02-08
forum: General Help
---

### Post by donmatas on 2013-02-08
HI,
I have Xubuntu 12.04 in a Samsung N210. I have the same problem described above: cannot wake up the laptop after suspending it. I tried the the solution proposed, namely, adding pci=nomsi to the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line and then upgrading the grub and rebooting without successs.

I would appreciate any help in this matter

Best,
DM

---

### Post by Toz on 2013-02-08
Moving post to its own thread - the system is different from the one being discussed in the original thread [here]("http://ubuntuforums.org/showthread.php?t=1981650").

Can you post back:

1. Your suspend log file - the contents of /var/log/pm-suspend.log using this method:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

2. Your current kernel and parameters:
```
cat /proc/cmdline
```

3. Any interesting related syslog messages:
```
cat /var/log/syslog* | grep PM:
```

4. Info about your video card:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by donmatas on 2013-02-09
Dear Taz,

thank for your concern. Here are the outcomes that you asked for:

1.
```

$ pastebinit /var/log/pm-suspend.log
[http://paste.ubuntu.com/1628248/](http://paste.ubuntu.com/1628248/)
```

2.
```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=1bf1a12f-1422-449f-b8e2-1a14fde66393 ro quiet splash pci=nomsi vt.handoff=7
```

3. Sorry but I do not know how to distinguish what is interesting and what is not.
```
$ cat /var/log/syslog* | grep PM:
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Feb  8 08:58:42 mini-computadorcito kernel: [    0.100480] PM: Registering ACPI NVS region [mem 0x7f5c0000-0x7f5c2fff] (12288 bytes)
Feb  8 08:58:42 mini-computadorcito kernel: [    0.872712] PM: Hibernation image not present or could not be loaded.
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Feb  8 09:15:14 mini-computadorcito kernel: [    0.100456] PM: Registering ACPI NVS region [mem 0x7f5c0000-0x7f5c2fff] (12288 bytes)
Feb  8 09:15:14 mini-computadorcito kernel: [    0.868815] PM: Hibernation image not present or could not be loaded.
Feb  8 09:49:52 mini-computadorcito kernel: [ 2093.836900] PM: Marking nosave pages: [mem 0x0009d000-0x000fffff]
Feb  8 09:49:52 mini-computadorcito kernel: [ 2093.836913] PM: Basic memory bitmaps created
Feb  8 09:50:52 mini-computadorcito kernel: [ 2093.836918] PM: Syncing filesystems ... done.
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.336314] PM: Preallocating image memory... done (allocated 195149 pages)
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.560985] PM: Allocated 780596 kbytes in 0.22 seconds (3548.16 MB/s)
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.708135] PM: freeze of drv:snd_hda_intel dev:0000:00:1b.0 complete after 119.783 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.708197] PM: freeze of drv: dev:pci0000:00 complete after 118.795 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.708228] PM: freeze of devices complete after 131.734 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.708479] PM: late freeze of devices complete after 0.243 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.709924] PM: noirq freeze of devices complete after 1.442 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.728512] PM: Saving platform NVS memory
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.832932] PM: Creating hibernation image:
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.836078] PM: Need to copy 194608 pages
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.836078] PM: Normal pages needed: 62117 + 1024, available pages: 194399
Feb  8 09:50:52 mini-computadorcito kernel: [ 2094.836078] PM: Restoring platform NVS memory
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.058339] PM: noirq restore of devices complete after 1.987 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.058485] PM: early restore of devices complete after 0.093 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312210] PM: restore of drv:hub dev:3-0:1.0 complete after 118.018 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312227] PM: restore of drv: dev:ep_00 complete after 117.881 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312232] PM: restore of drv:hub dev:4-0:1.0 complete after 117.732 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312239] PM: restore of drv: dev:ep_81 complete after 117.996 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312248] PM: restore of drv: dev:ep_00 complete after 117.605 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312276] PM: restore of drv: dev:ep_81 complete after 117.716 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312313] PM: restore of drv:hub dev:2-0:1.0 complete after 118.368 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312316] PM: restore of drv: dev:ep_00 complete after 118.254 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.312328] PM: restore of drv: dev:ep_81 complete after 118.326 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.416196] PM: restore of drv:hub dev:5-0:1.0 complete after 221.212 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.416200] PM: restore of drv: dev:ep_00 complete after 221.079 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.416212] PM: restore of drv: dev:ep_81 complete after 221.156 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.416217] PM: restore of drv:usb dev:5-1 complete after 220.028 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.528129] PM: restore of drv:scsi dev:host2 complete after 334.980 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.528134] PM: restore of drv:scsi dev:host1 complete after 335.120 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.528152] PM: restore of drv:scsi_host dev:host2 complete after 334.941 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.528168] PM: restore of drv:scsi_host dev:host1 complete after 335.099 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.532128] PM: restore of drv:scsi dev:host3 complete after 338.840 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.532164] PM: restore of drv:scsi_host dev:host3 complete after 338.601 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.548121] PM: restore of drv:hub dev:1-0:1.0 complete after 354.413 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.548125] PM: restore of drv: dev:ep_00 complete after 354.309 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.548137] PM: restore of drv:usb dev:1-8 complete after 352.434 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.548141] PM: restore of drv: dev:ep_81 complete after 354.380 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.580194] PM: restore of drv:scsi dev:host0 complete after 387.314 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.580220] PM: restore of drv:scsi_host dev:host0 complete after 387.285 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.580235] PM: restore of drv:scsi dev:target0:0:0 complete after 385.040 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.580257] PM: restore of drv:sd dev:0:0:0:0 complete after 385.002 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.580293] PM: restore of drv:ata_port dev:ata1 complete after 378.985 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.629174] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 433.817 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.801994] PM: restore of drv:uvcvideo dev:1-8:1.0 complete after 606.217 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.802001] PM: restore of drv: dev:ep_00 complete after 605.897 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.802025] PM: restore of drv:uvcvideo dev:1-8:1.1 complete after 606.106 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2095.802044] PM: restore of drv: dev:ep_81 complete after 606.193 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2096.370022] PM: restore of drv: dev:ep_00 complete after 1172.848 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2096.370034] PM: restore of drv:usbhid dev:5-1:1.0 complete after 1173.124 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2096.370058] PM: restore of drv: dev:ep_81 complete after 1173.111 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2096.370064] PM: restore of drv:hid-generic dev:0003:1C4F:0003.0001 complete after 740.838 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2096.388357] PM: restore of devices complete after 1204.633 msecs
Feb  8 09:50:52 mini-computadorcito kernel: [ 2096.388691] PM: Image restored successfully.
Feb  8 09:50:52 mini-computadorcito kernel: [ 2096.401939] PM: Basic memory bitmaps freed
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Feb  8 10:02:57 mini-computadorcito kernel: [    0.100480] PM: Registering ACPI NVS region [mem 0x7f5c0000-0x7f5c2fff] (12288 bytes)
Feb  8 10:02:57 mini-computadorcito kernel: [    0.872778] PM: Hibernation image not present or could not be loaded.
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Feb  8 11:59:17 mini-computadorcito kernel: [    0.104479] PM: Registering ACPI NVS region [mem 0x7f5c0000-0x7f5c2fff] (12288 bytes)
Feb  8 11:59:17 mini-computadorcito kernel: [    0.880605] PM: Hibernation image not present or could not be loaded.
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Feb  9 11:01:46 mini-computadorcito kernel: [    0.104480] PM: Registering ACPI NVS region [mem 0x7f5c0000-0x7f5c2fff] (12288 bytes)
Feb  9 11:01:46 mini-computadorcito kernel: [    0.880668] PM: Hibernation image not present or could not be loaded.

```

4. ```
$ sudo lspci -vnn | grep -A12 VGA
[sudo] password for ---: 
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])
	Subsystem: Samsung Electronics Co Ltd Device [144d:c072]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 18d0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915


```

---

### Post by Toz on 2013-02-09
According to your pm-suspend.log file, you are getting inconsistent results with susppend:

Feb 3 (working - note the Awake message to indicate the system is waking up):
```

Sun Feb  3 01:39:42 GMT 2013: Running hooks for suspend.
.....
Sun Feb  3 01:39:44 GMT 2013: performing suspend
Sun Feb  3 09:45:26 GMT 2013: Awake.
Sun Feb  3 09:45:26 GMT 2013: Running hooks for resume
.....
Sun Feb  3 09:45:28 GMT 2013: Finished.

```

Feb 4 (not working - note absence of Awake message):
```

Mon Feb  4 19:39:15 GMT 2013: Running hooks for suspend.
.....
Mon Feb  4 19:39:18 GMT 2013: performing suspend

```

Feb 5 (working):
```

Tue Feb  5 18:20:56 GMT 2013: Running hooks for suspend.
.....
Tue Feb  5 18:20:58 GMT 2013: performing suspend
Tue Feb  5 19:13:15 GMT 2013: Awake.
Tue Feb  5 19:13:15 GMT 2013: Running hooks for resume
.....
Tue Feb  5 19:13:17 GMT 2013: Finished.

```

Feb 6 (not working):
```

Wed Feb  6 07:30:03 GMT 2013: Running hooks for suspend.
.....
Wed Feb  6 07:30:05 GMT 2013: performing suspend

```

Feb 7 (working again):
```

Thu Feb  7 08:55:58 GMT 2013: Running hooks for suspend.
.....
Thu Feb  7 08:56:00 GMT 2013: performing suspend
Thu Feb  7 09:11:51 GMT 2013: Awake.
Thu Feb  7 09:11:51 GMT 2013: Running hooks for resume
.....
Thu Feb  7 09:11:53 GMT 2013: Finished.

```

Feb 8 (not working):
```

Fri Feb  8 09:00:52 GMT 2013: Running hooks for suspend.
.....
Fri Feb  8 09:00:54 GMT 2013: performing suspend

```

Then  hibernate that works:
```

vie feb  8 09:49:48 GMT 2013: Running hooks for hibernate.
.....
vie feb  8 09:49:51 GMT 2013: performing hibernate
vie feb  8 09:50:52 GMT 2013: Awake.
vie feb  8 09:50:52 GMT 2013: Running hooks for thaw
.....
vie feb  8 09:50:55 GMT 2013: Finished.

```

**_A question:_** Is the suspend function flaky? Does it work sometimes or do you never get a successful return to our system?

Since the pci=nomsi kernel parameter doesn't work, I'd suggest removing it and retrying a suspend again. This time, after the suspend attempt, post back the pm-suspend.log file again and indicate at what time you attempted the suspend.

You may be suffering from [this]("http://ubuntuforums.org/showthread.php?t=1651277") - a successful suspend/resume but a blank screen.

---

### Post by donmatas on 2013-02-10
> **Toz said:**
> According to your pm-suspend.log file, you are getting inconsistent results with susppend:...

**_A question:_** Is the suspend function flaky? Does it work sometimes or do you never get a successful return to our system?

Since the pci=nomsi kernel parameter doesn't work, I'd suggest removing it and retrying a suspend again. This time, after the suspend attempt, post back the pm-suspend.log file again and indicate at what time you attempted the suspend.

You may be suffering from [this]("http://ubuntuforums.org/showthread.php?t=1651277") - a successful suspend/resume but a blank screen.

Thanks Toz.

REgarding your question, I would say that at the beginging the problem appears randomly, but now it happens every time that I try to awake the Laptop.

Following your instructions, I have removed the pci=nomsi from the kernel parametrer, save the file and then update the grub and reboot the machine. Then I closed the lid of the machine and it goes stand by. THen I opened the lid and it is awake again! (it was at 13:07). Here is the outcome of the command:

```
$ pastebinit /var/log/pm-suspend.log
http://paste.ubuntu.com/1632945/

```

Best,
DM

---

### Post by donmatas on 2013-02-10
NOw I have tried again (13:13hrs) from the start menu. Now I could not awake the computer:
```

pastebinit /var/log/pm-suspend.log
[http://paste.ubuntu.com/1632963/](http://paste.ubuntu.com/1632963/)
```

---

### Post by Toz on 2013-02-10
Interesting.

Can you try this kernel parameter: **intel_idle.max_cstate=0 **.

After reboot, post back:
```
cat /proc/cmdline
```
...and whether repeated suspends work.

---

### Post by donmatas on 2013-02-10
> **Toz said:**
> Interesting.

Can you try this kernel parameter: **intel_idle.max_cstate=0 **.

After reboot, post back:
```
cat /proc/cmdline
```
...and whether repeated suspends work.

Thanks Toz,
where I should add that line. At the same place where I added before the "pci=nomsi" line (namely, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash")?

Best,

---

### Post by Toz on 2013-02-10
> **donmatas said:**
> Thanks Toz,
where I should add that line. At the same place where I added before the "pci=nomsi" line (namely, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash")?

Yes, in the same place where pci=nosi existed. Make sure to run "sudo update-grub" afterwards.

---

### Post by donmatas on 2013-02-11
> **Toz said:**
> Interesting.

Can you try this kernel parameter: **intel_idle.max_cstate=0 **.

After reboot, post back:
```
cat /proc/cmdline
```
...and whether repeated suspends work.

Thanks Toz:

The line now is like this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=0"

I have updated the grub and rebooted the Laptop.

```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=1bf1a12f-1422-449f-b8e2-1a14fde66393 ro quiet splash intel_idle.max_cstate=0 vt.handoff=7
```

It seems that it is working! I have tried twice successfully (about 13:40).

```
$ pastebinit /var/log/pm-suspend.log
http://paste.ubuntu.com/1636360/
```

I will report you any bad behaviour. What have you done?

Best

---

### Post by Toz on 2013-02-11
> What have you done?
I came across a number of posts suggesting this parameter to solve suspend problems. (e.g. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/640100]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/640100").

An interesting item in that bug report is post #168. If your suspend fails after 30 minutes, you may want to try: **intel_idle.max_cstate=3**.

There is a good description of intel_idle.max_cstate [here]("http://stackoverflow.com/questions/12111954/context-switches-much-slower-in-new-linux-kernels").

---

### Post by donmatas on 2013-02-11
thanks! I hope that I will not have problems after 30 min...

Best,
M

---

