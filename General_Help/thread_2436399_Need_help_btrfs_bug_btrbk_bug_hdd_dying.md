---
title: "Need help: btrfs bug? btrbk bug? hdd dying?"
date: 2020-02-05
forum: General Help
---

### Post by sandman852 on 2020-02-05
[COLOR=#242729][FONT=Arial]Hi guys, 

I have already placed this question at [askubuntu.com]("https://askubuntu.com/questions/1208063/is-it-a-btrfs-bug-a-btrbk-bug-or-is-my-hdd-dying"), but I didn't receive any answers, so I will try my luck here :-)

I'm using a BTRFS setup in my home server, where I'm having 3 disks in a btrfs-raid and a fourth disk is used to receive daily backup snapshots via [BTRBK]("https://github.com/digint/btrbk"). Some days ago I noticed, that BTRBK was throwing errors, because sending the snapshots to the backup disk was not possible as it was mounted readonly. Digging a little bit deeper I found that there were I/O errors (dmesg: BTRFS: error (device sde) in btrfs_run_delayed_refs:2978: errno=-5 IO failure). I did not manage to repair these errors, but ended up to recreate the filesystem at the backupdisk. This was running well now for a little more than one week and now I see the same errors.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now, I'm not sure, if this fault occurs due to a bug in BTRFS, a bug in BTRBK, or if my harddrive is going to die (actually it's quite old already). Can you please help me to find out what's going on?[/FONT][/COLOR]

System: Ubuntu 16.04.6 LTS with mainline kernel 4.20.17-042017-generic x86_64 
btrfs-progs v4.14.1 
BTRBK version: 0.22.2

**BTRBK Log:**
```
localtime type status duration target_url source_url parent_url message
2020-02-03T06:25:11+0100 startup v0.22.2 - - - - # btrbk command line client, version 0.22.2
2020-02-03T06:25:11+0100 snapshot starting - /mnt/dp0/snapshots/seafile.20200203 /mnt/dp0/seafile - -
2020-02-03T06:25:11+0100 snapshot success 0 /mnt/dp0/snapshots/seafile.20200203 /mnt/dp0/seafile - -
2020-02-03T06:25:11+0100 send-receive starting - /mnt/bp0/seafile/seafile.20200203 /mnt/dp0/snapshots/seafile.20200203 /mnt/dp0/snapshots/seafile.20200202 -
2020-02-03T06:25:11+0100 send-receive ERROR 18 /mnt/bp0/seafile/seafile.20200203 /mnt/dp0/snapshots/seafile.20200203 /mnt/dp0/snapshots/seafile.20200202 -
2020-02-03T06:25:29+0100 delete_garbled starting - /mnt/bp0/seafile/seafile.20200203 - - -
2020-02-03T06:25:29+0100 delete_garbled ERROR 0 /mnt/bp0/seafile/seafile.20200203 - - -
2020-02-03T06:25:29+0100 abort_target ABORT - /mnt/bp0/seafile - - # Failed to send/receive subvolume
2020-02-03T06:25:29+0100 finished partial 18 - - - # At least one backup task aborted
localtime type status duration target_url source_url parent_url message
2020-02-04T06:25:10+0100 startup v0.22.2 - - - - # btrbk command line client, version 0.22.2
2020-02-04T06:25:11+0100 snapshot starting - /mnt/dp0/snapshots/seafile.20200204 /mnt/dp0/seafile - -
2020-02-04T06:25:11+0100 snapshot success 0 /mnt/dp0/snapshots/seafile.20200204 /mnt/dp0/seafile - -
2020-02-04T06:25:11+0100 abort_target ABORT - /mnt/bp0/seafile - - # Target subvolume "/mnt/bp0/seafile/seafile.20200203" already exists
2020-02-04T06:25:11+0100 finished partial 1 - - - # At least one backup task aborted
```

**Syslog:**
```
Feb  4 06:25:04 somehost kernel: [41566.737968] BTRFS info (device sde): use zstd compression, level 0
Feb  4 06:25:04 somehost kernel: [41566.737969] BTRFS info (device sde): disk space caching is enabled
Feb  4 06:25:04 somehost kernel: [41566.737970] BTRFS info (device sde): has skinny extents
Feb  4 06:25:08 somehost kernel: [41570.639345] BTRFS info (device sde): balance: resuming
Feb  4 06:25:11 somehost kernel: [41572.990217] BTRFS info (device sde): relocating block group 1074173837312 flags data
Feb  4 06:25:14 somehost kernel: [41576.298186] BTRFS info (device sde): found 23 extents
Feb  4 06:25:15 somehost kernel: [41577.855201] WARNING: CPU: 2 PID: 17198 at fs/btrfs/extent-tree.c:1552 lookup_inline_extent_backref+0x57c/0x5c0 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855203] Modules linked in: binfmt_misc nls_iso8859_1 ext2 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp intel_cstate intel_rapl_perf input_leds mei_me joydev mei mac_hid acpi_pad ib_iser rdma_cm iw_cm ib_cm ib_core iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi autofs4 btrfs zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear hid_generic usbhid hid i915 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel kvmgt vfio_mdev mdev vfio_iommu_type1 vfio kvm irqbypass drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm aesni_intel drm_panel_orientation_quirks aes_x86_64 cfbfillrect crypto_simd cfbimgblt cfbcopyarea cryptd fb glue_helper igb fbdev e1000e dca i2c_algo_bit ahci i2c_core libahci video
Feb  4 06:25:15 somehost kernel: [41577.855225] CPU: 2 PID: 17198 Comm: btrfs-balance Not tainted 4.20.17-042017-generic #201903190933
Feb  4 06:25:15 somehost kernel: [41577.855226] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./H270M-ITX/ac, BIOS P2.00 03/29/2017
Feb  4 06:25:15 somehost kernel: [41577.855244] RIP: 0010:lookup_inline_extent_backref+0x57c/0x5c0 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855245] Code: 9d 60 ff ff ff 4c 8b a5 58 ff ff ff e9 37 fe ff ff 48 8b 9d 60 ff ff ff b8 8b ff ff ff e9 f8 fb ff ff 45 31 ed e9 9d fc ff ff <0f> 0b b8 fb ff ff ff e9 e4 fb ff ff 80 7d b6 bf 0f 87 5a fe ff ff
Feb  4 06:25:15 somehost kernel: [41577.855246] RSP: 0018:ffffaf8f41c7b838 EFLAGS: 00010202
Feb  4 06:25:15 somehost kernel: [41577.855247] RAX: 0000000000000001 RBX: ffff9ef8dfe36c40 RCX: 0000000000000000
Feb  4 06:25:15 somehost kernel: [41577.855248] RDX: 0000000000000008 RSI: 0000000000000000 RDI: 0000000000000000
Feb  4 06:25:15 somehost kernel: [41577.855248] RBP: ffffaf8f41c7b8e0 R08: 0000000000000000 R09: 0000000000000000
Feb  4 06:25:15 somehost kernel: [41577.855249] R10: 0000000000000000 R11: ffff9ef680000000 R12: 0000000001f80000
Feb  4 06:25:15 somehost kernel: [41577.855250] R13: 0000000000000000 R14: ffff9ef8e482f0d0 R15: 0000000000004000
Feb  4 06:25:15 somehost kernel: [41577.855251] FS:  0000000000000000(0000) GS:ffff9ef8e6f00000(0000) knlGS:0000000000000000
Feb  4 06:25:15 somehost kernel: [41577.855252] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb  4 06:25:15 somehost kernel: [41577.855253] CR2: 000055efd408d920 CR3: 000000026160a001 CR4: 00000000003606e0
Feb  4 06:25:15 somehost kernel: [41577.855253] Call Trace:
Feb  4 06:25:15 somehost kernel: [41577.855276]  ? set_extent_buffer_dirty+0x16/0xa0 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855293]  insert_inline_extent_backref+0x51/0xe0 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855295]  ? _cond_resched+0x19/0x30
Feb  4 06:25:15 somehost kernel: [41577.855312]  __btrfs_inc_extent_ref.isra.66+0x7b/0x220 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855329]  btrfs_run_delayed_refs_for_head+0x326/0x930 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855348]  ? btrfs_get_token_64+0x105/0x120 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855369]  ? btrfs_merge_delayed_refs+0x330/0x380 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855386]  __btrfs_run_delayed_refs+0xa1/0x770 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855403]  btrfs_run_delayed_refs+0x73/0x190 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855421]  btrfs_commit_transaction+0x52/0x840 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855441]  prepare_to_merge+0x1e4/0x210 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855461]  relocate_block_group+0x40e/0x4c7 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855479]  btrfs_relocate_block_group.cold.50+0x4d/0xfd [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855499]  btrfs_relocate_chunk+0x36/0xb0 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855519]  __btrfs_balance+0x51d/0xbb0 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855538]  ? insert_balance_item.isra.42+0xb8/0x390 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855559]  btrfs_balance+0x306/0x510 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855579]  balance_kthread.cold.71+0x20/0x27 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855582]  kthread+0x120/0x140
Feb  4 06:25:15 somehost kernel: [41577.855602]  ? btrfs_balance+0x510/0x510 [btrfs]
Feb  4 06:25:15 somehost kernel: [41577.855603]  ? __kthread_parkme+0x70/0x70
Feb  4 06:25:15 somehost kernel: [41577.855605]  ret_from_fork+0x35/0x40
Feb  4 06:25:15 somehost kernel: [41577.855607] ---[ end trace 137afcdc172cbf0a ]---
Feb  4 06:25:15 somehost kernel: [41577.855610] BTRFS: error (device sde) in btrfs_run_delayed_refs:2978: errno=-5 IO failure
Feb  4 06:25:15 somehost kernel: [41577.855649] BTRFS info (device sde): forced readonly
Feb  4 06:25:15 somehost kernel: [41577.856115] BTRFS error (device sde): pending csums is 1310720
```

**SMART Status of /dev/sde: **(=Backup Disk)
```
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.20.17-042017-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 5K3000
Device Model:     Hitachi HDS5C3030BLE630
***STRIPPED***
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
***STRIPPED***

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   144   144   054    Pre-fail  Offline      -       82
  3 Spin_Up_Time            0x0007   139   139   024    Pre-fail  Always       -       395 (Average 395)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       2544
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   138   138   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   098   098   000    Old_age   Always       -       18000
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       652
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       2612
193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       2612
194 Temperature_Celsius     0x0002   193   193   000    Old_age   Always       -       31 (Min/Max 1/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     17730         -
# 2  Short offline       Completed without error       00%     17696         -
# 3  Extended offline    Completed without error       00%     17675         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
```

Thanks in advance! 
simon

---

### Post by TheFu on 2020-02-05
SMART shows an old disk working fine.

sorry,  I don't know anything about BTRFS beyond that when building VM servers, CoW on CoW is problematic, so I avoided it.

---

### Post by sandman852 on 2020-02-06
Thanks for your reply!
> **TheFu said:**
> CoW on CoW is problematic

Maybe I‘m missing the forest through the trees, but what do you mean by CoW on CoW? I thought CoW implies the possibility of efficiently creating snapshots on a filesystem basis...

---

### Post by TheFu on 2020-02-06
> **sandman852 said:**
> Thanks for your reply!


Maybe I‘m missing the forest through the trees, but what do you mean by CoW on CoW? I thought CoW implies the possibility of efficiently creating snapshots on a filesystem basis...

For snapshots, I use LVM.  It has been stable for 20 yrs and is deployed in enterprises. My data is worth more.  I'm always a late adopter for new file systems and only after sufficient time without any data loss issues reported.  Plus, btrfs lies to **du** and **df**.  Those commands are just too important to my administration. Lying cannot be tolerated, even if there is a good reason.

Google found this: [https://btrfs.wiki.kernel.org/index.php/Gotchas#Fragmentation](https://btrfs.wiki.kernel.org/index.php/Gotchas#Fragmentation)  That is the main reason I decided BTRFS would never fit my needs.  If I need an advanced file system, I'd use ZFS. About a year ago, while building a new VM host box, I looked carefully at ZFS and decided against deployment.  Sticking with LVM+EXT4 and having LVM present an LV for each VM directly.  The VMs are on a quality SSD, so I didn't deploy onto a RAID1 set. That's the first time my VMs haven't been on RAID since 2005-ish.  Of course, I have backup religion.

But I do appreciate people who can try out new things with their data.  That ain't me.  Everyone has different requirements.

Sorry, I really cannot help with your specific situation.

---

