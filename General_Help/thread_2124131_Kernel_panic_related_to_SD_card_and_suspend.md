---
title: "Kernel panic related to SD card and suspend"
date: 2013-03-09
forum: General Help
---

### Post by nkorth on 2013-03-09
I have a Dell Mini 9 running Ubuntu 12.04. Today I got a 16GB SD card to supplement its tiny 8GB of internal storage, and I decided to set it up to auto-mount so I could link most of my home directory into the card. I found some helpful instructions on this very forum, and figured out how to modify the fstab to make it work. It worked quite nicely, and I immediately moved lots of stuff and made a bunch of symbolic links. It was a remarkably smooth process considering I had never messed with fstab before.


The problem occured when I woke up the laptop from sleep later. It woke up just fine, but the terminal I had left open was behaving oddly. I typed "ls" and it said something about a read error. Remembering that I was still in a directory on the SD card, I cd'd to home and tried opening a symbolic link to the card, and boom, kernel panic.[SIZE=2] Here's a picture of the screen when this happened.
[/SIZE][ATTACH=CONFIG]239993[/ATTACH]


If it helps, the fstab line I added was:
```
UUID=(snip) /mnt/data ext4 defaults,user,nodev,nosuid,relatime 0 2
```


When setting up the mount, I didn't do anything special. I formatted the card to ext4, created the directory, changed fstab, and ran "sudo mount -a".

Edit: Here's what seems to be the relevant part of syslog:
```
Mar  9 22:15:40 nkorth-mini kernel: [12566.175865] EXT4-fs error (device mmcblk0p1): ext4_find_entry:935: inode #261633: comm bash: reading directory lblock 0Mar  9 22:15:42 nkorth-mini kernel: [12567.858258] EXT4-fs error (device mmcblk0p1): __ext4_get_inode_loc:3680: inode #2: block 983: comm ls: unable to read itable block
Mar  9 22:15:42 nkorth-mini kernel: [12567.858283] EXT4-fs error (device mmcblk0p1) in ext4_reserve_inode_write:4502: IO failure
Mar  9 22:15:43 nkorth-mini kernel: [12569.054018] EXT4-fs error (device mmcblk0p1): ext4_find_entry:935: inode #2: comm bash: reading directory lblock 0
Mar  9 22:15:47 nkorth-mini kernel: [12573.008428] Aborting journal on device mmcblk0p1-8.
Mar  9 22:15:47 nkorth-mini kernel: [12573.008491] JBD2: I/O error detected when updating journal superblock for mmcblk0p1-8.
Mar  9 22:16:07 nkorth-mini kernel: [12592.672873] ------------[ cut here ]------------
Mar  9 22:16:07 nkorth-mini kernel: [12592.672896] WARNING: at /build/buildd/linux-3.2.0/fs/proc/generic.c:586 proc_register+0xaf/0x150()
Mar  9 22:16:07 nkorth-mini kernel: [12592.672903] Hardware name: Inspiron 910
Mar  9 22:16:07 nkorth-mini kernel: [12592.672907] proc_dir_entry 'ext4/mmcblk0p1' already registered
Mar  9 22:16:07 nkorth-mini kernel: [12592.672912] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat mmc_block joydev dell_laptop compal_laptop dcdbas snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi uvcvideo serio_raw snd_rawmidi videodev lib80211_crypt_tkip snd_seq_midi_event wl(P) snd_seq snd_timer snd_seq_device cfg80211 i915 snd rfcomm bnep drm_kms_helper bluetooth parport_pc drm jmb38x_ms mac_hid ppdev memstick lib80211 i2c_algo_bit soundcore video snd_page_alloc lp parport r8169 sdhci_pci sdhci
Mar  9 22:16:07 nkorth-mini kernel: [12592.673008] Pid: 6729, comm: mount Tainted: P           O 3.2.0-38-generic-pae #61-Ubuntu
Mar  9 22:16:07 nkorth-mini kernel: [12592.673014] Call Trace:
Mar  9 22:16:07 nkorth-mini kernel: [12592.673026]  [<c105a5e2>] warn_slowpath_common+0x72/0xa0
Mar  9 22:16:07 nkorth-mini kernel: [12592.673035]  [<c119840f>] ? proc_register+0xaf/0x150
Mar  9 22:16:07 nkorth-mini kernel: [12592.673042]  [<c119840f>] ? proc_register+0xaf/0x150
Mar  9 22:16:07 nkorth-mini kernel: [12592.673050]  [<c105a6b3>] warn_slowpath_fmt+0x33/0x40
Mar  9 22:16:07 nkorth-mini kernel: [12592.673058]  [<c119840f>] proc_register+0xaf/0x150
Mar  9 22:16:07 nkorth-mini kernel: [12592.673066]  [<c11988b6>] proc_mkdir_mode+0x36/0x60
Mar  9 22:16:07 nkorth-mini kernel: [12592.673073]  [<c11988f4>] proc_mkdir+0x14/0x20
Mar  9 22:16:07 nkorth-mini kernel: [12592.673083]  [<c11edc45>] ext4_fill_super+0xf75/0x1ba0
Mar  9 22:16:07 nkorth-mini kernel: [12592.673092]  [<c12b69a1>] ? vsnprintf+0xb1/0x390
Mar  9 22:16:07 nkorth-mini kernel: [12592.673101]  [<c1110001>] ? wait_iff_congested+0xa1/0x120
Mar  9 22:16:07 nkorth-mini kernel: [12592.673111]  [<c1147ca3>] mount_bdev+0x193/0x1d0
Mar  9 22:16:07 nkorth-mini kernel: [12592.673119]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:07 nkorth-mini kernel: [12592.673129]  [<c11dc76f>] ext4_mount+0x1f/0x30
Mar  9 22:16:07 nkorth-mini kernel: [12592.673137]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:07 nkorth-mini kernel: [12592.673145]  [<c1148656>] mount_fs+0x36/0x180
Mar  9 22:16:07 nkorth-mini kernel: [12592.673153]  [<c1112a7f>] ? __alloc_percpu+0xf/0x20
Mar  9 22:16:07 nkorth-mini kernel: [12592.673162]  [<c115f49e>] ? alloc_vfsmnt+0xae/0x130
Mar  9 22:16:07 nkorth-mini kernel: [12592.673171]  [<c115f5b1>] vfs_kern_mount+0x51/0xa0
Mar  9 22:16:07 nkorth-mini kernel: [12592.673179]  [<c11606de>] do_kern_mount+0x3e/0xe0
Mar  9 22:16:07 nkorth-mini kernel: [12592.673187]  [<c1161dd4>] do_mount+0x164/0x200
Mar  9 22:16:07 nkorth-mini kernel: [12592.673196]  [<c116220b>] sys_mount+0x6b/0xa0
Mar  9 22:16:07 nkorth-mini kernel: [12592.673206]  [<c15af49f>] sysenter_do_call+0x12/0x28
Mar  9 22:16:07 nkorth-mini kernel: [12592.673212] ---[ end trace 381b0a15b102e3d7 ]---
Mar  9 22:16:07 nkorth-mini kernel: [12592.674880] ------------[ cut here ]------------
Mar  9 22:16:07 nkorth-mini kernel: [12592.674897] WARNING: at /build/buildd/linux-3.2.0/fs/proc/generic.c:586 proc_register+0xaf/0x150()
Mar  9 22:16:07 nkorth-mini kernel: [12592.674903] Hardware name: Inspiron 910
Mar  9 22:16:07 nkorth-mini kernel: [12592.674908] proc_dir_entry 'jbd2/mmcblk0p1-8' already registered
Mar  9 22:16:07 nkorth-mini kernel: [12592.674912] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat mmc_block joydev dell_laptop compal_laptop dcdbas snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi uvcvideo serio_raw snd_rawmidi videodev lib80211_crypt_tkip snd_seq_midi_event wl(P) snd_seq snd_timer snd_seq_device cfg80211 i915 snd rfcomm bnep drm_kms_helper bluetooth parport_pc drm jmb38x_ms mac_hid ppdev memstick lib80211 i2c_algo_bit soundcore video snd_page_alloc lp parport r8169 sdhci_pci sdhci
Mar  9 22:16:07 nkorth-mini kernel: [12592.675007] Pid: 6729, comm: mount Tainted: P        W  O 3.2.0-38-generic-pae #61-Ubuntu
Mar  9 22:16:07 nkorth-mini kernel: [12592.675012] Call Trace:
Mar  9 22:16:07 nkorth-mini kernel: [12592.675025]  [<c105a5e2>] warn_slowpath_common+0x72/0xa0
Mar  9 22:16:07 nkorth-mini kernel: [12592.675033]  [<c119840f>] ? proc_register+0xaf/0x150
Mar  9 22:16:07 nkorth-mini kernel: [12592.675040]  [<c119840f>] ? proc_register+0xaf/0x150
Mar  9 22:16:07 nkorth-mini kernel: [12592.675049]  [<c105a6b3>] warn_slowpath_fmt+0x33/0x40
Mar  9 22:16:07 nkorth-mini kernel: [12592.675056]  [<c119840f>] proc_register+0xaf/0x150
Mar  9 22:16:07 nkorth-mini kernel: [12592.675064]  [<c11988b6>] proc_mkdir_mode+0x36/0x60
Mar  9 22:16:07 nkorth-mini kernel: [12592.675071]  [<c11988f4>] proc_mkdir+0x14/0x20
Mar  9 22:16:07 nkorth-mini kernel: [12592.675082]  [<c1218eef>] jbd2_stats_proc_init+0x1f/0x50
Mar  9 22:16:07 nkorth-mini kernel: [12592.675090]  [<c12b6c9c>] ? sprintf+0x1c/0x20
Mar  9 22:16:07 nkorth-mini kernel: [12592.675099]  [<c121afcd>] jbd2_journal_init_inode+0xbd/0x190
Mar  9 22:16:07 nkorth-mini kernel: [12592.675109]  [<c159922b>] ext4_get_journal+0xb7/0xf7
Mar  9 22:16:07 nkorth-mini kernel: [12592.675118]  [<c11129c6>] ? pcpu_alloc+0x296/0x340
Mar  9 22:16:07 nkorth-mini kernel: [12592.675125]  [<c15998ff>] ext4_load_journal+0x158/0x366
Mar  9 22:16:07 nkorth-mini kernel: [12592.675136]  [<c11ee214>] ext4_fill_super+0x1544/0x1ba0
Mar  9 22:16:07 nkorth-mini kernel: [12592.675143]  [<c12b69a1>] ? vsnprintf+0xb1/0x390
Mar  9 22:16:07 nkorth-mini kernel: [12592.675151]  [<c1110001>] ? wait_iff_congested+0xa1/0x120
Mar  9 22:16:07 nkorth-mini kernel: [12592.675162]  [<c1147ca3>] mount_bdev+0x193/0x1d0
Mar  9 22:16:07 nkorth-mini kernel: [12592.675170]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:07 nkorth-mini kernel: [12592.675180]  [<c11dc76f>] ext4_mount+0x1f/0x30
Mar  9 22:16:07 nkorth-mini kernel: [12592.675188]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:07 nkorth-mini kernel: [12592.675196]  [<c1148656>] mount_fs+0x36/0x180
Mar  9 22:16:07 nkorth-mini kernel: [12592.675204]  [<c1112a7f>] ? __alloc_percpu+0xf/0x20
Mar  9 22:16:07 nkorth-mini kernel: [12592.675212]  [<c115f49e>] ? alloc_vfsmnt+0xae/0x130
Mar  9 22:16:07 nkorth-mini kernel: [12592.675221]  [<c115f5b1>] vfs_kern_mount+0x51/0xa0
Mar  9 22:16:07 nkorth-mini kernel: [12592.675229]  [<c11606de>] do_kern_mount+0x3e/0xe0
Mar  9 22:16:07 nkorth-mini kernel: [12592.675237]  [<c1161dd4>] do_mount+0x164/0x200
Mar  9 22:16:07 nkorth-mini kernel: [12592.675246]  [<c116220b>] sys_mount+0x6b/0xa0
Mar  9 22:16:07 nkorth-mini kernel: [12592.675255]  [<c15af49f>] sysenter_do_call+0x12/0x28
Mar  9 22:16:07 nkorth-mini kernel: [12592.675262] ---[ end trace 381b0a15b102e3d8 ]---
Mar  9 22:16:09 nkorth-mini kernel: [12594.477154] ------------[ cut here ]------------
Mar  9 22:16:09 nkorth-mini kernel: [12594.477173] WARNING: at /build/buildd/linux-3.2.0/fs/sysfs/dir.c:481 sysfs_add_one+0xb3/0xf0()
Mar  9 22:16:09 nkorth-mini kernel: [12594.477179] Hardware name: Inspiron 910
Mar  9 22:16:09 nkorth-mini kernel: [12594.477184] sysfs: cannot create duplicate filename '/fs/ext4/mmcblk0p1'
Mar  9 22:16:09 nkorth-mini kernel: [12594.477189] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat mmc_block joydev dell_laptop compal_laptop dcdbas snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi uvcvideo serio_raw snd_rawmidi videodev lib80211_crypt_tkip snd_seq_midi_event wl(P) snd_seq snd_timer snd_seq_device cfg80211 i915 snd rfcomm bnep drm_kms_helper bluetooth parport_pc drm jmb38x_ms mac_hid ppdev memstick lib80211 i2c_algo_bit soundcore video snd_page_alloc lp parport r8169 sdhci_pci sdhci
Mar  9 22:16:09 nkorth-mini kernel: [12594.477286] Pid: 6729, comm: mount Tainted: P        W  O 3.2.0-38-generic-pae #61-Ubuntu
Mar  9 22:16:09 nkorth-mini kernel: [12594.477292] Call Trace:
Mar  9 22:16:09 nkorth-mini kernel: [12594.477305]  [<c105a5e2>] warn_slowpath_common+0x72/0xa0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477314]  [<c11a8313>] ? sysfs_add_one+0xb3/0xf0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477321]  [<c11a8313>] ? sysfs_add_one+0xb3/0xf0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477329]  [<c105a6b3>] warn_slowpath_fmt+0x33/0x40
Mar  9 22:16:09 nkorth-mini kernel: [12594.477337]  [<c11a8313>] sysfs_add_one+0xb3/0xf0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477345]  [<c11a83a7>] create_dir+0x57/0xb0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477352]  [<c11a84a1>] sysfs_create_dir+0x71/0xb0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477362]  [<c12ae9fd>] kobject_add_internal+0x8d/0x1d0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477370]  [<c12aed4a>] ? kobject_set_name_vargs+0x4a/0x60
Mar  9 22:16:09 nkorth-mini kernel: [12594.477379]  [<c12aed99>] kobject_init_and_add+0x39/0x60
Mar  9 22:16:09 nkorth-mini kernel: [12594.477390]  [<c11ee734>] ext4_fill_super+0x1a64/0x1ba0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477403]  [<c1110001>] ? wait_iff_congested+0xa1/0x120
Mar  9 22:16:09 nkorth-mini kernel: [12594.477417]  [<c1147ca3>] mount_bdev+0x193/0x1d0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477429]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:09 nkorth-mini kernel: [12594.477443]  [<c11dc76f>] ext4_mount+0x1f/0x30
Mar  9 22:16:09 nkorth-mini kernel: [12594.477454]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:09 nkorth-mini kernel: [12594.477466]  [<c1148656>] mount_fs+0x36/0x180
Mar  9 22:16:09 nkorth-mini kernel: [12594.477477]  [<c1112a7f>] ? __alloc_percpu+0xf/0x20
Mar  9 22:16:09 nkorth-mini kernel: [12594.477489]  [<c115f49e>] ? alloc_vfsmnt+0xae/0x130
Mar  9 22:16:09 nkorth-mini kernel: [12594.477500]  [<c115f5b1>] vfs_kern_mount+0x51/0xa0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477512]  [<c11606de>] do_kern_mount+0x3e/0xe0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477523]  [<c1161dd4>] do_mount+0x164/0x200
Mar  9 22:16:09 nkorth-mini kernel: [12594.477536]  [<c116220b>] sys_mount+0x6b/0xa0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477551]  [<c15af49f>] sysenter_do_call+0x12/0x28
Mar  9 22:16:09 nkorth-mini kernel: [12594.477560] ---[ end trace 381b0a15b102e3d9 ]---
Mar  9 22:16:09 nkorth-mini kernel: [12594.477582] kobject_add_internal failed for mmcblk0p1 with -EEXIST, don't try to register things with the same name in the same directory.
Mar  9 22:16:09 nkorth-mini kernel: [12594.477598] Pid: 6729, comm: mount Tainted: P        W  O 3.2.0-38-generic-pae #61-Ubuntu
Mar  9 22:16:09 nkorth-mini kernel: [12594.477605] Call Trace:
Mar  9 22:16:09 nkorth-mini kernel: [12594.477618]  [<c1592426>] ? printk+0x2d/0x2f
Mar  9 22:16:09 nkorth-mini kernel: [12594.477631]  [<c12aeaa8>] kobject_add_internal+0x138/0x1d0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477644]  [<c12aed99>] kobject_init_and_add+0x39/0x60
Mar  9 22:16:09 nkorth-mini kernel: [12594.477657]  [<c11ee734>] ext4_fill_super+0x1a64/0x1ba0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477669]  [<c1110001>] ? wait_iff_congested+0xa1/0x120
Mar  9 22:16:09 nkorth-mini kernel: [12594.477684]  [<c1147ca3>] mount_bdev+0x193/0x1d0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477695]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:09 nkorth-mini kernel: [12594.477706]  [<c11dc76f>] ext4_mount+0x1f/0x30
Mar  9 22:16:09 nkorth-mini kernel: [12594.477717]  [<c11eccd0>] ? ext4_calculate_overhead+0x190/0x190
Mar  9 22:16:09 nkorth-mini kernel: [12594.477728]  [<c1148656>] mount_fs+0x36/0x180
Mar  9 22:16:09 nkorth-mini kernel: [12594.477740]  [<c1112a7f>] ? __alloc_percpu+0xf/0x20
Mar  9 22:16:09 nkorth-mini kernel: [12594.477751]  [<c115f49e>] ? alloc_vfsmnt+0xae/0x130
Mar  9 22:16:09 nkorth-mini kernel: [12594.477762]  [<c115f5b1>] vfs_kern_mount+0x51/0xa0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477774]  [<c11606de>] do_kern_mount+0x3e/0xe0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477786]  [<c1161dd4>] do_mount+0x164/0x200
Mar  9 22:16:09 nkorth-mini kernel: [12594.477797]  [<c116220b>] sys_mount+0x6b/0xa0
Mar  9 22:16:09 nkorth-mini kernel: [12594.477810]  [<c15af49f>] sysenter_do_call+0x12/0x28
Mar  9 22:16:09 nkorth-mini kernel: [12594.477903] EXT4-fs (mmcblk0p1): mount failed
Mar  9 22:16:09 nkorth-mini kernel: [12594.484058] BUG: unable to handle kernel NULL pointer dereference at 00000054
Mar  9 22:16:09 nkorth-mini kernel: [12594.484328] IP: [<c1148663>] mount_fs+0x43/0x180
Mar  9 22:16:09 nkorth-mini kernel: [12594.484504] *pdpt = 00000000152bf001 *pde = 0000000000000000 
Mar  9 22:16:09 nkorth-mini kernel: [12594.484709] Oops: 0000 [#1] SMP 
Mar  9 22:16:09 nkorth-mini kernel: [12594.484839] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat mmc_block joydev dell_laptop compal_laptop dcdbas snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi uvcvideo serio_raw snd_rawmidi videodev lib80211_crypt_tkip snd_seq_midi_event wl(P) snd_seq snd_timer snd_seq_device cfg80211 i915 snd rfcomm bnep drm_kms_helper bluetooth parport_pc drm jmb38x_ms mac_hid ppdev memstick lib80211 i2c_algo_bit soundcore video snd_page_alloc lp parport r8169 sdhci_pci sdhci
Mar  9 22:16:09 nkorth-mini kernel: [12594.486638] 
Mar  9 22:16:09 nkorth-mini kernel: [12594.486683] Pid: 6729, comm: mount Tainted: P        W  O 3.2.0-38-generic-pae #61-Ubuntu Dell Inc. Inspiron 910/CN0J14
Mar  9 22:16:09 nkorth-mini kernel: [12594.486948] EIP: 0060:[<c1148663>] EFLAGS: 00010207 CPU: 0
Mar  9 22:16:09 nkorth-mini kernel: [12594.487079] EIP is at mount_fs+0x43/0x180
Mar  9 22:16:09 nkorth-mini kernel: [12594.487174] EAX: 00000000 EBX: 00000000 ECX: 8010000b EDX: 00000000
Mar  9 22:16:09 nkorth-mini kernel: [12594.487318] ESI: 00000000 EDI: c18363e0 EBP: cd831f18 ESP: cd831ee4
Mar  9 22:16:09 nkorth-mini kernel: [12594.487463]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Mar  9 22:16:09 nkorth-mini kernel: [12594.487589] Process mount (pid: 6729, ti=cd830000 task=c1c2f230 task.ti=cd830000)
Mar  9 22:16:09 nkorth-mini kernel: [12594.487759] Stack:
Mar  9 22:16:09 nkorth-mini kernel: [12594.487809]  00000000 d53d3c00 00000000 d53d3c70 cd831efc c1112a7f cd831f18 c115f49e
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  00000000 00000000 d53d3c00 c18363e0 fffffff4 cd831f38 c115f5b1 00000000
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  d5339ef0 00000000 c18363e0 ffffffed 00000000 cd831f58 c11606de 00000000
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022] Call Trace:
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  [<c1112a7f>] ? __alloc_percpu+0xf/0x20
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  [<c115f49e>] ? alloc_vfsmnt+0xae/0x130
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  [<c115f5b1>] vfs_kern_mount+0x51/0xa0
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  [<c11606de>] do_kern_mount+0x3e/0xe0
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  [<c1161dd4>] do_mount+0x164/0x200
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  [<c116220b>] sys_mount+0x6b/0xa0
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022]  [<c15af49f>] sysenter_do_call+0x12/0x28
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022] Code: c7 45 f0 00 00 00 00 74 0a f6 40 04 02 0f 84 85 00 00 00 8b 55 ec 89 f8 89 1c 24 ff 57 08 3d 00 f0 ff ff 89 c6 0f 87 cc 00 00 00 <8b> 58 54 85 db 0f 84 f4 00 00 00 8b 83 d4 00 00 00 85 c0 0f 84 
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022] EIP: [<c1148663>] mount_fs+0x43/0x180 SS:ESP 0068:cd831ee4
Mar  9 22:16:09 nkorth-mini kernel: [12594.488022] CR2: 0000000000000054
Mar  9 22:16:09 nkorth-mini kernel: [12594.572770] ---[ end trace 381b0a15b102e3da ]---
Mar  9 22:16:30 nkorth-mini acpid: client 1000[0:0] has disconnected
Mar  9 22:17:01 nkorth-mini CRON[6857]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

---

### Post by dcstar on 2013-03-10
> **nkorth said:**
> I have a Dell Mini 9 running Ubuntu 12.04. Today I got a 16GB SD card to supplement its tiny 8GB of internal storage, and I decided to set it up to auto-mount so I could link most of my home directory into the card.
..........


The **last **thing you want to do is use any external storage for critical system folders, these things are not part of the core hardware of systems and will usually not be powered up or activated until well after the internal hardware is finally working after a suspend etc.

You can use these things for non-core storage but trying to use them for anything that the system relies on only brings the sort of problems you are experiencing.

---

### Post by nkorth on 2013-03-10
I didn't think I moved any critical files to it. I only moved parts of my home folder. I didn't move any dotfiles, or anything from outside /home/nkorth. The only thing that might have caused some weirdness was moving my Dropbox folder, but I don't think Dropbox caused the kernel panic (it happened when using a terminal in a non-Dropbox folder). My question here is: why did I get a kernel panic for an "ordinary" auto-mount, and how should I have set it up to avoid problems?

Edit: I tried again to reproduce the kernel panic, but couldn't. Perhaps that was just a fluke, but I'm still wondering how to make the card work after resume. I was able to find some useful links: [http://superuser.com/questions/73028/force-unmount-in-ubuntu-to-fix-problems-after-netbook-sleep-mode](http://superuser.com/questions/73028/force-unmount-in-ubuntu-to-fix-problems-after-netbook-sleep-mode) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/883748](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/883748). Neither completely answers my question, though.

---

### Post by nkorth on 2013-03-12
Ok, I figured out how to fix it. For future Googlers, I put the following script in "/etc/pm/sleep.d/20_sdcard-unmount":

```
#!/bin/sh

# Unmount SD card when suspending


case "$1" in
  suspend|suspend_hybrid|hibernate)
    umount -l /mnt/data
    ;;
  resume|thaw)
    mount -a
    ;;
esac

```

The "/mnt/data" needs to be replaced with wherever your mount is located, of course.

---

