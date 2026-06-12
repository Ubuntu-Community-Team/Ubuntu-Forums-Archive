---
title: "NMI watchdog: BUG: soft lockup - CPU#1 stuck for 23s! [qemu-system-x86:1906]"
date: 2017-04-07
forum: General Help
---

### Post by yanghuan2017 on 2017-04-07
OS: ubuntu server 16.04 LTS 64bit
kernel: 4.4.0-62-generic




On my server, I just installed KVM, but it always crashed with cpu soft lock, the syslog like this:


Apr  7 13:55:40 RomensKVM kernel: [74803.333704] NMI watchdog: BUG: soft lockup - CPU#1 stuck for 23s! [qemu-system-x86:1906]
Apr  7 13:55:40 RomensKVM kernel: [74803.333740] Modules linked in: xfrm6_mode_tunnel drbg ansi_cprng seqiv esp4 xfrm4_mode_tunnel xt_nat xt_mark veth xfrm_user xfrm_algo xt_addrtype br_netfilter aufs vhost_net vhost macvtap macvlan xt_CHECKSUM iptable_mangle ipt_MASQUERADE nf_nat_masquerade_ipv4 iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT nf_reject_ipv4 xt_tcpudp ebtable_filter ebtables ip6table_filter ip6_tables iptable_filter ip_tables x_tables ppdev bridge stp llc snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic i915_bpo intel_ips snd_hda_intel intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_hda_codec hci_uart snd_hda_core btbcm btqca btintel kvm_intel bluetooth kvm snd_hwdep acpi_als snd_pcm mei_me ie31200_edac kfifo_buf parport_pc snd_timer edac_core industrialio mei serio_raw parport snd tpm_infineon shpchp irqbypass soundcore mac_hid intel_lpss_acpi intel_lpss 8250_fintek acpi_pad ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr sunrpc iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi coretemp autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid0 multipath linear raid1 nouveau crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel mxm_wmi i2c_algo_bit aes_x86_64 lrw ttm gf128mul glue_helper drm_kms_helper ablk_helper cryptd syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse r8169 ahci drm mii libahci wmi video i2c_hid pinctrl_sunrisepoint pinctrl_intel hid fjes
Apr  7 13:55:40 RomensKVM kernel: [74803.333787] CPU: 1 PID: 1906 Comm: qemu-system-x86 Not tainted 4.4.0-62-generic #83-Ubuntu
Apr  7 13:55:40 RomensKVM kernel: [74803.333788] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./X150M-PLUS WS-CF, BIOS F3 03/30/2016
Apr  7 13:55:40 RomensKVM kernel: [74803.333789] task: ffff88083ea78f00 ti: ffff8800926b0000 task.ti: ffff8800926b0000
Apr  7 13:55:40 RomensKVM kernel: [74803.333790] RIP: 0010:[<ffffffff81104558>]  [<ffffffff81104558>] smp_call_function_single+0xd8/0x130
Apr  7 13:55:40 RomensKVM kernel: [74803.333794] RSP: 0018:ffff8800926b3ae8  EFLAGS: 00000202
Apr  7 13:55:40 RomensKVM kernel: [74803.333795] RAX: 0000000000000000 RBX: 0000000000000002 RCX: 0000000000000000
Apr  7 13:55:40 RomensKVM kernel: [74803.333796] RDX: 0000000000000001 RSI: 00000000000000fb RDI: 0000000000000286
Apr  7 13:55:40 RomensKVM kernel: [74803.333796] RBP: ffff8800926b3b30 R08: ffff8800926b0000 R09: 0000000000000000
Apr  7 13:55:40 RomensKVM kernel: [74803.333797] R10: 00000001011c2343 R11: 0000000000000000 R12: ffffffffc0769d60
Apr  7 13:55:40 RomensKVM kernel: [74803.333797] R13: 0000000000000001 R14: ffff880837732c00 R15: 0000000000000000
Apr  7 13:55:40 RomensKVM kernel: [74803.333798] FS:  00007f5e3d2fa700(0000) GS:ffff880866440000(0000) knlGS:0000000000000000
Apr  7 13:55:40 RomensKVM kernel: [74803.333799] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Apr  7 13:55:40 RomensKVM kernel: [74803.333800] CR2: 00007f328c00e000 CR3: 000000083e7af000 CR4: 00000000003426e0
Apr  7 13:55:40 RomensKVM kernel: [74803.333800] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Apr  7 13:55:40 RomensKVM kernel: [74803.333801] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Apr  7 13:55:40 RomensKVM kernel: [74803.333802] Stack:
Apr  7 13:55:40 RomensKVM kernel: [74803.333802]  0000000000000087 ffff8800926b3b60 0000000000000000 ffffffffc0769d60
Apr  7 13:55:40 RomensKVM kernel: [74803.333803]  ffff88009188c510 0000000000000003 00000000735d0d4c ffff880091888000
Apr  7 13:55:40 RomensKVM kernel: [74803.333805]  0000000000000001 ffff8800926b3c50 ffffffffc0768660 0000000019d8479c
Apr  7 13:55:40 RomensKVM kernel: [74803.333806] Call Trace:
Apr  7 13:55:40 RomensKVM kernel: [74803.333810]  [<ffffffffc0769d60>] ? hardware_enable+0x1a0/0x1a0 [kvm_intel]
Apr  7 13:55:40 RomensKVM kernel: [74803.333813]  [<ffffffffc0768660>] vmx_vcpu_load+0x200/0x2f0 [kvm_intel]
Apr  7 13:55:40 RomensKVM kernel: [74803.333814]  [<ffffffff810b5239>] ? update_curr+0x79/0x160
Apr  7 13:55:40 RomensKVM kernel: [74803.333816]  [<ffffffff810b72eb>] ? dequeue_entity+0x41b/0xa80
Apr  7 13:55:40 RomensKVM kernel: [74803.333826]  [<ffffffffc06cff7b>] kvm_arch_vcpu_load+0x3b/0x220 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333832]  [<ffffffffc06b8699>] kvm_sched_in+0x39/0x40 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333833]  [<ffffffff810a9c86>] finish_task_switch+0x166/0x220
Apr  7 13:55:40 RomensKVM kernel: [74803.333835]  [<ffffffff81833e16>] __schedule+0x3b6/0xa30
Apr  7 13:55:40 RomensKVM kernel: [74803.333843]  [<ffffffffc06f1ba8>] ? kvm_apic_has_interrupt+0x28/0xd0 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333844]  [<ffffffff818344c5>] schedule+0x35/0x80
Apr  7 13:55:40 RomensKVM kernel: [74803.333849]  [<ffffffffc06b9552>] kvm_vcpu_block+0x82/0x2e0 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333851]  [<ffffffff810c41e0>] ? wake_atomic_t_function+0x60/0x60
Apr  7 13:55:40 RomensKVM kernel: [74803.333859]  [<ffffffffc06d5c13>] kvm_arch_vcpu_ioctl_run+0x1b3/0x400 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333864]  [<ffffffffc06bc52d>] kvm_vcpu_ioctl+0x33d/0x620 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333865]  [<ffffffff811036f7>] ? do_futex+0x107/0x540
Apr  7 13:55:40 RomensKVM kernel: [74803.333873]  [<ffffffffc06e7880>] ? check_perm_out+0x50/0x50 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333875]  [<ffffffff812227af>] do_vfs_ioctl+0x29f/0x490
Apr  7 13:55:40 RomensKVM kernel: [74803.333882]  [<ffffffffc06c9706>] ? kvm_on_user_return+0x66/0xa0 [kvm]
Apr  7 13:55:40 RomensKVM kernel: [74803.333883]  [<ffffffff8118af6b>] ? fire_user_return_notifiers+0x3b/0x50
Apr  7 13:55:40 RomensKVM kernel: [74803.333885]  [<ffffffff81222a19>] SyS_ioctl+0x79/0x90
Apr  7 13:55:40 RomensKVM kernel: [74803.333886]  [<ffffffff818385f2>] entry_SYSCALL_64_fastpath+0x16/0x71
Apr  7 13:55:40 RomensKVM kernel: [74803.333887] Code: 25 28 00 00 00 75 70 48 83 c4 38 5b 41 5c 5d c3 48 8d 75 c8 48 89 d1 89 df 4c 89 e2 e8 12 fe ff ff 8b 55 e0 83 e2 01 74 cf f3 90 <8b> 55 e0 83 e2 01 75 f6 eb c3 8b 05 30 81 00 01 85 c0 75 85 80


Is it a kernel bug or Kvm bug? How do I repair it.

---

### Post by TheFu on 2017-04-07
[https://ubuntuforums.org/showthread.php?t=2205211](https://ubuntuforums.org/showthread.php?t=2205211) has some ideas.  Not all of these have the same clear cause.

---

### Post by yanghuan2017 on 2017-04-07
Thanks for your reply.
I have already read this, and I have already change the power supply,but it got the same error.

---

### Post by yanghuan2017 on 2017-04-07
After I disabled the OC, it occurs an other error:

Apr  8 09:55:27 docker kernel: [ 3897.866438] INFO: rcu_bh detected stalls on CPUs/tasks:
Apr  8 09:55:27 docker kernel: [ 3897.867190] 	7-...: (1 GPs behind) idle=3e5/1/0 softirq=76392/76666 fqs=87785
Apr  8 09:55:27 docker kernel: [ 3897.867947] 	(detected by 1, t=195022 jiffies, g=-163, c=-164, q=30)
Apr  8 09:55:27 docker kernel: [ 3897.868713] Task dump for CPU 7:
Apr  8 09:55:27 docker kernel: [ 3897.868714] swapper/7       R  running task        0     0      1 0x00000008
Apr  8 09:55:27 docker kernel: [ 3897.868716]  0000000000000010 0000000000000246 ffff89ebc27e3e70 0000000000000018
Apr  8 09:55:27 docker kernel: [ 3897.868718]  7735940000000000 000002bb17db5789 0000000000000007 ffff89ebc27e4000
Apr  8 09:55:27 docker kernel: [ 3897.868719]  ffff89ebe65e1700 ffffffff912b95c0 ffff89ebc27e0000 ffff89ebc27e3eb8
Apr  8 09:55:27 docker kernel: [ 3897.868721] Call Trace:
Apr  8 09:55:27 docker kernel: [ 3897.868725]  [<ffffffff90b18e07>] ? cpuidle_enter+0x17/0x20
Apr  8 09:55:27 docker kernel: [ 3897.868727]  [<ffffffff904c79fa>] ? call_cpuidle+0x2a/0x50
Apr  8 09:55:27 docker kernel: [ 3897.868728]  [<ffffffff904c7dde>] ? cpu_startup_entry+0x29e/0x350
Apr  8 09:55:27 docker kernel: [ 3897.868729]  [<ffffffff904518b1>] ? start_secondary+0x151/0x190
Apr  8 09:56:32 docker kernel: [ 3963.068577] INFO: rcu_sched detected stalls on CPUs/tasks:
Apr  8 09:56:32 docker kernel: [ 3963.069363] 	7-...: (3 GPs behind) idle=3e5/1/0 softirq=76664/76666 fqs=108832
Apr  8 09:56:32 docker kernel: [ 3963.070152] 	(detected by 1, t=240027 jiffies, g=49915, c=49914, q=167734)
Apr  8 09:56:32 docker kernel: [ 3963.070954] Task dump for CPU 7:
Apr  8 09:56:32 docker kernel: [ 3963.070954] swapper/7       R  running task        0     0      1 0x00000008
Apr  8 09:56:32 docker kernel: [ 3963.070957]  0000000000000010 0000000000000246 ffff89ebc27e3e70 0000000000000018
Apr  8 09:56:32 docker kernel: [ 3963.070959]  7735940000000000 000002bb17db5789 0000000000000007 ffff89ebc27e4000
Apr  8 09:56:32 docker kernel: [ 3963.070960]  ffff89ebe65e1700 ffffffff912b95c0 ffff89ebc27e0000 ffff89ebc27e3eb8
Apr  8 09:56:32 docker kernel: [ 3963.070961] Call Trace:
Apr  8 09:56:32 docker kernel: [ 3963.070965]  [<ffffffff90b18e07>] ? cpuidle_enter+0x17/0x20
Apr  8 09:56:32 docker kernel: [ 3963.070967]  [<ffffffff904c79fa>] ? call_cpuidle+0x2a/0x50
Apr  8 09:56:32 docker kernel: [ 3963.070968]  [<ffffffff904c7dde>] ? cpu_startup_entry+0x29e/0x350
Apr  8 09:56:32 docker kernel: [ 3963.070970]  [<ffffffff904518b1>] ? start_secondary+0x151/0x190

---

### Post by yanghuan2017 on 2017-04-10
I have changed my os type from ubuntu server 16.04 to CentOS 7, it become normal, mybe it's ubuntu bug.

---

### Post by TheFu on 2017-04-11
You could be right. I see it on VM hosts and inside VM clients. Different kernel versions.
Can you please post the kernel info for Cent? It may help others.

---

### Post by yanghuan2017 on 2017-04-21
The kernel version is 3.10.0-514.el7.x86_64.

---

### Post by TheFu on 2017-04-21
> **yanghuan2017 said:**
> The kernel version is 3.10.0-514.el7.x86_64.

14.04 uses 3.13.x, so that's an old kernel. Typical RHEL.  Being old isn't an issue, since they properly maintain it.

---

