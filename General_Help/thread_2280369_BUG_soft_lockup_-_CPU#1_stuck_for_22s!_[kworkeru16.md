---
title: "BUG: soft lockup - CPU#1 stuck for 22s! [kworker/u16:5:142]"
date: 2015-05-30
forum: General Help
---

### Post by lvm on 2015-05-30
14.04 32-bit, upgraded kernel from 3.13.0-49 to 3.13.0-53, several minutes after the reboot noticed high wio and syslog was filling with the following:

```

May 30 10:27:04 server rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="997" x-info="http://www.rsyslog.com"] start
May 30 10:27:04 server rsyslogd: rsyslogd's groupid changed to 103
May 30 10:27:04 server rsyslogd: rsyslogd's userid changed to 101
May 30 10:27:04 server kernel: [    0.000000] Initializing cgroup subsys cpuset
May 30 10:27:04 server kernel: [    0.000000] Initializing cgroup subsys cpu
May 30 10:27:04 server kernel: [    0.000000] Initializing cgroup subsys cpuacct
May 30 10:27:04 server kernel: [    0.000000] Linux version 3.13.0-53-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #89-Ubuntu SMP Wed May 20 10:34:28 UTC 2015 (Ubuntu 3.13.0-53.89-generic 3.13.11-ckt19) 

[seemingly normal stuff is skipped]

May 30 10:55:06 server kernel: [ 1702.612692] BUG: soft lockup - CPU#1 stuck for 22s! [kworker/u16:5:142]
May 30 10:55:06 server kernel: [ 1702.612704] Modules linked in: snd_hrtimer pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) cuse dm_crypt bnep rfcomm bluetooth mxm_wmi snd_hda_codec_hdmi kvm_amd kvm serio_raw k10temp snd_hda_codec_realtek snd_hda_intel snd_hda_codec nvidia(POX) snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer drm snd soundcore i2c_piix4 shpchp wmi binfmt_misc mac_hid parport_pc ppdev xfs lp libcrc32c parport raid10 raid1 raid0 multipath linear raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq pata_acpi hid_generic usbhid hid usb_storage tg3 sata_sil24 pata_atiixp firewire_ohci ptp firewire_core pps_core ahci pata_via crc_itu_t libahci ati_agp
May 30 10:55:06 server kernel: [ 1702.612833] CPU: 1 PID: 142 Comm: kworker/u16:5 Tainted: P           OX 3.13.0-53-generic #89-Ubuntu
May 30 10:55:06 server kernel: [ 1702.612839] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./990FX Extreme4, BIOS P1.30 09/13/2011
May 30 10:55:06 server kernel: [ 1702.612854] Workqueue: writeback bdi_writeback_workfn (flush-9:1)
May 30 10:55:06 server kernel: [ 1702.612863] task: efa0ce00 ti: f6030000 task.ti: f6030000
May 30 10:55:06 server kernel: [ 1702.612871] EIP: 0060:[<c165e148>] EFLAGS: 00000286 CPU: 1
May 30 10:55:06 server kernel: [ 1702.612880] EIP is at _raw_spin_unlock_irqrestore+0x18/0x40
May 30 10:55:06 server kernel: [ 1702.612887] EAX: 00000286 EBX: 00000286 ECX: 00000019 EDX: 00000286
May 30 10:55:06 server kernel: [ 1702.612893] ESI: e17b5560 EDI: f26c14a0 EBP: f6031c10 ESP: f6031c0c
May 30 10:55:06 server kernel: [ 1702.612898]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 30 10:55:06 server kernel: [ 1702.612903] CR0: 8005003b CR2: b77ca000 CR3: 01aa6000 CR4: 000007f0
May 30 10:55:06 server kernel: [ 1702.612908] Stack:
May 30 10:55:06 server kernel: [ 1702.612911]  e17b5550 f6031c28 c112bd7e 00000286 f26c14a0 009c8000 f26c14a0 f6031c34
May 30 10:55:06 server kernel: [ 1702.612927]  c112be0d cef88540 f6031cc4 f8910331 f6031c9c 00000003 00000001 00000000
May 30 10:55:06 server kernel: [ 1702.612941]  c29b3200 00000001 01674000 00000000 00000000 f6031e08 009c9000 00000000
May 30 10:55:06 server kernel: [ 1702.612956] Call Trace:
May 30 10:55:06 server kernel: [ 1702.612969]  [<c112bd7e>] __set_page_dirty_nobuffers+0x6e/0xe0
May 30 10:55:06 server kernel: [ 1702.612979]  [<c112be0d>] redirty_page_for_writepage+0x1d/0x20
May 30 10:55:06 server kernel: [ 1702.613046]  [<f8910331>] xfs_vm_writepage+0xa1/0x590 [xfs]
May 30 10:55:06 server kernel: [ 1702.613058]  [<c112af40>] __writepage+0x10/0x40
May 30 10:55:06 server kernel: [ 1702.613067]  [<c112af30>] ? global_dirtyable_memory+0xa0/0xa0
May 30 10:55:06 server kernel: [ 1702.613075]  [<c112b8b3>] write_cache_pages+0x1a3/0x3c0
May 30 10:55:06 server kernel: [ 1702.613084]  [<c112af30>] ? global_dirtyable_memory+0xa0/0xa0
May 30 10:55:06 server kernel: [ 1702.613094]  [<c10b9c99>] ? tick_program_event+0x29/0x30
May 30 10:55:06 server kernel: [ 1702.613104]  [<c112bb03>] generic_writepages+0x33/0x60
May 30 10:55:06 server kernel: [ 1702.613164]  [<f890f3fa>] xfs_vm_writepages+0x3a/0x50 [xfs]
May 30 10:55:06 server kernel: [ 1702.613173]  [<c112ca1a>] do_writepages+0x1a/0x40
May 30 10:55:06 server kernel: [ 1702.613182]  [<c119e90c>] __writeback_single_inode+0x3c/0x1f0
May 30 10:55:06 server kernel: [ 1702.613191]  [<c119f6fd>] writeback_sb_inodes+0x1bd/0x2e0
May 30 10:55:06 server kernel: [ 1702.613201]  [<c119f89c>] __writeback_inodes_wb+0x7c/0xb0
May 30 10:55:06 server kernel: [ 1702.613209]  [<c119fac2>] wb_writeback+0x1f2/0x270
May 30 10:55:06 server kernel: [ 1702.613219]  [<c11a0cc7>] bdi_writeback_workfn+0x177/0x370
May 30 10:55:06 server kernel: [ 1702.613228]  [<c165ace8>] ? __schedule+0x358/0x770
May 30 10:55:06 server kernel: [ 1702.613238]  [<c106eeab>] process_one_work+0x11b/0x3b0
May 30 10:55:06 server kernel: [ 1702.613246]  [<c106fae9>] worker_thread+0xf9/0x380
May 30 10:55:06 server kernel: [ 1702.613254]  [<c106f9f0>] ? rescuer_thread+0x380/0x380
May 30 10:55:06 server kernel: [ 1702.613262]  [<c1075391>] kthread+0xa1/0xc0
May 30 10:55:06 server kernel: [ 1702.613271]  [<c1665877>] ret_from_kernel_thread+0x1b/0x28
May 30 10:55:06 server kernel: [ 1702.613280]  [<c10752f0>] ? kthread_create_on_node+0x140/0x140
May 30 10:55:06 server kernel: [ 1702.613285] Code: 83 e8 01 75 f2 89 c8 89 f2 8d b6 00 00 00 00 eb e1 66 90 55 89 e5 53 3e 8d 74 26 00 89 d3 3e 8d 74 26 00 f0 80 00 02 89 d8 50 9d <8d> 74 26 00 5b 5d c3 90 0f b7 10 f0 80 00 02 f6 40 01 01 74 e7
May 30 10:55:34 server kernel: [ 1730.593783] BUG: soft lockup - CPU#1 stuck for 22s! [kworker/u16:5:142]
May 30 10:55:34 server kernel: [ 1730.593793] Modules linked in: snd_hrtimer pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) cuse dm_crypt bnep rfcomm bluetooth mxm_wmi snd_hda_codec_hdmi kvm_amd kvm serio_raw k10temp snd_hda_codec_realtek snd_hda_intel snd_hda_codec nvidia(POX) snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer drm snd soundcore i2c_piix4 shpchp wmi binfmt_misc mac_hid parport_pc ppdev xfs lp libcrc32c parport raid10 raid1 raid0 multipath linear raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq pata_acpi hid_generic usbhid hid usb_storage tg3 sata_sil24 pata_atiixp firewire_ohci ptp firewire_core pps_core ahci pata_via crc_itu_t libahci ati_agp
May 30 10:55:34 server kernel: [ 1730.593917] CPU: 1 PID: 142 Comm: kworker/u16:5 Tainted: P           OX 3.13.0-53-generic #89-Ubuntu
May 30 10:55:34 server kernel: [ 1730.593923] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./990FX Extreme4, BIOS P1.30 09/13/2011
May 30 10:55:34 server kernel: [ 1730.593937] Workqueue: writeback bdi_writeback_workfn (flush-9:1)
May 30 10:55:34 server kernel: [ 1730.593946] task: efa0ce00 ti: f6030000 task.ti: f6030000
May 30 10:55:34 server kernel: [ 1730.593953] EIP: 0060:[<c165e148>] EFLAGS: 00000286 CPU: 1
May 30 10:55:34 server kernel: [ 1730.593962] EIP is at _raw_spin_unlock_irqrestore+0x18/0x40
May 30 10:55:34 server kernel: [ 1730.593968] EAX: 00000286 EBX: 00000286 ECX: 00000019 EDX: 00000286
May 30 10:55:34 server kernel: [ 1730.593974] ESI: e17b5560 EDI: f26bf1e0 EBP: f6031c10 ESP: f6031c0c
May 30 10:55:34 server kernel: [ 1730.593979]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 30 10:55:34 server kernel: [ 1730.593985] CR0: 8005003b CR2: b77ca000 CR3: 01aa6000 CR4: 000007f0
May 30 10:55:34 server kernel: [ 1730.593989] Stack:
May 30 10:55:34 server kernel: [ 1730.593993]  e17b5550 f6031c28 c112bd7e 00000286 f26bf1e0 010ad000 f26bf1e0 f6031c34
May 30 10:55:34 server kernel: [ 1730.594008]  c112be0d ce489348 f6031cc4 f8910331 f6031c9c 00000001 00000001 000000e0
May 30 10:55:34 server kernel: [ 1730.594022]  ffffff3d 00000001 01674000 00000000 00000000 f6031e08 010ae000 00000000
May 30 10:55:34 server kernel: [ 1730.594036] Call Trace:
May 30 10:55:34 server kernel: [ 1730.594048]  [<c112bd7e>] __set_page_dirty_nobuffers+0x6e/0xe0
May 30 10:55:34 server kernel: [ 1730.594058]  [<c112be0d>] redirty_page_for_writepage+0x1d/0x20
May 30 10:55:34 server kernel: [ 1730.594124]  [<f8910331>] xfs_vm_writepage+0xa1/0x590 [xfs]
May 30 10:55:34 server kernel: [ 1730.594136]  [<c112af40>] __writepage+0x10/0x40
May 30 10:55:34 server kernel: [ 1730.594144]  [<c112af30>] ? global_dirtyable_memory+0xa0/0xa0
May 30 10:55:34 server kernel: [ 1730.594153]  [<c112b8b3>] write_cache_pages+0x1a3/0x3c0
May 30 10:55:34 server kernel: [ 1730.594162]  [<c112af30>] ? global_dirtyable_memory+0xa0/0xa0
May 30 10:55:34 server kernel: [ 1730.594172]  [<c112bb03>] generic_writepages+0x33/0x60
May 30 10:55:34 server kernel: [ 1730.594232]  [<f890f3fa>] xfs_vm_writepages+0x3a/0x50 [xfs]
May 30 10:55:34 server kernel: [ 1730.594241]  [<c112ca1a>] do_writepages+0x1a/0x40
May 30 10:55:34 server kernel: [ 1730.594249]  [<c119e90c>] __writeback_single_inode+0x3c/0x1f0
May 30 10:55:34 server kernel: [ 1730.594258]  [<c119f6fd>] writeback_sb_inodes+0x1bd/0x2e0
May 30 10:55:34 server kernel: [ 1730.594268]  [<c119f89c>] __writeback_inodes_wb+0x7c/0xb0
May 30 10:55:34 server kernel: [ 1730.594276]  [<c119fac2>] wb_writeback+0x1f2/0x270
May 30 10:55:34 server kernel: [ 1730.594286]  [<c11a0cc7>] bdi_writeback_workfn+0x177/0x370
May 30 10:55:34 server kernel: [ 1730.594295]  [<c165ace8>] ? __schedule+0x358/0x770
May 30 10:55:34 server kernel: [ 1730.594305]  [<c106eeab>] process_one_work+0x11b/0x3b0
May 30 10:55:34 server kernel: [ 1730.594313]  [<c106fae9>] worker_thread+0xf9/0x380
May 30 10:55:34 server kernel: [ 1730.594321]  [<c106f9f0>] ? rescuer_thread+0x380/0x380
May 30 10:55:34 server kernel: [ 1730.594329]  [<c1075391>] kthread+0xa1/0xc0
May 30 10:55:34 server kernel: [ 1730.594338]  [<c1665877>] ret_from_kernel_thread+0x1b/0x28
May 30 10:55:34 server kernel: [ 1730.594347]  [<c10752f0>] ? kthread_create_on_node+0x140/0x140
May 30 10:55:34 server kernel: [ 1730.594351] Code: 83 e8 01 75 f2 89 c8 89 f2 8d b6 00 00 00 00 eb e1 66 90 55 89 e5 53 3e 8d 74 26 00 89 d3 3e 8d 74 26 00 f0 80 00 02 89 d8 50 9d <8d> 74 26 00 5b 5d c3 90 0f b7 10 f0 80 00 02 f6 40 01 01 74 e7
May 30 10:55:41 server kernel: [ 1737.161349] INFO: rcu_sched self-detected stall on CPU { 1}  (t=15000 jiffies g=31808 c=31807 q=45949)
May 30 10:55:41 server kernel: [ 1737.161366] sending NMI to all CPUs:
May 30 10:55:41 server kernel: [ 1737.161386] NMI backtrace for cpu 2
May 30 10:55:41 server kernel: [ 1737.161402] CPU: 2 PID: 0 Comm: swapper/2 Tainted: P           OX 3.13.0-53-generic #89-Ubuntu
May 30 10:55:41 server kernel: [ 1737.161410] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./990FX Extreme4, BIOS P1.30 09/13/2011
May 30 10:55:41 server kernel: [ 1737.161417] task: f00f9a00 ti: f0154000 task.ti: f0102000
May 30 10:55:41 server kernel: [ 1737.161425] EIP: 0060:[<c10856bc>] EFLAGS: 00200082 CPU: 2
May 30 10:55:41 server kernel: [ 1737.161437] EIP is at sched_clock_cpu+0xc/0x150
May 30 10:55:41 server kernel: [ 1737.161443] EAX: 00000000 EBX: 00000000 ECX: 00000005 EDX: f00bce00
May 30 10:55:41 server kernel: [ 1737.161448] ESI: f7b83300 EDI: f7b83300 EBP: f0155eb4 ESP: f0155e90
May 30 10:55:41 server kernel: [ 1737.161454]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 30 10:55:41 server kernel: [ 1737.161459] CR0: 8005003b CR2: b1d82000 CR3: 224ba000 CR4: 000007f0
May 30 10:55:41 server kernel: [ 1737.161464] Stack:
May 30 10:55:41 server kernel: [ 1737.161468]  00200082 00000000 f0155f00 c108136e ef896800 00200046 f7b83300 f7b83300
May 30 10:55:41 server kernel: [ 1737.161484]  f7b83300 f0155ec8 c107e5f8 f7b83300 f7b83300 f7b83300 f0155ee4 c107e68d
May 30 10:55:41 server kernel: [ 1737.161498]  00000005 f00bce00 00000000 f7b83300 f7b83300 f0155ef0 c1080f82 f00bce00
May 30 10:55:41 server kernel: [ 1737.161512] Call Trace:
May 30 10:55:41 server kernel: [ 1737.161524]  [<c108136e>] ? set_task_cpu+0x4e/0x140
May 30 10:55:41 server kernel: [ 1737.161534]  [<c107e5f8>] update_rq_clock.part.76+0x18/0x50
May 30 10:55:41 server kernel: [ 1737.161541]  [<c107e68d>] enqueue_task+0x5d/0x70
May 30 10:55:41 server kernel: [ 1737.161549]  [<c1080f82>] activate_task+0x22/0x30
May 30 10:55:41 server kernel: [ 1737.161557]  [<c108129c>] ttwu_do_activate.constprop.87+0x2c/0x60
May 30 10:55:41 server kernel: [ 1737.161565]  [<c1082e4d>] try_to_wake_up+0x12d/0x240
May 30 10:55:41 server kernel: [ 1737.161574]  [<c1082f7f>] wake_up_process+0x1f/0x40
May 30 10:55:41 server kernel: [ 1737.161583]  [<c1061fad>] process_timeout+0xd/0x10
May 30 10:55:41 server kernel: [ 1737.161592]  [<c1061fe0>] call_timer_fn+0x30/0xf0
May 30 10:55:41 server kernel: [ 1737.161600]  [<c108e572>] ? rebalance_domains+0x122/0x240
May 30 10:55:41 server kernel: [ 1737.161610]  [<c1061fa0>] ? ftrace_raw_output_tick_stop+0x60/0x60
May 30 10:55:41 server kernel: [ 1737.161619]  [<c1062fd4>] run_timer_softirq+0x174/0x250
May 30 10:55:41 server kernel: [ 1737.161628]  [<c1061fa0>] ? ftrace_raw_output_tick_stop+0x60/0x60
May 30 10:55:41 server kernel: [ 1737.161636]  [<c105b768>] __do_softirq+0xc8/0x220
May 30 10:55:41 server kernel: [ 1737.161644]  [<c105b6a0>] ? cpu_callback+0x160/0x160
May 30 10:55:41 server kernel: [ 1737.161649]  <IRQ> 
May 30 10:55:41 server kernel: [ 1737.161652]  [<c105bb75>] ? irq_exit+0x95/0xa0
May 30 10:55:41 server kernel: [ 1737.161668]  [<c16660d8>] ? smp_apic_timer_interrupt+0x38/0x50
May 30 10:55:41 server kernel: [ 1737.161677]  [<c165ead4>] ? apic_timer_interrupt+0x34/0x3c
May 30 10:55:41 server kernel: [ 1737.161686]  [<c1045f15>] ? native_safe_halt+0x5/0x10
May 30 10:55:41 server kernel: [ 1737.161695]  [<c1016e4c>] ? default_idle+0x1c/0xa0
May 30 10:55:41 server kernel: [ 1737.161703]  [<c1017576>] ? arch_cpu_idle+0x26/0x30
May 30 10:55:41 server kernel: [ 1737.161712]  [<c10a59e9>] ? cpu_startup_entry+0x1c9/0x210
May 30 10:55:41 server kernel: [ 1737.161721]  [<c103a3bb>] ? setup_APIC_timer+0xab/0x130
May 30 10:55:41 server kernel: [ 1737.161730]  [<c10389a8>] ? start_secondary+0x208/0x2d0
May 30 10:55:41 server kernel: [ 1737.161734] Code: 00 3b 05 c8 96 9b c1 7c c6 c7 05 10 8e 9b c1 01 00 00 00 83 c4 04 5b 5e 5f 5d c3 8d 74 26 00 55 89 e5 57 56 53 89 c3 83 ec 14 9c <58> 8d 74 26 00 f6 c4 02 0f 85 01 01 00 00 8b 15 0c 8e 9b c1 85
May 30 10:55:41 server kernel: [ 1737.161818] NMI backtrace for cpu 1
May 30 10:55:41 server kernel: [ 1737.161829] CPU: 1 PID: 142 Comm: kworker/u16:5 Tainted: P           OX 3.13.0-53-generic #89-Ubuntu
May 30 10:55:41 server kernel: [ 1737.161837] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./990FX Extreme4, BIOS P1.30 09/13/2011
May 30 10:55:41 server kernel: [ 1737.161851] Workqueue: writeback bdi_writeback_workfn (flush-9:1)
May 30 10:55:41 server kernel: [ 1737.161860] task: efa0ce00 ti: f6030000 task.ti: f6030000
May 30 10:55:41 server kernel: [ 1737.161867] EIP: 0060:[<c12fe6c2>] EFLAGS: 00000817 CPU: 1
May 30 10:55:41 server kernel: [ 1737.161876] EIP is at __const_udelay+0x12/0x20
May 30 10:55:41 server kernel: [ 1737.161882] EAX: 6f3fc600 EBX: 00002710 ECX: fffff000 EDX: 0036bc88
May 30 10:55:41 server kernel: [ 1737.161888] ESI: c1943b00 EDI: f7b8c900 EBP: f6031a80 ESP: f6031a80
May 30 10:55:41 server kernel: [ 1737.161893]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 30 10:55:41 server kernel: [ 1737.161898] CR0: 8005003b CR2: b77ca000 CR3: 01aa6000 CR4: 000007f0
May 30 10:55:41 server kernel: [ 1737.161902] Stack:
May 30 10:55:41 server kernel: [ 1737.161906]  f6031a90 c103c775 c1828cad c1943b00 f6031ad8 c10af318 c18392bc 00003a98
May 30 10:55:41 server kernel: [ 1737.161921]  00007c40 00007c3f 0000b37d 00000001 00000000 00000001 00000194 c19b8dcc
May 30 10:55:41 server kernel: [ 1737.161935]  c1943b00 f7b8c900 00000001 efa0ce00 00000000 00000001 f6031aec c1063b9c
May 30 10:55:41 server kernel: [ 1737.161949] Call Trace:
May 30 10:55:41 server kernel: [ 1737.161962]  [<c103c775>] arch_trigger_all_cpu_backtrace+0x55/0x70
May 30 10:55:41 server kernel: [ 1737.161973]  [<c10af318>] rcu_check_callbacks+0x388/0x5a0
May 30 10:55:41 server kernel: [ 1737.161983]  [<c1063b9c>] update_process_times+0x3c/0x60
May 30 10:55:41 server kernel: [ 1737.161992]  [<c10ba2f6>] tick_sched_handle.isra.12+0x26/0x60
May 30 10:55:41 server kernel: [ 1737.162001]  [<c10ba367>] tick_sched_timer+0x37/0x70
May 30 10:55:41 server kernel: [ 1737.162009]  [<c1077d78>] ? __remove_hrtimer+0x38/0x90
May 30 10:55:41 server kernel: [ 1737.162017]  [<c107823f>] __run_hrtimer+0x6f/0x190
May 30 10:55:41 server kernel: [ 1737.162026]  [<c10ba330>] ? tick_sched_handle.isra.12+0x60/0x60
May 30 10:55:41 server kernel: [ 1737.162034]  [<c1078e05>] hrtimer_interrupt+0x1f5/0x2b0
May 30 10:55:41 server kernel: [ 1737.162043]  [<c10821aa>] ? scheduler_tick+0x8a/0xc0
May 30 10:55:41 server kernel: [ 1737.162053]  [<c103a8df>] local_apic_timer_interrupt+0x2f/0x60
May 30 10:55:41 server kernel: [ 1737.162061]  [<c105ba85>] ? irq_enter+0x15/0x70
May 30 10:55:41 server kernel: [ 1737.162071]  [<c16660d3>] smp_apic_timer_interrupt+0x33/0x50
May 30 10:55:41 server kernel: [ 1737.162079]  [<c165ead4>] apic_timer_interrupt+0x34/0x3c
May 30 10:55:41 server kernel: [ 1737.162088]  [<c165e148>] ? _raw_spin_unlock_irqrestore+0x18/0x40
May 30 10:55:41 server kernel: [ 1737.162098]  [<c112bd7e>] __set_page_dirty_nobuffers+0x6e/0xe0
May 30 10:55:41 server kernel: [ 1737.162107]  [<c112be0d>] redirty_page_for_writepage+0x1d/0x20
May 30 10:55:41 server kernel: [ 1737.162179]  [<f8910331>] xfs_vm_writepage+0xa1/0x590 [xfs]
May 30 10:55:41 server kernel: [ 1737.162190]  [<c112af40>] __writepage+0x10/0x40
May 30 10:55:41 server kernel: [ 1737.162199]  [<c112af30>] ? global_dirtyable_memory+0xa0/0xa0
May 30 10:55:41 server kernel: [ 1737.162207]  [<c112b8b3>] write_cache_pages+0x1a3/0x3c0
May 30 10:55:41 server kernel: [ 1737.162216]  [<c112af30>] ? global_dirtyable_memory+0xa0/0xa0
May 30 10:55:41 server kernel: [ 1737.162226]  [<c112bb03>] generic_writepages+0x33/0x60
May 30 10:55:41 server kernel: [ 1737.162284]  [<f890f3fa>] xfs_vm_writepages+0x3a/0x50 [xfs]
May 30 10:55:41 server kernel: [ 1737.162293]  [<c112ca1a>] do_writepages+0x1a/0x40
May 30 10:55:41 server kernel: [ 1737.162301]  [<c119e90c>] __writeback_single_inode+0x3c/0x1f0
May 30 10:55:41 server kernel: [ 1737.162310]  [<c119f6fd>] writeback_sb_inodes+0x1bd/0x2e0
May 30 10:55:41 server kernel: [ 1737.162319]  [<c119f89c>] __writeback_inodes_wb+0x7c/0xb0
May 30 10:55:41 server kernel: [ 1737.162328]  [<c119fac2>] wb_writeback+0x1f2/0x270
May 30 10:55:41 server kernel: [ 1737.162337]  [<c11a0cc7>] bdi_writeback_workfn+0x177/0x370
May 30 10:55:41 server kernel: [ 1737.162347]  [<c165ace8>] ? __schedule+0x358/0x770
May 30 10:55:41 server kernel: [ 1737.162356]  [<c106eeab>] process_one_work+0x11b/0x3b0
May 30 10:55:41 server kernel: [ 1737.162364]  [<c106fae9>] worker_thread+0xf9/0x380
May 30 10:55:41 server kernel: [ 1737.162372]  [<c106f9f0>] ? rescuer_thread+0x380/0x380
May 30 10:55:41 server kernel: [ 1737.162380]  [<c1075391>] kthread+0xa1/0xc0
May 30 10:55:41 server kernel: [ 1737.162389]  [<c1665877>] ret_from_kernel_thread+0x1b/0x28
May 30 10:55:41 server kernel: [ 1737.162398]  [<c10752f0>] ? kthread_create_on_node+0x140/0x140
May 30 10:55:41 server kernel: [ 1737.162402] Code: 76 00 8d bc 27 00 00 00 00 55 89 e5 3e 8d 74 26 00 ff 15 b0 82 96 c1 5d c3 55 89 e5 64 8b 15 1c 9e a9 c1 c1 e0 02 6b d2 3e f7 e2 <8d> 42 01 ff 15 b0 82 96 c1 5d c3 8d 76 00 55 89 e5 3e 8d 74 26
May 30 10:55:41 server kernel: [ 1737.162490] NMI backtrace for cpu 3
May 30 10:55:41 server kernel: [ 1737.162498] INFO: NMI handler (arch_trigger_all_cpu_backtrace_handler) took too long to run: 1.103 msecs
May 30 10:55:41 server kernel: [ 1737.162516] CPU: 3 PID: 0 Comm: swapper/3 Tainted: P           OX 3.13.0-53-generic #89-Ubuntu
May 30 10:55:41 server kernel: [ 1737.162523] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./990FX Extreme4, BIOS P1.30 09/13/2011
May 30 10:55:41 server kernel: [ 1737.162530] task: f00fa700 ti: f017a000 task.ti: f0104000
May 30 10:55:41 server kernel: [ 1737.162537] EIP: 0060:[<c1082e75>] EFLAGS: 00200292 CPU: 3
May 30 10:55:41 server kernel: [ 1737.162548] EIP is at try_to_wake_up+0x155/0x240
May 30 10:55:41 server kernel: [ 1737.162554] EAX: 00000001 EBX: ef0de800 ECX: 00000000 EDX: 00200246
May 30 10:55:41 server kernel: [ 1737.162560] ESI: 00000001 EDI: f7b83300 EBP: f017bf2c ESP: f017bf20
May 30 10:55:41 server kernel: [ 1737.162565]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 30 10:55:41 server kernel: [ 1737.162571] CR0: 8005003b CR2: 9183c000 CR3: 224ba000 CR4: 000007f0
May 30 10:55:41 server kernel: [ 1737.162575] Stack:
May 30 10:55:41 server kernel: [ 1737.162579]  ef0de800 ef3d7ecc 00000100 f017bf38 c1082f7f f017bf9c f017bf40 c1061fad
May 30 10:55:41 server kernel: [ 1737.162596]  f017bf74 c1061fe0 00002f35 00000000 f017bf90 c108e572 00000000 f017bf80
May 30 10:55:41 server kernel: [ 1737.162610]  ef0de800 c1061fa0 f017bf9c ef3d7ecc f0124000 f017bfb0 c1062fd4 00057ced
May 30 10:55:41 server kernel: [ 1737.162624] Call Trace:
May 30 10:55:41 server kernel: [ 1737.162636]  [<c1082f7f>] wake_up_process+0x1f/0x40
May 30 10:55:41 server kernel: [ 1737.162647]  [<c1061fad>] process_timeout+0xd/0x10
May 30 10:55:41 server kernel: [ 1737.162656]  [<c1061fe0>] call_timer_fn+0x30/0xf0
May 30 10:55:41 server kernel: [ 1737.162664]  [<c108e572>] ? rebalance_domains+0x122/0x240
May 30 10:55:41 server kernel: [ 1737.162674]  [<c1061fa0>] ? ftrace_raw_output_tick_stop+0x60/0x60
May 30 10:55:41 server kernel: [ 1737.162683]  [<c1062fd4>] run_timer_softirq+0x174/0x250
May 30 10:55:41 server kernel: [ 1737.162693]  [<c1061fa0>] ? ftrace_raw_output_tick_stop+0x60/0x60
May 30 10:55:41 server kernel: [ 1737.162700]  [<c105b768>] __do_softirq+0xc8/0x220
May 30 10:55:41 server kernel: [ 1737.162709]  [<c105b6a0>] ? cpu_callback+0x160/0x160
May 30 10:55:41 server kernel: [ 1737.162713]  <IRQ> 
May 30 10:55:41 server kernel: [ 1737.162716]  [<c105bb75>] ? irq_exit+0x95/0xa0
May 30 10:55:41 server kernel: [ 1737.162731]  [<c16660d8>] ? smp_apic_timer_interrupt+0x38/0x50
May 30 10:55:41 server kernel: [ 1737.162740]  [<c165ead4>] ? apic_timer_interrupt+0x34/0x3c
May 30 10:55:41 server kernel: [ 1737.162749]  [<c1045f15>] ? native_safe_halt+0x5/0x10
May 30 10:55:41 server kernel: [ 1737.162757]  [<c1016e4c>] ? default_idle+0x1c/0xa0
May 30 10:55:41 server kernel: [ 1737.162765]  [<c1017576>] ? arch_cpu_idle+0x26/0x30
May 30 10:55:41 server kernel: [ 1737.162774]  [<c10a59e9>] ? cpu_startup_entry+0x1c9/0x210
May 30 10:55:41 server kernel: [ 1737.162783]  [<c103a3bb>] ? setup_APIC_timer+0xab/0x130
May 30 10:55:41 server kernel: [ 1737.162791]  [<c10389a8>] ? start_secondary+0x208/0x2d0
May 30 10:55:41 server kernel: [ 1737.162796] Code: e4 ff ff 89 f8 e8 bc b3 5d 00 8b 4d f0 89 f2 89 d8 be 01 00 00 00 e8 1b 9a ff ff 8b 45 ec 8b 55 e8 e8 c0 b2 5d 00 89 f0 83 c4 18 <5b> 5e 5f 5d c3 8d b6 00 00 00 00 ba 00 a3 a9 c1 89 f0 89 55 e4
May 30 10:55:41 server kernel: [ 1737.162882] NMI backtrace for cpu 0
May 30 10:55:41 server kernel: [ 1737.162891] INFO: NMI handler (arch_trigger_all_cpu_backtrace_handler) took too long to run: 1.495 msecs
May 30 10:55:41 server kernel: [ 1737.162909] CPU: 0 PID: 0 Comm: swapper/0 Tainted: P           OX 3.13.0-53-generic #89-Ubuntu
May 30 10:55:41 server kernel: [ 1737.162916] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./990FX Extreme4, BIOS P1.30 09/13/2011
May 30 10:55:41 server kernel: [ 1737.162923] task: c192aa00 ti: c191e000 task.ti: c191e000
May 30 10:55:41 server kernel: [ 1737.162948] EIP: 0060:[<c1045f15>] EFLAGS: 00200286 CPU: 0
May 30 10:55:41 server kernel: [ 1737.162971] EIP is at native_safe_halt+0x5/0x10
May 30 10:55:41 server kernel: [ 1737.162993] EAX: ffffffed EBX: a867b8b7 ECX: 00000000 EDX: 00000000
May 30 10:55:41 server kernel: [ 1737.163012] ESI: 0008f800 EDI: 00000000 EBP: c191ff80 ESP: c191ff80
May 30 10:55:41 server kernel: [ 1737.163033]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 30 10:55:41 server kernel: [ 1737.163052] CR0: 8005003b CR2: b77ca000 CR3: 224ba000 CR4: 000007f0
May 30 10:55:41 server kernel: [ 1737.163069] Stack:
May 30 10:55:41 server kernel: [ 1737.163088]  c191ff94 c1016e4c a867b8b7 0008f800 c191e000 c191ff9c c1017576 c191ffc0
May 30 10:55:41 server kernel: [ 1737.163206]  c10a59e9 00200286 c1a1b888 61f01190 a867b8b7 c1a233a0 0008f800 c1aa8800
May 30 10:55:41 server kernel: [ 1737.163323]  c191ffc8 c164d612 c191ffec c19bfaf1 000000f4 ffffffff ffffffff c19bf575
May 30 10:55:41 server kernel: [ 1737.163358] Call Trace:
May 30 10:55:41 server kernel: [ 1737.163371]  [<c1016e4c>] default_idle+0x1c/0xa0
May 30 10:55:41 server kernel: [ 1737.163380]  [<c1017576>] arch_cpu_idle+0x26/0x30
May 30 10:55:41 server kernel: [ 1737.163390]  [<c10a59e9>] cpu_startup_entry+0x1c9/0x210
May 30 10:55:41 server kernel: [ 1737.163400]  [<c164d612>] rest_init+0x62/0x70
May 30 10:55:41 server kernel: [ 1737.163409]  [<c19bfaf1>] start_kernel+0x3b3/0x3b9
May 30 10:55:41 server kernel: [ 1737.163417]  [<c19bf575>] ? repair_env_string+0x51/0x51
May 30 10:55:41 server kernel: [ 1737.163427]  [<c19bf39c>] i386_start_kernel+0x137/0x13a
May 30 10:55:41 server kernel: [ 1737.163430] Code: bc 27 00 00 00 00 55 89 e5 fa 5d c3 8d 76 00 8d bc 27 00 00 00 00 55 89 e5 fb 5d c3 8d 76 00 8d bc 27 00 00 00 00 55 89 e5 fb f4 <5d> c3 89 f6 8d bc 27 00 00 00 00 55 89 e5 f4 5d c3 8d 76 00 8d
May 30 10:55:41 server kernel: [ 1737.163520] INFO: NMI handler (arch_trigger_all_cpu_backtrace_handler) took too long to run: 2.130 msecs
May 30 10:56:06 server kernel: [ 1762.572180] BUG: soft lockup - CPU#1 stuck for 22s! [kworker/u16:5:142]
May 30 10:56:06 server kernel: [ 1762.572190] Modules linked in: snd_hrtimer pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) cuse dm_crypt bnep rfcomm bluetooth mxm_wmi snd_hda_codec_hdmi kvm_amd kvm serio_raw k10temp snd_hda_codec_realtek snd_hda_intel snd_hda_codec nvidia(POX) snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer drm snd soundcore i2c_piix4 shpchp wmi binfmt_misc mac_hid parport_pc ppdev xfs lp libcrc32c parport raid10 raid1 raid0 multipath linear raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq pata_acpi hid_generic usbhid hid usb_storage tg3 sata_sil24 pata_atiixp firewire_ohci ptp firewire_core pps_core ahci pata_via crc_itu_t libahci ati_agp
May 30 10:56:06 server kernel: [ 1762.572314] CPU: 1 PID: 142 Comm: kworker/u16:5 Tainted: P           OX 3.13.0-53-generic #89-Ubuntu
May 30 10:56:06 server kernel: [ 1762.572320] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./990FX Extreme4, BIOS P1.30 09/13/2011
May 30 10:56:06 server kernel: [ 1762.572334] Workqueue: writeback bdi_writeback_workfn (flush-9:1)
May 30 10:56:06 server kernel: [ 1762.572343] task: efa0ce00 ti: f6030000 task.ti: f6030000
May 30 10:56:06 server kernel: [ 1762.572350] EIP: 0060:[<c112b89f>] EFLAGS: 00000202 CPU: 1
May 30 10:56:06 server kernel: [ 1762.572360] EIP is at write_cache_pages+0x18f/0x3c0
May 30 10:56:06 server kernel: [ 1762.572367] EAX: f62d10d8 EBX: 00000000 ECX: ffffffff EDX: 00000020
May 30 10:56:06 server kernel: [ 1762.572372] ESI: 00000004 EDI: f26a8a00 EBP: f6031d68 ESP: f6031cd8
May 30 10:56:06 server kernel: [ 1762.572378]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 30 10:56:06 server kernel: [ 1762.572383] CR0: 8005003b CR2: b77ca000 CR3: 01aa6000 CR4: 000007f0
May 30 10:56:06 server kernel: [ 1762.572388] Stack:
May 30 10:56:06 server kernel: [ 1762.572391]  00000000 0000000e 00001392 00000000 00000000 00000000 f6031d08 c112af30
May 30 10:56:06 server kernel: [ 1762.572406]  00000221 00001572 9ec06400 f6031e08 0000000e c10b9c99 ffffffff e17b5550
May 30 10:56:06 server kernel: [ 1762.572420]  0000157c 0000000e 00000000 f26a8980 f26a89a0 f26a89c0 f26a89e0 f26a8a00
May 30 10:56:06 server kernel: [ 1762.572433] Call Trace:
May 30 10:56:06 server kernel: [ 1762.572445]  [<c112af30>] ? global_dirtyable_memory+0xa0/0xa0
May 30 10:56:06 server kernel: [ 1762.572456]  [<c10b9c99>] ? tick_program_event+0x29/0x30
May 30 10:56:06 server kernel: [ 1762.572466]  [<c112bb03>] generic_writepages+0x33/0x60
May 30 10:56:06 server kernel: [ 1762.572532]  [<f890f3fa>] xfs_vm_writepages+0x3a/0x50 [xfs]
May 30 10:56:06 server kernel: [ 1762.572542]  [<c112ca1a>] do_writepages+0x1a/0x40
May 30 10:56:06 server kernel: [ 1762.572551]  [<c119e90c>] __writeback_single_inode+0x3c/0x1f0
May 30 10:56:06 server kernel: [ 1762.572560]  [<c119f6fd>] writeback_sb_inodes+0x1bd/0x2e0
May 30 10:56:06 server kernel: [ 1762.572569]  [<c119f89c>] __writeback_inodes_wb+0x7c/0xb0
May 30 10:56:06 server kernel: [ 1762.572578]  [<c119fac2>] wb_writeback+0x1f2/0x270
May 30 10:56:06 server kernel: [ 1762.572587]  [<c11a0cc7>] bdi_writeback_workfn+0x177/0x370
May 30 10:56:06 server kernel: [ 1762.572598]  [<c165ace8>] ? __schedule+0x358/0x770
May 30 10:56:06 server kernel: [ 1762.572608]  [<c106eeab>] process_one_work+0x11b/0x3b0
May 30 10:56:06 server kernel: [ 1762.572615]  [<c106fae9>] worker_thread+0xf9/0x380
May 30 10:56:06 server kernel: [ 1762.572623]  [<c106f9f0>] ? rescuer_thread+0x380/0x380
May 30 10:56:06 server kernel: [ 1762.572632]  [<c1075391>] kthread+0xa1/0xc0
May 30 10:56:06 server kernel: [ 1762.572641]  [<c1665877>] ret_from_kernel_thread+0x1b/0x28
May 30 10:56:06 server kernel: [ 1762.572650]  [<c10752f0>] ? kthread_create_on_node+0x140/0x140
May 30 10:56:06 server kernel: [ 1762.572654] Code: 75 c2 8b 07 a8 10 74 bc 8b 07 f6 c4 20 75 a5 8b 07 f6 c4 20 0f 85 e4 00 00 00 89 f8 e8 9b fd ff ff 85 c0 74 9f 8b 45 ac 8b 40 4c <89> c2 3e 8d 74 26 00 8b 4d 08 89 f8 8b 55 9c 8b 5d 8c ff d3 85

```

Tried to reboot (shutdown -r now) and it locked up, had to powercycle the computer. Booted back to kernel 49 - works fine. Asrock 990FX extereme 4 motherboard, phenom II X4 975 CPU, nvidia GT 240 video, PCI-E Silicon Image 3132 SATA controller, 8 SATA disks in md raid 6 plus one for the system. Previously was clocking uptimes of several months without any issues. Any ideas?

---

### Post by tgalati4 on 2015-05-30
You are running a tainted kernel, which means that there are binary blobs (proprietary drivers such as an nvidia graphics card) that are linked to the kernel.  It's possible that the patch has caused a serious regression.  I would file a bug report against that version of the kernel.  You could try to revert to the nv (open nvidia driver) run that for a while and see if it is stable, then reinstall the proprietary driver.

Unfortunately, using some proprietary drivers will cause this regression cycle for each kernel upgrade.  This is why the word "Tainted" is used throughout the system logs--to alert you to the fact that some issues may be related to the direct linking of these binary blobs to the kernel.

---

