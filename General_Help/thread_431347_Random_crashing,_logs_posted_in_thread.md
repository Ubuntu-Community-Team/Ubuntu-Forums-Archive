---
title: "Random crashing, logs posted in thread"
date: 2007-05-02
forum: General Help
---

### Post by atomicfire on 2007-05-02
My system is an up to date Fiesty desktop with a MythTV setup, nVidia GeForce 2 MX400 video card, and 512mb of ram on a P4.

The computer will just randomly hardlock. Here is the log from /var/log/messages, and since I am a Red Hat user, I really don't know how to read these files and interprept what caused the crash. Any help is apprecieated.

May  2 22:06:50 Baccus kernel: [ 3716.499900] eth1: Link autonegation speed 100M bps full duplex
May  2 22:06:52 Baccus kernel: [ 3718.570848] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  2 22:06:55 Baccus dhcpd: DHCPDISCOVER from 00:50:2c:0a:35:88 (Baccus) via eth1
May  2 22:06:56 Baccus dhcpd: DHCPOFFER on 192.168.1.101 to 00:50:2c:0a:35:88 (Baccus) via eth1
May  2 22:06:56 Baccus dhcpd: Wrote 6 leases to leases file.
May  2 22:06:56 Baccus dhcpd: DHCPREQUEST for 192.168.1.101 (192.168.1.1) from 00:50:2c:0a:35:88 (Baccus) via eth1
May  2 22:06:56 Baccus dhcpd: DHCPACK on 192.168.1.101 to 00:50:2c:0a:35:88 (Baccus) via eth1
May  2 22:07:37 Baccus gconfd (root-7856): GConf server is not in use, shutting down.
May  2 22:07:37 Baccus gconfd (root-7856): Exiting
May  2 22:25:54 Baccus -- MARK --
May  2 22:45:55 Baccus -- MARK --
May  2 23:05:55 Baccus -- MARK --

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857486] Oops: 0002 [#1]

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857488] SMP

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857635] CPU:    0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857636] EIP:    0060:[cache_alloc_refill+298/1360]    Tainted: P      VLI

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857637] EFLAGS: 00010046   (2.6.20-15-generic #2)

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857651] EIP is at cache_alloc_refill+0x12a/0x550

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857655] eax: de63a7c0   ebx: 00000003   ecx: 0000000c   edx: 211a1f29

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857660] esi: 00000008   edi: d7742000   ebp: dfa587c0   esp: d2593d00

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857663] ds: 007b   es: 007b   ss: 0068

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857667] Process squid (pid: 5558, ti=d2592000 task=c8522560 task.ti=d2592000)

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857670] Stack: 00000010 00000050 00000001 00000050 dffb4540 dfb6cc00 de63a7c0 00000000

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857680]        c7d53d78 00000001 da0ef438 00000000 c760cac0 d774201c 00000246 00000050

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857690]        dffb4540 002f8351 c0172c00 00000000 df9f9800 df9f9800 e098e58f c0189d06

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857700] Call Trace:

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857773]  [kmem_cache_alloc+128/144] kmem_cache_alloc+0x80/0x90

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857794]  [<e098e58f>] ext3_alloc_inode+0xf/0x40 [ext3]

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857819]  [alloc_inode+22/384] alloc_inode+0x16/0x180

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857839]  [iget_locked+87/320] iget_locked+0x57/0x140

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857870]  [<e098e259>] ext3_lookup+0x89/0x100 [ext3]

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857889]  [d_alloc+263/400] d_alloc+0x107/0x190

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857918]  [do_lookup+328/400] do_lookup+0x148/0x190

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.857956]  [__link_path_walk+2151/3696] __link_path_walk+0x867/0xe70

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858043]  [link_path_walk+69/192] link_path_walk+0x45/0xc0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858083]  [sched_balance_self+347/752] sched_balance_self+0x15b/0x2f0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858148]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858181]  [__path_lookup_intent_open+81/160] __path_lookup_intent_open+0x51/0xa0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858210]  [path_lookup_open+32/48] path_lookup_open+0x20/0x30

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858231]  [open_namei+90/1552] open_namei+0x5a/0x610

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858247]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858266]  [ack_apic+13/16] ack_apic+0xd/0x10

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858275]  [handle_fasteoi_irq+155/240] handle_fasteoi_irq+0x9b/0xf0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858307]  [do_filp_open+51/96] do_filp_open+0x33/0x60

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858352]  [sched_balance_self+347/752] sched_balance_self+0x15b/0x2f0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858412]  [do_sys_open+78/240] do_sys_open+0x4e/0xf0

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858444]  [sys_open+28/32] sys_open+0x1c/0x20
May  2 23:19:51 Baccus kernel: [ 8095.857478] c0172d3a
May  2 23:19:51 Baccus kernel: [ 8095.857494] Modules linked in: binfmt_misc rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_stats cpufreq_powersave cpufreq_ondemand cpufreq_userspace freq_table cpufreq_conservative sony_acpi dev_acpi tc1100_wmi pcc_acpi battery button container video ac dock sbs i2c_ec asus_acpi backlight btaudio lp fuse snd_atiixp snd_ac97_codec nvidia(P) psmouse xpad ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss parport_pc parport snd_seq_midi snd_rawmidi bt878 serio_raw snd_seq_midi_event snd_seq snd_timer snd_seq_device pcspkr i2c_piix4 tuner msp3400 bttv video_buf ir_common compat_ioctl32 i2c_algo_bit btcx_risc tveeprom videodev v4l2_common v4l1_compat i2c_core snd soundcore snd_page_alloc shpchp ati_agp agpgart pci_hotplug af_packet ipt_MASQUERADE ipt_REDIRECT xt_tcpudp iptable_nat nf_nat nf_conntrack_ipv4 xt_state nf_conntrack nfnetlink xt_multiport iptable_filter ip_tables x_tables tsdev joydev evdev ipv6 ext3 jbd mbcache ide_cd cdrom ide_disk usbhid hid atiix
May  2 23:19:51 Baccus kernel:  generic ata_generic libata scsi_mod via_velocity crc_ccitt tulip ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
May  2 23:19:51 Baccus squid[5556]: Squid Parent: child process 5558 exited due to signal 11

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858453]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858530]  =======================

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858532] Code: 8b 77 14 8b 44 24 34 03 57 0c 8b 34 b0 8d 41 01 89 77 14 89 54 8d 14 89 45 00 8b 44 24 10 8b 77 10 3b 70 3c 72 be 8b 17 8b 47 04 <89> 42 04 89 10 83 7f 14 ff c7 07 00 01 10 00 c7 47 04 00 02 20

Message from syslogd@Baccus at Wed May  2 23:19:51 2007 ...
Baccus kernel: [ 8095.858584] EIP: [cache_alloc_refill+298/1360] cache_alloc_refill+0x12a/0x550 SS:ESP 0068:d2593d00

---

### Post by atomicfire on 2007-05-04
bump, looking for help please :)

---

### Post by public_void on 2007-05-04
It looks like the log is for a process squid. The log gives the values of the CPU registers, a stack trace, a call trace and modules loaded. It also says that child of this processed exit with a signal 11. This is usually a program trying to access an area of memory it shouldn't. This probably isn't the cause, but a reaction from its parent crashing.

---

