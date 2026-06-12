---
title: "Unable to mount BTRFS FS after hard reboot"
date: 2015-11-01
forum: General Help
---

### Post by Swiss_Knight on 2015-11-01
Hello, 

It seems that I just encountered my first real problem with a btrfs file system on which my Ubuntu 14.04 OS is installed for almost two years.

After a simple session closing I had a black screen with nothing else than a blinking cursor: _ 
As I was not able to recover a graphical session using the F7 usual shortcut, nor any access to a TTY, I decided to hard reboot my system.

After that hard reboot, while first scanning for btrfs file system, the computer leaves me with this message :
[IMG]http://pix.toile-libre.org/upload/original/1446377230.jpg[/IMG]

It's just like my partition can't be mounted at this point. 
I only have a **initramfs** prompt with only a few basic programs.

So I have strictly no access to my Ubuntu system as you can see.

I have tried some more commands :
[IMG]http://pix.toile-libre.org/upload/original/1446375736.jpg[/IMG]
Without any form of success. 

I am now writing from a Live USB (Ubuntu 14.04).
From this Live USB, I've tried to to mount my btrfs partition trough Nautilus but I have this error message :
[IMG]http://reho.st/self/faf9352b2170579571c2160c3e35ffd959b36413.png[/IMG]

And **$ dmesg** gave me these lines :

```
[  428.274876] btrfs: device fsid f02867d2-b05d-4fb6-a055-3a1ef22fa5b7 devid 1 transid 472602 /dev/sda6
[  428.275598] btrfs: disk space caching is enabled
[  429.296324] btrfs: corrupt leaf, slot offset bad: block=912031744,root=1, slot=28
[  429.296476] btrfs: corrupt leaf, slot offset bad: block=912031744,root=1, slot=28
[  429.309698] btrfs: corrupt leaf, slot offset bad: block=912031744,root=1, slot=28
[  429.309950] BTRFS error (device sda6) in open_ctree:2839: errno=-5 IO failure (Failed to recover log tree)
[  429.310794] ------------[ cut here ]------------
[  429.310817] WARNING: CPU: 0 PID: 4706 at /build/buildd/linux-3.13.0/fs/btrfs/extent-tree.c:133 btrfs_put_block_group+0x69/0x70 [btrfs]()
[  429.310818] Modules linked in: xfs jfs ctr ccm joydev arc4 iwlmvm x86_pkg_temp_thermal intel_powerclamp mac80211 coretemp snd_hda_codec_hdmi kvm_intel snd_hda_codec_realtek snd_hda_intel kvm snd_hda_codec dm_crypt snd_hwdep crct10dif_pclmul snd_pcm crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 snd_page_alloc lrw snd_seq_midi iwlwifi asus_nb_wmi snd_seq_midi_event asus_wmi gf128mul snd_rawmidi sparse_keymap glue_helper snd_seq dm_multipath ablk_helper cfg80211 scsi_dh snd_seq_device cryptd bnep btusb snd_timer mei_me rtsx_pci_ms psmouse snd mei memstick lpc_ich rfcomm soundcore serio_raw mac_hid bluetooth parport_pc ppdev lp parport squashfs overlayfs btrfs xor raid6_pq libcrc32c nls_iso8859_1 dm_mirror dm_region_hash dm_log usb_storage rtsx_pci_sdmmc nouveau i915 mxm_wmi ttm i2c_algo_bit drm_kms_helper ahci drm r8169 rtsx_pci libahci mii video wmi
[  429.310858] CPU: 0 PID: 4706 Comm: mount Tainted: G        W    3.13.0-24-generic #46-Ubuntu
[  429.310859] Hardware name: ASUSTeK COMPUTER INC. N56JR/N56JR, BIOS N56JR.204 10/31/2013
[  429.310860]  0000000000000009 ffff88009d383b90 ffffffff81715a64 0000000000000000
[  429.310863]  ffff88009d383bc8 ffffffff810676bd ffff8802f946a000 ffff88031661c000
[  429.310865]  ffff8802f946a000 ffff88031661c080 ffff88031661c090 ffff88009d383bd8
[  429.310868] Call Trace:
[  429.310873]  [<ffffffff81715a64>] dump_stack+0x45/0x56
[  429.310876]  [<ffffffff810676bd>] warn_slowpath_common+0x7d/0xa0
[  429.310878]  [<ffffffff8106779a>] warn_slowpath_null+0x1a/0x20
[  429.310885]  [<ffffffffa030d759>] btrfs_put_block_group+0x69/0x70 [btrfs]
[  429.310893]  [<ffffffffa0316a60>] btrfs_free_block_groups+0xb0/0x390 [btrfs]
[  429.310902]  [<ffffffffa03253e8>] open_ctree+0x1848/0x1f80 [btrfs]
[  429.310908]  [<ffffffffa02fc56e>] btrfs_mount+0x63e/0x800 [btrfs]
[  429.310913]  [<ffffffff8116ebca>] ? pcpu_alloc+0x7da/0x9e0
[  429.310919]  [<ffffffff811bd3f9>] mount_fs+0x39/0x1b0
[  429.310921]  [<ffffffff8116ede0>] ? __alloc_percpu+0x10/0x20
[  429.310925]  [<ffffffff811d86d7>] vfs_kern_mount+0x67/0x110
[  429.310927]  [<ffffffff811daece>] do_mount+0x23e/0xad0
[  429.310930]  [<ffffffff81169e6b>] ? strndup_user+0x4b/0xf0
[  429.310932]  [<ffffffff811dba53>] SyS_mount+0x83/0xc0
[  429.310935]  [<ffffffff8172663f>] tracesys+0xe1/0xe6
[  429.310936] ---[ end trace 325c4aa1c2531a9f ]---
[  429.338170] btrfs: open_ctree failed
```


Before doing whatever things you can told me, I just wonder if it's : 1) a good idea and 2) useful to do a backup using **dd **of my btrfs partition on an external HDD ?
After that -- if useful -- I've also planned to try a **$ btrfs restore**.

I have read that **$ btrfs-zero-log** and **$ btrfs check --repair **may be harmful, so I haven't tested them yet because I should really be able to recover this partition (I hadn't backup all my /home data and other system stuff, I know, it's not good...).

I have also tried this : **$ badblocks -b 512 -n /dev/sda6** but it gave me strictly nothing except the hand back in my terminal after some long minutes.

My HDD as several partitions : a Windows 8 (pre-installaed on this laptop) as well as a windows recovery partition, a Data partition (ext4), etc. 
All of them except my Ubuntu OS -- which is the only btrfs one -- are fully accessible from the Live USB.
Also, the HDD has a 0 reallocated sectors count (SMART data seems OK) ; it's a two years old SATA HDD.

I also tried this :
**$ mount -t btrfs -o re,recovery** 
but it gave me only this back :
```
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


And last thing, as you can see in the second image, my btrfs partition is almost full (I've heard that in such cases, btrfs file system may behave strangely so it may be the cause, I don't know...).

Every kind of help or any redirection to some people working and knowing  really well btrfs file systems is highly appreciated at this point. [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]


Thanks a lot&#8313;&#8313;&#8313;&#8313; !!

---

