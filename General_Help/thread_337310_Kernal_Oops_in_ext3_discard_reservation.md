---
title: "Kernal Oops in ext3_discard_reservation"
date: 2007-01-12
forum: General Help
---

### Post by Jaykul on 2007-01-12
Well, I'm not really sure what to say here.  My /home dirs  are on a seperate hard drive in reiserfs, but pretty much everything else is on an 80GB drive (the swap and the main partition, which is ext3).

This is just an experimentation and backup server for the house, so it's running everything from apache and tomcat to ejabberd, as well as CUPS and SAMBA for our printer and Windows file shares ... this afternoon I was SSHd in, running popfile and checking my mail ... when I suddenly got a bunch of messages from syslogd ... quick examination of my dmesg shows this:

> 
[45986458.650000] BUG: unable to handle kernel paging request at virtual address 0400001c
[45986458.650000]  printing eip:
[45986458.650000] e0916b6a
[45986458.650000] *pde = 08e2f001
[45986458.650000] Oops: 0000 [#1]
[45986458.650000] SMP
[45986458.650000] Modules linked in: reiserfs ipv6 dm_mod md_mod af_packet lp snd_seq_dummy snd_seq_oss snd_seq_midi s      nd_seq_midi_event snd_seq snd_via82xx snd_ac97_codec snd_ac97_bus i2c_viapro usblp snd_pcm_oss snd_mixer_oss analog i2      c_core snd_pcm snd_timer snd_page_alloc floppy via_ircc psmouse serio_raw pcspkr gameport evdev parport_pc parport snd      _mpu401 snd_mpu401_uart snd_rawmidi snd_seq_device irda snd 8139too via_agp shpchp pci_hotplug crc_ccitt soundcore mii       agpgart ext3 jbd ehci_hcd uhci_hcd ohci_hcd usbcore ide_generic ide_cd cdrom ide_disk via82cxxx generic thermal proce      ssor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[45986458.650000] CPU:    0
[45986458.650000] EIP:    0060:[<e0916b6a>]    Tainted: G S    VLI
[45986458.650000] EFLAGS: 00010206   (2.6.17-10-server #2)
[45986458.650000] EIP is at ext3_discard_reservation+0x2a/0x80 [ext3]
[45986458.650000] eax: df9ef400   ebx: cd5318a4   ecx: 00000000   edx: ffffffff
[45986458.650000] esi: 04000000   edi: 04000018   ebp: dfd56000   esp: dff07ed4
[45986458.650000] ds: 007b   es: 007b   ss: 0068
[45986458.650000] Process kswapd0 (pid: 108, threadinfo=dff06000 task=dff7b050)
[45986458.650000] Stack: cd53180c cd5318a4 04000000 00000033 e092235a cd5318a4 00000000 dff07f24
[45986458.650000]        c0183fbd dff07f24 cd5318ac cd5318a4 c01842fa 00000080 d6cc60d4 00000080
[45986458.650000]        dff07f24 c018452b 00000000 00000080 cd531aa0 c73e4e88 00004970 00000091
[45986458.650000] Call Trace:
[45986458.650000]  <e092235a> ext3_clear_inode+0x5a/0x90 [ext3]  <c0183fbd> clear_inode+0x9d/0x120
[45986458.650000]  <c01842fa> dispose_list+0x1a/0xe0  <c018452b> shrink_icache_memory+0x16b/0x240
[45986458.650000]  <c0153767> shrink_slab+0x117/0x180  <c0154549> kswapd+0x359/0x440
[45986458.650000]  <c0135020> autoremove_wake_function+0x0/0x50  <c01541f0> kswapd+0x0/0x440
[45986458.650000]  <c0101005> kernel_thread_helper+0x5/0x10
[45986458.650000] Code: 00 83 ec 10 89 1c 24 89 c3 89 74 24 04 89 7c 24 08 89 6c 24 0c 8b 70 bc 8b 80 9c 00 00 00 85 f      6 8b a8 60 01 00 00 74 0a 8d 7e 18 <8b> 47 04 85 c0 75 13 8b 1c 24 8b 74 24 04 8b 7c 24 08 8b 6c 24
[45986458.650000] EIP: [<e0916b6a>] ext3_discard_reservation+0x2a/0x80 [ext3] SS:ESP 0068:dff07ed4
[45986458.650000]


One of the drives is fairly old, but I've never really had any problems, and it's got over a month uptime ... :-k should I be freaking out and finding a replacement hard drive, or is this just some random one time thing?

---

### Post by dtfinch on 2007-01-13
Ext3 reservations are fairly new (couple years or so), supposed to improve performance and reduce fragmentation. I think I saw a post a some time ago from a rhel or centos user who had a reservation related problem writing too much too fast at once, backing up large files, but I can't find it now. I couldn't find how to disable the feature either, short of a kernel recompile, as it's probably assumed to work by now.

Do you use rsync or something similar for your backups? Differential backups are much faster and less disk intense than a straight copy. Cwrsync is a good Windows port. BackupPC is supposedly a good rsync-like backup system for multiple desktops, and more space efficient, but I've never tried it. A last resort would be to throttle your backups, but you shouldn't have to do that, and if you have anything less than a gigabit network, the problem is likely something else entirely.

---

