---
title: "kernel problem in feisty"
date: 2007-08-20
forum: General Help
---

### Post by anirudh.iitm on 2007-08-20
I have been getting this problem in feisty lately.

```

[48885.363368] BUG: unable to handle kernel paging request at virtual address 00dfd93a
[48885.363377]  printing eip:
[48885.363379] c01898d4
[48885.363381] *pde = 00000000
[48885.363386] Oops: 0000 [#1]
[48885.363388] SMP 
[48885.363392] Modules linked in: usb_storage libusual binfmt_misc rfcomm l2cap bluetooth ppdev i915 drm ipv6 speedstep_lib cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table cpufreq_powersave tc1100_wmi dev_acpi sony_acpi pcc_acpi asus_acpi dock battery container video sbs i2c_ec i2c_core backlight ac button lp fuse snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iTCO_wdt iTCO_vendor_support snd_seq snd_timer serio_raw snd_seq_device parport_pc parport snd soundcore psmouse pcspkr af_packet snd_page_alloc shpchp pci_hotplug intel_agp agpgart tsdev evdev ext3 jbd mbcache sg sd_mod sr_mod cdrom generic ata_generic ehci_hcd ata_piix libata scsi_mod e100 mii uhci_hcd usbcore thermal processor fan capability commoncap vesafb fbcon tileblit font bitblit softcursor
[48885.363490] CPU:    1
[48885.363491] EIP:    0060:[<c01898d4>]    Not tainted VLI
[48885.363493] EFLAGS: 00010283   (2.6.20-16-generic #2)
[48885.363503] EIP is at iput+0x14/0x70
[48885.363506] eax: 00dfd91a   ebx: f5e2f0d5   ecx: f5e2f0ec   edx: e8000000
[48885.363510] esi: 00000023   edi: 00000000   ebp: dfd91a3c   esp: dff35ee0
[48885.363513] ds: 007b   es: 007b   ss: 0068
[48885.363516] Process kswapd0 (pid: 162, ti=dff34000 task=c1999030 task.ti=dff34000)
[48885.363519] Stack: f0c7242c c0188514 f0c7242c 00000023 c018866b 00000a28 00000080 dfffeaa0 
[48885.363528]        000000d0 c01886f7 c016053d 000058dc 00000000 00000000 00000002 00000000 
[48885.363536]        c0429e80 00000000 00000180 00037c8f 00000060 00000002 c03aa280 c03a9c00 
[48885.363545] Call Trace:
[48885.363551]  [<c0188514>] prune_one_dentry+0x54/0x80
[48885.363562]  [<c018866b>] prune_dcache+0x12b/0x180
[48885.363576]  [<c01886f7>] shrink_dcache_memory+0x37/0x40
[48885.363581]  [<c016053d>] shrink_slab+0x11d/0x180
[48885.363614]  [<c01609a6>] kswapd+0x346/0x430
[48885.363663]  [<c013ae00>] autoremove_wake_function+0x0/0x50
[48885.363687]  [<c0160660>] kswapd+0x0/0x430
[48885.363691]  [<c013ac4a>] kthread+0xba/0xf0
[48885.363701]  [<c013ab90>] kthread+0x0/0xf0
[48885.363712]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[48885.363730]  =======================
[48885.363732] Code: df 01 00 eb d6 66 90 b8 01 00 00 00 86 05 bc b7 3a c0 5b 5e 5f 5d c3 85 c0 53 89 c3 74 4f 8b 80 98 00 00 00 83 bb 34 01 00 00 20 <8b> 40 20 74 49 85 c0 74 0b 8b 50 14 85 d2 74 04 89 d8 ff d2 8d 
[48885.363777] EIP: [<c01898d4>] iput+0x14/0x70 SS:ESP 0068:dff35ee0
[48885.363784]


```

The problem persists whether i use kernel 2.6.16,2.6.15,or even the latest 2.6.22(from gutsy repo).It started after a power spike caused the computer to reboot.
What can i do to correct it.
Also the sudden reboot caused a lot of problems on the hard-disk.I ran fsck which deleted some inodes.As a result ,some libraries do not exist on the hard disk,but apt thinks they exist.is there any way to fix the problem short of a reinstall?

---

