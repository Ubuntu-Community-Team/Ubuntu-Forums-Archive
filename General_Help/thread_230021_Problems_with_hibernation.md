---
title: "Problems with hibernation"
date: 2006-08-05
forum: General Help
---

### Post by Blender on 2006-08-05
Hi everybody!

I'm not sure if this is the correct forum to post in.

I am having a problem with hibernation.
I am running Dapper Drake (with latest updates) on amd64 desktop computer. Sometimes when I hibernate and then turn on the computer, I get the notification about HAL and some FAQ ([http://www.ubuntuforums.org/showthread.php?t=197062](http://www.ubuntuforums.org/showthread.php?t=197062)).
I just turned on my PC, got this notification message (went to this FAQ and could not find anything regarding my problem) and this time took a look at dmesg. I spotted the following:

```

[16626.574521] ACPI: PCI interrupt for device 0000:00:02.1 disabled
[16626.589612] ACPI: PCI interrupt for device 0000:00:02.0 disabled
[16626.625502] swsusp: Need to copy 55679 pages
[   58.456915] BUG: soft lockup detected on CPU#0!
[   58.456922] CPU 0:
[   58.456924] Modules linked in: nls_utf8 nls_cp437 vfat fat binfmt_misc rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec md_mod parport_pc lp parport nvidia tsdev psmouse serio_raw snd_intel8x0 snd_ac97_codec snd_ac97_bus pcspkr snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug usbhid i2c_nforce2 ipv6 i2c_core sg evdev ext3 jbd dm_mod usb_storage ide_generic ehci_hcd ohci_hcd usbcore ide_cd cdrom generic sd_mod amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[   58.456971] Pid: 13574, comm: hibernate.sh Tainted: P      2.6.15-26-amd64-k8 #1
[   58.456974] RIP: 0010:[<ffffffff8016f093>] <ffffffff8016f093>{free_hot_cold_page+275}
[   58.456984] RSP: 0018:ffff8100005d3e18  EFLAGS: 00000286
[   58.456987] RAX: 000000000000001f RBX: ffffffff8016ec14 RCX: ffff8100010bbf88
[   58.456992] RDX: ffff8100010bbff8 RSI: 0000000000000002 RDI: ffff81000000b380
[   58.456996] RBP: 0000000000000002 R08: ffff81000000b300 R09: ffff81000000b000
[   58.457000] R10: ffffffff8038dc6a R11: ffff81001fc036f0 R12: 0000000000000002
[   58.457004] R13: ffff81001a326140 R14: ffff81001f9f9b80 R15: ffff81001f9f9b80
[   58.457009] FS:  00002aaaab0596d0(0000) GS:ffffffff8044a800(0000) knlGS:00000000556b2a90
[   58.457012] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   58.457015] CR2: 00000000005395c6 CR3: 000000000069c000 CR4: 00000000000006e0
[   58.457017] 
[   58.457018] Call Trace:<ffffffff80160b66>{swsusp_free+278} <ffffffff8015fe4c>{pm_suspend_disk+236}
[   58.457036]        <ffffffff8015dd36>{enter_state+118} <ffffffff8015df76>{state_store+134}
[   58.457045]        <ffffffff801d68c4>{sysfs_write_file+212} <ffffffff8019060e>{vfs_write+222}
[   58.457059]        <ffffffff801910d3>{sys_write+83} <ffffffff8010febe>{system_call+126}
[   58.457072]

```

One more thing: Regardless of this message, everything seems to be OK, all modules (network, video, etc) get loaded automatically, i.e. I don't have to rmmod and then modprobe.

Could someone give some more details on why this might be happening? Is it a bug in the kernel itself or is it caused by some Debian/Ubuntu patches? Should I file a bug report to the kernel's bugzilla?

Thanks!

---

