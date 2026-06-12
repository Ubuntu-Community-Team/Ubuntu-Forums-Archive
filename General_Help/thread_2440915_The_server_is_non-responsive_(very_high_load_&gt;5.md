---
title: "The server is non-responsive (very high load &gt;500)"
date: 2020-04-16
forum: General Help
---

### Post by kk-ase-tcs on 2020-04-16
[COLOR=#000000][FONT=Helvetica]Apr 15 05:05:01 gamma10 CRON[21603]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:05:01 gamma10 CRON[21604]: (root) CMD (/usr/sbin/icsisnap /var/lib/icsisnap)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:04 gamma10 systemd[1]: Started Session 2262 of user hsiangchiah.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:55 gamma10 kernel: [329549.452881] VTestDriver[22371]: segfault at 7f36922e8000 ip 000000000082f856 sp 00007f36922b5e50 error 6[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:55 gamma10 kernel: [329549.453514] VTestDriver[22372]: segfault at 7f3b84224000 ip 000000000082f856 sp 00007f3b841f1e50 error 6 in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:55 gamma10 kernel: [329549.454107] VTestDriver[22370]: segfault at 7fbdf11d0000 ip 000000000082f856 sp 00007fbdf119de50 error 6 in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:55 gamma10 kernel: [329549.461554] VTestDriver[22373]: segfault at 7f2246274000 ip 000000000082f856 sp 00007f2246241e50 error 6 in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:55 gamma10 kernel: [329549.503127]  in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:56 gamma10 kernel: [329549.784338] VTestDriver[22465]: segfault at 7f54fcdfa000 ip 000000000082f856 sp 00007f54fcdc7e50 error 6[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:56 gamma10 kernel: [329549.784793] VTestDriver[22466]: segfault at 7faa79506000 ip 000000000082f856 sp 00007faa794d3e50 error 6 in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:56 gamma10 kernel: [329549.800526] VTestDriver[22493]: segfault at 7f18c5ab3000 ip 000000000082f856 sp 00007f18c5a80e50 error 6 in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:56 gamma10 kernel: [329549.820944]  in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:56 gamma10 kernel: [329549.829486] VTestDriver[22508]: segfault at 7f8bab53a000 ip 000000000082f856 sp 00007f8bab507e50 error 6 in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:06:56 gamma10 kernel: [329550.075417] VTestDriver[22533]: segfault at 7fbbe4933000 ip 000000000082f856 sp 00007fbbe4900e50 error 6 in VTestDriver[400000+e0b000][/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:07:09 gamma10 systemd[1]: Started Session 2263 of user hsiangchiah.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:01 gamma10 CRON[22663]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329731.939142] ------------[ cut here ]------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329731.945643] kernel BUG at /build/linux-tLcfih/linux-4.4.0/mm/memory.c:3214![/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329731.954454] invalid opcode: 0000 [#4] SMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329731.960421] Modules linked in: rpcsec_gss_krb5 auth_rpcgss nfsv4 nfs lockd grace fscache 8021q garp stp mrp llc binfmt_misc intel_rapl joydev input_leds x86_pkg_temp_thermal intel_powerclamp ipmi_ssif coretemp kvm_intel kvm irqbypass sb_edac mei_me ipmi_si shpchp lpc_ich edac_core mei ioatdma mac_hid 8250_fintek ipmi_msghandler acpi_power_meter acpi_pad tcp_htcp ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi sunrpc scsi_transport_iscsi autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear mlx4_en vxlan ip6_udp_tunnel udp_tunnel ast ttm drm_kms_helper syscopyarea igb crct10dif_pclmul crc32_pclmul sysfillrect ghash_clmulni_intel sysimgblt fb_sys_fops aesni_intel dca aes_x86_64 lrw ptp gf128mul glue_helper hid_generic ablk_helper cryptd usbhid drm ahci pps_core hid i2c_algo_bit mlx4_core libahci wmi fjes[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.059868] CPU: 1 PID: 22693 Comm: gdb Tainted: G      D         4.4.0-171-generic #200-Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.070684] Hardware name: Silicon Mechanics Rackform_R308.v6/X10DRL-i, BIOS 2.0a 08/25/2016[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.081263] task: ffff880645edb800 ti: ffff8801173c4000 task.ti: ffff8801173c4000[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.090905] RIP: 0010:[<ffffffff811ce9ee>]  [<ffffffff811ce9ee>] handle_mm_fault+0x13de/0x1b80[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.101732] RSP: 0018:ffff8801173c7be0  EFLAGS: 00010246[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.109237] RAX: 0000000000000100 RBX: 0000000000000000 RCX: 0000000000000320[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.118579] RDX: ffff88010d972550 RSI: 00003ffffffff000 RDI: 0000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.127921] RBP: ffff8801173c7ca0 R08: 00003ffffdf31320 R09: 00000000000000aa[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.137265] R10: ffff880000000550 R11: 0000000000000550 R12: ffff88010643e578

Apr 15 05:09:58 gamma10 kernel: [329731.945643] kernel BUG at /build/linux-tLcfih/linux-4.4.0/mm/memory.c:3214!

The servers load increasing rapidly, number of processes are 2000; out of them, many are in D state.


NAME="Ubuntu"
VERSION="16.04.6 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.6 LTS"
VERSION_ID="16.04"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

$ uname -r
4.4.0-171-generic
[/FONT][/COLOR]

---

### Post by kk-ase-tcs on 2020-04-21
[COLOR=#000000][COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329731.945643] kernel BUG at /build/linux-tLcfih/linux-4.4.0/mm/memory.c:3214![/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329731.954454] invalid opcode: 0000 [#4] SMP[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.059868] CPU: 1 PID: 22693 Comm: gdb Tainted: G D 4.4.0-171-generic #200-Ubuntu[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.070684] Hardware name: Silicon Mechanics Rackform_R308.v6/X10DRL-i, BIOS 2.0a 08/25/2016[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.081263] task: ffff880645edb800 ti: ffff8801173c4000 task.ti: ffff8801173c4000[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Helvetica]Apr 15 05:09:58 gamma10 kernel: [329732.090905] RIP: 0010:[<ffffffff811ce9ee>] [<ffffffff811ce9ee>] handle_mm_fault+0x13de/0x1b80

[/FONT][/COLOR][/COLOR][COLOR=#000000][FONT=Helvetica]ernel BUG at /build/linux-tLcfih/linux-4.4.0/mm/memory.c:3214!
[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR][/COLOR][COLOR=#000000][FONT=Helvetica]The servers load increasing rapidly, number of processes are 2000; out of them, many are in D state.

[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Helvetica]Rebooted, running fine. 

Please suggest is this a kernel bug or anything else. Thanks[/FONT][/COLOR][/COLOR]

---

