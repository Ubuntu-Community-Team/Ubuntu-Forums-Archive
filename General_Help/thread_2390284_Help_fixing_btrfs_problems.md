---
title: "Help fixing btrfs problems"
date: 2018-04-27
forum: General Help
---

### Post by David_Partridge on 2018-04-27
I rebooted my server today as it wasn't responding.

When I rebooted the root FS was read only.

I booted a live Ubuntu CD and checked the drive.

```
root@ubuntu:/home/amonra# btrfs check /dev/mapper/Charon--vg-root
Checking filesystem on /dev/mapper/Charon--vg-root
UUID: a0a6c5a6-061f-4c86-bc14-7f9abf3cb57e
checking extents
owner ref check failed [224304857088 16384]
checking free space cache
cache and super generation don't match, space cache will be invalidated
checking fs roots
checking csums
checking root refs
found 26552455179 bytes used err is 0
total csum bytes: 23801264
total tree bytes: 2076573696
total fs tree bytes: 1966374912
total extent tree bytes: 77348864
btree space waste bytes: 571010485
file data blocks allocated: 192698544128
 referenced 132293222400
root@ubunturoot@ubuntu:/home/amonra# btrfs check --repair /dev/mapper/Charon--vg-root
enabling repair mode
Checking filesystem on /dev/mapper/Charon--vg-root
UUID: a0a6c5a6-061f-4c86-bc14-7f9abf3cb57e
checking extents
owner ref check failed [224304857088 16384]
repair deleting extent record: key 224304857088 168 16384
adding new tree backref on start 224304857088 len 16384 parent 140827475968 root 140827475968
repaired damaged extent references
Fixed 0 roots.
checking free space cache
cache and super generation don't match, space cache will be invalidated
checking fs roots
checking csums
checking root refs
found 26552459274 bytes used err is 0
total csum bytes: 23801264
total tree bytes: 2076557312
total fs tree bytes: 1966374912
total extent tree bytes: 77332480
btree space waste bytes: 570994311
file data blocks allocated: 192698544128
 referenced 132293222400
root@ubuntu:/home/amonra# btrfs check /dev/mapper/Charon--vg-root
Checking filesystem on /dev/mapper/Charon--vg-root
UUID: a0a6c5a6-061f-4c86-bc14-7f9abf3cb57e
checking extents
owner ref check failed [224304857088 16384]
checking free space cache
cache and super generation don't match, space cache will be invalidated
checking fs roots
checking csums
checking root refs
found 26552455179 bytes used err is 0
total csum bytes: 23801264
total tree bytes: 2076573696
total fs tree bytes: 1966374912
total extent tree bytes: 77348864
btree space waste bytes: 571010485
file data blocks allocated: 192698544128
 referenced 132293222400
root@ubuntu
```

The error was still there after completing the btrfs check --repair :(  And when I deleted some old subvolumes from there after that I got this in dmesg:

```
[ 3157.354150] BTRFS error (device dm-0): unable to find ref byte nr 259932127232 parent 0 root 257  owner 4401121 offset 0
[ 3157.354160] ------------[ cut here ]------------
[ 3157.354226] WARNING: CPU: 1 PID: 6221 at /home/kernel/COD/linux/fs/btrfs/extent-tree.c:6951 __btrfs_free_extent.isra.71+0x995/0xca0 [btrfs]
[ 3157.354229] BTRFS: Transaction aborted (error -2)
[ 3157.354231] Modules linked in: bnep gpio_ich arc4 ath9k ath9k_common ath9k_hw snd_hda_codec_realtek ath snd_hda_codec_generic mac80211 snd_hda_intel btusb snd_hda_codec btrtl snd_hda_core btbcm btintel cfg80211 snd_hwdep bluetooth snd_pcm input_leds snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq coretemp snd_seq_device snd_timer serio_raw ib_iser snd lpc_ich rdma_cm iw_cm soundcore ib_cm mac_hid shpchp ib_core nfsd configfs iscsi_tcp libiscsi_tcp auth_rpcgss libiscsi nfs_acl scsi_transport_iscsi lockd grace sunrpc parport_pc ppdev lp parport autofs4 isofs nls_iso8859_1 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear dm_mirror dm_region_hash dm_log overlay uas usb_storage hid_generic usbhid hid pata_acpi i915
[ 3157.354381]  video i2c_algo_bit drm_kms_helper psmouse syscopyarea r8169 sysfillrect mii sysimgblt fb_sys_fops ahci drm aacraid libahci pata_jmicron fjes
[ 3157.354419] CPU: 1 PID: 6221 Comm: btrfs-cleaner Tainted: G        W       4.8.13-040813-generic #201612081531
[ 3157.354422] Hardware name: ZOTAC ATOM D525/NM10, BIOS 080016  12/22/2010
[ 3157.354427]  0000000000000286 000000007dca1675 ffff8a18ec897a98 ffffffff97a12d12
[ 3157.354438]  ffff8a18ec897ae8 0000000000000000 ffff8a18ec897ad8 ffffffff97682d9b
[ 3157.354448]  00001b27004327e1 0000003c85298000 00000000fffffffe ffff8a1864c858c0
[ 3157.354457] Call Trace:
[ 3157.354468]  [<ffffffff97a12d12>] dump_stack+0x63/0x81
[ 3157.354477]  [<ffffffff97682d9b>] __warn+0xcb/0xf0
[ 3157.354484]  [<ffffffff97682e1f>] warn_slowpath_fmt+0x5f/0x80
[ 3157.354540]  [<ffffffffc03f9ba5>] __btrfs_free_extent.isra.71+0x995/0xca0 [btrfs]
[ 3157.354601]  [<ffffffffc03fdd3e>] __btrfs_run_delayed_refs+0x59e/0x1280 [btrfs]
[ 3157.354610]  [<ffffffff97a3cfdf>] ? __percpu_counter_add+0x4f/0x60
[ 3157.354666]  [<ffffffffc0401aef>] btrfs_run_delayed_refs+0x9f/0x2c0 [btrfs]
[ 3157.354718]  [<ffffffffc03ff827>] ? walk_up_tree+0xe7/0x1f0 [btrfs]
[ 3157.354780]  [<ffffffffc04171ba>] btrfs_should_end_transaction+0x5a/0x60 [btrfs]
[ 3157.354833]  [<ffffffffc04000b5>] btrfs_drop_snapshot+0x3e5/0x850 [btrfs]
[ 3157.354843]  [<ffffffff97e7e648>] ? __schedule+0x308/0x770
[ 3157.354903]  [<ffffffffc0418534>] btrfs_clean_one_deleted_snapshot+0xb4/0x100 [btrfs]
[ 3157.354957]  [<ffffffffc040efbd>] cleaner_kthread+0x15d/0x1c0 [btrfs]
[ 3157.355011]  [<ffffffffc040ee60>] ? btrfs_destroy_pinned_extent+0x130/0x130 [btrfs]
[ 3157.355034]  [<ffffffff976a3a08>] kthread+0xd8/0xf0
[ 3157.355049]  [<ffffffff97e834df>] ret_from_fork+0x1f/0x40
[ 3157.355065]  [<ffffffff976a3930>] ? kthread_create_on_node+0x1b0/0x1b0
[ 3157.355074] ---[ end trace 51383c1b314f929e ]---
[ 3157.355085] BTRFS: error (device dm-0) in __btrfs_free_extent:6951: errno=-2 No such entry
[ 3157.355102] BTRFS info (device dm-0): forced readonly
[ 3157.355123] BTRFS: error (device dm-0) in btrfs_run_delayed_refs:2960: errno=-2 No such entry
[ 3157.398600] pending csums is 749568
root@ubuntu:/mnt/root# 


```

Of course my last backup was longer ago than I like to think about.  Though I could restore back to about 8 months ago,  I'd very much prefer not to ...

On my bootable CD the Kernel is 4.18.3 and btrfs-progs is 4.7.3-1

HELP!!!

Thank you David

---

### Post by David_Partridge on 2018-04-28
OK I've posted this to the linux-btrfs mailing list where it being looked at.

---

