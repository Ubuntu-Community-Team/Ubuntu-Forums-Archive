---
title: "Kernel OOPS when swapping"
date: 2007-07-15
forum: General Help
---

### Post by kelt65 on 2007-07-15
I have a i386 PC system with 2GB RAM / 1GB swap, Feisty.

As soon as the system begins to swap I start getting oopses, caused by kswapd. It eventually will panic if I don't reboot. I'm running  2.6.20-16-386. Is anyone else getting oopses like this?

My sysctl settings are at the defaults.

---

### Post by tgalati4 on 2007-07-15
You may need 2 to 2.5 GB of swap.  If swap is less than physical RAM then bad things can happen.  If you can't resize your swap, take out a stick of RAM.

---

### Post by southernman on 2007-07-15
@tgalati4 - I've read that with ram approaching the capacities it is, that there is really no need to use a swap partition. IYO, is that a correct statement?

---

### Post by kelt65 on 2007-07-17
Well, while my swap might be insufficient (actually it hardly ever swaps), that is not the problem here. This happens as soon as the system begins using swap.
Can defective RAM cause this?

Here's the oops if anyone can make better sense of it :

[[FONT="Courier New"]162686.265592] BUG: unable to handle kernel paging request at virtual address 970a7124
[162686.265602]  printing eip:
[162686.265604] c0174f2d
[162686.265606] *pde = 00000000
[162686.265611] Oops: 0000 [#1]
[162686.265613] Modules linked in: isofs udf bluetooth vmnet(P) vmblock(P) vmmon(P) binfmt
_misc nfs nfsd exportfs lockd sunrpc ppdev autofs4 ipv6 cpufreq_userspace cpufreq_stats cp
ufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative tc1100_wmi sony_acpi pcc_
acpi dev_acpi video sbs i2c_ec dock container button battery asus_acpi backlight ac reiser
fs it87 hwmon_vid eeprom i2c_isa psmouse parport_pc lp parport snd_emu10k1_synth snd_emux_
synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_util_mem s
nd_hwdep snd_pcm_oss snd_pcm snd_page_alloc snd_mixer_oss snd_seq_dummy snd_seq_oss pcspkr
 usbhid hid rtc snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_devi
ce nvidia(P) ide_cd serio_raw snd soundcore emu10k1_gp gameport via_agp i2c_viapro i2c_cor
e agpgart shpchp pci_hotplug af_packet evdev tsdev jfs via82cxxx generic sd_mod sg sr_mod
cdrom ehci_hcd uhci_hcd usbcore ata_generic sata_via libata aic7xxx scsi_transport_spi scs
i_mod e1000 raid10 raid456 xor raid1 raid0 multipath linear md_mod thermal processor fan d
m_mod fbcon tileblit font bitblit softcursor vesafb capability commoncap
[162686.265683] CPU:    0
[162686.265685] EIP:    0060:[<c0174f2d>]    Tainted: P      VLI
[162686.265686] EFLAGS: 00010282   (2.6.20-16-386 #2)
[162686.265696] EIP is at iput+0x1d/0x70
[162686.265700] eax: 970a7110   ebx: ecffb400   ecx: f95d5b20   edx: ecffb400
[162686.265703] esi: ecffb400   edi: 00000000   ebp: f514d03c   esp: c2199ed0
[162686.265706] ds: 007b   es: 007b   ss: 0068
[162686.265709] Process kswapd0 (pid: 144, ti=c2198000 task=c2242a70 task.ti=c2198000)
[162686.265711] Stack: d7eabab4 c0173174 dcafe4a4 0000006b d7eabab4 0000006a c0173ee4 d7ea
bab4
[162686.265717]        0000006a c01740d4 00003bc4 00000081 dfffeaa0 000000d0 c0174147 c014
e92f
[162686.265723]        00005800 00000000 00000000 00000002 00000000 00000000 00000080 0007
4fc5
[162686.265728] Call Trace:
[162686.265732]  [<c0173174>] dentry_iput+0x44/0x90
[162686.265739]  [<c0173ee4>] prune_one_dentry+0x54/0x80
[162686.265745]  [<c01740d4>] prune_dcache+0x104/0x140
[162686.265752]  [<c0174147>] shrink_dcache_memory+0x37/0x40
[162686.265756]  [<c014e92f>] shrink_slab+0xff/0x160
[162686.265771]  [<c014ed76>] kswapd+0x326/0x410
[162686.265791]  [<c012ded0>] autoremove_wake_function+0x0/0x50
[162686.265806]  [<c014ea50>] kswapd+0x0/0x410
[162686.265809]  [<c012dbf8>] kthread+0xa8/0xe0
[162686.265815]  [<c012db50>] kthread+0x0/0xe0
[162686.265821]  [<c0104207>] kernel_thread_helper+0x7/0x10
[162686.265831]  =======================
[162686.265833] Code: 5f 5d c3 8d 74 26 00 8d bc 27 00 00 00 00 85 c0 53 89 c3 74 4f 8b 80 88 00 00 00 83 bb 14 01 00 00 20 8b 40 20 74 49
 85 c0 74 0b <8b> 50 14 85 d2 74 04 89 d8 ff d2 8d 43 24 ba c0 c9 44 c0 e8 4b
[162686.265854] EIP: [<c0174f2d>] iput+0x1d/0x70 SS:ESP 0068:c2199ed0
[162686.265859][/FONT]

---

### Post by Rui Pais on 2007-07-17
hi,

i had weird problems once with swap, like yours, and they were caused by a bad formated swap (something failed when i make/format the partition...)

Try to boot from recovery or a live cd, format the partition again, check if UUIDs are correct on /etc/fstab and reboot.

Another solution would be turn off swap of (no it's not needed if you have 2G of RAM) and do all format and fstab edit with the live OS without problems. After format just need a mount -a or a manual sudo swapon <device>

good luck

---

### Post by kelt65 on 2007-07-17
I tried making a new swapfile and turning off the old partition, but get the same problems.

This started happening with 2.6.20

This is an Athlon 2GHz, 2GB ram, i386.

---

### Post by Rui Pais on 2007-07-17
mmm... bad luck.

Maybe go back then to the previous version of the kernel. 
Btw have you tried the 2.6.20-16-generic? are you using the i386 for some specific reason?

---

