---
title: "BTRFS error"
date: 2023-11-23
forum: General Help
---

### Post by c-tuxe on 2023-11-23
I have an issue with a BTRFS snapshot that I can't delete.
If I try to delete it, I get the below error in dmesg and the whole volume is mounted read only necessitating a reboot.
I noticed that the snapshot name reported by btrfs subvolume list is incorrectly capitalised compared to the name in 'ls' - it is DoWnloads.2020xxxx instead of Downloads.2020xxxx which I find very strange.

Any ideas how to rescue the situation?

```
BTRFS: Transaction aborted (error -2)
[Thu Nov 23 17:53:13 2023] WARNING: CPU: 4 PID: 3333 at fs/btrfs/inode.c:3847 btrfs_unlink_subvol+0x4c3/0x520 [btrfs]
[Thu  Nov 23 17:53:13 2023] Modules linked in: bluetooth ecdh_generic ecc  nf_conntrack_netlink nfnetlink xfrm_user xfrm_algo br_netfilter bridge  stp llc overlay vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) xt_MASQUERADE  iptable_nat ip6t_REJECT nf_reject_ipv6 xt_hl ip6t_rt  snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio  snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg soundwire_intel  soundwire_generic_allocation soundwire_cadence snd_hda_codec  intel_rapl_msr snd_hda_core snd_hwdep soundwire_bus mei_hdcp  snd_soc_core snd_compress ac97_bus intel_rapl_common snd_pcm_dmaengine  ipt_REJECT nf_reject_ipv4 x86_pkg_temp_thermal intel_powerclamp snd_pcm  xt_comment xt_multiport kvm_intel kvm snd_seq_midi snd_seq_midi_event  crct10dif_pclmul snd_rawmidi crc32_pclmul ghash_clmulni_intel  aesni_intel crypto_simd snd_seq at24 cryptd glue_helper xt_limit  snd_seq_device xt_tcpudp snd_timer rapl binfmt_misc xt_addrtype  intel_cstate eeprom serio_raw mei_me snd lpc_ich soundcore mei  intel_smartconnect mac_hid
[Thu Nov 23 17:53:13 2023]  xt_conntrack  ip6table_filter ip6_tables nf_conntrack_netbios_ns  nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack  nf_defrag_ipv6 nf_defrag_ipv4 sch_fq_codel nct6775 hwmon_vid coretemp  parport_pc iptable_filter ppdev bpfilter lp parport ip_tables x_tables  autofs4 btrfs blake2b_generic raid10 raid456 async_raid6_recov  async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1  raid0 multipath linear psmouse i2c_i801 ahci r8169 i2c_smbus xhci_pci  libahci realtek xhci_pci_renesas video
[Thu Nov 23 17:53:13 2023] CPU: 4 PID: 3333 Comm: mv Tainted: G           OE     5.10.6-051006-generic #202101091334
[Thu Nov 23 17:53:13 2023] Hardware name: xxxxx
[Thu Nov 23 17:53:13 2023] RIP: 0010:btrfs_unlink_subvol+0x4c3/0x520 [btrfs]
[Thu  Nov 23 17:53:13 2023] Code: 8b 55 50 f0 48 0f ba aa 40 0a 00 00 02 72  20 83 f8 fb 74 3c 83 f8 e2 74 37 89 c6 48 c7 c7 78 e8 43 c0 89 45 a0 e8  e4 5f a2 c1 <0f> 0b 8b 45 a0 89 c1 ba 07 0f 00 00 4c 89 ef 89 45  a0 48 c7 c6 40
[Thu Nov 23 17:53:13 2023] RSP: 0018:ffffab16c186fc80 EFLAGS: 00010282
[Thu Nov 23 17:53:13 2023] RAX: 0000000000000000 RBX: ffff985a10059d90 RCX: ffff985c8ed18a48
[Thu Nov 23 17:53:13 2023] RDX: 00000000ffffffd8 RSI: 0000000000000027 RDI: ffff985c8ed18a40
[Thu Nov 23 17:53:13 2023] RBP: ffffab16c186fd00 R08: 0000000000000000 R09: ffffab16c186fa60
[Thu Nov 23 17:53:13 2023] R10: ffffab16c186fa58 R11: ffffffff82f52ce8 R12: ffff98598baf03f0
[Thu Nov 23 17:53:13 2023] R13: ffff98598b161c30 R14: 0000000000000100 R15: ffff985a09305d70
[Thu Nov 23 17:53:13 2023] FS:  00007f4eca3c6800(0000) GS:ffff985c8ed00000(0000) knlGS:0000000000000000
[Thu Nov 23 17:53:13 2023] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[Thu Nov 23 17:53:13 2023] CR2: 00005618eede72d8 CR3: 000000026c378005 CR4: 00000000001706e0
[Thu Nov 23 17:53:13 2023] Call Trace:
[Thu Nov 23 17:53:13 2023]  btrfs_rename+0x9ca/0xb30 [btrfs]
[Thu Nov 23 17:53:13 2023]  btrfs_rename2+0x1d/0x30 [btrfs]
[Thu Nov 23 17:53:13 2023]  vfs_rename+0x729/0xb60
[Thu Nov 23 17:53:13 2023]  do_renameat2+0x4f4/0x540
[Thu Nov 23 17:53:13 2023]  __x64_sys_rename+0x23/0x30
[Thu Nov 23 17:53:13 2023]  do_syscall_64+0x38/0x90
[Thu Nov 23 17:53:13 2023]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[Thu Nov 23 17:53:13 2023] RIP: 0033:0x7f4ec9830ce7
[Thu  Nov 23 17:53:13 2023] Code: 75 12 48 89 df e8 a9 60 09 00 85 c0 0f 95  c0 0f b6 c0 f7 d8 5b c3 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 b8 52 00  00 00 0f 05 <48> 3d 00 f0 ff ff 77 09 f3 c3 0f 1f 80 00 00 00 00  48 8b 15 69 f1
[Thu Nov 23 17:53:13 2023] RSP: 002b:00007fffc2f96c18 EFLAGS: 00000202 ORIG_RAX: 0000000000000052
[Thu Nov 23 17:53:13 2023] RAX: ffffffffffffffda RBX: 00007fffc2f9704f RCX: 00007f4ec9830ce7
[Thu Nov 23 17:53:13 2023] RDX: 00005618ee81b330 RSI: 00007fffc2f9887c RDI: 00007fffc2f98868
[Thu Nov 23 17:53:13 2023] RBP: 00007fffc2f96ff0 R08: 0000000000000000 R09: 0000000000000000
[Thu Nov 23 17:53:13 2023] R10: 00005618eede5010 R11: 0000000000000202 R12: 00007fffc2f970d0
[Thu Nov 23 17:53:13 2023] R13: 0000000000000000 R14: 0000000000000000 R15: 00007fffc2f98868
[Thu Nov 23 17:53:13 2023] ---[ end trace fb0ce9a12a95c5dc ]---
[Thu Nov 23 17:53:13 2023] BTRFS: error (device sde1) in btrfs_unlink_subvol:3847: errno=-2 No such entry
[Thu Nov 23 17:53:13 2023] BTRFS info (device sde1): forced readonly
[Thu Nov 23 17:53:13 2023] BTRFS: error (device sde1) in btrfs_rename:9249: errno=-2 No such entry[COLOR=#888888]
[/COLOR]

```

---

### Post by MAFoElffen on 2023-11-23
Can you please run the 'system-info' script in my signature line to provide more details on your system layout and details about how BTRFS is laid out on your system?

To turn on the mode that will provide that in the report, when you go to run it, instead of doing 
```

./system-info

```
Do
```

./system-info --details

```
Choose to upload it to a pastebin and post the URL of where the report uploads to.

What are you using to do your Snapshots? Commandline? Timeshift? Snapper?

---

### Post by #&amp;thj^% on 2023-11-23
> **MAFoElffen said:**
> Can you please run the 'system-info' script in my signature line to provide more details on your system layout and details about how BTRFS is laid out on your system?

To turn on the mode that will provide that in the report, when you go to run it, instead of doing 
```

./system-info

```
Do
```

./system-info --details

```
Choose to upload it to a pastebin and post the URL of where the report uploads to.

What are you using to do your Snapshots? Commandline? Timeshift? Snapper?

+1
And i was going to ask the same "What are you using to do your Snapshots? Commandline? Timeshift? Snapper?"
```
ls /run/timeshift/16227/backup/timeshift-btrfs/snapshots
2023-11-11_18-51-07  2023-11-23_13-06-52  2023-11-23_13-21-05
2023-11-23_12-57-32  2023-11-23_13-19-39

```

---

### Post by c-tuxe on 2023-11-23
OK sure.

I use btrbk.

---

### Post by c-tuxe on 2023-11-23
detailed report as requested

---

### Post by #&amp;thj^% on 2023-11-23
> **c-tuxe said:**
> detailed report as requested 
[http://paste.ubuntu.com/p/tZN4XBWMDR/](http://paste.ubuntu.com/p/tZN4XBWMDR/)

is this your backup drive then? "/mnt/backup3tb" /dev/sdd1

---

### Post by c-tuxe on 2023-11-23
That is a backup drive but the snapshot I'm trying to delete is on /mnt/4tb, specifically within /mnt/4tb/_snapshots

---

### Post by MAFoElffen on 2023-11-23
In that case, please post the output of this within CODE Tags:
```

sudo find /mnt/4tb/_snapshots -type f | xargs ls -l {}

```

---

### Post by c-tuxe on 2023-11-25
> **MAFoElffen said:**
> In that case, please post the output of this within CODE Tags:
```

sudo find /mnt/4tb/_snapshots -type f | xargs ls -l {}

```

Could you explain this command please?

---

### Post by #&amp;thj^% on 2023-11-25
it will look for your snaphots and provide us how to proceed with any advice.

---

### Post by c-tuxe on 2023-11-25
Thank you. The command appears to have some issue with files/directories with spaces, but the output contains solely files within the problematic snapshot. What does that mean?

---

### Post by #&amp;thj^% on 2023-11-25
> **c-tuxe said:**
> Thank you. The command appears to have some issue with files/directories with spaces, but the output contains solely files within the problematic snapshot. What does that mean?
Don't know yet.
Can you show us the that return please?

---

### Post by c-tuxe on 2023-11-25
> **1fallen said:**
> Don't know yet.
Can you show us the that return please?

Sure (with some edits for information governance reasons)

```

[FONT=&amp]-rwxrwxr-x 1 user user 23234 Apr 1  2012 /mnt/4tb/_snapshots/Downloads.20201125/file1[/FONT]
[FONT=&amp]-rwxrwxr-x 1 user user 23424 Jan 3  2015 /mnt/4tb/_snapshots/Downloads.20201125/file2[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user  34234 Jan 2  2019 /mnt/4tb/_snapshots/Downloads.20201125/file3[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user  52342 Jul 3  2018 /mnt/4tb/_snapshots/Downloads.20201125/file4[/FONT]
[FONT=&amp]-rw-rw-r--  1 user user     2323 May 1  2014 /mnt/4tb/_snapshots/Downloads.20201125/file5[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user 4232 Jul  4  2019 /mnt/4tb/_snapshots/Downloads.20201125/file6[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user     2323 Nov  8  2019 /mnt/4tb/_snapshots/Downloads.20201125/file7[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user    25252 Nov  9  2019 /mnt/4tb/_snapshots/Downloads.20201125/file8[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user    23232 Aug 19  2019 /mnt/4tb/_snapshots/Downloads.20201125/dir1/file1[/FONT]
```

---

### Post by Doug S on 2023-11-25
Your kernel is tainted, with externally built and unsigned modules. Your OS of 18.04.6 is past EOL. Suggest upgrade.
EDIT: Kernel isn't even standard or up to date (I think).

---

### Post by c-tuxe on 2023-11-25
suggestion noted

---

### Post by #&amp;thj^% on 2023-11-25
I was thinking the same as Doug S
Please show:
```
sudo dmesg | grep taint && uname -r

```
Mine will produce:
```
[    4.811141] spl: loading out-of-tree module taints kernel.
[    4.862053] zfs: module license 'CDDL' taints kernel.
[    4.862058] Disabling lock debugging due to kernel taint
[    4.862080] zfs: module license taints kernel.
6.5.0-13-generic

```

---

### Post by c-tuxe on 2023-11-25
> **1fallen said:**
> I was thinking the same as Doug S
Please show:
```
sudo dmesg | grep taint && uname -r

```
Mine will produce:
```
[    4.811141] spl: loading out-of-tree module taints kernel.
[    4.862053] zfs: module license 'CDDL' taints kernel.
[    4.862058] Disabling lock debugging due to kernel taint
[    4.862080] zfs: module license taints kernel.
6.5.0-13-generic

```

Mine only lists vboxdrv as causing tainted kernel, so not sure if that is relevant

---

### Post by c-tuxe on 2023-11-25
My concern is that

```
sudo btrfs subvolume list /mnt/4tb  | grep 20201125
```

produces

```
ID 5635 gen 1940343 top level 2727 path _snapshots/DoWnloads.20201125
```

but 

```
ls -l /mnt/4tb/_snapshots/ | grep 20201125
```

produces

```
drwxr-xr-x 1 user user  1904 Nov 17  2020 Downloads.20201125
```

without the weird capital W. 

I should probably just upgrade everything in case it is a btrfs issue with old kernel or userland tools

---

### Post by #&amp;thj^% on 2023-11-25
Keep us posted then, and Good Luck

---

### Post by MAFoElffen on 2023-11-25
> **c-tuxe said:**
> Sure (with some edits for information governance reasons)

```

[FONT=&amp]-rwxrwxr-x 1 user user 23234 Apr 1  2012 /mnt/4tb/_snapshots/Downloads.20201125/file1[/FONT]
[FONT=&amp]-rwxrwxr-x 1 user user 23424 Jan 3  2015 /mnt/4tb/_snapshots/Downloads.20201125/file2[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user  34234 Jan 2  2019 /mnt/4tb/_snapshots/Downloads.20201125/file3[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user  52342 Jul 3  2018 /mnt/4tb/_snapshots/Downloads.20201125/file4[/FONT]
[FONT=&amp]-rw-rw-r--  1 user user     2323 May 1  2014 /mnt/4tb/_snapshots/Downloads.20201125/file5[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user 4232 Jul  4  2019 /mnt/4tb/_snapshots/Downloads.20201125/file6[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user     2323 Nov  8  2019 /mnt/4tb/_snapshots/Downloads.20201125/file7[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user    25252 Nov  9  2019 /mnt/4tb/_snapshots/Downloads.20201125/file8[/FONT]
[FONT=&amp]-rwxrwxr-x  1 user user    23232 Aug 19  2019 /mnt/4tb/_snapshots/Downloads.20201125/dir1/file1[/FONT]
```
 What did you use as a command to create this? Was there a 'name' override? What was the command that threw the error in post #1 (not shown).

---

