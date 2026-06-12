---
title: "Kernel Panic when writing to raid5 array"
date: 2006-12-01
forum: General Help
---

### Post by neversphere on 2006-12-01
I upgraded to Ubuntu 6.10 and things were going well until I decided to increase my storage capacity. I bought 3 new drives, installed them and created a new array in evms. So far so good. I started moving data from my old raid5 array to my new larger raid 5 array when I received a kernel panic. Thinking this was bizarre I downloaded the latest kernel source and compiled my own kernel. I'm now getting a kernel oops instead of a panic but I'm still unable to copy any data. Has anyone else experienced this? Syslog attached:

Nov 30 23:35:53 raidbox kernel: [  484.129986] ------------[ cut here ]------------
Nov 30 23:35:53 raidbox kernel: [  484.130074] kernel BUG at drivers/md/raid5.c:247!
Nov 30 23:35:53 raidbox kernel: [  484.130169] invalid opcode: 0000 [#1]
Nov 30 23:35:53 raidbox kernel: [  484.130247] Modules linked in: ext2 raid456 xor md_mod af_packet dm_mod parport_pc lp parport evdev psmouse serio_raw shpchp pci
_hotplug nvidia_agp i2c_amd756 i2c_core agpgart snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc f
loppy forcedeth pcspkr ext3 jbd mbcache ohci_hcd usbcore ide_generic siimage ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan
Nov 30 23:35:53 raidbox kernel: [  484.132916] CPU:    0
Nov 30 23:35:53 raidbox kernel: [  484.132918] EIP:    0060:[pg0+143380727/1069298688]    Not tainted VLI
Nov 30 23:35:53 raidbox kernel: [  484.132920] EFLAGS: 00010096   (2.6.18.3-try2 #1)
Nov 30 23:35:53 raidbox kernel: [  484.133093] EIP is at get_active_stripe+0x327/0x450 [raid456]
Nov 30 23:35:53 raidbox kernel: [  484.133152] eax: 00000042   ebx: c6bec360   ecx: c033a9c0   edx: c033a9c0
Nov 30 23:35:53 raidbox kernel: [  484.133213] esi: 00000002   edi: c6bec258   ebp: 00000000   esp: c7f1fabc
Nov 30 23:35:53 raidbox kernel: [  484.133272] ds: 007b   es: 007b   ss: 0068
Nov 30 23:35:53 raidbox kernel: [  484.133327] Process pdflush (pid: 134, ti=c7f1e000 task=c7fb4ab0 task.ti=c7f1e000)
Nov 30 23:35:53 raidbox kernel: [  484.133388] Stack: c8d0fcd7 0b8d5398 00000000 00000002 00000000 46000000 00000000 00000000
Nov 30 23:35:53 raidbox kernel: [  484.133779]        c6b3ba68 46000000 00000000 0b8d5398 00000000 000009cc c6b3b9c0 00000000
Nov 30 23:35:53 raidbox kernel: [  484.134169]        002e354e 00000000 171aa718 00000018 00000003 c3c29900 00000002 00000000
Nov 30 23:35:53 raidbox kernel: [  484.134559] Call Trace:
Nov 30 23:35:53 raidbox kernel: [  484.134665]  [pg0+143402897/1069298688] make_request+0x1d1/0x6c0 [raid456]
Nov 30 23:35:53 raidbox kernel: [  484.134780]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
Nov 30 23:35:53 raidbox kernel: [  484.134893]  [generic_make_request+199/576] generic_make_request+0xc7/0x240
Nov 30 23:35:53 raidbox kernel: [  484.135005]  [bio_clone+48/64] bio_clone+0x30/0x40
Nov 30 23:35:53 raidbox kernel: [  484.135101]  [pg0+142992575/1069298688] __map_bio+0x3f/0xc0 [dm_mod]
Nov 30 23:35:53 raidbox kernel: [  484.135220]  [pg0+142993492/1069298688] __split_bio+0x184/0x460 [dm_mod]
Nov 30 23:35:53 raidbox kernel: [  484.135325]  [ide_do_request+1562/2032] ide_do_request+0x61a/0x7f0
Nov 30 23:35:53 raidbox kernel: [  484.135431]  [freed_request+42/96] freed_request+0x2a/0x60
Nov 30 23:35:53 raidbox kernel: [  484.135530]  [pg0+142996087/1069298688] dm_request+0x97/0xd0 [dm_mod]
Nov 30 23:35:53 raidbox kernel: [  484.135634]  [generic_make_request+199/576] generic_make_request+0xc7/0x240
Nov 30 23:35:53 raidbox kernel: [  484.135728]  [generic_make_request+199/576] generic_make_request+0xc7/0x240
Nov 30 23:35:53 raidbox kernel: [  484.135831]  [__do_IRQ+160/224] __do_IRQ+0xa0/0xe0
Nov 30 23:35:53 raidbox kernel: [  484.135925]  [mempool_alloc+47/208] mempool_alloc+0x2f/0xd0
Nov 30 23:35:53 raidbox kernel: [  484.136025]  [submit_bio+74/224] submit_bio+0x4a/0xe0
Nov 30 23:35:53 raidbox kernel: [  484.136127]  [bio_add_page+55/80] bio_add_page+0x37/0x50
Nov 30 23:35:53 raidbox kernel: [  484.136218]  [mpage_end_io_read+0/128] mpage_end_io_read+0x0/0x80
Nov 30 23:35:53 raidbox kernel: [  484.136316]  [mpage_bio_submit+25/32] mpage_bio_submit+0x19/0x20
Nov 30 23:35:53 raidbox kernel: [  484.136410]  [__mpage_writepage+652/1824] __mpage_writepage+0x28c/0x720
Nov 30 23:35:53 raidbox kernel: [  484.136506]  [pg0+143097264/1069298688] ext2_get_block+0x0/0x650 [ext2]
Nov 30 23:35:53 raidbox kernel: [  484.136641]  [find_get_pages_tag+39/112] find_get_pages_tag+0x27/0x70
Nov 30 23:35:53 raidbox kernel: [  484.136736]  [pg0+143002301/1069298688] dm_table_any_congested+0xd/0x50 [dm_mod]
Nov 30 23:35:53 raidbox kernel: [  484.136847]  [mpage_writepages+862/1008] mpage_writepages+0x35e/0x3f0
Nov 30 23:35:53 raidbox kernel: [  484.136942]  [pg0+143093280/1069298688] ext2_writepage+0x0/0x10 [ext2]
Nov 30 23:35:53 raidbox kernel: [  484.137041]  [pg0+143097264/1069298688] ext2_get_block+0x0/0x650 [ext2]
Nov 30 23:35:53 raidbox kernel: [  484.137159]  [do_writepages+43/80] do_writepages+0x2b/0x50
Nov 30 23:35:53 raidbox kernel: [  484.137255]  [__writeback_single_inode+137/880] __writeback_single_inode+0x89/0x370
Nov 30 23:35:53 raidbox kernel: [  484.137355]  [pg0+143002301/1069298688] dm_table_any_congested+0xd/0x50 [dm_mod]
Nov 30 23:35:53 raidbox kernel: [  484.137465]  [sync_sb_inodes+369/560] sync_sb_inodes+0x171/0x230
Nov 30 23:35:53 raidbox kernel: [  484.137562]  [writeback_inodes+99/128] writeback_inodes+0x63/0x80
Nov 30 23:35:53 raidbox kernel: [  484.137657]  [background_writeout+125/160] background_writeout+0x7d/0xa0
Nov 30 23:35:53 raidbox kernel: [  484.137759]  [pdflush+0/384] pdflush+0x0/0x180
Nov 30 23:35:53 raidbox kernel: [  484.137852]  [pdflush+197/384] pdflush+0xc5/0x180
Nov 30 23:35:53 raidbox kernel: [  484.137945]  [background_writeout+0/160] background_writeout+0x0/0xa0
Nov 30 23:35:53 raidbox kernel: [  484.138041]  [kthread+228/240] kthread+0xe4/0xf0
Nov 30 23:35:53 raidbox kernel: [  484.138134]  [kthread+0/240] kthread+0x0/0xf0
Nov 30 23:35:53 raidbox kernel: [  484.138227]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Nov 30 23:35:53 raidbox kernel: [  484.138323] Code: 44 24 1c 8b 44 24 24 89 74 24 0c 89 54 24 04 89 4c 24 08 89 44 24 14 8b 44 24 28 c7 04 24 d7 fc d0 c8 89 44 24
 10 e8 a9 d9 41 f7 <0f> 0b f7 00 c4 fc d0 c8 89 d8 c7 43 68 00 00 00 00 e8 93 0e 46
Nov 30 23:35:53 raidbox kernel: [  484.140735] EIP: [pg0+143380727/1069298688] get_active_stripe+0x327/0x450 [raid456] SS:ESP 0068:c7f1fabc

---

### Post by Merkidemis on 2007-10-19
I am getting something simular when copying to my RAID5 array.  I have an 8 disk (200GB drives) array running on an 3Ware 7810 card.  This is a PATA controller.

I am able to write too it, for a while.  After several gigs of writing, it either opps or panics and freezes the machine.  It doesn't seem to happen when doing large reads, and if its left idle it will stay up for days.  Writing I can bring it down in 10-20min.

I had simular issues when I was running the same setup under Windows (yes, I've reformatted the array to ext3).  In the Windows case, the computer would reboot itself.

I haven't tried much to narrow the problem down, though I have swapped RAM modules.  Two other things I think could be causing this from a hardware perspective are the controller card iteslf (could it be getting too hot while doing the parity calculations?  The case is pretty well ventalated, but the IDE cables are smooshed against the card), and it is somewhat old and tired, or the PSU.  The PSU is a 500W Ultra, which was probably a bad move on my part to get that brand.  The machine is running 9 hard drives (8 in the array + 1 60GB for the OS and such), a socket AM2 Athlon 64 3000+, and a low ball nVidia based PCIe video card.  Its a server, so I got the cheapest card I could.

The fact that I was seeing simular behavior in Windows lead me to think its more of a hardware issuse then software, but I'll post the syslog when I get home to see if anyone can see anything there.

---

### Post by fjgaude on 2007-10-20
Seems as if you have pointed to the solution to your problem, eh? Get some new hardware and get a better case for more venilation.

---

### Post by Merkidemis on 2007-10-21
Potential source of the problem, yes.  The case is pretty well vented, side panel removed and 3 120mm fans up front.

As for the better hardware, I do have a new server build in the pipeline for spring.

---

