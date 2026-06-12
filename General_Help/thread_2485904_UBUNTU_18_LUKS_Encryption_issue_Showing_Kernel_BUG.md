---
title: "UBUNTU 18 LUKS Encryption issue Showing Kernel BUG"
date: 2023-04-13
forum: General Help
---

### Post by spawarbabu on 2023-04-13
I have ubuntu server running, having the issue while formatting the volume with LUKS encryption.

# cryptsetup --verbose --verify-passphrase luksFormat /dev/mapper/vgdata-lv_luks


WARNING!
========
This will overwrite data on /dev/mapper/vgdata-lv_luks irrevocably.


Are you sure? (Type uppercase yes): YES
Enter passphrase for /dev/mapper/vgdata-lv_luks:
Verify passphrase:
[COLOR=#424242][FONT=&amp]
----Server Hangs without output ------------

We have below kernel messages.


[/FONT][/COLOR] kernel: [35628.447598] ------------[ cut here ]------------
 kernel: [35628.447602] kernel BUG at /build/linux-KwB9tO/linux-4.15.0/drivers/block/xen-blkfront.c:771!
 kernel: [35628.447682] invalid opcode: 0000 [#1] SMP PTI
 kernel: [35628.447712] Modules linked in: algif_skcipher af_alg tcp_diag udp_diag inet_diag ppdev crct10dif_pclmul crc32_pclmul joydev ghash_clmulni_intel input_leds serio_raw parport_
pc parport binfmt_misc ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_multiport xt_limit xt_tcpudp xt_addrt
ype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns sch_fq_codel nf_conntrack_broadcast ib_iser rdma_cm nf_nat_ftp iw_cm nf_nat ib_cm ib_core nf_conntrack_ftp
iscsi_tcp nf_conntrack libiscsi_tcp libiscsi iptable_filter scsi_transport_iscsi xenfs xen_privcmd ip_tables x_tables autofs4 btrfs zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_x
or async_tx
 kernel: [35628.448183]  xor raid6_pq libcrc32c raid1 raid0 multipath linear hid_generic usbhid hid aesni_intel aes_x86_64 crypto_simd cryptd glue_helper psmouse floppy
 kernel: [35628.448275] CPU: 1 PID: 508 Comm: kworker/1:1H Not tainted 4.15.0-208-generic #220-Ubuntu
 kernel: [35628.448337] Hardware name: Xen HVM domU, BIOS 4.7 09/01/2021
 kernel: [35628.448399] Workqueue: kblockd blk_mq_run_work_fn
 kernel: [35628.448447] RIP: 0010:blkif_queue_rq+0x7a0/0x7d0
 kernel: [35628.448490] RSP: 0018:ffffb9aa40723ca8 EFLAGS: 00010006
 kernel: [35628.448549] RAX: ffff8eb4f65c0000 RBX: ffff8eb4f65c0000 RCX: fffffbba00e09080
 kernel: [35628.448612] RDX: 0000000000020000 RSI: 0000000000000400 RDI: ffff8eb4f60c83e0
 kernel: [35628.448663] RBP: ffffb9aa40723d78 R08: 0000000000000000 R09: ffff8eb4f60c83e0
 kernel: [35628.448706] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000020
 kernel: [35628.448771] R13: ffff8eb4f65c0000 R14: 0000000000000020 R15: ffff8eb52e650900
 kernel: [35628.448838] FS:  0000000000000000(0000) GS:ffff8eb53ce40000(0000) knlGS:0000000000000000
 kernel: [35628.448911] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
 kernel: [35628.448948] CR2: ffffffffff600000 CR3: 000000001220a002 CR4: 00000000000606e0
 kernel: [35628.449009] Call Trace:
 kernel: [35628.449033]  blk_mq_dispatch_rq_list+0x8e/0x530
 kernel: [35628.451129]  ? __switch_to_asm+0x41/0x70
 kernel: [35628.453197]  ? __switch_to_asm+0x35/0x70
 kernel: [35628.455101]  ? __switch_to_asm+0x41/0x70
 kernel: [35628.456798]  ? entry_SYSCALL_64_after_hwframe+0xbc/0xbe
 kernel: [35628.458146]  ? entry_SYSCALL_64_after_hwframe+0xbd/0xbe
 kernel: [35628.459838]  blk_mq_sched_dispatch_requests+0x110/0x190
 kernel: [35628.461179]  __blk_mq_run_hw_queue+0x57/0xe0
 kernel: [35628.462520]  blk_mq_run_work_fn+0x2c/0x30
 kernel: [35628.463766]  process_one_work+0x1de/0x420
 kernel: [35628.465049]  worker_thread+0x32/0x410
 kernel: [35628.466255]  kthread+0x121/0x140
 kernel: [35628.467465]  ? process_one_work+0x420/0x420
 kernel: [35628.468634]  ? kthread_create_worker_on_cpu+0x70/0x70
 kernel: [35628.469869]  ret_from_fork+0x35/0x40
 kernel: [35628.471064] Code: 00 00 00 48 8b 52 70 49 89 95 a8 00 00 00 c7 84 03 3c 01 00 00 01 00 00 00 e9 89 fe ff ff 41 c6 85 a8 00 00 00 02 e9 4b fd ff ff <0f> 0b 48 8b 4d 80 f6 41 50 08 0f 84 24 ff ff ff c6 82 a9 00 00
 kernel: [35628.474478] RIP: blkif_queue_rq+0x7a0/0x7d0 RSP: ffffb9aa40723ca8
 kernel: [35628.475669] ---[ end trace 6d7c9753ee83f7df ]---
[COLOR=#424242][FONT=&amp]
[/FONT][/COLOR]

OS Details:-

# uname -r
4.15.0-208-generic


# cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04.6 LTS (Bionic Beaver)"

---

### Post by ActionParsnip on 2023-04-13
Bionic is end of life at the end of the month. You may want to use this as a catalyst to upgrade to a newer release.

---

### Post by spawarbabu on 2023-04-13
I know its going to EOL, But if some one can help here in the issue will be helpful.

---

