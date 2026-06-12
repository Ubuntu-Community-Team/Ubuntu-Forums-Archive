---
title: "USB mouse not working after resume from suspend"
date: 2014-05-28
forum: General Help
---

### Post by dannyboy79 on 2014-05-28
Running Xubuntu 14.04. When I resume my desktop computer from a suspend, sometimes the mouse won't come back. The lights are completely out on the mouse, it's like it's not receiving any signal from the computer. What I always do is unplug it and plug it back in and that always works but I finally got sick of doing that and finally want to resolve the issue. I googled for a little bit but can't figure out what I need to do. I checked my syslog and see the following for when I put it into suspend mode this morning at 7:15am
```
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> sleep requested (sleeping: no  enabled: yes)
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> sleeping or disabling...
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> (eth2): deactivating device (reason 'sleeping') [37]
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> Removing DNS information from /sbin/resolvconf
May 28 07:15:57 saucy-haswell whoopsie[1307]: offline
May 28 07:15:57 saucy-haswell avahi-daemon[1061]: Withdrawing address record for fe80::d63d:7eff:fee2:273b on eth2.
May 28 07:15:57 saucy-haswell avahi-daemon[1061]: Leaving mDNS multicast group on interface eth2.IPv6 with address fe80::d63d:7eff:fee2:273b.
May 28 07:15:57 saucy-haswell avahi-daemon[1061]: Interface eth2.IPv6 no longer relevant for mDNS.
May 28 07:15:57 saucy-haswell avahi-daemon[1061]: Withdrawing address record for 192.168.0.6 on eth2.
May 28 07:15:57 saucy-haswell avahi-daemon[1061]: Leaving mDNS multicast group on interface eth2.IPv4 with address 192.168.0.6.
May 28 07:15:57 saucy-haswell avahi-daemon[1061]: Interface eth2.IPv4 no longer relevant for mDNS.
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> (eth2): cleaning up...
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> (eth2): taking down device.
May 28 07:15:57 saucy-haswell NetworkManager[1074]: <info> NetworkManager state is now ASLEEP
May 28 07:15:57 saucy-haswell dbus[947]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 28 07:15:57 saucy-haswell dbus[947]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
May 28 07:15:57 saucy-haswell dbus[947]: [system] Successfully activated service 'org.freedesktop.systemd1'
May 28 07:15:57 saucy-haswell dbus[947]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 28 07:15:57 saucy-haswell anacron[11120]: Anacron 2.3 started on 2014-05-28
May 28 07:15:57 saucy-haswell anacron[11120]: Normal exit (0 jobs run)

```

then when I clicked the power button to wake it up, i see the following
```
May 28 16:23:06 saucy-haswell kernel: [34100.472125] PM: Syncing filesystems ... done.
May 28 16:23:06 saucy-haswell kernel: [34100.565196] PM: Preparing system for mem sleep
May 28 16:23:06 saucy-haswell kernel: [34100.565307] Freezing user space processes ... (elapsed 0.001 seconds) done.
May 28 16:23:06 saucy-haswell kernel: [34100.566906] Freezing remaining freezable tasks ... (elapsed 6.367 seconds) done.
May 28 16:23:06 saucy-haswell kernel: [34106.934434] PM: Entering mem sleep
May 28 16:23:06 saucy-haswell kernel: [34106.934481] Suspending console(s) (use no_console_suspend to debug)
May 28 16:23:06 saucy-haswell kernel: [34106.934773] sd 5:0:0:0: [sdd] Synchronizing SCSI cache
May 28 16:23:06 saucy-haswell kernel: [34106.934828] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
May 28 16:23:06 saucy-haswell kernel: [34106.934878] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
May 28 16:23:06 saucy-haswell kernel: [34106.934888] sd 5:0:0:0: [sdd] Stopping disk
May 28 16:23:06 saucy-haswell kernel: [34106.934970] sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 28 16:23:06 saucy-haswell kernel: [34106.935001] sd 1:0:0:0: [sdb] Stopping disk
May 28 16:23:06 saucy-haswell kernel: [34106.936522] sd 3:0:0:0: [sdc] Stopping disk
May 28 16:23:06 saucy-haswell kernel: [34106.941984] sd 0:0:0:0: [sda] Stopping disk
May 28 16:23:06 saucy-haswell kernel: [34106.966031] i8042 kbd 00:09: System wakeup enabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34106.988039] ------------[ cut here ]------------
May 28 16:23:06 saucy-haswell kernel: [34106.988058] WARNING: CPU: 0 PID: 11358 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_pm.c:5834 i915_release_power_well+0x5a/0x60 [i915]()
May 28 16:23:06 saucy-haswell kernel: [34106.988072] Modules linked in: arc4 md4 pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) autofs4 rfcomm bnep bluetooth nfsd auth_rpcgss nfs_acl binfmt_misc nfs lockd sunrpc nls_utf8 cifs fscache joydev xpad ff_memless x86_pkg_temp_thermal snd_usb_audio intel_powerclamp snd_usbmidi_lib uvcvideo kvm_intel videobuf2_vmalloc videobuf2_memops videobuf2_core videodev kvm crct10dif_pclmul nvidia(POF) crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_hda_codec_hdmi snd_hda_codec_realtek serio_raw snd_rawmidi snd_hda_intel snd_hda_codec snd_seq snd_seq_device snd_hwdep snd_pcm mei_me shpchp lpc_ich snd_page_alloc snd_timer mei intel_smartconnect snd soundcore mac_hid parport_pc ppdev coretemp lp parport hid_generic usbhid hid uvesafb i915 mxm_wmi i2c_algo_bit drm_kms_helper ahci r8169 drm libahci mii video wmi
May 28 16:23:06 saucy-haswell kernel: [34106.988077] CPU: 0 PID: 11358 Comm: kworker/u8:23 Tainted: PF       W  O 3.13.0-27-generic #50-Ubuntu
May 28 16:23:06 saucy-haswell kernel: [34106.988077] Hardware name: MSI MS-7850/Z87-G41 PC Mate(MS-7850), BIOS V1.5 12/02/2013
May 28 16:23:06 saucy-haswell kernel: [34106.988079] Workqueue: events_unbound async_run_entry_fn
May 28 16:23:06 saucy-haswell kernel: [34106.988081]  0000000000000009 ffff8800a72efc88 ffffffff817199c4 0000000000000000
May 28 16:23:06 saucy-haswell kernel: [34106.988082]  ffff8800a72efcc0 ffffffff810676bd 0000000000000000 ffff88021ef80000
May 28 16:23:06 saucy-haswell kernel: [34106.988083]  ffff88021ef80098 ffff880223cf9000 0000000000000100 ffff8800a72efcd0
May 28 16:23:06 saucy-haswell kernel: [34106.988083] Call Trace:
May 28 16:23:06 saucy-haswell kernel: [34106.988086]  [<ffffffff817199c4>] dump_stack+0x45/0x56
May 28 16:23:06 saucy-haswell kernel: [34106.988088]  [<ffffffff810676bd>] warn_slowpath_common+0x7d/0xa0
May 28 16:23:06 saucy-haswell kernel: [34106.988089]  [<ffffffff8106779a>] warn_slowpath_null+0x1a/0x20
May 28 16:23:06 saucy-haswell kernel: [34106.988096]  [<ffffffffa011b01a>] i915_release_power_well+0x5a/0x60 [i915]
May 28 16:23:06 saucy-haswell kernel: [34106.988099]  [<ffffffffa02b3e38>] hda_display_power+0x28/0x40 [snd_hda_intel]
May 28 16:23:06 saucy-haswell kernel: [34106.988101]  [<ffffffffa02b112b>] azx_suspend+0x10b/0x160 [snd_hda_intel]
May 28 16:23:06 saucy-haswell kernel: [34106.988103]  [<ffffffff813a62bc>] pci_pm_suspend+0x6c/0x150
May 28 16:23:06 saucy-haswell kernel: [34106.988104]  [<ffffffff813a6250>] ? pci_pm_freeze+0xe0/0xe0
May 28 16:23:06 saucy-haswell kernel: [34106.988106]  [<ffffffff8149a049>] dpm_run_callback+0x49/0xa0
May 28 16:23:06 saucy-haswell kernel: [34106.988107]  [<ffffffff8149a44b>] __device_suspend+0xdb/0x280
May 28 16:23:06 saucy-haswell kernel: [34106.988108]  [<ffffffff8109a66a>] ? try_to_wake_up+0x1fa/0x2c0
May 28 16:23:06 saucy-haswell kernel: [34106.988109]  [<ffffffff8149a60f>] async_suspend+0x1f/0xa0
May 28 16:23:06 saucy-haswell kernel: [34106.988109]  [<ffffffff81091517>] async_run_entry_fn+0x37/0x130
May 28 16:23:06 saucy-haswell kernel: [34106.988111]  [<ffffffff810838a2>] process_one_work+0x182/0x450
May 28 16:23:06 saucy-haswell kernel: [34106.988112]  [<ffffffff81084641>] worker_thread+0x121/0x410
May 28 16:23:06 saucy-haswell kernel: [34106.988113]  [<ffffffff81084520>] ? rescuer_thread+0x3e0/0x3e0
May 28 16:23:06 saucy-haswell kernel: [34106.988114]  [<ffffffff8108b312>] kthread+0xd2/0xf0
May 28 16:23:06 saucy-haswell kernel: [34106.988115]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
May 28 16:23:06 saucy-haswell kernel: [34106.988117]  [<ffffffff8172a2fc>] ret_from_fork+0x7c/0xb0
May 28 16:23:06 saucy-haswell kernel: [34106.988118]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
May 28 16:23:06 saucy-haswell kernel: [34106.988118] ---[ end trace f15a06f7b5212ea1 ]---
May 28 16:23:06 saucy-haswell kernel: [34108.012125] PM: suspend of devices complete after 1077.567 msecs
May 28 16:23:06 saucy-haswell kernel: [34108.012236] PM: late suspend of devices complete after 0.109 msecs
May 28 16:23:06 saucy-haswell kernel: [34108.012400] r8169 0000:03:00.0: System wakeup enabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.028117] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.032113] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.040035] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.044337] PM: noirq suspend of devices complete after 32.098 msecs
May 28 16:23:06 saucy-haswell kernel: [34108.044510] ACPI: Preparing to enter system sleep state S3
May 28 16:23:06 saucy-haswell kernel: [34108.044714] PM: Saving platform NVS memory
May 28 16:23:06 saucy-haswell kernel: [34108.045207] Disabling non-boot CPUs ...
May 28 16:23:06 saucy-haswell kernel: [34108.045389] Broke affinity for irq 41
May 28 16:23:06 saucy-haswell kernel: [34108.045390] Broke affinity for irq 42
May 28 16:23:06 saucy-haswell kernel: [34108.046390] kvm: disabling virtualization on CPU1
May 28 16:23:06 saucy-haswell kernel: [34108.148012] smpboot: CPU 1 is now offline
May 28 16:23:06 saucy-haswell kernel: [34108.148342] Broke affinity for irq 23
May 28 16:23:06 saucy-haswell kernel: [34108.149342] kvm: disabling virtualization on CPU2
May 28 16:23:06 saucy-haswell kernel: [34108.252010] smpboot: CPU 2 is now offline
May 28 16:23:06 saucy-haswell kernel: [34108.252320] Broke affinity for irq 16
May 28 16:23:06 saucy-haswell kernel: [34108.253327] kvm: disabling virtualization on CPU3
May 28 16:23:06 saucy-haswell kernel: [34108.356009] smpboot: CPU 3 is now offline
May 28 16:23:06 saucy-haswell kernel: [34108.356168] ACPI: Low-level resume complete
May 28 16:23:06 saucy-haswell kernel: [34108.356168] PM: Restoring platform NVS memory
May 28 16:23:06 saucy-haswell kernel: [34108.356168] Enabling non-boot CPUs ...
May 28 16:23:06 saucy-haswell kernel: [34108.356168] x86: Booting SMP configuration:
May 28 16:23:06 saucy-haswell kernel: [34108.356168] smpboot: Booting Node 0 Processor 1 APIC 0x2
May 28 16:23:06 saucy-haswell kernel: [34108.356168] kvm: enabling virtualization on CPU1
May 28 16:23:06 saucy-haswell kernel: [34108.368255] CPU1 is up
May 28 16:23:06 saucy-haswell kernel: [34108.368265] smpboot: Booting Node 0 Processor 2 APIC 0x4
May 28 16:23:06 saucy-haswell kernel: [34108.368256] kvm: enabling virtualization on CPU2
May 28 16:23:06 saucy-haswell kernel: [34108.380253] CPU2 is up
May 28 16:23:06 saucy-haswell kernel: [34108.380262] smpboot: Booting Node 0 Processor 3 APIC 0x6
May 28 16:23:06 saucy-haswell kernel: [34108.380254] kvm: enabling virtualization on CPU3
May 28 16:23:06 saucy-haswell kernel: [34108.392247] CPU3 is up
May 28 16:23:06 saucy-haswell kernel: [34108.394579] ACPI: Waking up from system sleep state S3
May 28 16:23:06 saucy-haswell kernel: [34108.400043] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.408048] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.416041] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.452178] PM: noirq resume of devices complete after 57.139 msecs
May 28 16:23:06 saucy-haswell kernel: [34108.452263] PM: early resume of devices complete after 0.070 msecs
May 28 16:23:06 saucy-haswell kernel: [34108.452283] ------------[ cut here ]------------
May 28 16:23:06 saucy-haswell kernel: [34108.452302] WARNING: CPU: 0 PID: 11359 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_pm.c:5817 i915_request_power_well+0x77/0x80 [i915]()
May 28 16:23:06 saucy-haswell kernel: [34108.452313] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
May 28 16:23:06 saucy-haswell kernel: [34108.452317] Modules linked in: arc4 md4 pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) autofs4 rfcomm bnep bluetooth nfsd auth_rpcgss nfs_acl binfmt_misc nfs lockd sunrpc nls_utf8 cifs fscache joydev xpad ff_memless x86_pkg_temp_thermal snd_usb_audio intel_powerclamp snd_usbmidi_lib uvcvideo kvm_intel videobuf2_vmalloc videobuf2_memops videobuf2_core videodev kvm crct10dif_pclmul nvidia(POF) crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event snd_hda_codec_hdmi snd_hda_codec_realtek serio_raw snd_rawmidi snd_hda_intel snd_hda_codec snd_seq snd_seq_device snd_hwdep snd_pcm mei_me shpchp lpc_ich snd_page_alloc snd_timer mei intel_smartconnect snd soundcore mac_hid parport_pc ppdev coretemp lp parport hid_generic usbhid hid uvesafb i915 mxm_wmi i2c_algo_bit drm_kms_helper ahci r8169 drm libahci mii video wmi
May 28 16:23:06 saucy-haswell kernel: [34108.452321] CPU: 0 PID: 11359 Comm: kworker/u8:24 Tainted: PF       W  O 3.13.0-27-generic #50-Ubuntu
May 28 16:23:06 saucy-haswell kernel: [34108.452322] Hardware name: MSI MS-7850/Z87-G41 PC Mate(MS-7850), BIOS V1.5 12/02/2013
May 28 16:23:06 saucy-haswell kernel: [34108.452324] Workqueue: events_unbound async_run_entry_fn
May 28 16:23:06 saucy-haswell kernel: [34108.452325]  0000000000000009 ffff8800a60e1cb0 ffffffff817199c4 0000000000000000
May 28 16:23:06 saucy-haswell kernel: [34108.452326]  ffff8800a60e1ce8 ffffffff810676bd 0000000000000000 ffff880223cf9098
May 28 16:23:06 saucy-haswell kernel: [34108.452327]  ffff88021ef82400 ffffffff81ad38b8 0000000000000100 ffff8800a60e1cf8
May 28 16:23:06 saucy-haswell kernel: [34108.452328] Call Trace:
May 28 16:23:06 saucy-haswell kernel: [34108.452331]  [<ffffffff817199c4>] dump_stack+0x45/0x56
May 28 16:23:06 saucy-haswell kernel: [34108.452332]  [<ffffffff810676bd>] warn_slowpath_common+0x7d/0xa0
May 28 16:23:06 saucy-haswell kernel: [34108.452333]  [<ffffffff8106779a>] warn_slowpath_null+0x1a/0x20
May 28 16:23:06 saucy-haswell kernel: [34108.452341]  [<ffffffffa011dea7>] i915_request_power_well+0x77/0x80 [i915]
May 28 16:23:06 saucy-haswell kernel: [34108.452428] r8169 0000:03:00.0: System wakeup disabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.452435]  [<ffffffffa02b3e42>] hda_display_power+0x32/0x40 [snd_hda_intel]
May 28 16:23:06 saucy-haswell kernel: [34108.452437]  [<ffffffffa02b1be2>] azx_resume+0xe2/0x160 [snd_hda_intel]
May 28 16:23:06 saucy-haswell kernel: [34108.452440]  [<ffffffff813a6024>] pci_pm_resume+0x64/0xb0
May 28 16:23:06 saucy-haswell kernel: [34108.452441]  [<ffffffff813a5fc0>] ? pci_pm_thaw+0xa0/0xa0
May 28 16:23:06 saucy-haswell kernel: [34108.452442]  [<ffffffff8149a049>] dpm_run_callback+0x49/0xa0
May 28 16:23:06 saucy-haswell kernel: [34108.452443]  [<ffffffff8149a1a6>] device_resume+0xc6/0x1f0
May 28 16:23:06 saucy-haswell kernel: [34108.452444]  [<ffffffff8149a2ed>] async_resume+0x1d/0x50
May 28 16:23:06 saucy-haswell kernel: [34108.452445]  [<ffffffff81091517>] async_run_entry_fn+0x37/0x130
May 28 16:23:06 saucy-haswell kernel: [34108.452446]  [<ffffffff810838a2>] process_one_work+0x182/0x450
May 28 16:23:06 saucy-haswell kernel: [34108.452448]  [<ffffffff81084641>] worker_thread+0x121/0x410
May 28 16:23:06 saucy-haswell kernel: [34108.452449]  [<ffffffff81084520>] ? rescuer_thread+0x3e0/0x3e0
May 28 16:23:06 saucy-haswell kernel: [34108.452450]  [<ffffffff8108b312>] kthread+0xd2/0xf0
May 28 16:23:06 saucy-haswell kernel: [34108.452451]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
May 28 16:23:06 saucy-haswell kernel: [34108.452453]  [<ffffffff8172a2fc>] ret_from_fork+0x7c/0xb0
May 28 16:23:06 saucy-haswell kernel: [34108.452454]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
May 28 16:23:06 saucy-haswell kernel: [34108.452455] ---[ end trace f15a06f7b5212ea2 ]---
May 28 16:23:06 saucy-haswell kernel: [34108.460078] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
May 28 16:23:06 saucy-haswell kernel: [34108.460168] snd_hda_intel 0000:00:03.0: irq 46 for MSI/MSI-X
May 28 16:23:06 saucy-haswell kernel: [34108.460274] i8042 kbd 00:09: System wakeup disabled by ACPI
May 28 16:23:06 saucy-haswell kernel: [34108.788047] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
May 28 16:23:06 saucy-haswell kernel: [34108.792059] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
May 28 16:23:06 saucy-haswell kernel: [34108.792493] ata1.00: supports DRM functions and may not be fully accessible
May 28 16:23:06 saucy-haswell kernel: [34108.795437] ata1.00: disabling queued TRIM support
May 28 16:23:06 saucy-haswell kernel: [34108.798980] ata1.00: supports DRM functions and may not be fully accessible
May 28 16:23:06 saucy-haswell kernel: [34108.801872] ata1.00: disabling queued TRIM support
May 28 16:23:06 saucy-haswell kernel: [34108.805148] ata1.00: configured for UDMA/133
May 28 16:23:06 saucy-haswell kernel: [34108.805246] sd 0:0:0:0: [sda] Starting disk
May 28 16:23:06 saucy-haswell kernel: [34108.809622] ata4.00: configured for UDMA/133
May 28 16:23:06 saucy-haswell kernel: [34108.810140] sd 3:0:0:0: [sdc] Starting disk
May 28 16:23:06 saucy-haswell kernel: [34108.872245] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34108.872391] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34109.076160] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34109.280038] usb 3-1: device not accepting address 2, error -71
May 28 16:23:06 saucy-haswell kernel: [34109.392121] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34109.392245] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34109.596160] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34109.800039] usb 3-1: device not accepting address 2, error -71
May 28 16:23:06 saucy-haswell kernel: [34109.912129] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34109.912253] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34110.116159] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34110.320039] usb 3-1: device not accepting address 2, error -71
May 28 16:23:06 saucy-haswell kernel: [34110.432119] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34110.432243] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34110.636157] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34110.840051] usb 3-1: device not accepting address 2, error -71
May 28 16:23:06 saucy-haswell kernel: [34110.952229] usb 3-3: reset high-speed USB device number 3 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34111.092243] usb 3-7: reset full-speed USB device number 4 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34111.110252] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021efc3900
May 28 16:23:06 saucy-haswell kernel: [34111.110253] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021efc3940
May 28 16:23:06 saucy-haswell kernel: [34111.110253] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036379a00
May 28 16:23:06 saucy-haswell kernel: [34111.110254] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036379a40
May 28 16:23:06 saucy-haswell kernel: [34111.110254] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036379ac0
May 28 16:23:06 saucy-haswell kernel: [34111.110255] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036379a80
May 28 16:23:06 saucy-haswell kernel: [34111.110256] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021e867680
May 28 16:23:06 saucy-haswell kernel: [34111.183884] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021e867440
May 28 16:23:06 saucy-haswell kernel: [34111.183885] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88022203f400
May 28 16:23:06 saucy-haswell kernel: [34112.436046] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 28 16:23:06 saucy-haswell kernel: [34112.437044] ata6.00: LPM support broken, forcing max_power
May 28 16:23:06 saucy-haswell kernel: [34112.437060] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
May 28 16:23:06 saucy-haswell kernel: [34112.437062] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff8802240e2aa0), AE_NOT_FOUND (20131115/psparse-536)
May 28 16:23:06 saucy-haswell kernel: [34112.438157] ata6.00: LPM support broken, forcing max_power
May 28 16:23:06 saucy-haswell kernel: [34112.438169] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
May 28 16:23:06 saucy-haswell kernel: [34112.438171] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff8802240e2aa0), AE_NOT_FOUND (20131115/psparse-536)
May 28 16:23:06 saucy-haswell kernel: [34112.438173] ata6.00: configured for UDMA/100
May 28 16:23:06 saucy-haswell kernel: [34112.438260] sd 5:0:0:0: [sdd] Starting disk
May 28 16:23:06 saucy-haswell kernel: [34113.832049] ata2: link is slow to respond, please be patient (ready=0)
May 28 16:23:06 saucy-haswell kernel: [34115.400043] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 28 16:23:06 saucy-haswell kernel: [34115.429202] ata2.00: configured for UDMA/100
May 28 16:23:06 saucy-haswell kernel: [34115.429266] sd 1:0:0:0: [sdb] Starting disk
May 28 16:23:06 saucy-haswell kernel: [34115.431257] PM: resume of devices complete after 6978.991 msecs
May 28 16:23:06 saucy-haswell kernel: [34115.431316] input: Afterglow Gamepad for Xbox 360 as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/input/input21
May 28 16:23:06 saucy-haswell kernel: [34116.595481] usb_audio: Warning! Unlikely big volume range (=6144), cval->res is probably wrong.
May 28 16:23:06 saucy-haswell kernel: [34116.595830] usb_audio: [5] FU [Mic Capture Volume] ch = 1, val = 1536/7680/1
May 28 16:23:06 saucy-haswell kernel: [34116.595830] PM: Finishing wakeup.
May 28 16:23:06 saucy-haswell acpid: client 1388[0:0] has disconnected
May 28 16:23:06 saucy-haswell pulseaudio[2296]: [alsa-source-USB Audio] alsa-util.c: Got POLLNVAL from ALSA
May 28 16:23:06 saucy-haswell pulseaudio[2296]: [alsa-source-USB Audio] alsa-util.c: Could not recover from POLLERR|POLLNVAL|POLLHUP with snd_pcm_prepare(): No such device
May 28 16:23:06 saucy-haswell kernel: [34116.600705] usb 3-1: USB disconnect, device number 2
May 28 16:23:06 saucy-haswell kernel: [34116.604612] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021e981c40
May 28 16:23:06 saucy-haswell kernel: [34116.604614] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88021e981e80
May 28 16:23:06 saucy-haswell kernel: [34116.605536] r8169 0000:03:00.0: no hotplug settings from platform
May 28 16:23:06 saucy-haswell kernel: [34116.605625] pci_bus 0000:05: Allocating resources
May 28 16:23:06 saucy-haswell kernel: [34116.605638] pci 0000:04:00.0: PCI bridge to [bus 05]
May 28 16:23:06 saucy-haswell kernel: [34116.605641] pci 0000:04:00.0:   bridge window [io  0x3000-0x3fff]
May 28 16:23:06 saucy-haswell kernel: [34116.605648] pci 0000:04:00.0:   bridge window [mem 0xcf600000-0xcf7fffff]
May 28 16:23:06 saucy-haswell kernel: [34116.605652] pci 0000:04:00.0:   bridge window [mem 0xcf800000-0xcf9fffff 64bit pref]
May 28 16:23:06 saucy-haswell kernel: [34116.605664] pci 0000:04:00.0: no hotplug settings from platform
May 28 16:23:06 saucy-haswell kernel: [34116.595831] Restarting tasks ... done.
May 28 16:23:06 saucy-haswell kernel: [34116.612515] video LNXVIDEO:00: Restoring backlight state
May 28 02:35:46 saucy-haswell rtkit-daemon[1641]: message repeated 4 times: [ Recovering from system lockup, not allowing further RT threads.]
May 28 16:23:06 saucy-haswell rtkit-daemon[1641]: Successfully made thread 11527 of process 2296 (n/a) owned by '1000' RT at priority 5.
May 28 16:23:06 saucy-haswell rtkit-daemon[1641]: Supervising 1 threads of 1 processes of 1 users.
May 28 16:23:06 saucy-haswell anacron[11583]: Anacron 2.3 started on 2014-05-28
May 28 16:23:06 saucy-haswell anacron[11583]: Normal exit (0 jobs run)
May 28 16:23:06 saucy-haswell kernel: [34116.716026] usb 3-1: new full-speed USB device number 6 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34116.716139] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell anacron[11663]: Anacron 2.3 started on 2014-05-28
May 28 16:23:06 saucy-haswell anacron[11663]: Normal exit (0 jobs run)
May 28 16:23:06 saucy-haswell acpid: client connected from 1388[0:0]
May 28 16:23:06 saucy-haswell acpid: 1 client rule loaded
May 28 16:23:06 saucy-haswell NetworkManager[1074]: <info> wake requested (sleeping: yes  enabled: yes)
May 28 16:23:06 saucy-haswell NetworkManager[1074]: <info> waking up and re-enabling...
May 28 16:23:06 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 28 16:23:06 saucy-haswell NetworkManager[1074]: <info> (eth2): bringing up device.
May 28 16:23:06 saucy-haswell NetworkManager[1074]: <info> (eth2): preparing device.
May 28 16:23:06 saucy-haswell NetworkManager[1074]: <info> (eth2): deactivating device (reason 'managed') [2]
May 28 16:23:06 saucy-haswell NetworkManager[1074]: <info> NetworkManager state is now DISCONNECTED
May 28 16:23:06 saucy-haswell kernel: [34116.862095] r8169 0000:03:00.0 eth2: link down
May 28 16:23:06 saucy-haswell kernel: [34116.862111] r8169 0000:03:00.0 eth2: link down
May 28 16:23:06 saucy-haswell kernel: [34116.862151] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
May 28 16:23:06 saucy-haswell kernel: [34116.920208] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34117.124075] usb 3-1: device not accepting address 6, error -71
May 28 16:23:06 saucy-haswell kernel: [34117.236172] usb 3-1: new full-speed USB device number 7 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34117.236344] usb 3-1: Device not responding to set address.
May 28 16:23:06 saucy-haswell kernel: [34117.440192] usb 3-1: Device not responding to set address.
May 28 16:23:07 saucy-haswell kernel: [34117.644037] usb 3-1: device not accepting address 7, error -71
May 28 16:23:07 saucy-haswell kernel: [34117.756092] usb 3-1: new full-speed USB device number 8 using xhci_hcd
May 28 16:23:07 saucy-haswell kernel: [34117.756213] usb 3-1: Device not responding to set address.
May 28 16:23:07 saucy-haswell kernel: [34117.960238] usb 3-1: Device not responding to set address.
May 28 16:23:07 saucy-haswell kernel: [34118.164051] usb 3-1: device not accepting address 8, error -71
May 28 16:23:07 saucy-haswell kernel: [34118.276160] usb 3-1: new full-speed USB device number 9 using xhci_hcd
May 28 16:23:07 saucy-haswell kernel: [34118.276329] usb 3-1: Device not responding to set address.
May 28 16:23:08 saucy-haswell kernel: [34118.480113] usb 3-1: Device not responding to set address.
May 28 16:23:08 saucy-haswell kernel: [34118.684053] usb 3-1: device not accepting address 9, error -71
May 28 16:23:08 saucy-haswell kernel: [34118.684109] hub 3-0:1.0: unable to enumerate USB device on port 1
May 28 16:23:09 saucy-haswell kernel: [34120.079922] r8169 0000:03:00.0 eth2: link up
May 28 16:23:09 saucy-haswell kernel: [34120.079929] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> (eth2): carrier now ON (device state 20)
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Auto-activating connection 'Wired connection 1'.
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) starting connection 'Wired connection 1'
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> NetworkManager state is now CONNECTING
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) started...
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) starting...
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: prepare -> config (reason 'none') [40 50 0]
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) successful.
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled.
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) complete.
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 3 of 5 (IP Configure Start) started...
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: config -> ip-config (reason 'none') [50 70 0]
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Beginning IP6 addrconf.
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
May 28 16:23:09 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) started...
May 28 16:23:09 saucy-haswell avahi-daemon[1061]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.0.6.
May 28 16:23:09 saucy-haswell avahi-daemon[1061]: New relevant interface eth2.IPv4 for mDNS.
May 28 16:23:09 saucy-haswell avahi-daemon[1061]: Registering new address record for 192.168.0.6 on eth2.IPv4.
May 28 16:23:10 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May 28 16:23:10 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) complete.
May 28 16:23:10 saucy-haswell NetworkManager[1074]: <info> (eth2): device state change: secondaries -> activated (reason 'none') [90 100 0]
May 28 16:23:10 saucy-haswell NetworkManager[1074]: <info> NetworkManager state is now CONNECTED_GLOBAL
May 28 16:23:10 saucy-haswell NetworkManager[1074]: <info> Policy set 'Wired connection 1' (eth2) as default for IPv4 routing and DNS.
May 28 16:23:10 saucy-haswell NetworkManager[1074]: <info> Writing DNS information to /sbin/resolvconf
May 28 16:23:10 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) successful, device activated.
May 28 16:23:10 saucy-haswell dbus[947]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 28 16:23:10 saucy-haswell dbus[947]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 28 16:23:11 saucy-haswell avahi-daemon[1061]: Joining mDNS multicast group on interface eth2.IPv6 with address fe80::d63d:7eff:fee2:273b.
May 28 16:23:11 saucy-haswell avahi-daemon[1061]: New relevant interface eth2.IPv6 for mDNS.
May 28 16:23:11 saucy-haswell avahi-daemon[1061]: Registering new address record for fe80::d63d:7eff:fee2:273b on eth2.*.
May 28 16:23:10 saucy-haswell whoopsie[1307]: message repeated 5 times: [ offline]
May 28 16:23:11 saucy-haswell whoopsie[1307]: online
May 28 16:23:17 saucy-haswell ntpdate[11838]: adjust time server 91.189.94.4 offset 0.486845 sec
May 28 16:23:29 saucy-haswell NetworkManager[1074]: <info> (eth2): IP6 addrconf timed out or failed.
May 28 16:23:29 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 28 16:23:29 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 28 16:23:29 saucy-haswell NetworkManager[1074]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

Can anyone help me figure out what I must do so that when I wake from suspend my USB mouse also resumes without me having to unplug it and plug it back in.

---

### Post by dannyboy79 on 2014-05-28
Apparently I found my own solution, so I can document it for others here goes. 
> May 28 16:23:06 saucy-haswell kernel: [34116.716026] usb 3-1: new full-speed USB device number 6 using xhci_hcd
May 28 16:23:06 saucy-haswell kernel: [34116.716139] usb 3-1: Device not responding to set address.

These 2 lines lead me looking for an answer relating to USB 3.0 i think

First we need to find out what our xhci_hcd identifier is, you can find out by issuing
```
ls /sys/bus/pci/drivers/xhci_hcd/
```
Mine returned
> 0000:00:14.0  bind  module  new_id  remove_id  uevent  unbind

Now that we have that information we just need to add an unbind during suspend and a bind for resuming, that's done by doing the below commands
NOTE: if you have Ubuntu use gedit because that's your default text editor, mine is mousepad since i use Xubuntu
```
gksudo mousepad /etc/pm/sleep.d/20_custom-xhci_hcd
```

Within that file we need to add this code
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".

case "${1}" in
  hibernate|suspend)
    # Unbind xhci_hcd devices
    echo -n "0000:00:14.0" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
  ;;
  resume|thaw)
    # Bind xhci_hcd devices
    echo -n "0000:00:14.0" | tee /sys/bus/pci/drivers/xhci_hcd/bind
  ;;
esac
```

Notice my usb identifiers that we figured out with the first command, make sure those match your result from the first command. Save the file and exit mousepad (or gedit)

Now we just need to make sure the script is executable, that's done by issuing
```
sudo chmod a+x /etc/pm/sleep.d/20_custom-xhci_hcd
```

That's it, now when you resume your USB 3.0 mouse should wake up just fine

---

### Post by wd5gnr2 on 2014-09-27
Thank you! This did the trick on a Lenovo Yoga 2 11. Great work.

Update Well... no... it didn't fix it consistently :(

Still looking for a solution.

---

