---
title: "do a suspend and get an immediate restart on 13.10"
date: 2013-12-19
forum: General Help
---

### Post by sdowney717 on 2013-12-19
dmesg
```
[   87.540164] e100: Copyright(c) 1999-2006 Intel Corporation
[   87.580658] e100 0000:03:08.0 eth0: addr 0xfeafb000, irq 20, MAC addr 00:11:11:52:96:85
[   87.641220] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[   87.641229] e1000: Copyright (c) 1999-2006 Intel Corporation.
[   87.641370] e1000 0000:02:01.0: setting latency timer to 64
[   88.126176] e1000 0000:02:01.0 eth1: (PCI:33MHz:32-bit) 00:11:11:52:96:83
[   88.126192] e1000 0000:02:01.0 eth1: Intel(R) PRO/1000 Network Connection
[   89.078014] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   89.097832] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   89.099466] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   89.102894] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   89.104683] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   91.108415] e1000: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   91.108466] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  248.484623] PM: Syncing filesystems ... done.
[  248.631353] PM: Preparing system for mem sleep
[  249.176705] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  249.178136] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  249.179448] PM: Entering mem sleep
[  249.179518] Suspending console(s) (use no_console_suspend to debug)
[  249.180205] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  249.180392] sd 0:0:0:0: [sda] Stopping disk
[  249.184650] parport_pc 00:08: disabled
[  249.184954] serial 00:07: disabled
[  249.184988] serial 00:07: System wakeup disabled by ACPI
[  249.185061] serial 00:06: disabled
[  249.185091] serial 00:06: System wakeup disabled by ACPI
[  249.326607] PM: suspend of devices complete after 146.863 msecs
[  249.326888] PM: late suspend of devices complete after 0.276 msecs
[  249.327176] pci 0000:00:1e.0: System wakeup enabled by ACPI
[  249.340048] pci 0000:00:1e.0: System wakeup enabled by ACPI
[  249.356044] pci 0000:00:1e.0: System wakeup enabled by ACPI
[  249.372048] pci 0000:00:1e.0: System wakeup enabled by ACPI
[  249.388217] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
[  249.404077] uhci_hcd 0000:00:1d.3: System wakeup enabled by ACPI
[  249.404133] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
[  249.404186] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
[  249.404239] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
[  249.404348] PM: noirq suspend of devices complete after 77.456 msecs
[  249.404522] ACPI: Preparing to enter system sleep state S3
[  249.404760] PM: Saving platform NVS memory
[  249.405968] Disabling non-boot CPUs ...
[  249.508015] smpboot: CPU 1 is now offline
[  249.508333] ACPI: Low-level resume complete
[  249.508333] PM: Restoring platform NVS memory
[  249.508333] Force enabled HPET at resume
[  249.508333] Enabling non-boot CPUs ...
[  249.508333] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  249.407412] Initializing CPU#1
[  249.522014] CPU1 is up
[  249.523308] ACPI: Waking up from system sleep state S3
[  249.531100] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
[  249.531157] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
[  249.531213] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
[  249.531268] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
[  249.544088] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
[  249.576062] pci 0000:00:1e.0: System wakeup disabled by ACPI
[  249.592055] pci 0000:00:1e.0: System wakeup disabled by ACPI
[  249.608051] pci 0000:00:1e.0: System wakeup disabled by ACPI
[  249.624065] pci 0000:00:1e.0: System wakeup disabled by ACPI
[  249.656258] PM: noirq resume of devices complete after 125.344 msecs
[  249.656473] PM: early resume of devices complete after 0.178 msecs
[  249.656629] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[  249.656654] usb usb3: root hub lost power or was reset
[  249.656759] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[  249.656775] pci 0000:00:1e.0: setting latency timer to 64
[  249.656784] usb usb4: root hub lost power or was reset
[  249.656976] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[  249.657000] usb usb5: root hub lost power or was reset
[  249.657202] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[  249.657226] usb usb6: root hub lost power or was reset
[  249.657340] ehci-pci 0000:00:1d.7: setting latency timer to 64
[  249.657428] ata_piix 0000:00:1f.1: setting latency timer to 64
[  249.657488] ata_piix 0000:00:1f.2: setting latency timer to 64
[  249.657564] [drm] AGP mode requested: 8
[  249.657569] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[  249.657595] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[  249.657647] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[  249.657726] radeon 0000:01:00.0: GTT: 64M 0xF8000000 - 0xFBFFFFFF
[  249.674134] serial 00:06: activated
[  249.674775] serial 00:07: activated
[  249.675414] parport_pc 00:08: activated
[  249.677244] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[  249.677257] radeon 0000:01:00.0: WB disabled
[  249.677263] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000f8000000 and cpu addr 0xf8416000
[  249.677313] [drm] radeon: ring at 0x00000000F8001000
[  249.677348] [drm] ring test succeeded in 5 usecs
[  249.677365] [drm] ib test succeeded in 0 usecs
[  249.714021] usb usb7: root hub lost power or was reset
[  249.714023] usb usb8: root hub lost power or was reset
[  249.716039] usb usb9: root hub lost power or was reset
[  250.136056] usb 5-1: reset low-speed USB device number 2 using uhci_hcd
[  250.228063] firewire_core 0000:03:01.4: rediscovered device fw0
[  250.728309] ata2.01: ACPI cmd ef/03:22:00:00:00:b0 (SET FEATURES) filtered out
[  250.728312] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[  250.752297] ata2.00: ACPI cmd ef/03:44:00:00:00:a0 (SET FEATURES) filtered out
[  250.752301] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[  250.752304] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  250.784175] ata2.00: configured for UDMA/66
[  250.800176] ata2.01: configured for MWDMA2
[  253.812299] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[  253.812303] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[  253.812472] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[  253.812476] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  253.836351] ata1.00: configured for UDMA/100
[  253.837124] sd 0:0:0:0: [sda] Starting disk
[  256.840016] 
[  256.840017] floppy driver state
[  256.840018] -------------------
[  256.840038] now=4294956506 last interrupt=4294892614 diff=63892 last called handler=reset_interrupt [floppy]
[  256.840039] timeout_message=lock fdc
[  256.840040] last output bytes:
[  256.840042]  8 80 4294892606
[  256.840044]  8 80 4294892606
[  256.840045]  8 80 4294892606
[  256.840046]  8 80 4294892612
[  256.840047]  8 80 4294892612
[  256.840049]  8 80 4294892612
[  256.840050]  8 80 4294892612
[  256.840051]  e 80 4294892613
[  256.840052] 13 80 4294892613
[  256.840054]  0 90 4294892613
[  256.840055] 1a 90 4294892613
[  256.840056]  0 90 4294892613
[  256.840057] 12 90 4294892613
[  256.840059]  0 90 4294892613
[  256.840060] 14 90 4294892613
[  256.840061] 18 80 4294892613
[  256.840062]  8 80 4294892614
[  256.840064]  8 80 4294892614
[  256.840065]  8 80 4294892614
[  256.840066]  8 80 4294892614
[  256.840067] last result at 4294892614
[  256.840068] last redo_fd_request at 4294914106
[  256.840076] status=0
[  256.840077] fdc_busy=1
[  256.840084] do_floppy=reset_interrupt [floppy]
[  256.840085] cont=f842e294
[  256.840086] current_req=  (null)
[  256.840087] command_status=-1
[  256.840088] 
[  256.840091] floppy0: floppy timeout called
[  256.840176] PM: resume of devices complete after 7183.697 msecs
[  256.840599] PM: Finishing wakeup.
[  256.840602] Restarting tasks ... done.
[  257.195619] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[  257.195629] e100: Copyright(c) 1999-2006 Intel Corporation
[  257.237889] e100 0000:03:08.0 eth0: addr 0xfeafb000, irq 20, MAC addr 00:11:11:52:96:85
[  257.291637] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[  257.291646] e1000: Copyright (c) 1999-2006 Intel Corporation.
[  257.291784] e1000 0000:02:01.0: setting latency timer to 64
[  257.746510] e1000 0000:02:01.0 eth1: (PCI:33MHz:32-bit) 00:11:11:52:96:83
[  257.746528] e1000 0000:02:01.0 eth1: Intel(R) PRO/1000 Network Connection
[  258.405921] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  258.425816] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  258.426853] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  258.430380] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  258.431241] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  259.304183] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  259.304221] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  259.304238] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  260.436423] e1000: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  260.436476] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
scott875@scott875-desktop:~$ 

```

suspend log
```
Initial commandline parameters: 
Thu Dec 19 14:06:19 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800usb              22485  0 
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00usb              20041  1 rt2800usb
rt2800lib              70115  1 rt2800usb
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
snd_emu10k1           141168  3 snd_emu10k1_synth
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        105668  1 snd_emu10k1
binfmt_misc            13140  1 
cfg80211              401436  2 mac80211,rt2x00lib
ac97_bus               12642  1 snd_ac97_codec
radeon               1307301  3 
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
ttm                    71886  1 radeon
soundcore              12600  1 snd
drm_kms_helper         46867  1 radeon
drm                   242354  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
emu10k1_gp             12541  0 
microcode              18830  0 
gameport               14952  2 emu10k1_gp
serio_raw              13189  0 
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
e100                   35945  0 
firewire_core          57656  1 firewire_ohci
ohci_pci               13305  0 
crc_itu_t              12627  1 firewire_core
mii                    13654  1 e100
floppy                 55378  0 
e1000                 128369  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     504300     521136          0      11880     205352
-/+ buffers/cache:     287068     738368
Swap:      2026452      45560    1980892
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:06:21 EST 2013: performing suspend
Thu Dec 19 14:06:31 EST 2013: Awake.
Thu Dec 19 14:06:32 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:06:33 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:06:52 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800usb              22485  0 
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00usb              20041  1 rt2800usb
rt2800lib              70115  1 rt2800usb
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
snd_emu10k1           141168  3 snd_emu10k1_synth
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        105668  1 snd_emu10k1
binfmt_misc            13140  1 
cfg80211              401436  2 mac80211,rt2x00lib
ac97_bus               12642  1 snd_ac97_codec
radeon               1307301  4 
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
ttm                    71886  1 radeon
soundcore              12600  1 snd
drm_kms_helper         46867  1 radeon
drm                   242354  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
emu10k1_gp             12541  0 
microcode              18830  0 
gameport               14952  2 emu10k1_gp
serio_raw              13189  0 
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
ohci_pci               13305  0 
crc_itu_t              12627  1 firewire_core
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     578724     446712          0      14244     219400
-/+ buffers/cache:     345080     680356
Swap:      2026452      41388    1985064
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:06:53 EST 2013: performing suspend
Thu Dec 19 14:07:04 EST 2013: Awake.
Thu Dec 19 14:07:04 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:07:05 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:09:23 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800usb              22485  0 
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00usb              20041  1 rt2800usb
rt2800lib              70115  1 rt2800usb
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
snd_emu10k1           141168  5 snd_emu10k1_synth
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        105668  1 snd_emu10k1
binfmt_misc            13140  1 
cfg80211              401436  2 mac80211,rt2x00lib
ac97_bus               12642  1 snd_ac97_codec
radeon               1307301  3 
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
snd                    60790  21 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
ttm                    71886  1 radeon
soundcore              12600  1 snd
drm_kms_helper         46867  1 radeon
drm                   242354  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
emu10k1_gp             12541  0 
microcode              18830  0 
gameport               14952  2 emu10k1_gp
serio_raw              13189  0 
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
ohci_pci               13305  0 
crc_itu_t              12627  1 firewire_core
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     732944     292492          0      28840     368848
-/+ buffers/cache:     335256     690180
Swap:      2026452       9292    2017160
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:09:24 EST 2013: performing suspend
Thu Dec 19 14:09:32 EST 2013: Awake.
Thu Dec 19 14:09:32 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:09:34 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:14:46 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800usb              22485  0 
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00usb              20041  1 rt2800usb
rt2800lib              70115  1 rt2800usb
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
snd_emu10k1           141168  3 snd_emu10k1_synth
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        105668  1 snd_emu10k1
binfmt_misc            13140  1 
cfg80211              401436  2 mac80211,rt2x00lib
ac97_bus               12642  1 snd_ac97_codec
radeon               1307301  4 
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
ttm                    71886  1 radeon
soundcore              12600  1 snd
drm_kms_helper         46867  1 radeon
drm                   242354  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
emu10k1_gp             12541  0 
microcode              18830  0 
gameport               14952  2 emu10k1_gp
serio_raw              13189  0 
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
ohci_pci               13305  0 
crc_itu_t              12627  1 firewire_core
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     934020      91416          0      23664     403532
-/+ buffers/cache:     506824     518612
Swap:      2026452       9520    2016932
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:14:47 EST 2013: performing suspend
Thu Dec 19 14:14:55 EST 2013: Awake.
Thu Dec 19 14:14:55 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:14:57 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:32:22 EST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800usb              22485  0 
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00usb              20041  1 rt2800usb
rt2800lib              70115  1 rt2800usb
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
snd_emu10k1           141168  3 snd_emu10k1_synth
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
snd_ac97_codec        105668  1 snd_emu10k1
binfmt_misc            13140  1 
cfg80211              401436  2 mac80211,rt2x00lib
ac97_bus               12642  1 snd_ac97_codec
radeon               1307301  4 
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
ttm                    71886  1 radeon
soundcore              12600  1 snd
drm_kms_helper         46867  1 radeon
drm                   242354  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
emu10k1_gp             12541  0 
microcode              18830  0 
gameport               14952  2 emu10k1_gp
serio_raw              13189  0 
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
ohci_pci               13305  0 
crc_itu_t              12627  1 firewire_core
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     910240     115196          0      12444     230748
-/+ buffers/cache:     667048     358388
Swap:      2026452      11760    2014692
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:
/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.

Thu Dec 19 14:32:24 EST 2013: performing hibernate
Initial commandline parameters: 
Thu Dec 19 14:34:59 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
binfmt_misc            13140  1 
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
rt2800usb              22485  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
rt2x00usb              20041  1 rt2800usb
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800lib              70115  1 rt2800usb
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_emu10k1           141168  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
cfg80211              401436  2 mac80211,rt2x00lib
snd_ac97_codec        105668  1 snd_emu10k1
radeon               1307301  3 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
ttm                    71886  1 radeon
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242354  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
microcode              18830  0 
emu10k1_gp             12541  0 
serio_raw              13189  0 
gameport               14952  2 emu10k1_gp
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
e100                   35945  0 
mii                    13654  1 e100
crc_itu_t              12627  1 firewire_core
ohci_pci               13305  0 
floppy                 55378  0 
e1000                 128369  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     496276     529160          0      41432     221180
-/+ buffers/cache:     233664     791772
Swap:      2026452          0    2026452
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:35:00 EST 2013: performing suspend
Thu Dec 19 14:35:11 EST 2013: Awake.
Thu Dec 19 14:35:11 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:35:13 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:37:52 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
binfmt_misc            13140  1 
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
rt2800usb              22485  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
rt2x00usb              20041  1 rt2800usb
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800lib              70115  1 rt2800usb
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_emu10k1           141168  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
cfg80211              401436  2 mac80211,rt2x00lib
snd_ac97_codec        105668  1 snd_emu10k1
radeon               1307301  3 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
ttm                    71886  1 radeon
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242354  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
microcode              18830  0 
emu10k1_gp             12541  0 
serio_raw              13189  0 
gameport               14952  2 emu10k1_gp
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ohci_pci               13305  0 
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     901140     124296          0      46796     427292
-/+ buffers/cache:     427052     598384
Swap:      2026452          0    2026452
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:37:52 EST 2013: performing suspend
Thu Dec 19 14:38:02 EST 2013: Awake.
Thu Dec 19 14:38:02 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:38:04 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:42:26 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
binfmt_misc            13140  1 
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
rt2800usb              22485  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
rt2x00usb              20041  1 rt2800usb
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800lib              70115  1 rt2800usb
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_emu10k1           141168  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
cfg80211              401436  2 mac80211,rt2x00lib
snd_ac97_codec        105668  1 snd_emu10k1
radeon               1307301  4 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
ttm                    71886  1 radeon
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242354  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
microcode              18830  0 
emu10k1_gp             12541  0 
serio_raw              13189  0 
gameport               14952  2 emu10k1_gp
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ohci_pci               13305  0 
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     935832      89604          0      29684     435192
-/+ buffers/cache:     470956     554480
Swap:      2026452          0    2026452
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:
/etc/pm/sleep.d/20_custom-ehci_hcd: 22: /etc/pm/sleep.d/20_custom-ehci_hcd: cannot create /sys/bus/pci/drivers/ehci_hcd/unbind: Directory nonexistent
/etc/pm/sleep.d/20_custom-ehci_hcd: 22: /etc/pm/sleep.d/20_custom-ehci_hcd: cannot create /sys/bus/pci/drivers/ehci_hcd/unbind: Directory nonexistent
/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: Returned exit code 2.

Thu Dec 19 14:42:26 EST 2013: Inhibit found, will not perform suspend
Thu Dec 19 14:42:26 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Initial commandline parameters: 
Thu Dec 19 14:44:39 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
binfmt_misc            13140  1 
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
rt2800usb              22485  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
rt2x00usb              20041  1 rt2800usb
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800lib              70115  1 rt2800usb
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_emu10k1           141168  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
cfg80211              401436  2 mac80211,rt2x00lib
snd_ac97_codec        105668  1 snd_emu10k1
radeon               1307301  4 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
ttm                    71886  1 radeon
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242354  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
microcode              18830  0 
emu10k1_gp             12541  0 
serio_raw              13189  0 
gameport               14952  2 emu10k1_gp
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ohci_pci               13305  0 
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     935608      89828          0      30088     434324
-/+ buffers/cache:     471196     554240
Swap:      2026452          0    2026452
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:
/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:44:39 EST 2013: performing suspend
Thu Dec 19 14:44:49 EST 2013: Awake.
Thu Dec 19 14:44:49 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:
/etc/pm/sleep.d/20_custom-ehci_hcd resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:44:51 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:44:56 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
binfmt_misc            13140  1 
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
rt2800usb              22485  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
rt2x00usb              20041  1 rt2800usb
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800lib              70115  1 rt2800usb
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_emu10k1           141168  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
cfg80211              401436  2 mac80211,rt2x00lib
snd_ac97_codec        105668  1 snd_emu10k1
radeon               1307301  4 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
ttm                    71886  1 radeon
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242354  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
microcode              18830  0 
emu10k1_gp             12541  0 
serio_raw              13189  0 
gameport               14952  2 emu10k1_gp
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ohci_pci               13305  0 
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     936624      88812          0      29928     425208
-/+ buffers/cache:     481488     543948
Swap:      2026452          0    2026452
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:
/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:44:56 EST 2013: performing suspend
Thu Dec 19 14:45:06 EST 2013: Awake.
Thu Dec 19 14:45:06 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:
/etc/pm/sleep.d/20_custom-ehci_hcd resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:45:08 EST 2013: Finished.
Initial commandline parameters: 
Thu Dec 19 14:47:52 EST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux scott875-desktop 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
e1000                 128369  0 
e100                   35945  0 
mii                    13654  1 e100
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323622  10 bnep,rfcomm
binfmt_misc            13140  1 
gpio_ich               13229  0 
arc4                   12536  2 
ppdev                  17391  0 
rt2800usb              22485  0 
snd_emu10k1_synth      13007  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
rt2x00usb              20041  1 rt2800usb
snd_seq_midi_emul      13432  1 snd_emux_synth
rt2800lib              70115  1 rt2800usb
snd_seq_virmidi        13220  1 snd_emux_synth
rt2x00lib              48854  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              513247  3 rt2x00lib,rt2x00usb,rt2800lib
snd_emu10k1           141168  3 snd_emu10k1_synth
snd_util_mem           13821  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  2 snd_emux_synth,snd_emu10k1
cfg80211              401436  2 mac80211,rt2x00lib
snd_ac97_codec        105668  1 snd_emu10k1
radeon               1307301  4 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  2 snd_ac97_codec,snd_emu10k1
crc_ccitt              12627  1 rt2800lib
snd_page_alloc         14230  2 snd_pcm,snd_emu10k1
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25094  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq                55383  5 snd_seq_midi_event,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi
snd_seq_device         14137  5 snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi
snd_timer              24447  3 snd_pcm,snd_seq,snd_emu10k1
ttm                    71886  1 radeon
snd                    60790  17 snd_ac97_codec,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_device,snd_seq_midi_emul,snd_seq_midi
drm_kms_helper         46867  1 radeon
soundcore              12600  1 snd
drm                   242354  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
microcode              18830  0 
emu10k1_gp             12541  0 
serio_raw              13189  0 
gameport               14952  2 emu10k1_gp
lpc_ich                16864  0 
shpchp                 32129  0 
intel_rng              12700  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ohci_pci               13305  0 
floppy                 55378  0 
             total       used       free     shared    buffers     cached
Mem:       1025436     928224      97212          0      28896     386172
-/+ buffers/cache:     513156     512280
Swap:      2026452          0    2026452
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
Unloading kernel module e1000...Done.
Unloading kernel module e100...Done.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Thu Dec 19 14:47:53 EST 2013: performing suspend
Thu Dec 19 14:48:02 EST 2013: Awake.
Thu Dec 19 14:48:02 EST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Thu Dec 19 14:48:04 EST 2013: Finished.
```

---

### Post by sdowney717 on 2013-12-19
> Thu Dec 19 14:47:53 EST 2013: performing suspend
Thu Dec 19 14:48:02 EST 2013: Awake.

It gets this Awake command microseconds after performing suspend.

So why is that?

---

### Post by sdowney717 on 2013-12-19
I disabled all usb using acpitool, no go.
I then disabled all, still no fix, it immediately resumes regardless.

```
scott875@scott875-desktop:~$ sudo acpitool -W 1
  Changed status for wakeup device #1 (TANA)

   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. TANA	  S4	*enabled   pci:0000:02:01.0
  2. P0P3	  S4	*disabled  pci:0000:00:1e.0
  3. AC97	  S4	*disabled
  4. USB0	  S3	*disabled  pci:0000:00:1d.0
  5. USB1	  S3	*disabled  pci:0000:00:1d.1
  6. USB2	  S3	*disabled  pci:0000:00:1d.2
  7. USB3	  S3	*disabled  pci:0000:00:1d.3
  8. USB7	  S3	*disabled  pci:0000:00:1d.7
  9. UAR1	  S4	*disabled  pnp:00:06
  10. UAR2	  S4	*disabled  pnp:00:07
  11. SLPB	  S4	*enabled 
scott875@scott875-desktop:~$ 

```

---

### Post by sdowney717 on 2013-12-19
also tried these fixes.

[http://askubuntu.com/questions/152403/how-do-i-make-changes-to-proc-acpi-wakeup-permanent](http://askubuntu.com/questions/152403/how-do-i-make-changes-to-proc-acpi-wakeup-permanent)

I dont think the problem is usb devices as setting them disabled does not make a diff.

---

### Post by Toz on 2013-12-19
Try unloading your rt2800usb module before sleep. Create **/etc/pm/config.d/modules** with the following content:
```
SUSPEND_MODULES=rt2800usb
```

---

### Post by sdowney717 on 2013-12-19
Ok, tried it and does no make a diff.

I also tried blacklisting USB3 module.
[http://ubuntuforums.org/showthread.php?t=1668950](http://ubuntuforums.org/showthread.php?t=1668950)

I upgraded from 13.04
It used to suspend and leave the network unconfigured.
Now it just immediately resumes.:(

---

### Post by Toz on 2013-12-19
> **sdowney717 said:**
> Ok, tried it and does no make a diff.
Anything new in /var/log/pm-suspend.log? Or:
```
cat /var/log/syslog | grep PM:
```

Maybe try the whole process manually:
```
sudo modprobe -r rt2800usb
sudo pm-suspend
```
...and post back any error messages that appear on the terminal window.

On resume, you'll need to:
```
sudo modprobe rt2800usb
```
...to re-enable the module.

---

### Post by sdowney717 on 2013-12-19
```
scott875@scott875-desktop:~$ cat /var/log/syslog | grep PM:
Dec 19 10:14:35 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Dec 19 10:14:35 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e5fff]
Dec 19 10:14:35 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e6000-0x000fffff]
Dec 19 10:14:35 scott875-desktop kernel: [    0.085141] PM: Registering ACPI NVS region [mem 0x3fe30000-0x3fe4149f] (70816 bytes)
Dec 19 10:14:35 scott875-desktop kernel: [    0.085141] PM: Registering ACPI NVS region [mem 0x3ff40000-0x3ffeffff] (720896 bytes)
Dec 19 10:14:35 scott875-desktop kernel: [    0.806277] PM: Hibernation image not present or could not be loaded.
Dec 19 14:06:22 scott875-desktop kernel: [13921.139688] PM: Syncing filesystems ... done.
Dec 19 14:06:22 scott875-desktop kernel: [13921.612781] PM: Preparing system for mem sleep
Dec 19 14:06:31 scott875-desktop kernel: [13922.527517] PM: Entering mem sleep
Dec 19 14:06:31 scott875-desktop kernel: [13922.724092] PM: suspend of devices complete after 196.280 msecs
Dec 19 14:06:31 scott875-desktop kernel: [13922.724364] PM: late suspend of devices complete after 0.267 msecs
Dec 19 14:06:31 scott875-desktop kernel: [13922.804341] PM: noirq suspend of devices complete after 79.973 msecs
Dec 19 14:06:31 scott875-desktop kernel: [13922.804751] PM: Saving platform NVS memory
Dec 19 14:06:31 scott875-desktop kernel: [13922.908400] PM: Restoring platform NVS memory
Dec 19 14:06:31 scott875-desktop kernel: [13923.116266] PM: noirq resume of devices complete after 185.226 msecs
Dec 19 14:06:31 scott875-desktop kernel: [13923.116481] PM: early resume of devices complete after 0.177 msecs
Dec 19 14:06:32 scott875-desktop kernel: [13930.248181] PM: resume of devices complete after 7131.696 msecs
Dec 19 14:06:32 scott875-desktop kernel: [13930.248600] PM: Finishing wakeup.
Dec 19 14:06:54 scott875-desktop kernel: [13952.377628] PM: Syncing filesystems ... done.
Dec 19 14:06:54 scott875-desktop kernel: [13952.477659] PM: Preparing system for mem sleep
Dec 19 14:07:04 scott875-desktop kernel: [13952.665472] PM: Entering mem sleep
Dec 19 14:07:04 scott875-desktop kernel: [13952.859828] PM: suspend of devices complete after 194.059 msecs
Dec 19 14:07:04 scott875-desktop kernel: [13952.860112] PM: late suspend of devices complete after 0.279 msecs
Dec 19 14:07:04 scott875-desktop kernel: [13952.940347] PM: noirq suspend of devices complete after 80.230 msecs
Dec 19 14:07:04 scott875-desktop kernel: [13952.940758] PM: Saving platform NVS memory
Dec 19 14:07:04 scott875-desktop kernel: [13953.044363] PM: Restoring platform NVS memory
Dec 19 14:07:04 scott875-desktop kernel: [13953.196261] PM: noirq resume of devices complete after 127.869 msecs
Dec 19 14:07:04 scott875-desktop kernel: [13953.196474] PM: early resume of devices complete after 0.176 msecs
Dec 19 14:07:04 scott875-desktop kernel: [13960.625622] PM: resume of devices complete after 7429.141 msecs
Dec 19 14:07:04 scott875-desktop kernel: [13960.626148] PM: Finishing wakeup.
Dec 19 14:09:24 scott875-desktop kernel: [14099.945542] PM: Syncing filesystems ... done.
Dec 19 14:09:24 scott875-desktop kernel: [14100.228746] PM: Preparing system for mem sleep
Dec 19 14:09:32 scott875-desktop kernel: [14100.384357] PM: Entering mem sleep
Dec 19 14:09:32 scott875-desktop kernel: [14100.580098] PM: suspend of devices complete after 195.438 msecs
Dec 19 14:09:32 scott875-desktop kernel: [14100.580376] PM: late suspend of devices complete after 0.273 msecs
Dec 19 14:09:32 scott875-desktop kernel: [14100.660345] PM: noirq suspend of devices complete after 79.965 msecs
Dec 19 14:09:32 scott875-desktop kernel: [14100.660759] PM: Saving platform NVS memory
Dec 19 14:09:32 scott875-desktop kernel: [14100.764356] PM: Restoring platform NVS memory
Dec 19 14:09:32 scott875-desktop kernel: [14100.912258] PM: noirq resume of devices complete after 125.259 msecs
Dec 19 14:09:32 scott875-desktop kernel: [14100.912473] PM: early resume of devices complete after 0.178 msecs
Dec 19 14:09:32 scott875-desktop kernel: [14108.104196] PM: resume of devices complete after 7191.718 msecs
Dec 19 14:09:32 scott875-desktop kernel: [14108.104620] PM: Finishing wakeup.
Dec 19 14:14:47 scott875-desktop kernel: [14421.087762] PM: Syncing filesystems ... done.
Dec 19 14:14:47 scott875-desktop kernel: [14421.245181] PM: Preparing system for mem sleep
Dec 19 14:14:55 scott875-desktop kernel: [14421.399432] PM: Entering mem sleep
Dec 19 14:14:55 scott875-desktop kernel: [14421.796084] PM: suspend of devices complete after 396.353 msecs
Dec 19 14:14:55 scott875-desktop kernel: [14421.796365] PM: late suspend of devices complete after 0.276 msecs
Dec 19 14:14:55 scott875-desktop kernel: [14421.876217] PM: noirq suspend of devices complete after 79.848 msecs
Dec 19 14:14:55 scott875-desktop kernel: [14421.876643] PM: Saving platform NVS memory
Dec 19 14:14:55 scott875-desktop kernel: [14421.980338] PM: Restoring platform NVS memory
Dec 19 14:14:55 scott875-desktop kernel: [14422.136265] PM: noirq resume of devices complete after 128.447 msecs
Dec 19 14:14:55 scott875-desktop kernel: [14422.136489] PM: early resume of devices complete after 0.186 msecs
Dec 19 14:14:55 scott875-desktop kernel: [14429.328178] PM: resume of devices complete after 7191.684 msecs
Dec 19 14:14:55 scott875-desktop kernel: [14429.328592] PM: Finishing wakeup.
Dec 19 14:32:25 scott875-desktop kernel: [15477.603105] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Dec 19 14:32:25 scott875-desktop kernel: [15477.603120] PM: Basic memory bitmaps created
Dec 19 14:34:00 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Dec 19 14:34:00 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e5fff]
Dec 19 14:34:00 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e6000-0x000fffff]
Dec 19 14:34:00 scott875-desktop kernel: [    0.085140] PM: Registering ACPI NVS region [mem 0x3fe30000-0x3fe4149f] (70816 bytes)
Dec 19 14:34:00 scott875-desktop kernel: [    0.085140] PM: Registering ACPI NVS region [mem 0x3ff40000-0x3ffeffff] (720896 bytes)
Dec 19 14:34:00 scott875-desktop kernel: [    0.806281] PM: Hibernation image not present or could not be loaded.
Dec 19 14:35:01 scott875-desktop kernel: [   78.662667] PM: Syncing filesystems ... done.
Dec 19 14:35:01 scott875-desktop kernel: [   78.808583] PM: Preparing system for mem sleep
Dec 19 14:35:11 scott875-desktop kernel: [   79.519233] PM: Entering mem sleep
Dec 19 14:35:11 scott875-desktop kernel: [   79.728087] PM: suspend of devices complete after 208.556 msecs
Dec 19 14:35:11 scott875-desktop kernel: [   79.728360] PM: late suspend of devices complete after 0.269 msecs
Dec 19 14:35:11 scott875-desktop kernel: [   79.808338] PM: noirq suspend of devices complete after 79.974 msecs
Dec 19 14:35:11 scott875-desktop kernel: [   79.808748] PM: Saving platform NVS memory
Dec 19 14:35:11 scott875-desktop kernel: [   79.912366] PM: Restoring platform NVS memory
Dec 19 14:35:11 scott875-desktop kernel: [   80.112262] PM: noirq resume of devices complete after 184.541 msecs
Dec 19 14:35:11 scott875-desktop kernel: [   80.112477] PM: early resume of devices complete after 0.178 msecs
Dec 19 14:35:11 scott875-desktop kernel: [   87.240176] PM: resume of devices complete after 7127.694 msecs
Dec 19 14:35:11 scott875-desktop kernel: [   87.240583] PM: Finishing wakeup.
Dec 19 14:37:53 scott875-desktop kernel: [  248.484623] PM: Syncing filesystems ... done.
Dec 19 14:37:53 scott875-desktop kernel: [  248.631353] PM: Preparing system for mem sleep
Dec 19 14:38:02 scott875-desktop kernel: [  249.179448] PM: Entering mem sleep
Dec 19 14:38:02 scott875-desktop kernel: [  249.326607] PM: suspend of devices complete after 146.863 msecs
Dec 19 14:38:02 scott875-desktop kernel: [  249.326888] PM: late suspend of devices complete after 0.276 msecs
Dec 19 14:38:02 scott875-desktop kernel: [  249.404348] PM: noirq suspend of devices complete after 77.456 msecs
Dec 19 14:38:02 scott875-desktop kernel: [  249.404760] PM: Saving platform NVS memory
Dec 19 14:38:02 scott875-desktop kernel: [  249.508333] PM: Restoring platform NVS memory
Dec 19 14:38:02 scott875-desktop kernel: [  249.656258] PM: noirq resume of devices complete after 125.344 msecs
Dec 19 14:38:02 scott875-desktop kernel: [  249.656473] PM: early resume of devices complete after 0.178 msecs
Dec 19 14:38:02 scott875-desktop kernel: [  256.840176] PM: resume of devices complete after 7183.697 msecs
Dec 19 14:38:02 scott875-desktop kernel: [  256.840599] PM: Finishing wakeup.
Dec 19 14:44:40 scott875-desktop kernel: [  654.125746] PM: Syncing filesystems ... done.
Dec 19 14:44:40 scott875-desktop kernel: [  654.300423] PM: Preparing system for mem sleep
Dec 19 14:44:49 scott875-desktop kernel: [  654.647315] PM: Entering mem sleep
Dec 19 14:44:49 scott875-desktop kernel: [  654.793092] PM: suspend of devices complete after 145.483 msecs
Dec 19 14:44:49 scott875-desktop kernel: [  654.793373] PM: late suspend of devices complete after 0.277 msecs
Dec 19 14:44:49 scott875-desktop kernel: [  654.872352] PM: noirq suspend of devices complete after 78.975 msecs
Dec 19 14:44:49 scott875-desktop kernel: [  654.872768] PM: Saving platform NVS memory
Dec 19 14:44:49 scott875-desktop kernel: [  654.976341] PM: Restoring platform NVS memory
Dec 19 14:44:49 scott875-desktop kernel: [  655.124268] PM: noirq resume of devices complete after 125.374 msecs
Dec 19 14:44:49 scott875-desktop kernel: [  655.124485] PM: early resume of devices complete after 0.179 msecs
Dec 19 14:44:49 scott875-desktop kernel: [  662.320264] PM: resume of devices complete after 7195.773 msecs
Dec 19 14:44:49 scott875-desktop kernel: [  662.320685] PM: Finishing wakeup.
Dec 19 14:44:57 scott875-desktop kernel: [  669.648054] PM: Syncing filesystems ... done.
Dec 19 14:44:57 scott875-desktop kernel: [  669.804980] PM: Preparing system for mem sleep
Dec 19 14:45:06 scott875-desktop kernel: [  670.027452] PM: Entering mem sleep
Dec 19 14:45:06 scott875-desktop kernel: [  670.186948] PM: suspend of devices complete after 159.205 msecs
Dec 19 14:45:06 scott875-desktop kernel: [  670.187224] PM: late suspend of devices complete after 0.271 msecs
Dec 19 14:45:06 scott875-desktop kernel: [  670.264358] PM: noirq suspend of devices complete after 77.130 msecs
Dec 19 14:45:06 scott875-desktop kernel: [  670.264767] PM: Saving platform NVS memory
Dec 19 14:45:06 scott875-desktop kernel: [  670.368385] PM: Restoring platform NVS memory
Dec 19 14:45:06 scott875-desktop kernel: [  670.516266] PM: noirq resume of devices complete after 125.222 msecs
Dec 19 14:45:06 scott875-desktop kernel: [  670.516481] PM: early resume of devices complete after 0.178 msecs
Dec 19 14:45:06 scott875-desktop kernel: [  677.704205] PM: resume of devices complete after 7187.719 msecs
Dec 19 14:45:06 scott875-desktop kernel: [  677.704633] PM: Finishing wakeup.
Dec 19 14:47:53 scott875-desktop kernel: [  844.241346] PM: Syncing filesystems ... done.
Dec 19 14:47:53 scott875-desktop kernel: [  844.399455] PM: Preparing system for mem sleep
Dec 19 14:48:02 scott875-desktop kernel: [  844.679488] PM: Entering mem sleep
Dec 19 14:48:02 scott875-desktop kernel: [  844.828230] PM: suspend of devices complete after 148.441 msecs
Dec 19 14:48:02 scott875-desktop kernel: [  844.828507] PM: late suspend of devices complete after 0.272 msecs
Dec 19 14:48:02 scott875-desktop kernel: [  844.908357] PM: noirq suspend of devices complete after 79.845 msecs
Dec 19 14:48:02 scott875-desktop kernel: [  844.908771] PM: Saving platform NVS memory
Dec 19 14:48:02 scott875-desktop kernel: [  845.012367] PM: Restoring platform NVS memory
Dec 19 14:48:02 scott875-desktop kernel: [  845.164269] PM: noirq resume of devices complete after 127.882 msecs
Dec 19 14:48:02 scott875-desktop kernel: [  845.164483] PM: early resume of devices complete after 0.176 msecs
Dec 19 14:48:02 scott875-desktop kernel: [  852.352210] PM: resume of devices complete after 7187.722 msecs
Dec 19 14:48:02 scott875-desktop kernel: [  852.352627] PM: Finishing wakeup.
Dec 19 15:07:49 scott875-desktop kernel: [ 2038.847295] PM: Syncing filesystems ... done.
Dec 19 15:07:49 scott875-desktop kernel: [ 2038.974155] PM: Preparing system for mem sleep
Dec 19 15:07:58 scott875-desktop kernel: [ 2039.537645] PM: Entering mem sleep
Dec 19 15:07:58 scott875-desktop kernel: [ 2039.704090] PM: suspend of devices complete after 166.142 msecs
Dec 19 15:07:58 scott875-desktop kernel: [ 2039.704369] PM: late suspend of devices complete after 0.275 msecs
Dec 19 15:07:58 scott875-desktop kernel: [ 2039.784217] PM: noirq suspend of devices complete after 79.845 msecs
Dec 19 15:07:58 scott875-desktop kernel: [ 2039.784643] PM: Saving platform NVS memory
Dec 19 15:07:58 scott875-desktop kernel: [ 2039.888366] PM: Restoring platform NVS memory
Dec 19 15:07:58 scott875-desktop kernel: [ 2040.040265] PM: noirq resume of devices complete after 127.837 msecs
Dec 19 15:07:58 scott875-desktop kernel: [ 2040.040478] PM: early resume of devices complete after 0.176 msecs
Dec 19 15:07:58 scott875-desktop kernel: [ 2047.232185] PM: resume of devices complete after 7191.701 msecs
Dec 19 15:07:58 scott875-desktop kernel: [ 2047.232592] PM: Finishing wakeup.
Dec 19 15:08:44 scott875-desktop kernel: [ 2092.383530] PM: Syncing filesystems ... done.
Dec 19 15:08:44 scott875-desktop kernel: [ 2092.540656] PM: Preparing system for mem sleep
Dec 19 15:08:53 scott875-desktop kernel: [ 2092.855565] PM: Entering mem sleep
Dec 19 15:08:53 scott875-desktop kernel: [ 2092.997753] PM: suspend of devices complete after 141.891 msecs
Dec 19 15:08:53 scott875-desktop kernel: [ 2092.998028] PM: late suspend of devices complete after 0.270 msecs
Dec 19 15:08:53 scott875-desktop kernel: [ 2093.076218] PM: noirq suspend of devices complete after 78.186 msecs
Dec 19 15:08:53 scott875-desktop kernel: [ 2093.076637] PM: Saving platform NVS memory
Dec 19 15:08:53 scott875-desktop kernel: [ 2093.180332] PM: Restoring platform NVS memory
Dec 19 15:08:53 scott875-desktop kernel: [ 2093.328259] PM: noirq resume of devices complete after 125.271 msecs
Dec 19 15:08:53 scott875-desktop kernel: [ 2093.328475] PM: early resume of devices complete after 0.178 msecs
Dec 19 15:08:53 scott875-desktop kernel: [ 2100.536190] PM: resume of devices complete after 7207.710 msecs
Dec 19 15:08:53 scott875-desktop kernel: [ 2100.536592] PM: Finishing wakeup.
Dec 19 15:11:44 scott875-desktop kernel: [ 2271.002186] PM: Syncing filesystems ... done.
Dec 19 15:11:44 scott875-desktop kernel: [ 2271.158559] PM: Preparing system for mem sleep
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.407516] PM: Entering mem sleep
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.569428] PM: suspend of devices complete after 161.613 msecs
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.569691] PM: late suspend of devices complete after 0.259 msecs
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.648226] PM: noirq suspend of devices complete after 78.531 msecs
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.648656] PM: Saving platform NVS memory
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.752364] PM: Restoring platform NVS memory
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.904270] PM: noirq resume of devices complete after 127.860 msecs
Dec 19 15:11:54 scott875-desktop kernel: [ 2271.904480] PM: early resume of devices complete after 0.173 msecs
Dec 19 15:11:54 scott875-desktop kernel: [ 2279.080191] PM: resume of devices complete after 7175.706 msecs
Dec 19 15:11:54 scott875-desktop kernel: [ 2279.080585] PM: Finishing wakeup.
Dec 19 15:23:32 scott875-desktop kernel: [ 2976.862224] PM: Syncing filesystems ... done.
Dec 19 15:23:32 scott875-desktop kernel: [ 2976.986498] PM: Preparing system for mem sleep
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.170074] PM: Entering mem sleep
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.364104] PM: suspend of devices complete after 193.735 msecs
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.364368] PM: late suspend of devices complete after 0.259 msecs
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.444216] PM: noirq suspend of devices complete after 79.844 msecs
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.444645] PM: Saving platform NVS memory
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.548357] PM: Restoring platform NVS memory
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.696253] PM: noirq resume of devices complete after 126.385 msecs
Dec 19 15:23:41 scott875-desktop kernel: [ 2977.696463] PM: early resume of devices complete after 0.173 msecs
Dec 19 15:23:41 scott875-desktop kernel: [ 2984.880170] PM: resume of devices complete after 7183.701 msecs
Dec 19 15:23:41 scott875-desktop kernel: [ 2984.880567] PM: Finishing wakeup.
Dec 19 15:40:09 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Dec 19 15:40:09 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e5fff]
Dec 19 15:40:09 scott875-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e6000-0x000fffff]
Dec 19 15:40:09 scott875-desktop kernel: [    0.081142] PM: Registering ACPI NVS region [mem 0x3fe30000-0x3fe4149f] (70816 bytes)
Dec 19 15:40:09 scott875-desktop kernel: [    0.081142] PM: Registering ACPI NVS region [mem 0x3ff40000-0x3ffeffff] (720896 bytes)
Dec 19 15:40:09 scott875-desktop kernel: [    0.802293] PM: Hibernation image not present or could not be loaded.
Dec 19 15:40:51 scott875-desktop kernel: [   67.081027] PM: Syncing filesystems ... done.
Dec 19 15:40:51 scott875-desktop kernel: [   67.245955] PM: Preparing system for mem sleep
Dec 19 15:41:01 scott875-desktop kernel: [   67.639361] PM: Entering mem sleep
Dec 19 15:41:01 scott875-desktop kernel: [   67.796383] PM: suspend of devices complete after 156.730 msecs
Dec 19 15:41:01 scott875-desktop kernel: [   67.796646] PM: late suspend of devices complete after 0.259 msecs
Dec 19 15:41:01 scott875-desktop kernel: [   67.876348] PM: noirq suspend of devices complete after 79.698 msecs
Dec 19 15:41:01 scott875-desktop kernel: [   67.876761] PM: Saving platform NVS memory
Dec 19 15:41:01 scott875-desktop kernel: [   67.980372] PM: Restoring platform NVS memory
Dec 19 15:41:01 scott875-desktop kernel: [   68.188269] PM: noirq resume of devices complete after 185.419 msecs
Dec 19 15:41:01 scott875-desktop kernel: [   68.188479] PM: early resume of devices complete after 0.172 msecs
Dec 19 15:41:01 scott875-desktop kernel: [   75.320176] PM: resume of devices complete after 7131.692 msecs
Dec 19 15:41:01 scott875-desktop kernel: [   75.320576] PM: Finishing wakeup.
Dec 19 15:45:57 scott875-desktop kernel: [  370.475741] PM: Syncing filesystems ... done.
Dec 19 15:45:57 scott875-desktop kernel: [  370.760367] PM: Preparing system for mem sleep
Dec 19 15:46:06 scott875-desktop kernel: [  371.175261] PM: Entering mem sleep
Dec 19 15:46:06 scott875-desktop kernel: [  371.317776] PM: suspend of devices complete after 142.219 msecs
Dec 19 15:46:06 scott875-desktop kernel: [  371.318042] PM: late suspend of devices complete after 0.262 msecs
Dec 19 15:46:06 scott875-desktop kernel: [  371.396347] PM: noirq suspend of devices complete after 78.301 msecs
Dec 19 15:46:06 scott875-desktop kernel: [  371.396756] PM: Saving platform NVS memory
Dec 19 15:46:06 scott875-desktop kernel: [  371.500341] PM: Restoring platform NVS memory
Dec 19 15:46:06 scott875-desktop kernel: [  371.648258] PM: noirq resume of devices complete after 127.850 msecs
Dec 19 15:46:06 scott875-desktop kernel: [  371.648468] PM: early resume of devices complete after 0.173 msecs
Dec 19 15:46:07 scott875-desktop kernel: [  378.840176] PM: resume of devices complete after 7191.702 msecs
Dec 19 15:46:07 scott875-desktop kernel: [  378.840595] PM: Finishing wakeup.
scott875@scott875-desktop:~$ 

```

---

### Post by sdowney717 on 2013-12-19
> scott875@scott875-desktop:~$ sudo modprobe -r rt2800usb
[sudo] password for scott875: 
scott875@scott875-desktop:~$ sudo pm-suspend
scott875@scott875-desktop:~$ 

tried this and still the same

no errors showing up.
When it resumes it is like instantaneous right after sleep.

---

### Post by Toz on 2013-12-19
Probably barking up the wrong tree then. 

Can you try the script from [this post]("http://ubuntuforums.org/showthread.php?t=1969615&p=11904554&viewfull=1#post11904554") to see if unbinding your uhci ports solves the problem?

---

### Post by sdowney717 on 2013-12-20
I tried that script and also this one '8_disable_USB.sh '

still nothing.

I will try booting from liveusb drive and see if it shuts down.
If it does, then will a new install clear up this?

---

### Post by sdowney717 on 2013-12-20
I found out part of the problem.:D
I removed an add on USB-firewire pci card.
Now it suspends!
And stays off.

The pci card is an ALi with 3 usb and 2 firewires and a plug for remote usb.

Remove card and it works fine.
I would have liked to keep the card, is there something about this card I can disable regarding sleep?

---

### Post by sdowney717 on 2013-12-20
ULi in red is the problem!

```
scott875@scott875-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
[B][COLOR="#FF0000"]03:01.0 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
03:01.1 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
03:01.2 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
03:01.3 USB controller: ULi Electronics Inc. USB 2.0 Controller (rev 01)
03:01.4 FireWire (IEEE 1394): ULi Electronics Inc. M5253 P1394 OHCI 1.1 Controller[/COLOR][/B]
03:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
03:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
03:06.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Rage XL PCI (rev 27)
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)
scott875@scott875-desktop:~$ 
```

with ALi card
```
scott875@scott875-desktop:~$ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. TANA	  S4	*enabled   pci:0000:02:01.0
  2. P0P3	  S4	*disabled  pci:0000:00:1e.0
  3. AC97	  S4	*disabled
  4. USB0	  S3	*enabled   pci:0000:00:1d.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.1
  6. USB2	  S3	*enabled   pci:0000:00:1d.2
  7. USB3	  S3	*enabled   pci:0000:00:1d.3
  8. USB7	  S3	*enabled   pci:0000:00:1d.7
  9. UAR1	  S4	*disabled  pnp:00:06
  10. UAR2	  S4	*disabled  pnp:00:07
  11. SLPB	  S4	*enabled 
```


without ALi card
```
scott875@scott875-desktop:~$ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. TANA	  S4	*enabled   pci:0000:02:01.0
  2. P0P3	  S4	*disabled  pci:0000:00:1e.0
  3. AC97	  S4	*disabled
  4. USB0	  S3	*enabled   pci:0000:00:1d.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.1
  6. USB2	  S3	*enabled   pci:0000:00:1d.2
  7. USB3	  S3	*enabled   pci:0000:00:1d.3
  8. USB7	  S3	*enabled   pci:0000:00:1d.7
  9. UAR1	  S4	*disabled  pnp:00:06
  10. UAR2	  S4	*disabled  pnp:00:07
  11. SLPB	  S4	*enabled 
scott875@scott875-desktop:~$ 

```

acpitool shows no diff with or without card

---

### Post by sdowney717 on 2013-12-20
"ALI chipset based PCI cards require that PCI power management be disabled in the BIOS (the problem of their system constantly rebooting once the card is installed)"

[http://iogear.custhelp.com/app/answers/detail/a_id/2436/~/usb-2.0-pci-cards%3A-sleep-support](http://iogear.custhelp.com/app/answers/detail/a_id/2436/~/usb-2.0-pci-cards%3A-sleep-support)

Think that is the problem?

---

### Post by sdowney717 on 2013-12-20
"PCI power management be disabled in the BIOS "
On this intel server board, I go into the bios and under power, the only option is s1 or s3 states, and wake on lan.
There are no options to turn off PCI power management that I can see.

Any thoughts?

driver issue with ACPI?

[http://download.intel.com/support/motherboards/server/s875wp1-e/sb/s875wp1tps.pdf](http://download.intel.com/support/motherboards/server/s875wp1-e/sb/s875wp1tps.pdf)

> 3.6.1 Advanced Configuration and Power Interface (ACPI) 
ACPI gives the operating system direct control over the power management and Plug and Play 
functions of a computer. The use of ACPI with the Intel Server Board S875WP1-E requires an 
operating system that provides full ACPI support. ACPI features include: 
12 Plug and Play (including bus and device enumeration) 
13 Power management control of individual devices, [B]add-in boards (some add-in boards 
may require an ACPI-aware driver[/B]), video displays, and hard disk drives 
14 Methods for achieving less than 15-watt system operation in the standby or 
sleeping state 
15 A Soft-off feature that enables the operating system to power-off the computer 
16 Support for multiple wake-up events (see Table 7) 
• Support for a front panel power and sleep mode switch 

pg25 says
> . PCI devices for example, are not configured by ACPI.

maybe so out of luck with using this card.?

> The server board supports the PCI Bus Power Management Interface Specification. Add-in 
boards that also support this specification can participate in power management and can be 
used to wake the computer. 
The use of Instantly Available PC technology requires operating system support and PCI 2.2 
compliant add-in cards and drivers. 


screenshot of the page showing the ACPI settings

---

### Post by Toz on 2013-12-20
> firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ohci_pci               13305  0 
What happens if you unload the firewire modules prior to suspend. Start first with:
```
sudo modprobe -r ohci_pci
sudo pm-suspend
.... (and on resume)
sudo modprobe ohci_pci
```

If that doesn't work, try unloading them all:
```
sudo modprobe -r crc_itu_t firewire_core firewire_ohci ohci_pci
sudo pm-suspend
.... (and on resume)
sudo modprobe ohci_pci firewire_ohci firewire_core crc_itu_t
```

---

### Post by sdowney717 on 2013-12-20
ok, I will try it.
I put that card in an xp box and it immediately resumes on suspend.
I will put it into a win7 box and see what it does.

---

### Post by sdowney717 on 2013-12-20
> scott875@scott875-desktop:~$ sudo modprobe -r ohci_pci
[sudo] password for scott875: 
scott875@scott875-desktop:~$ sudo pm-suspend
scott875@scott875-desktop:~$ sudo modprobe ohci_pci
scott875@scott875-desktop:~$ sudo modprobe -r crc_itu_t firewire_core firewire_ohci ohci_pci
FATAL: Module crc_itu_t is in use.
scott875@scott875-desktop:~$ sudo modprobe -r crc_itu_t firewire_core firewire_ohci ohci_pci
FATAL: Module crc_itu_t is in use.
scott875@scott875-desktop:~$ sudo modprobe -r  firewire_core firewire_ohci ohci_pci
FATAL: Module firewire_core is in use.
scott875@scott875-desktop:~$ sudo modprobe -r   firewire_ohci ohci_pciscott875@scott875-desktop:~$ sudo pm-suspend
scott875@scott875-desktop:~$ 



did not work, also says those other modules are in use

win7 box also immediate resume.
These PC are all the same except for running differing OS's

---

### Post by Toz on 2013-12-20
> **sdowney717 said:**
> "ALI chipset based PCI cards require that PCI power management be disabled in the BIOS (the problem of their system constantly rebooting once the card is installed)"

[http://iogear.custhelp.com/app/answers/detail/a_id/2436/~/usb-2.0-pci-cards%3A-sleep-support](http://iogear.custhelp.com/app/answers/detail/a_id/2436/~/usb-2.0-pci-cards%3A-sleep-support)

Think that is the problem?

This might just be the reason why its not working.

---

