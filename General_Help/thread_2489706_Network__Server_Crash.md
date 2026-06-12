---
title: "Network / Server Crash"
date: 2023-08-08
forum: General Help
---

### Post by keyin on 2023-08-08
Hello,

our Server crashes (freeze) with the following Call Trace, it happens at random times, but i need a hard reset over BMC to get him Online again

```

Aug  8 03:23:27 dus1 kernel: [239773.230357] ice 0000:85:00.0 irdma0: ICE OICR event notification: oicr = 0x04000003
Aug  8 03:23:27 dus1 kernel: [239773.230365] ice 0000:85:00.0 irdma0: HMC Error
Aug  8 03:23:27 dus1 kernel: [239773.230406] ice 0000:85:00.0 irdma0: Requesting a reset
Aug  8 03:23:27 dus1 kernel: [239773.230408] BUG: scheduling while atomic: swapper/2/0/0x00010000
Aug  8 03:23:27 dus1 kernel: [239773.230447] Modules linked in: xt_tcpudp nft_chain_nat xt_nat nf_nat xt_state xt_conntrack nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 nft_compat nft_counter nf_tables nfnetlink ipmi_ssif intel_rapl_msr intel_rapl_common binfmt_misc edac_mce_amd kvm_amd nls_iso8859_1 irdma kvm i40e ib_uverbs rapl ib_core joydev input_leds hpilo ccp acpi_ipmi k10temp ptdma ipmi_si ipmi_devintf ipmi_msghandler acpi_tad mac_hid acpi_power_meter dm_multipath scsi_dh_rdac scsi_dh_emc sch_fq_codel scsi_dh_alua ramoops reed_solomon efi_pstore ip_tables x_tables autofs4 btrfs blake2b_generic zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear ses enclosure mgag200 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect qede hid_generic sysimgblt crct10dif_pclmul fb_sys_fops crc32_pclmul ghash_clmulni_intel cec rc_core aesni_intel usbhid xhci_pci smartpqi qed crypto_simd drm ice cryptd hid crc8 i2c_piix4 xhci_pci_renesas
Aug  8 03:23:27 dus1 kernel: [239773.230533]  scsi_transport_sas wmi
Aug  8 03:23:27 dus1 kernel: [239773.230538] CPU: 2 PID: 0 Comm: swapper/2 Not tainted 5.15.0-051500-generic #202110312130
Aug  8 03:23:27 dus1 kernel: [239773.230543] Hardware name: HPE ProLiant DL325 Gen10 Plus/ProLiant DL325 Gen10 Plus, BIOS A43 02/10/2022
Aug  8 03:23:27 dus1 kernel: [239773.230545] Call Trace:
Aug  8 03:23:27 dus1 kernel: [239773.230548]  <IRQ>
Aug  8 03:23:27 dus1 kernel: [239773.230551]  show_stack+0x52/0x58
Aug  8 03:23:27 dus1 kernel: [239773.230559]  dump_stack_lvl+0x4a/0x5f
Aug  8 03:23:27 dus1 kernel: [239773.230564]  dump_stack+0x10/0x12
Aug  8 03:23:27 dus1 kernel: [239773.230567]  __schedule_bug.cold+0x4e/0x5c
Aug  8 03:23:27 dus1 kernel: [239773.230573]  __schedule+0x444/0x540
Aug  8 03:23:27 dus1 kernel: [239773.230580]  schedule+0x4e/0xb0
Aug  8 03:23:27 dus1 kernel: [239773.230584]  schedule_preempt_disabled+0xe/0x10
Aug  8 03:23:27 dus1 kernel: [239773.230589]  __mutex_lock.constprop.0+0x480/0x490
Aug  8 03:23:27 dus1 kernel: [239773.230592]  ? dev_printk_emit+0x4e/0x65
Aug  8 03:23:27 dus1 kernel: [239773.230598]  __mutex_lock_slowpath+0x13/0x20
Aug  8 03:23:27 dus1 kernel: [239773.230601]  mutex_lock+0x34/0x40
Aug  8 03:23:27 dus1 kernel: [239773.230603]  device_del+0x3b/0x3f0
Aug  8 03:23:27 dus1 kernel: [239773.230610]  ice_unplug_aux_dev+0x1e/0x40 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.230646]  ice_schedule_reset+0x3b/0xd0 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.230674]  ice_rdma_request_reset+0x21/0x30 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.230703]  irdma_request_reset+0x2f/0x33 [irdma]
Aug  8 03:23:27 dus1 kernel: [239773.230727]  irdma_iidc_event_handler.cold+0xb9/0xd3 [irdma]
Aug  8 03:23:27 dus1 kernel: [239773.230746]  ? find_busiest_group+0x4d/0x190
Aug  8 03:23:27 dus1 kernel: [239773.230755]  ice_send_event_to_aux+0x59/0x70 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.230784]  ice_misc_intr+0x1f7/0x2d0 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.230812]  __handle_irq_event_percpu+0x42/0x160
Aug  8 03:23:27 dus1 kernel: [239773.230817]  handle_irq_event+0x59/0xb0
Aug  8 03:23:27 dus1 kernel: [239773.230821]  handle_edge_irq+0x8c/0x220
Aug  8 03:23:27 dus1 kernel: [239773.230824]  __common_interrupt+0x4b/0xb0
Aug  8 03:23:27 dus1 kernel: [239773.230829]  common_interrupt+0x88/0xa0
Aug  8 03:23:27 dus1 kernel: [239773.230835]  </IRQ>
Aug  8 03:23:27 dus1 kernel: [239773.230836]  asm_common_interrupt+0x1e/0x40
Aug  8 03:23:27 dus1 kernel: [239773.230840] RIP: 0010:cpuidle_enter_state+0xd7/0x3e0
Aug  8 03:23:27 dus1 kernel: [239773.230845] Code: 3d 26 bc 25 4d e8 99 72 73 ff 49 89 c7 0f 1f 44 00 00 31 ff e8 2a 7e 73 ff 80 7d d0 00 0f 85 1d 01 00 00 fb 66 0f 1f 44 00 00 <45> 85 f6 0f 88 29 01 00 00 49 63 d6 48 83 fa 09 0f 87 e4 02 00 00
Aug  8 03:23:27 dus1 kernel: [239773.230848] RSP: 0018:ffff9fbf40157e50 EFLAGS: 00000246
Aug  8 03:23:27 dus1 kernel: [239773.230851] RAX: ffff8abc3eaa8f40 RBX: ffff8a9d4a56f800 RCX: 000000000000001f
Aug  8 03:23:27 dus1 kernel: [239773.230853] RDX: 0000000000000000 RSI: 000000002c39470c RDI: 0000000000000000
Aug  8 03:23:27 dus1 kernel: [239773.230856] RBP: ffff9fbf40157e88 R08: 0000da128e38b1e2 R09: 0000000000000000
Aug  8 03:23:27 dus1 kernel: [239773.230858] R10: 0000000000000001 R11: 071c71c71c71c71c R12: 0000000000000002
Aug  8 03:23:27 dus1 kernel: [239773.230860] R13: ffffffffb4460300 R14: 0000000000000002 R15: 0000da128e38b1e2
Aug  8 03:23:27 dus1 kernel: [239773.230864]  cpuidle_enter+0x2e/0x40
Aug  8 03:23:27 dus1 kernel: [239773.230867]  cpuidle_idle_call+0x132/0x1d0
Aug  8 03:23:27 dus1 kernel: [239773.230870]  do_idle+0x83/0xf0
Aug  8 03:23:27 dus1 kernel: [239773.230873]  cpu_startup_entry+0x20/0x30
Aug  8 03:23:27 dus1 kernel: [239773.230876]  start_secondary+0x127/0x160
Aug  8 03:23:27 dus1 kernel: [239773.230880]  secondary_startup_64_no_verify+0xc2/0xcb
Aug  8 03:23:27 dus1 kernel: [239773.231673] bad: scheduling from the idle thread!
Aug  8 03:23:27 dus1 kernel: [239773.231709] CPU: 2 PID: 0 Comm: swapper/2 Tainted: G        W         5.15.0-051500-generic #202110312130
Aug  8 03:23:27 dus1 kernel: [239773.231713] Hardware name: HPE ProLiant DL325 Gen10 Plus/ProLiant DL325 Gen10 Plus, BIOS A43 02/10/2022
Aug  8 03:23:27 dus1 kernel: [239773.231715] Call Trace:
Aug  8 03:23:27 dus1 kernel: [239773.231717]  <IRQ>
Aug  8 03:23:27 dus1 kernel: [239773.231718]  show_stack+0x52/0x58
Aug  8 03:23:27 dus1 kernel: [239773.231724]  dump_stack_lvl+0x4a/0x5f
Aug  8 03:23:27 dus1 kernel: [239773.231727]  dump_stack+0x10/0x12
Aug  8 03:23:27 dus1 kernel: [239773.231730]  dequeue_task_idle+0x2b/0x50
Aug  8 03:23:27 dus1 kernel: [239773.231734]  dequeue_task+0x41/0x190
Aug  8 03:23:27 dus1 kernel: [239773.231739]  __schedule+0x2dc/0x540
Aug  8 03:23:27 dus1 kernel: [239773.231744]  schedule+0x4e/0xb0
Aug  8 03:23:27 dus1 kernel: [239773.231749]  schedule_preempt_disabled+0xe/0x10
Aug  8 03:23:27 dus1 kernel: [239773.231755]  __mutex_lock.constprop.0+0x263/0x490
Aug  8 03:23:27 dus1 kernel: [239773.231759]  ? dev_printk_emit+0x4e/0x65
Aug  8 03:23:27 dus1 kernel: [239773.231764]  __mutex_lock_slowpath+0x13/0x20
Aug  8 03:23:27 dus1 kernel: [239773.231767]  mutex_lock+0x34/0x40
Aug  8 03:23:27 dus1 kernel: [239773.231769]  device_del+0x3b/0x3f0
Aug  8 03:23:27 dus1 kernel: [239773.231775]  ice_unplug_aux_dev+0x1e/0x40 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.231803]  ice_schedule_reset+0x3b/0xd0 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.231832]  ice_rdma_request_reset+0x21/0x30 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.231860]  irdma_request_reset+0x2f/0x33 [irdma]
Aug  8 03:23:27 dus1 kernel: [239773.231881]  irdma_iidc_event_handler.cold+0xb9/0xd3 [irdma]
Aug  8 03:23:27 dus1 kernel: [239773.231899]  ? find_busiest_group+0x4d/0x190
Aug  8 03:23:27 dus1 kernel: [239773.231906]  ice_send_event_to_aux+0x59/0x70 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.231935]  ice_misc_intr+0x1f7/0x2d0 [ice]
Aug  8 03:23:27 dus1 kernel: [239773.231962]  __handle_irq_event_percpu+0x42/0x160
Aug  8 03:23:27 dus1 kernel: [239773.231967]  handle_irq_event+0x59/0xb0
Aug  8 03:23:27 dus1 kernel: [239773.231972]  handle_edge_irq+0x8c/0x220
Aug  8 03:23:27 dus1 kernel: [239773.231974]  __common_interrupt+0x4b/0xb0
Aug  8 03:23:27 dus1 kernel: [239773.231979]  common_interrupt+0x88/0xa0
Aug  8 03:23:27 dus1 kernel: [239773.231983]  </IRQ>
Aug  8 03:23:27 dus1 kernel: [239773.231985]  asm_common_interrupt+0x1e/0x40
Aug  8 03:23:27 dus1 kernel: [239773.231989] RIP: 0010:cpuidle_enter_state+0xd7/0x3e0
Aug  8 03:23:27 dus1 kernel: [239773.231992] Code: 3d 26 bc 25 4d e8 99 72 73 ff 49 89 c7 0f 1f 44 00 00 31 ff e8 2a 7e 73 ff 80 7d d0 00 0f 85 1d 01 00 00 fb 66 0f 1f 44 00 00 <45> 85 f6 0f 88 29 01 00 00 49 63 d6 48 83 fa 09 0f 87 e4 02 00 00
Aug  8 03:23:27 dus1 kernel: [239773.231995] RSP: 0018:ffff9fbf40157e50 EFLAGS: 00000246
Aug  8 03:23:27 dus1 kernel: [239773.231998] RAX: ffff8abc3eaa8f40 RBX: ffff8a9d4a56f800 RCX: 000000000000001f
Aug  8 03:23:27 dus1 kernel: [239773.232000] RDX: 0000000000000000 RSI: 000000002c39470c RDI: 0000000000000000
Aug  8 03:23:27 dus1 kernel: [239773.232001] RBP: ffff9fbf40157e88 R08: 0000da128e38b1e2 R09: 0000000000000000
Aug  8 03:23:27 dus1 kernel: [239773.232003] R10: 0000000000000001 R11: 071c71c71c71c71c R12: 0000000000000002
Aug  8 03:23:27 dus1 kernel: [239773.232005] R13: ffffffffb4460300 R14: 0000000000000002 R15: 0000da128e38b1e2
Aug  8 03:23:27 dus1 kernel: [239773.232009]  cpuidle_enter+0x2e/0x40
Aug  8 03:23:27 dus1 kernel: [239773.232012]  cpuidle_idle_call+0x132/0x1d0
Aug  8 03:23:27 dus1 kernel: [239773.232015]  do_idle+0x83/0xf0
Aug  8 03:23:27 dus1 kernel: [239773.232018]  cpu_startup_entry+0x20/0x30
Aug  8 03:23:27 dus1 kernel: [239773.232020]  start_secondary+0x127/0x160
Aug  8 03:23:27 dus1 kernel: [239773.232023]  secondary_startup_64_no_verify+0xc2/0xcb
Aug  8 03:23:27 dus1 kernel: [239773.232524] bad: scheduling from the idle thread!
Aug  8 03:23:27 dus1 kernel: [239773.232559] CPU: 2 PID: 0 Comm: swapper/2 Tainted: G        W         5.15.0-051500-generic #202110312130
Aug  8 03:23:27 dus1 kernel: [239773.232563] Hardware name: HPE ProLiant DL325 Gen10 Plus/ProLiant DL325 Gen10 Plus, BIOS A43 02/10/2022
Aug  8 03:23:27 dus1 kernel: [239773.232565] Call Trace:
Aug  8 03:23:27 dus1 kernel: [239773.232566]  <IRQ>
Aug  8 03:23:27 dus1 kernel: [239773.232568]  show_stack+0x52/0x58
Aug  8 03:23:27 dus1 kernel: [239773.232573]  dump_stack_lvl+0x4a/0x5f
Aug  8 03:23:27 dus1 kernel: [239773.232577]  dump_stack+0x10/0x12
Aug  8 03:23:27 dus1 kernel: [239773.232580]  dequeue_task_idle+0x2b/0x50
Aug  8 03:23:27 dus1 kernel: [239773.232583]  dequeue_task+0x41/0x190
Aug  8 03:23:27 dus1 kernel: [239773.232587]  __schedule+0x2dc/0x540
Aug  8 03:23:27 dus1 kernel: [239773.232592]  ? string+0x5c/0xd0
Aug  8 03:23:27 dus1 kernel: [239773.232599]  schedule+0x4e/0xb0
Aug  8 03:23:27 dus1 kernel: [239773.232604]  schedule_timeout+0xfb/0x140
Aug  8 03:23:27 dus1 kernel: [239773.232609]  ? __smp_call_single_queue+0x42/0x50
Aug  8 03:23:27 dus1 kernel: [239773.232613]  ? ttwu_queue_wakelist+0xf4/0x110
Aug  8 03:23:27 dus1 kernel: [239773.232616]  __wait_for_common+0xae/0x150
Aug  8 03:23:27 dus1 kernel: [239773.232621]  ? usleep_range+0x90/0x90
Aug  8 03:23:27 dus1 kernel: [239773.232625]  wait_for_completion+0x24/0x30
Aug  8 03:23:27 dus1 kernel: [239773.232630]  devtmpfs_submit_req+0x75/0x90
Aug  8 03:23:27 dus1 kernel: [239773.232636]  devtmpfs_delete_node+0x61/0x90
Aug  8 03:23:27 dus1 kernel: [239773.232641]  device_del+0x360/0x3f0
Aug  8 03:23:27 dus1 kernel: [239773.232648]  cdev_device_del+0x1a/0x50
Aug  8 03:23:27 dus1 kernel: [239773.232654]  ib_uverbs_remove_one+0x39/0x1c0 [ib_uverbs]
Aug  8 03:23:36 dus1 systemd[1]: Started Checkmk agent (PID 1046/UID 999).
Aug  8 03:23:52 dus1 bird: Netlink: File exists
Aug  8 03:24:52 dus1 bird: Netlink: File exists
Aug  8 03:25:01 dus1 CRON[597235]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Aug  8 03:25:52 dus1 bird: Netlink: File exists

```

OS Used: 22.04.2 LTS
Netowrk-Card Used: E810-C  (Dual 100GiG)
Kernel Used: 5.15.0-051500-generic

UPDATE:
I updated the ICE Driver from intel's website to 1.11.17.1, i will update this Thread if this helps or not

---

### Post by keyin on 2023-08-21
Kernel Upgrade to 6.1.46 Solved The Problem.

---

### Post by TheFu on 2023-08-21
> **keyin said:**
> Kernel Upgrade to 6.1.46 Solved The Problem.

Please mark the thread "SOLVED" using the thread-tools button.  This will save people looking to help troubleshoot time for an already-solved problem.
Thanks for posting the solution.

---

