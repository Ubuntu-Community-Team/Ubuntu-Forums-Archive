---
title: "Problems with Dapper system"
date: 2007-05-04
forum: General Help
---

### Post by imekon on 2007-05-04
I thought this might be hardware related, so I checked the hard disks first with the Maxtor test utility - they all check out fine. I then tested memory and that checks out too.

I stopped X from starting - this is a server, not a desktop machine. The mobo has a built in nVidia chipset - the driver causes a hang if leave a screen saver running.

The system is a Duron 1.2GHz on an nVidia2 motherboard with 640MBytes of RAM and three disks. There is a Promise controller with one of the disks on it.

What I saw at first were applications core dumping - nano and mutt did this one day, then were working the next. The clock seems to be drifting - ntpdate seems to bring it back in line.

Now I'm seeing various daemons dying:

```

May  2 00:18:19 xxxxxx kernel: [18226887.832000] Modules linked in: rfcomm l2cap bluetooth appletalk ppdev cpufreq_powersave cpufreq_stats
 cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acp
i sony_acpi ac dev_acpi hotkey ipv6 dm_mod md_mod sr_mod sbp2 ieee1394 parport_pc lp parport rsrc_nonstatic pcmcia_core tsdev sk98lin nvid
ia psmouse serio_raw i2c_nforce2 i2c_core snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm shpchp pci_hotplug rt
c floppy pcspkr nvidia_agp snd_timer agpgart snd soundcore snd_page_alloc evdev reiserfs ide_generic ehci_hcd ohci_hcd usbcore ide_cd cdro
m sata_nv libata scsi_mod generic amd74xx ide_disk pdc202xx_new thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit
 font bitblit softcursor
May  2 00:18:19 xxxxxx kernel: [18226887.832000] CPU:    0
May  2 00:18:19 xxxxxx kernel: [18226887.832000] EIP:    0060:[find_lock_page+61/192]    Tainted: P      VLI
May  2 00:18:19 xxxxxx kernel: [18226887.832000] EFLAGS: 00010006   (2.6.15-28-386)
May  2 00:18:19 xxxxxx kernel: [18226887.832000] EIP is at find_lock_page+0x3d/0xc0
May  2 00:18:19 xxxxxx kernel: [18226887.832000] eax: f55ebf44   ebx: 14000000   ecx: 00000000   edx: 0000319f
May  2 00:18:19 xxxxxx kernel: [18226887.832000] esi: dbccc000   edi: f55ebf44   ebp: 0000319f   esp: dbccdd48
May  2 00:18:19 xxxxxx kernel: [18226887.832000] ds: 007b   es: 007b   ss: 0068
May  2 00:18:19 xxxxxx kernel: [18226887.832000] Process smbd (pid: 26141, threadinfo=dbccc000 task=ce4a2ab0)
May  2 00:18:19 xxxxxx kernel: [18226887.832000] Stack: dbccde98 00000000 000200d2 0000319f c013feab f55ebf40 0000319f c03385a8
May  2 00:18:19 xxxxxx kernel: [18226887.832000]        00000002 dbccde98 00000001 f55ebf40 0000319e f898e401 f55ebf40 0000319f
May  2 00:18:19 xxxxxx kernel: [18226887.832000]        000200d2 00000001 f7813080 c0279ccc 000008af 00000edb 00000001 c02b357e
May  2 00:18:19 xxxxxx kernel: [18226887.832000] Call Trace:
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [find_or_create_page+59/192] find_or_create_page+0x3b/0xc0
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [pg0+945177601/1069368320] reiserfs_prepare_file_region_for_write+0xc1/0x8a0 [reiserfs]
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [kfree_skbmem+60/144] kfree_skbmem+0x3c/0x90
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [tcp_rcv_established+94/2080] tcp_rcv_established+0x5e/0x820
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [tcp_v4_do_rcv+159/240] tcp_v4_do_rcv+0x9f/0xf0
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [pg0+945176890/1069368320] reiserfs_check_for_tail_and_convert+0x1a/0x220 [reiserfs]
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [pg0+945180900/1069368320] reiserfs_file_write+0x504/0x6a0 [reiserfs]
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [__posix_lock_file+397/1584] __posix_lock_file+0x18d/0x630
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [fcntl_getlk64+272/336] fcntl_getlk64+0x110/0x150
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [vfs_write+150/336] vfs_write+0x96/0x150
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [sys_pwrite64+101/128] sys_pwrite64+0x65/0x80
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
May  2 00:18:19 xxxxxx kernel: [18226887.832000] Code: 14 8b 54 24 14 8d 7a 04 89 c6 eb 10 89 f6 89 d8 e8 19 fe ff ff 53 e8 23 a1 00 00 5b
 55 57 e8 9b b8 09 00 89 c3 58 5a 85 db 74 3d <8b> 03 f6 c4 40 75 65 89 d8 ff 40 04 0f ba 2b 00 19 c0 85 c0 74
May  2 00:18:19 xxxxxx kernel: [18226887.832000]  <6>note: smbd[26141] exited with preempt_count 1

```

then

```

May  2 00:42:21 xxxxxx kernel: [18228330.084000] c01553d1
May  2 00:42:21 xxxxxx kernel: [18228330.100000] PREEMPT
May  2 00:42:21 xxxxxx kernel: [18228330.100000] Modules linked in: rfcomm l2cap bluetooth appletalk ppdev cpufreq_powersave cpufreq_stats
 cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table tc1100_wmi video acpi_sbs battery i2c_acpi_ec container button pcc_acp
i sony_acpi ac dev_acpi hotkey ipv6 dm_mod md_mod sr_mod sbp2 ieee1394 parport_pc lp parport rsrc_nonstatic pcmcia_core tsdev sk98lin nvid
ia psmouse serio_raw i2c_nforce2 i2c_core snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm shpchp pci_hotplug rt
c floppy pcspkr nvidia_agp snd_timer agpgart snd soundcore snd_page_alloc evdev reiserfs ide_generic ehci_hcd ohci_hcd usbcore ide_cd cdro
m sata_nv libata scsi_mod generic amd74xx ide_disk pdc202xx_new thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit
 font bitblit softcursor
May  2 00:42:21 xxxxxx kernel: [18228330.100000] CPU:    0
May  2 00:42:21 xxxxxx kernel: [18228330.100000] EIP:    0060:[anon_vma_unlink+33/112]    Tainted: P      VLI
May  2 00:42:21 xxxxxx kernel: [18228330.100000] EFLAGS: 00010202   (2.6.15-28-386)
May  2 00:42:21 xxxxxx kernel: [18228330.100000] EIP is at anon_vma_unlink+0x21/0x70
May  2 00:42:21 xxxxxx kernel: [18228330.100000] eax: e6512000   ebx: eefe1314   ecx: 00000000   edx: 00000000
May  2 00:42:21 xxxxxx kernel: [18228330.100000] esi: eefe12dc   edi: 93000000   ebp: 00000000   esp: e6513f1c
May  2 00:42:21 xxxxxx kernel: [18228330.100000] ds: 007b   es: 007b   ss: 0068
May  2 00:42:21 xxxxxx kernel: [18228330.100000] Process imap (pid: 26125, threadinfo=e6512000 task=e4f84570)
May  2 00:42:21 xxxxxx kernel: [18228330.100000] Stack: eefe1d84 eefe12dc b7e0d000 c014e74a eefe12dc e6513f70 eefe1284 e6512000
May  2 00:42:21 xxxxxx kernel: [18228330.100000]        dfcd5060 c0153c33 e6513f70 eefe1284 00000000 00000000 e6513f70 eefe1284
May  2 00:42:21 xxxxxx kernel: [18228330.100000]        00000000 ffffffff e6513f6c 00000000 000000b1 c03dc944 dfcd5060 e4f84570
May  2 00:42:21 xxxxxx kernel: [18228330.100000] Call Trace:
May  2 00:42:21 xxxxxx kernel: [18228330.100000]  [free_pgtables+154/192] free_pgtables+0x9a/0xc0
May  2 00:42:21 xxxxxx kernel: [18228330.100000]  [exit_mmap+115/240] exit_mmap+0x73/0xf0
May  2 00:42:21 xxxxxx kernel: [18228330.100000]  [mmput+45/144] mmput+0x2d/0x90
May  2 00:42:21 xxxxxx kernel: [18228330.100000]  [do_exit+209/1008] do_exit+0xd1/0x3f0
May  2 00:42:21 xxxxxx kernel: [18228330.100000]  [do_group_exit+47/176] do_group_exit+0x2f/0xb0
May  2 00:42:21 xxxxxx kernel: [18228330.100000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
May  2 00:42:21 xxxxxx kernel: [18228330.100000] Code: e9 75 75 19 00 90 8d 74 26 00 57 56 53 8b 74 24 10 8b 7e 40 85 ff 74 36 b8 00 e0 ff
 ff 21 e0 ff 40 14 8d 5e 38 8b 4e 38 8b 53 04 <89> 51 04 89 0a c7 46 38 00 01 10 00 c7 43 04 00 02 20 00 8b 1f
May  2 00:42:21 xxxxxx kernel: [18228330.100000]  <1>Fixing recursive fault but reboot is needed!
May  2 00:42:21 xxxxxx kernel: [18228330.380000]  [schedule+1474/1680] schedule+0x5c2/0x690
May  2 00:42:21 xxxxxx kernel: [18228330.388000]  [tasklet_action+58/112] tasklet_action+0x3a/0x70
May  2 00:42:21 xxxxxx kernel: [18228330.396000]  [__do_softirq+79/176] __do_softirq+0x4f/0xb0
May  2 00:42:21 xxxxxx kernel: [18228330.404000]  [irq_exit+53/64] irq_exit+0x35/0x40
May  2 00:42:21 xxxxxx kernel: [18228330.412000]  [do_IRQ+31/48] do_IRQ+0x1f/0x30
May  2 00:42:21 xxxxxx kernel: [18228330.416000]  [do_exit+728/1008] do_exit+0x2d8/0x3f0
May  2 00:42:21 xxxxxx kernel: [18228330.424000]  [die+355/368] die+0x163/0x170
May  2 00:42:21 xxxxxx kernel: [18228330.432000]  [do_page_fault+489/1562] do_page_fault+0x1e9/0x61a
May  2 00:42:21 xxxxxx kernel: [18228330.436000]  [anon_vma_unlink+33/112] anon_vma_unlink+0x21/0x70
May  2 00:42:21 xxxxxx kernel: [18228330.444000]  [do_page_fault+0/1562] do_page_fault+0x0/0x61a
May  2 00:42:21 xxxxxx kernel: [18228330.448000]  [error_code+79/96] error_code+0x4f/0x60
May  2 00:42:21 xxxxxx kernel: [18228330.456000]  [anon_vma_unlink+33/112] anon_vma_unlink+0x21/0x70
May  2 00:42:21 xxxxxx kernel: [18228330.460000]  [free_pgtables+154/192] free_pgtables+0x9a/0xc0
May  2 00:42:21 xxxxxx kernel: [18228330.464000]  [exit_mmap+115/240] exit_mmap+0x73/0xf0
May  2 00:42:21 xxxxxx kernel: [18228330.472000]  [mmput+45/144] mmput+0x2d/0x90
May  2 00:42:21 xxxxxx kernel: [18228330.476000]  [do_exit+209/1008] do_exit+0xd1/0x3f0
May  2 00:42:21 xxxxxx kernel: [18228330.484000]  [do_group_exit+47/176] do_group_exit+0x2f/0xb0
May  2 00:42:21 xxxxxx kernel: [18228330.488000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79

```

Finally I saw a kernel panic (can't find it in the logs now).

Is this a hardware fault or something else? This is a system which has been running Dapper for quite a while - then recently all these issues start to show up. I've been using

```

apt-get update
apt-get upgrade

```

to keep the system up to date.

---

