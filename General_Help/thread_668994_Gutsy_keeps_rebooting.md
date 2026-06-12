---
title: "Gutsy keeps rebooting"
date: 2008-01-16
forum: General Help
---

### Post by Magellan on 2008-01-16
I have the 64bit version of Gutsy installed one a new pc with a Core 2 Duo processor and an Intel MB.  This has been up and running for about a month now. A week or 2 ago, I noticed that the pc would reboot on its own.  It may have happened before and I just didn't notice since it logs in the "family" user automatically.

I checked the system logs, and it looks like it is rebooting every hour.  Here's snippet:

Jan 15 01:36:49 family-room-desktop syslogd 1.4.1#21ubuntu3: **restart.**
Jan 15 01:36:49 family-room-desktop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan 15 01:36:49 family-room-desktop syslogd: /var/log/kern.log: No space left on device
Jan 15 01:36:49 family-room-desktop kernel: Loaded 26084 symbols from /boot/System.map-2.6.22-14-generic.
Jan 15 01:36:49 family-room-desktop kernel: Symbols match kernel version 2.6.22.
Jan 15 01:36:49 family-room-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Command line: root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 ro 
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000098000 (usable)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 0000000000098000 - 00000000000a0000 (reserved)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007e411000 (usable)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e411000 - 000000007e413000 (reserved)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e413000 - 000000007e4ee000 (usable)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e4ee000 - 000000007e5ea000 (ACPI NVS)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e5ea000 - 000000007e5ee000 (usable)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e5ee000 - 000000007e5f3000 (ACPI data)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e5f3000 - 000000007e5f4000 (usable)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e5f4000 - 000000007e5ff000 (ACPI data)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e5ff000 - 000000007e600000 (usable)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 000000007e600000 - 000000007f000000 (reserved)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 152) 0 entries of 3200 used
Jan 15 01:36:49 family-room-desktop syslogd: /var/log/debug: No space left on device
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Entering add_active_range(0, 256, 517137) 1 entries of 3200 used
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Entering add_active_range(0, 517139, 517358) 2 entries of 3200 used
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Entering add_active_range(0, 517610, 517614) 3 entries of 3200 used
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Entering add_active_range(0, 517619, 517620) 4 entries of 3200 used
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] Entering add_active_range(0, 517631, 517632) 5 entries of 3200 used
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] end_pfn_map = 1048576
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] DMI 2.4 present.
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FE020 checksum 0
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
Jan 15 01:36:49 family-room-desktop kernel: [    0.000000] ACPI: RSDT 7E5FD038, 004C (r1 INTEL  DG33TL         D8       1000013)
Jan 15 01:36:4Jan 15 02:37:14 family-room-desktop syslogd 1.4.1#21ubuntu3: **restart.**
Jan 15 02:37:14 family-room-desktop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan 15 02:37:14 family-room-desktop syslogd: /var/log/kern.log: No space left on device
Jan 15 02:37:14 family-room-desktop kernel: Loaded 26084 symbols from /boot/System.map-2.6.22-14-generic.
Jan 15 02:37:14 family-room-desktop kernel: Symbols match kernel version 2.6.22.

Could this be related to ACPI somehow?  

Thanks,

James

---

### Post by OoooMatron on 2008-01-16
In my experience, reboots are usually a sign of an insufficient power supply. Check the wattage of the current supply and post up your hardware that you use and it might be easier to determine if that is one of the causes.

It might also be worthwhile running memtest to see if any ram errors occur.

You've also got no space on drive errors. Maybe try making some free space.

---

### Post by Magellan on 2008-01-16
> **OoooMatron said:**
> In my experience, reboots are usually a sign of an insufficient power supply. Check the wattage of the current supply and post up your hardware that you use and it might be easier to determine if that is one of the causes.

It might also be worthwhile running memtest to see if any ram errors occur.

You've also got no space on drive errors. Maybe try making some free space.

Here's what I have:
[LIST]
[*]Antec Fusion Case with 430W power supply
[*]Intel DG33TLM MB
[*]Intel Core 2 Duo E6550 Processor
[*]Hauppage WinTV-PVR-150
[*]2GB Ram ( 2 X 1GB, Kingston, DDR2 800)
[*]Seagate 320GB SATA Drive
[*]NEC DL DVD Burner
[*]Logitech Edge keyboard & mouse (wireless, RF)
[/LIST]

Here's what Antec has to say about the PS:
> Power Supply
 High-efficiency 430 Watt
ATX12V v2.0 power supply
Universal input
Active PFC and high efficiency design 

I suppose it could be a hardware problem, but the fact that occurs almost exactly every 60 minutes makes me think it is software related.  If I look at the log, I see the Reboot message at 60 minute intervals 24 hours a day in most cases.  Sometimes it occurs at 61 minutes, but it is very steady.  The computer reboots and is then fine for another hour.  

I noticed the error log issue as well.  I installed MythTV recently (this problem preceded that) and forgot to turn off some logging for replication.  I turned off the logging, but still have to go clean some things up.

Thanks,

James

---

### Post by OoooMatron on 2008-01-17
Yeah that should be enough Watts to run that rig.

It's very odd your problem occurs almost on the hour. If you are really busy with the machine and try hard to fill up the RAM and use the CPU does it reboot any sooner?

---

### Post by Magellan on 2008-02-01
> **OoooMatron said:**
> Yeah that should be enough Watts to run that rig.

It's very odd your problem occurs almost on the hour. If you are really busy with the machine and try hard to fill up the RAM and use the CPU does it reboot any sooner?

That's probably a good thing to try.  The heaviest load I've put this through is in ripping some dvds using MythTV.

I added acpi=off to the default boot entry in menu.lst and that has solved the problem, but now when I shutdown the pc from the menu, it doesn't power down.  That's not a big deal, but it would be nice if would work.  

I figure turning off the power control turned off that function.  At least this tells me where the problem lies.    I'll do some searches on ACPI and see what I can find.

I'm not marking this as solved because I just traded one problem for another at this point.

Thanks for the input.

James.

---

