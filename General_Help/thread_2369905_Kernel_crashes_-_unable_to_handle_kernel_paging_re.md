---
title: "Kernel crashes - unable to handle kernel paging request"
date: 2017-08-28
forum: General Help
---

### Post by philled on 2017-08-28
I have a MythBuntu 16.04 virtual machine running MythTV. I only recently upgraded to 16.04 but since I did I'm getting regular freezes of the machine - I can't SSH in, can't VNC in and can't access it by KVM virt-manager.

I've found this in syslog which I think indicates there's some sort of kernel crash, but what can I do to stop this happening? I've applied all the latest updates via apt-get.

```
[FONT=courier new]Aug 28 00:09:34 mbe3 kernel: [ 6329.768235] BUG: unable to handle kernel paging request at 00000000751c5006
Aug 28 00:09:34 mbe3 kernel: [ 6329.768241] IP: [<00000000751c5006>] 0x751c5006
Aug 28 00:09:34 mbe3 kernel: [ 6329.768244] PGD 7c3da067 PUD 0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768245] Oops: 0010 [#1] SMP
Aug 28 00:09:34 mbe3 kernel: [ 6329.768249] Modules linked in: arc4 md4 nls_utf8 cifs ccm fscache snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm crct10dif_pclmul snd_seq_midi crc32_pclmul ghash_clmulni_intel snd_seq_midi_event aesni_intel aes_x86_64 lrw gf128mul snd_rawmidi snd_seq snd_seq_device glue_helper 8250_fintek ablk_helper cryptd input_leds snd_timer snd serio_raw soundcore i2c_piix4 mac_hid nfsd parport_pc ppdev auth_rpcgss nfs_acl lp lockd parport grace sunrpc autofs4 qxl ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm floppy psmouse pata_acpi
Aug 28 00:09:34 mbe3 kernel: [ 6329.768270] CPU: 1 PID: 34 Comm: kswapd0 Not tainted 4.4.0-92-generic #115-Ubuntu
Aug 28 00:09:34 mbe3 kernel: [ 6329.768272] Hardware name: QEMU Standard PC (i440FX + PIIX, 1996), BIOS Ubuntu-1.8.2-1ubuntu1 04/01/2014
Aug 28 00:09:34 mbe3 kernel: [ 6329.768273] task: ffff88007ca9e200 ti: ffff88007c018000 task.ti: ffff88007c018000
Aug 28 00:09:34 mbe3 kernel: [ 6329.768274] RIP: 0010:[<00000000751c5006>]  [<00000000751c5006>] 0x751c5006
Aug 28 00:09:34 mbe3 kernel: [ 6329.768276] RSP: 0018:ffff88007c01ba40  EFLAGS: 00010082
Aug 28 00:09:34 mbe3 kernel: [ 6329.768277] RAX: 0000000000000000 RBX: ffffea0001cb4380 RCX: 00000000ffffffec
Aug 28 00:09:34 mbe3 kernel: [ 6329.768291] RDX: 000000000001a82c RSI: 000000000000000a RDI: ffff88007ffdb7c0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768292] RBP: ffff88007c01ba78 R08: 0000000000000014 R09: 00002000000067e8
Aug 28 00:09:34 mbe3 kernel: [ 6329.768293] R10: ffff88007c01b9f8 R11: 0000000000000000 R12: ffff880079f28ac8
Aug 28 00:09:34 mbe3 kernel: [ 6329.768294] R13: 0000000000000001 R14: ffff88007d08dc00 R15: ffff880079f28ab0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768295] FS:  0000000000000000(0000) GS:ffff88007fd00000(0000) knlGS:0000000000000000
Aug 28 00:09:34 mbe3 kernel: [ 6329.768296] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 28 00:09:34 mbe3 kernel: [ 6329.768296] CR2: 00000000751c5006 CR3: 000000007b71d000 CR4: 00000000000406e0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768299] Stack:
Aug 28 00:09:34 mbe3 kernel: [ 6329.768300]  0000000000000000 0000000000000246 ffff88007c01be50 ffffea0001cb4380
Aug 28 00:09:34 mbe3 kernel: [ 6329.768302]  ffff88007c01bc00 ffffea0001cb43a0 ffff88007c01bb28 ffff88007c01bb78
Aug 28 00:09:34 mbe3 kernel: [ 6329.768303]  ffffffff811a54b3 ffff88007ca9e200 0000000100000001 ffff88007ffdb7c0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768304] Call Trace:
Aug 28 00:09:34 mbe3 kernel: [ 6329.768315]  [<ffffffff811a54b3>] shrink_page_list+0x453/0x7a0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768317]  [<ffffffff811a5e99>] shrink_inactive_list+0x209/0x520
Aug 28 00:09:34 mbe3 kernel: [ 6329.768318]  [<ffffffff811a6b23>] shrink_lruvec+0x583/0x740
Aug 28 00:09:34 mbe3 kernel: [ 6329.768320]  [<ffffffff811a6dcf>] shrink_zone+0xef/0x2e0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768321]  [<ffffffff811a808e>] kswapd+0x51e/0x990
Aug 28 00:09:34 mbe3 kernel: [ 6329.768323]  [<ffffffff811a7b70>] ? mem_cgroup_shrink_node_zone+0x1c0/0x1c0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768326]  [<ffffffff810a0cc5>] kthread+0xe5/0x100
Aug 28 00:09:34 mbe3 kernel: [ 6329.768328]  [<ffffffff810a0be0>] ? kthread_create_on_node+0x1e0/0x1e0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768338]  [<ffffffff8184238f>] ret_from_fork+0x3f/0x70
Aug 28 00:09:34 mbe3 kernel: [ 6329.768339]  [<ffffffff810a0be0>] ? kthread_create_on_node+0x1e0/0x1e0
Aug 28 00:09:34 mbe3 kernel: [ 6329.768340] Code:  Bad RIP value.
Aug 28 00:09:34 mbe3 kernel: [ 6329.768341] RIP  [<00000000751c5006>] 0x751c5006
Aug 28 00:09:34 mbe3 kernel: [ 6329.768342]  RSP <ffff88007c01ba40>
Aug 28 00:09:34 mbe3 kernel: [ 6329.768343] CR2: 00000000751c5006
[/FONT][FONT=fixedsys][FONT=courier new]Aug 28 00:09:34 mbe3 kernel: [ 6329.768344] ---[ end trace 8714225605968f25 ]---[/FONT]
[/FONT]

```

---

