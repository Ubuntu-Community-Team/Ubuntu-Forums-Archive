---
title: "Kernel bug in hfsplus driver"
date: 2015-02-26
forum: General Help
---

### Post by Vladimir_Oltean on 2015-02-26
Hi,

I am trying to share an external HDD between Ubuntu 14.04 and Mac OS X, and I have read that I can get full R/W support for HFS+ in Linux as long as the drive is unjournaled.
However, the support for this FS seems flaky at best. When I'm trying to copy a large amount of files onto the drive, the driver crashes (needless to say, filesystem gets corrupted) and this is what I could read in my dmesg output:

```
[15286.823978] hfsplus: xattr search failed
[15286.856154] hfsplus: xattr search failed
[15286.946904] hfsplus: xattr search failed
[15287.610663] hfsplus: xattr search failed
[15287.881516] hfsplus: xattr search failed
[15287.941881] hfsplus: xattr search failed
[15288.004710] hfsplus: xattr search failed
[15288.163431] hfsplus: xattr search failed
[15288.185533] hfsplus: xattr search failed
[15288.239362] hfsplus: xattr search failed
[15288.366436] hfsplus: xattr search failed
[15288.435764] hfsplus: xattr search failed
[15288.473955] hfsplus: xattr search failed
[15288.512721] hfsplus: xattr search failed
[15288.542679] hfsplus: xattr search failed
[15288.574929] hfsplus: xattr search failed
[15288.635328] hfsplus: xattr search failed
[15288.695685] hfsplus: xattr search failed
[15288.983285] hfsplus: xattr search failed
[15289.144490] hfsplus: xattr search failed
[15289.336085] hfsplus: xattr search failed
[15289.542347] hfsplus: xattr search failed
[15289.664919] hfsplus: xattr search failed
[15289.668956] hfsplus: xattr searching failed
[15289.717392] hfsplus: xattr search failed
[15289.786139] hfsplus: xattr search failed
[15289.846585] hfsplus: xattr search failed
[15289.908808] hfsplus: xattr search failed
[15289.960832] hfsplus: xattr search failed
[15290.178332] hfsplus: xattr search failed
[15290.398800] hfsplus: xattr search failed
[15290.469507] hfsplus: xattr search failed
[15290.546530] hfsplus: xattr search failed
[15290.606911] hfsplus: xattr search failed
[15290.692309] hfsplus: xattr search failed
[15290.763350] hfsplus: xattr search failed
[15290.763833] hfsplus: new node 2 already hashed?
[15290.763837] ------------[ cut here ]------------
[15290.763852] WARNING: CPU: 0 PID: 8871 at /build/buildd/linux-3.13.0/fs/hfsplus/bnode.c:592 hfsplus_bnode_create+0x19d/0x1b0 [hfsplus]()
[15290.763855] Modules linked in: btrfs raid6_pq xor ufs qnx4 hfs minix ntfs msdos jfs xfs libcrc32c nls_utf8 hfsplus nls_iso8859_1 pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) vmnet(OX) vmw_vsock_vmci_transport vsock vmw_vmci vmmon(OX) rfcomm bnep bluetooth snd_hda_codec_hdmi joydev hid_generic mxm_wmi kvm_amd kvm usbhid crct10dif_pclmul crc32_pclmul hid ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_codec_realtek serio_raw fam15h_power k10temp snd_hda_intel snd_hda_codec edac_core edac_mce_amd snd_hwdep snd_pcm sp5100_tco snd_seq_midi i2c_piix4 snd_seq_midi_event snd_page_alloc snd_rawmidi nvidia(POX) snd_seq snd_seq_device snd_timer snd drm soundcore parport_pc shpchp ppdev mac_hid wmi it87 hwmon_vid lp parport usb_storage firewire_ohci r8169 firewire_core ahci mii crc_itu_t libahci
[15290.763953] CPU: 0 PID: 8871 Comm: pool Tainted: P           OX 3.13.0-46-generic #75-Ubuntu
[15290.763957] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./990FXA-UD3, BIOS F3i 10/07/2014
[15290.763960]  0000000000000009 ffff8803b9d5f718 ffffffff817212c6 0000000000000000
[15290.763969]  ffff8803b9d5f750 ffffffff810677dd 0000000000000002 ffff88041e4a0000
[15290.763975]  ffff88041e4a0074 ffff8803faff9180 ffff88041e4a0000 ffff8803b9d5f760
[15290.763982] Call Trace:
[15290.763992]  [<ffffffff817212c6>] dump_stack+0x45/0x56
[15290.764000]  [<ffffffff810677dd>] warn_slowpath_common+0x7d/0xa0
[15290.764006]  [<ffffffff810678ba>] warn_slowpath_null+0x1a/0x20
[15290.764016]  [<ffffffffa0ea6c7d>] hfsplus_bnode_create+0x19d/0x1b0 [hfsplus]
[15290.764025]  [<ffffffffa0ea5482>] hfsplus_bmap_alloc+0x362/0x380 [hfsplus]
[15290.764033]  [<ffffffff8116d9d9>] ? zone_statistics+0x89/0xa0
[15290.764042]  [<ffffffffa0ea56ea>] ? hfsplus_bnode_read+0x8a/0x100 [hfsplus]
[15290.764051]  [<ffffffffa0ea6cbd>] hfs_bnode_split+0x2d/0x3d0 [hfsplus]
[15290.764059]  [<ffffffffa0ea56ea>] ? hfsplus_bnode_read+0x8a/0x100 [hfsplus]
[15290.764069]  [<ffffffffa0ea7403>] hfsplus_brec_insert+0x73/0x3d0 [hfsplus]
[15290.764078]  [<ffffffffa0eaa643>] hfsplus_create_attr+0x1f3/0x230 [hfsplus]
[15290.764088]  [<ffffffffa0eaaf57>] __hfsplus_setxattr+0x1d7/0x9b0 [hfsplus]
[15290.764096]  [<ffffffffa0ea62d4>] ? hfsplus_bnode_dump+0x84/0xd0 [hfsplus]
[15290.764105]  [<ffffffffa0ea56ea>] ? hfsplus_bnode_read+0x8a/0x100 [hfsplus]
[15290.764114]  [<ffffffffa0ea56ea>] ? hfsplus_bnode_read+0x8a/0x100 [hfsplus]
[15290.764122]  [<ffffffffa0ea3011>] ? hfsplus_cat_case_cmp_key+0x31/0x40 [hfsplus]
[15290.764130]  [<ffffffffa0ea7be4>] ? hfs_find_rec_by_key+0x24/0x60 [hfsplus]
[15290.764139]  [<ffffffffa0ea7bc0>] ? hfsplus_brec_remove+0x180/0x180 [hfsplus]
[15290.764147]  [<ffffffffa0ea7ddd>] ? __hfsplus_brec_find+0x6d/0x170 [hfsplus]
[15290.764156]  [<ffffffffa0ea7fbd>] ? hfsplus_brec_find+0xdd/0x150 [hfsplus]
[15290.764164]  [<ffffffffa0ea7bc0>] ? hfsplus_brec_remove+0x180/0x180 [hfsplus]
[15290.764173]  [<ffffffffa0ea328a>] ? hfsplus_find_cat+0xca/0x120 [hfsplus]
[15290.764180]  [<ffffffffa0ec101a>] ? char2uni+0x1a/0x50 [nls_utf8]
[15290.764188]  [<ffffffffa0ea8e01>] ? hfsplus_compare_dentry+0x171/0x450 [hfsplus]
[15290.764198]  [<ffffffffa0eac52b>] hfsplus_user_setxattr+0xab/0xe0 [hfsplus]
[15290.764207]  [<ffffffff811e2722>] generic_setxattr+0x62/0x80
[15290.764213]  [<ffffffff811e2f83>] __vfs_setxattr_noperm+0x63/0x1b0
[15290.764220]  [<ffffffff8132336c>] ? evm_inode_setxattr+0x3c/0x50
[15290.764227]  [<ffffffff811e3185>] vfs_setxattr+0xb5/0xc0
[15290.764233]  [<ffffffff811e32be>] setxattr+0x12e/0x1c0
[15290.764240]  [<ffffffff811cdce2>] ? final_putname+0x22/0x50
[15290.764246]  [<ffffffff811cdee9>] ? putname+0x29/0x40
[15290.764252]  [<ffffffff811cea3f>] ? user_path_at_empty+0x5f/0x90
[15290.764260]  [<ffffffff811c0469>] ? __sb_start_write+0x49/0xe0
[15290.764265]  [<ffffffff811ddb74>] ? mntput+0x24/0x40
[15290.764271]  [<ffffffff811c7b0e>] ? path_put+0x1e/0x30
[15290.764277]  [<ffffffff811e354f>] SyS_setxattr+0x8f/0xe0
[15290.764284]  [<ffffffff81731d7d>] system_call_fastpath+0x1a/0x1f
[15290.764288] ---[ end trace 75b8fd2b45af474f ]---
[15290.764384] ------------[ cut here ]------------
[15290.764388] kernel BUG at /build/buildd/linux-3.13.0/fs/hfsplus/bnode.c:639!
[15290.764391] invalid opcode: 0000 [#1] SMP 
[15290.764396] Modules linked in: btrfs raid6_pq xor ufs qnx4 hfs minix ntfs msdos jfs xfs libcrc32c nls_utf8 hfsplus nls_iso8859_1 pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) vmnet(OX) vmw_vsock_vmci_transport vsock vmw_vmci vmmon(OX) rfcomm bnep bluetooth snd_hda_codec_hdmi joydev hid_generic mxm_wmi kvm_amd kvm usbhid crct10dif_pclmul crc32_pclmul hid ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_codec_realtek serio_raw fam15h_power k10temp snd_hda_intel snd_hda_codec edac_core edac_mce_amd snd_hwdep snd_pcm sp5100_tco snd_seq_midi i2c_piix4 snd_seq_midi_event snd_page_alloc snd_rawmidi nvidia(POX) snd_seq snd_seq_device snd_timer snd drm soundcore parport_pc shpchp ppdev mac_hid wmi it87 hwmon_vid lp parport usb_storage firewire_ohci r8169 firewire_core ahci mii crc_itu_t libahci
[15290.764485] CPU: 0 PID: 8871 Comm: pool Tainted: P        W  OX 3.13.0-46-generic #75-Ubuntu
[15290.764489] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./990FXA-UD3, BIOS F3i 10/07/2014
[15290.764493] task: ffff8804268b6000 ti: ffff8803b9d5e000 task.ti: ffff8803b9d5e000
[15290.764496] RIP: 0010:[<ffffffffa0ea66fa>]  [<ffffffffa0ea66fa>] hfsplus_bnode_put+0xba/0xc0 [hfsplus]
[15290.764505] RSP: 0018:ffff8803b9d5f870  EFLAGS: 00010246
[15290.764509] RAX: 0000000000000000 RBX: ffff8803faff9180 RCX: ffff8803b9d5f864
[15290.764512] RDX: 00000000000008a6 RSI: ffff88010ef66000 RDI: ffff8803faff9180
[15290.764515] RBP: ffff8803b9d5f890 R08: ffff8803b9d5f85c R09: ffff8801334cecb0
[15290.764518] R10: ffff880400a55cb0 R11: 0000000000000000 R12: ffff8803faff9180
[15290.764521] R13: ffff88041e4a0000 R14: 0000000000000036 R15: 000000000000002a
[15290.764525] FS:  00007f74af217700(0000) GS:ffff88043ec00000(0000) knlGS:0000000000000000
[15290.764528] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[15290.764531] CR2: 00000000033ca048 CR3: 00000003ef16a000 CR4: 00000000000407f0
[15290.764534] Stack:
[15290.764537]  ffff8803faff9180 ffff8803b9d5f928 000000000000005e 0000000000000036
[15290.764544]  ffff8803b9d5f908 ffffffffa0ea75d1 ffff880425ae0f00 0000002800000036
[15290.764551]  ffff880300001fa8 00000f920000002a ffff88041e4a0000 ffff8803faff9180
[15290.764557] Call Trace:
[15290.764568]  [<ffffffffa0ea75d1>] hfsplus_brec_insert+0x241/0x3d0 [hfsplus]
[15290.764578]  [<ffffffffa0eaa643>] hfsplus_create_attr+0x1f3/0x230 [hfsplus]
[15290.764588]  [<ffffffffa0eaaf57>] __hfsplus_setxattr+0x1d7/0x9b0 [hfsplus]
[15290.764596]  [<ffffffffa0ea62d4>] ? hfsplus_bnode_dump+0x84/0xd0 [hfsplus]
[15290.764606]  [<ffffffffa0ea56ea>] ? hfsplus_bnode_read+0x8a/0x100 [hfsplus]
[15290.764615]  [<ffffffffa0ea56ea>] ? hfsplus_bnode_read+0x8a/0x100 [hfsplus]
[15290.764624]  [<ffffffffa0ea3011>] ? hfsplus_cat_case_cmp_key+0x31/0x40 [hfsplus]
[15290.764633]  [<ffffffffa0ea7be4>] ? hfs_find_rec_by_key+0x24/0x60 [hfsplus]
[15290.764641]  [<ffffffffa0ea7bc0>] ? hfsplus_brec_remove+0x180/0x180 [hfsplus]
[15290.764650]  [<ffffffffa0ea7ddd>] ? __hfsplus_brec_find+0x6d/0x170 [hfsplus]
[15290.764659]  [<ffffffffa0ea7fbd>] ? hfsplus_brec_find+0xdd/0x150 [hfsplus]
[15290.764668]  [<ffffffffa0ea7bc0>] ? hfsplus_brec_remove+0x180/0x180 [hfsplus]
[15290.764676]  [<ffffffffa0ea328a>] ? hfsplus_find_cat+0xca/0x120 [hfsplus]
[15290.764683]  [<ffffffffa0ec101a>] ? char2uni+0x1a/0x50 [nls_utf8]
[15290.764692]  [<ffffffffa0ea8e01>] ? hfsplus_compare_dentry+0x171/0x450 [hfsplus]
[15290.764702]  [<ffffffffa0eac52b>] hfsplus_user_setxattr+0xab/0xe0 [hfsplus]
[15290.764710]  [<ffffffff811e2722>] generic_setxattr+0x62/0x80
[15290.764717]  [<ffffffff811e2f83>] __vfs_setxattr_noperm+0x63/0x1b0
[15290.764723]  [<ffffffff8132336c>] ? evm_inode_setxattr+0x3c/0x50
[15290.764730]  [<ffffffff811e3185>] vfs_setxattr+0xb5/0xc0
[15290.764736]  [<ffffffff811e32be>] setxattr+0x12e/0x1c0
[15290.764743]  [<ffffffff811cdce2>] ? final_putname+0x22/0x50
[15290.764749]  [<ffffffff811cdee9>] ? putname+0x29/0x40
[15290.764756]  [<ffffffff811cea3f>] ? user_path_at_empty+0x5f/0x90
[15290.764763]  [<ffffffff811c0469>] ? __sb_start_write+0x49/0xe0
[15290.764768]  [<ffffffff811ddb74>] ? mntput+0x24/0x40
[15290.764774]  [<ffffffff811c7b0e>] ? path_put+0x1e/0x30
[15290.764781]  [<ffffffff811e354f>] SyS_setxattr+0x8f/0xe0
[15290.764787]  [<ffffffff81731d7d>] system_call_fastpath+0x1a/0x1f
[15290.764791] Code: e0 41 8b 55 70 31 f6 4c 89 e7 c1 e2 0c e8 8f f2 ff ff 4c 89 e7 e8 b7 ed ff ff 4c 89 e7 e8 3f bb 2f e0 5b 41 5c 41 5d 41 5e 5d c3 <0f> 0b 0f 1f 40 00 66 66 66 66 90 55 48 89 e5 41 57 41 56 41 89 
[15290.764850] RIP  [<ffffffffa0ea66fa>] hfsplus_bnode_put+0xba/0xc0 [hfsplus]
[15290.764858]  RSP <ffff8803b9d5f870>
[15290.764863] ---[ end trace 75b8fd2b45af4750 ]---

```

Basically, what I need as an answer is how to reliably share (very important) data between Ubuntu and OS X.

---

### Post by tgalati4 on 2015-02-26
hfs stores more metadata than ext4 about each file in the file system.  Perhaps put in a timer in your script and send files over in smaller groups with some wait times in between.  It's possible that the Mac machine/disk drive is not fast enough to update the metadata while the file copies take place.

The trace dump seems to have happened while setting file attributes, so is that a disk problem, a system IO problem, or a kernel/file system bug?  Who knows?

There are a few hfs tools available:

> tgalati4@Mint17 ~ $ apt-cache search hfs
hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes
libhfsp-dev - Library to access HFS+ formatted volumes
libhfsp0 - Shared library to access HFS+ formatted volumes
dmg2img - Tool for converting compress dmg files to hfsplus images
hfsprogs - mkfs and fsck for HFS and HFS+ file systems
hfsutils-tcltk - Tcl/Tk interfaces for reading and writing Macintosh volumes

Most Mac drives are designed for Firewire400 or 800 speeds.  So if you are writing through USB2, that might be a problem.  Try connecting with a firewire port.

---

### Post by Vladimir_Oltean on 2015-02-27
Well, copying small amounts of data at a time just to make sure it doesn't blow doesn't sound too reliable to me.

---

### Post by tgalati4 on 2015-02-27
It would isolate the problem.  If slower copy works and faster copy fails for the exact same data set, then that would help with troubleshooting.

---

