---
title: "Kubuntu 20.04 freezes when left alone for a while. Auto-suspend is off?"
date: 2020-06-03
forum: General Help
---

### Post by jorxster on 2020-06-03
Hi folks, 

My kubuntu 18 quit booting on me so I figured it was a good time to do a fresh install of kubuntu 20.04. Only been running a couple of weeks, and have kept software packages updated.
Hardware : AMD Ryzen 3000, Nvidia GTX 1070, Asus motherboard.

However recently within the last week, I noticed that my computer will freeze with the screens off, if I leave it for an hour or two. Screens will remain off, keyboard and mouse input do nothing.
The sleep function works normally when triggered manually, but despite "**Suspend Session**" being turned off in **System Settings > Energy Saving**, it seems to be doing something and freezing when I leave it for a while.

How can I troubleshoot this?
Are there any other settings besides **System Settings > Energy Saving** where I can check for auto-suspend or timeouts happening?

cheers,
Jordan

P.S.

Dmesg gives me this. Not sure if related... or where else to look for logs

[FONT=monospace][COLOR=#18B218][    9.164267] [/COLOR][COLOR=#B26818]IPv6[/COLOR][COLOR=#000000]: ADDRCONF(NETDEV_CHANGE): enp35s0: link becomes ready[/COLOR]
[COLOR=#18B218][ 1522.729949] [/COLOR][COLOR=#B26818]PM[/COLOR][COLOR=#000000]: suspend entry (deep)[/COLOR]
[COLOR=#18B218][ 1522.738248] [/COLOR][COLOR=#B26818]Filesystems sync[/COLOR][COLOR=#000000]: 0.008 seconds[/COLOR]
[COLOR=#18B218][ 1523.959487] [/COLOR][COLOR=#000000]Freezing user space processes ... (elapsed 0.004 seconds) done.[/COLOR]
[COLOR=#18B218][ 1523.963679] [/COLOR][COLOR=#000000]OOM killer disabled.[/COLOR]
[COLOR=#18B218][ 1523.963680] [/COLOR][COLOR=#000000]Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.[/COLOR]
[COLOR=#18B218][ 1523.964907] [/COLOR][COLOR=#B26818]printk[/COLOR][COLOR=#000000]: Suspending console(s) (use no_console_suspend to debug)[/COLOR]
[COLOR=#18B218][ 1523.993623] [/COLOR][COLOR=#B26818]sd 3:0:0:0[/COLOR][COLOR=#000000]: [sdb] Synchronizing SCSI cache[/COLOR]
[COLOR=#18B218][ 1523.993978] [/COLOR][COLOR=#B26818]sd 2:0:0:0[/COLOR][COLOR=#000000]: [sda] Synchronizing SCSI cache[/COLOR]
[COLOR=#18B218][ 1523.994118] [/COLOR][COLOR=#B26818]sd 2:0:0:0[/COLOR][COLOR=#000000]: [sda] Stopping disk[/COLOR]
[COLOR=#18B218][ 1523.999634] [/COLOR][COLOR=#B26818]sd 3:0:0:0[/COLOR][COLOR=#000000]: [sdb] Stopping disk[/COLOR]
[COLOR=#18B218][ 1525.511249] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: EC: interrupt blocked[/COLOR]
[COLOR=#18B218][ 1525.589845] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: Preparing to enter system sleep state S3[/COLOR]
[COLOR=#18B218][ 1525.917860] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: EC: event blocked[/COLOR]
[COLOR=#18B218][ 1525.917861] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: EC: EC stopped[/COLOR]
[COLOR=#18B218][ 1525.917862] [/COLOR][COLOR=#B26818]PM[/COLOR][COLOR=#000000]: Saving platform NVS memory[/COLOR]
[COLOR=#18B218][ 1525.917900] [/COLOR][COLOR=#000000]Disabling non-boot CPUs ...[/COLOR]
[COLOR=#18B218][ 1525.919168] [/COLOR][COLOR=#B26818]IRQ 75[/COLOR][COLOR=#000000]**: no longer affine to CPU1**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.920236] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 1 is now offline[/COLOR]
[COLOR=#18B218][ 1525.923369] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 2 is now offline[/COLOR]
[COLOR=#18B218][ 1525.926692] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 3 is now offline[/COLOR]
[COLOR=#18B218][ 1525.929992] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 4 is now offline[/COLOR]
[COLOR=#18B218][ 1525.932290] [/COLOR][COLOR=#B26818]IRQ 46[/COLOR][COLOR=#000000]**: no longer affine to CPU5**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.933308] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 5 is now offline[/COLOR]
[COLOR=#18B218][ 1525.936498] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 6 is now offline[/COLOR]
[COLOR=#18B218][ 1525.939072] [/COLOR][COLOR=#B26818]IRQ 31[/COLOR][COLOR=#000000]**: no longer affine to CPU7**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.940083] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 7 is now offline[/COLOR]
[COLOR=#18B218][ 1525.943303] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 8 is now offline[/COLOR]
[COLOR=#18B218][ 1525.945557] [/COLOR][COLOR=#B26818]IRQ 45[/COLOR][COLOR=#000000]**: no longer affine to CPU9**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.946575] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 9 is now offline[/COLOR]
[COLOR=#18B218][ 1525.948451] [/COLOR][COLOR=#B26818]IRQ 49[/COLOR][COLOR=#000000]**: no longer affine to CPU10**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.949512] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 10 is now offline[/COLOR]
[COLOR=#18B218][ 1525.951643] [/COLOR][COLOR=#B26818]IRQ 29[/COLOR][COLOR=#000000]**: no longer affine to CPU11**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.951648] [/COLOR][COLOR=#B26818]IRQ 30[/COLOR][COLOR=#000000]**: no longer affine to CPU11**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.952667] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 11 is now offline[/COLOR]
[COLOR=#18B218][ 1525.954498] [/COLOR][COLOR=#B26818]IRQ 58[/COLOR][COLOR=#000000]**: no longer affine to CPU12**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.955514] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 12 is now offline[/COLOR]
[COLOR=#18B218][ 1525.958529] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 13 is now offline[/COLOR]
[COLOR=#18B218][ 1525.960216] [/COLOR][COLOR=#B26818]IRQ 76[/COLOR][COLOR=#000000]**: no longer affine to CPU14**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1525.961297] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 14 is now offline[/COLOR]
[COLOR=#18B218][ 1525.964204] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: CPU 15 is now offline[/COLOR]
[COLOR=#18B218][ 1525.966347] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: Low-level resume complete[/COLOR]
[COLOR=#18B218][ 1525.966394] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: EC: EC started[/COLOR]
[COLOR=#18B218][ 1525.966394] [/COLOR][COLOR=#B26818]PM[/COLOR][COLOR=#000000]: Restoring platform NVS memory[/COLOR]
[COLOR=#18B218][ 1525.966900] [/COLOR][COLOR=#000000]Enabling non-boot CPUs ...[/COLOR]
[COLOR=#18B218][ 1525.966942] [/COLOR][COLOR=#B26818]x86[/COLOR][COLOR=#000000]: Booting SMP configuration:[/COLOR]
[COLOR=#18B218][ 1525.966943] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 1 APIC 0x1[/COLOR]
[COLOR=#18B218][ 1525.967070] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU1: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.969479] [/COLOR][COLOR=#000000]CPU1 is up[/COLOR]
[COLOR=#18B218][ 1525.969512] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 2 APIC 0x2[/COLOR]
[COLOR=#18B218][ 1525.969618] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU2: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.971997] [/COLOR][COLOR=#000000]CPU2 is up[/COLOR]
[COLOR=#18B218][ 1525.972014] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 3 APIC 0x3[/COLOR]
[COLOR=#18B218][ 1525.972115] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU3: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.974581] [/COLOR][COLOR=#000000]CPU3 is up[/COLOR]
[COLOR=#18B218][ 1525.974598] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 4 APIC 0x4[/COLOR]
[COLOR=#18B218][ 1525.974777] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU4: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.977157] [/COLOR][COLOR=#000000]CPU4 is up[/COLOR]
[COLOR=#18B218][ 1525.977172] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 5 APIC 0x5[/COLOR]
[COLOR=#18B218][ 1525.977272] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU5: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.979684] [/COLOR][COLOR=#000000]CPU5 is up[/COLOR]
[COLOR=#18B218][ 1525.979698] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 6 APIC 0x6[/COLOR]
[COLOR=#18B218][ 1525.979805] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU6: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.982225] [/COLOR][COLOR=#000000]CPU6 is up[/COLOR]
[COLOR=#18B218][ 1525.982240] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 7 APIC 0x7[/COLOR]
[COLOR=#18B218][ 1525.982340] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU7: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.984793] [/COLOR][COLOR=#000000]CPU7 is up[/COLOR]
[COLOR=#18B218][ 1525.984807] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 8 APIC 0x8[/COLOR]
[COLOR=#18B218][ 1525.984966] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU8: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.987499] [/COLOR][COLOR=#000000]CPU8 is up[/COLOR]
[COLOR=#18B218][ 1525.987515] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 9 APIC 0x9[/COLOR]
[COLOR=#18B218][ 1525.987657] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU9: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.990205] [/COLOR][COLOR=#000000]CPU9 is up[/COLOR]
[COLOR=#18B218][ 1525.990223] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 10 APIC 0xa[/COLOR]
[COLOR=#18B218][ 1525.990380] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU10: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.992915] [/COLOR][COLOR=#000000]CPU10 is up[/COLOR]
[COLOR=#18B218][ 1525.992931] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 11 APIC 0xb[/COLOR]
[COLOR=#18B218][ 1525.993072] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU11: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.995664] [/COLOR][COLOR=#000000]CPU11 is up[/COLOR]
[COLOR=#18B218][ 1525.995680] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 12 APIC 0xc[/COLOR]
[COLOR=#18B218][ 1525.995840] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU12: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1525.998447] [/COLOR][COLOR=#000000]CPU12 is up[/COLOR]
[COLOR=#18B218][ 1525.998463] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 13 APIC 0xd[/COLOR]
[COLOR=#18B218][ 1525.998608] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU13: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1526.001271] [/COLOR][COLOR=#000000]CPU13 is up[/COLOR]
[COLOR=#18B218][ 1526.001286] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 14 APIC 0xe[/COLOR]
[COLOR=#18B218][ 1526.001448] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU14: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1526.004078] [/COLOR][COLOR=#000000]CPU14 is up[/COLOR]
[COLOR=#18B218][ 1526.004096] [/COLOR][COLOR=#B26818]smpboot[/COLOR][COLOR=#000000]: Booting Node 0 Processor 15 APIC 0xf[/COLOR]
[COLOR=#18B218][ 1526.004241] [/COLOR][COLOR=#B26818]microcode[/COLOR][COLOR=#000000]: CPU15: patch_level=0x08001126[/COLOR]
[COLOR=#18B218][ 1526.006914] [/COLOR][COLOR=#000000]CPU15 is up[/COLOR]
[COLOR=#18B218][ 1526.008486] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: Waking up from system sleep state S3[/COLOR]
[COLOR=#18B218][ 1526.009222] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: EC: interrupt unblocked[/COLOR]
[COLOR=#18B218][ 1526.091633] [/COLOR][COLOR=#B26818]ACPI[/COLOR][COLOR=#000000]: EC: event unblocked[/COLOR]
[COLOR=#18B218][ 1526.091752] [/COLOR][COLOR=#B26818]usb usb1[/COLOR][COLOR=#000000]: root hub lost power or was reset[/COLOR]
[COLOR=#18B218][ 1526.091755] [/COLOR][COLOR=#B26818]usb usb2[/COLOR][COLOR=#000000]: root hub lost power or was reset[/COLOR]
[COLOR=#18B218][ 1526.092132] [/COLOR][COLOR=#B26818]sd 2:0:0:0[/COLOR][COLOR=#000000]: [sda] Starting disk[/COLOR]
[COLOR=#18B218][ 1526.092133] [/COLOR][COLOR=#B26818]sd 3:0:0:0[/COLOR][COLOR=#000000]: [sdb] Starting disk[/COLOR]
[COLOR=#18B218][ 1526.263802] [/COLOR][COLOR=#B26818]nvme nvme0[/COLOR][COLOR=#000000]: 7/0/0 default/read/poll queues[/COLOR]
[COLOR=#18B218][ 1526.404206] [/COLOR][COLOR=#B26818]ata1[/COLOR][COLOR=#000000]: SATA link down (SStatus 0 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.404590] [/COLOR][COLOR=#B26818]ata8[/COLOR][COLOR=#000000]: SATA link down (SStatus 0 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.406024] [/COLOR][COLOR=#B26818]ata7[/COLOR][COLOR=#000000]: SATA link down (SStatus 0 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.406025] [/COLOR][COLOR=#B26818]ata9[/COLOR][COLOR=#000000]: SATA link down (SStatus 0 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.406214] [/COLOR][COLOR=#B26818]ata6[/COLOR][COLOR=#000000]: SATA link down (SStatus 0 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.406234] [/COLOR][COLOR=#B26818]ata2[/COLOR][COLOR=#000000]: SATA link down (SStatus 0 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.406251] [/COLOR][COLOR=#B26818]ata5[/COLOR][COLOR=#000000]: SATA link down (SStatus 0 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.566125] [/COLOR][COLOR=#B26818]ata3[/COLOR][COLOR=#000000]: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.566192] [/COLOR][COLOR=#B26818]ata4[/COLOR][COLOR=#000000]: SATA link up 6.0 Gbps (SStatus 133 SControl 300)[/COLOR]
[COLOR=#18B218][ 1526.566874] [/COLOR][COLOR=#B26818]ata3.00[/COLOR][COLOR=#000000]**: supports DRM functions and may not be fully accessible**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1526.567538] [/COLOR][COLOR=#B26818]ata3.00[/COLOR][COLOR=#000000]**: supports DRM functions and may not be fully accessible**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1526.568113] [/COLOR][COLOR=#B26818]ata3.00[/COLOR][COLOR=#000000]: configured for UDMA/133[/COLOR]
[COLOR=#18B218][ 1526.570389] [/COLOR][COLOR=#B26818]ata4.00[/COLOR][COLOR=#000000]: configured for UDMA/133[/COLOR]
[COLOR=#18B218][ 1526.766947] [/COLOR][COLOR=#B26818]usb 2-8[/COLOR][COLOR=#000000]: reset SuperSpeed Gen 1 USB device number 3 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1526.915259] [/COLOR][COLOR=#B26818]usb 2-3[/COLOR][COLOR=#000000]: reset SuperSpeed Gen 1 USB device number 2 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1527.062207] [/COLOR][COLOR=#B26818]usb 1-12[/COLOR][COLOR=#000000]: reset full-speed USB device number 6 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1527.418199] [/COLOR][COLOR=#B26818]usb 1-7[/COLOR][COLOR=#000000]: reset full-speed USB device number 3 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1527.774279] [/COLOR][COLOR=#B26818]usb 1-8[/COLOR][COLOR=#000000]: reset high-speed USB device number 4 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1527.930862] [/COLOR][COLOR=#B26818]usb 1-11[/COLOR][COLOR=#000000]: reset full-speed USB device number 5 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1528.294593] [/COLOR][COLOR=#B26818]usb 1-6[/COLOR][COLOR=#000000]: reset full-speed USB device number 2 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1528.606601] [/COLOR][COLOR=#B26818]usb 1-8.4[/COLOR][COLOR=#000000]: reset full-speed USB device number 8 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1528.922571] [/COLOR][COLOR=#B26818]usb 1-8.5[/COLOR][COLOR=#000000]: reset high-speed USB device number 9 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1528.926534] [/COLOR][COLOR=#B26818]igb 0000:23:00.0 enp35s0[/COLOR][COLOR=#B21818]: Reset adapter[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1529.054583] [/COLOR][COLOR=#B26818]usb 1-8.3[/COLOR][COLOR=#000000]: reset full-speed USB device number 7 using xhci_hcd[/COLOR]
[COLOR=#18B218][ 1529.305510] [/COLOR][COLOR=#B26818]fbcon[/COLOR][COLOR=#000000]: Taking over console[/COLOR]
[COLOR=#18B218][ 1529.305523] [/COLOR][COLOR=#000000]OOM killer enabled.[/COLOR]
[COLOR=#18B218][ 1529.305524] [/COLOR][COLOR=#000000]Restarting tasks ...  [/COLOR]
[COLOR=#18B218][ 1529.306911] [/COLOR][COLOR=#B26818]Console[/COLOR][COLOR=#000000]: switching to colour frame buffer device 210x65[/COLOR]
[COLOR=#18B218][ 1529.312559] [/COLOR][COLOR=#000000]**done.**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1529.326131] [/COLOR][COLOR=#B26818]PM[/COLOR][COLOR=#000000]: suspend exit[/COLOR]
[COLOR=#18B218][ 1532.702607] [/COLOR][COLOR=#B26818]igb 0000:23:00.0 enp35s0[/COLOR][COLOR=#000000]: igb: enp35s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Contr[/COLOR]
ol: RX/TX
[COLOR=#18B218][ 1532.702925] [/COLOR][COLOR=#B26818]IPv6[/COLOR][COLOR=#000000]: ADDRCONF(NETDEV_CHANGE): enp35s0: link becomes ready[/COLOR]
[COLOR=#18B218][ 1534.487446] [/COLOR][COLOR=#B26818]kauditd_printk_skb[/COLOR][COLOR=#000000]**: 21 callbacks suppressed**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][ 1534.487448] [/COLOR][COLOR=#B26818]audit[/COLOR][COLOR=#000000]: type=1400 audit(1591215829.516:33): apparmor="DENIED" operation="capable" profil[/COLOR]
e="/usr/sbin/cups-browsed" pid=4296 comm="cups-browsed" capability=23  capname="sys_nice"
[/FONT]

---

### Post by mastablasta on 2020-06-04
open KsystemLog to view other logs. [https://userbase.kde.org/KSystemLog](https://userbase.kde.org/KSystemLog)

also logs are in /var/log/

```
[COLOR=#18B218][FONT=monospace][ 1525.511249] [/FONT][/COLOR][COLOR=#B26818][FONT=monospace]ACPI[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]: EC: interrupt blocked[/FONT][/COLOR][/COLOR]
[COLOR=#18B218][FONT=monospace][ 1525.589845] [/FONT][/COLOR][COLOR=#B26818][FONT=monospace]ACPI[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]: Preparing to enter system sleep state S3[/FONT][/COLOR][/COLOR]
[COLOR=#18B218][FONT=monospace][ 1525.917860] [/FONT][/COLOR][COLOR=#B26818][FONT=monospace]ACPI[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]: EC: event blocked[/FONT][/COLOR][/COLOR]
[COLOR=#18B218][FONT=monospace][ 1525.917861] [/FONT][/COLOR][COLOR=#B26818][FONT=monospace]ACPI[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=monospace]: EC: EC stopped[/FONT][/COLOR][/COLOR]
```

check settings in UEFI, check if you have it updated (or if any of the available UEFI updates fixes such an issue).

I am not sure from your post, if this only happens when PC is idle or at random.

if PC is freezing at random, make sure it is not an overheat issue. Psensor application can help you with a nice GUI for lm_sensors. 

it could be an issue with ACPI. if that is the case, there are some kernel switches available as well as settings in UEFI. check what is setup.

edit: 
> [COLOR=#000000]However recently within the last week, I noticed that my computer will freeze with the screens off, if I leave it for an hour or two. Screens will remain off, keyboard and mouse input do nothing.[/COLOR]

try pressing the ON button on the box. It could be that it is only hibernating.

---

### Post by jorxster on 2020-06-07
Thanks Mastablasta,

The issue with KSystemLog is that it only captures logs from the current session -- once I've force rebooted, I've lost those logs, it seems. (Or are they backed up somewhere?)

By the way, I have more details. I disabled "Screen Energy Saving" to leave screens on and now what happens is this : I leave it locked, and the keyboard input no longer does anything, but the mouse is fine. So I'm stuck at a lockscreen where my mouse moves perfectly fine, but typing on the keyboard does nothing. Not even after unplugging USB and re-plugging into a different port.
Also, because my keyboard or inputs quits working, I can't switch to a pseudoterminal (teleterminal?) and access my computer that way.

So something is locking up X or KDE / blocking my keyboard after being left idle for an hour, and I can't figure out what it is... my only option is to force reboot the machine.

Do my logs get backed up somewhere else?

cheers,
Jordan

---

### Post by CelticWarrior on 2020-06-07
Have you installed Nvidia drivers? Not mentioned so I assume not installed.

---

### Post by jorxster on 2020-06-10
> **CelticWarrior said:**
> Have you installed Nvidia drivers? Not mentioned so I assume not installed.
Thank you CelticWarrior -- I do have the latest installed via Ubuntu official sources -- nvidia-driver-440.
That's an interesting point, maybe I should try downgrading to 435 to see if that helps.

---

### Post by mastablasta on 2020-06-11
> **jorxster said:**
> 
Do my logs get backed up somewhere else?



how to view log files in temrinal: [https://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](https://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/)

they are found in  /var/log


you will find the old ones with extension .old next to them. sometimes they are compressed (.tar.gz). and if i am not mistaking, there should be an option in [COLOR=#000000]KsystemLog[/COLOR] to see old logs as well.

[https://docs.kde.org/trunk5/en/kdeadmin/ksystemlog/reading.html](https://docs.kde.org/trunk5/en/kdeadmin/ksystemlog/reading.html)

if you can't open them in [COLOR=#000000]KsystemLog, you can view them in Kate (the KDE text editor) just as well. unkompress them using ark (if they are compressed) and then double click them or right click and open with Kate. they might also open in log viewer. i just got used to view them in editor.[/COLOR]

---

