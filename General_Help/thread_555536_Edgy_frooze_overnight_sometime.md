---
title: "Edgy frooze overnight sometime"
date: 2007-09-20
forum: General Help
---

### Post by stealth17 on 2007-09-20
I woke up this morning to everything being locked up tight, could not even get out of GDM or anything. I had to do a hard reset. I checked my syslog, does this mean anything? You can see the last entry I copied was when I restarted at 8:43, so the last entry before reboot was at 4:25. There is some debug lines there, but I don't know what they mean.

Looks like a kernel problem doesn't it?

```
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124278] BUG: unable to handle kernel paging request at virtual address 029c0010
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124285]  printing eip:
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124287] c015c8c8
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124289] *pde = 00000000
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124292] Oops: 0000 [#1]
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124294] SMP 
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124297] Modules linked in: nls_iso8859_1 vfat fat usb_storage libusual binfmt_misc nls_cp437 isofs udf vmnet(P) vmmon(P) af_packet ipt_TCPMSS xt_limit xt_tcpudp nf_nat_irc nf_nat_ftp iptable_nat iptable_mangle ipt_LOG ipt_MASQUERADE nf_nat ipt_TOS ipt_REJECT nf_conntrack_irc nf_conntrack_ftp nf_conntrack_ipv4 xt_state nf_conntrack nfnetlink iptable_filter ip_tables x_tables ppdev cpufreq_userspace cpufreq_ondemand cpufreq_powersave cpufreq_conservative cpufreq_stats freq_table dev_acpi pcc_acpi tc1100_wmi sony_acpi sbs video battery container dock ac button asus_acpi backlight i2c_ec ext2 sbp2 parport_pc lp parport fuse snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device nvidia(P) snd agpgart sk98lin psmouse i2c_nforce2 pcspkr ide_cd cdrom k8temp ide_disk soundcore serio_raw shpchp pci_hotplug i2c_core snd_page_alloc tsdev evdev ipv6 ext3 jbd mbcache s
Sep 20 04:25:08 stealth17-desktop kernel:  sd_mod amd74xx generic usbhid hid sata_nv skge ohci1394 ieee1394 forcedeth ehci_hcd ata_generic libata scsi_mod ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124365] CPU:    0
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124366] EIP:    0060:[set_page_dirty+24/80]    Tainted: P      VLI
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124367] EFLAGS: 00013282   (2.6.20-16-generic #2)
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124374] EIP is at set_page_dirty+0x18/0x50
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124378] eax: 029c0000   ebx: c1e0e700   ecx: c1e0e700   edx: ee010702
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124381] esi: c19dd92c   edi: fffb474c   ebp: c1e0e700   esp: f1d4dec0
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124384] ds: 007b   es: 007b   ss: 0068
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124387] Process vmware-vmx (pid: 2787, ti=f1d4c000 task=c7cad560 task.ti=f1d4c000)
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124390] Stack: c015d5a8 c19dd92c c01633df 0004f94f 01040000 931d3000 f2d5de48 f693f3c0 
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124397]        01020000 00000012 c1e0e700 0002a791 01000000 c19dd92c fffb474c 70738025 
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124404]        c0429e80 c0164a6f fffb474c e5070930 c19dd92c 70738025 0001aaf1 0001aaf1 
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124410] Call Trace:
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124413]  [set_page_dirty_balance+8/64] set_page_dirty_balance+0x8/0x40
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124421]  [do_wp_page+591/1184] do_wp_page+0x24f/0x4a0
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124471]  [__handle_mm_fault+1887/2624] __handle_mm_fault+0x75f/0xa40
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124562]  [do_page_fault+296/1520] do_page_fault+0x128/0x5f0
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124609]  [do_page_fault+0/1520] do_page_fault+0x0/0x5f0
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124616]  [error_code+124/144] error_code+0x7c/0x90
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124678]  =======================
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124680] Code: 24 8b 74 24 04 8b 7c 24 08 8b 6c 24 0c 83 c4 10 c3 66 90 89 c1 8b 50 10 8b 00 66 85 c0 78 3b f6 c2 01 75 1e 85 d2 74 1a 8b 42 38 <8b> 50 10 85 d2 74 09 89 c8 ff d2 89 c2 89 d0 c3 ba 00 91 19 c0 
Sep 20 04:25:08 stealth17-desktop kernel: [1394287.124701] EIP: [set_page_dirty+24/80] set_page_dirty+0x18/0x50 SS:ESP 0068:f1d4dec0
Sep 20 08:43:29 stealth17-desktop syslogd 1.4.1#20ubuntu4: restart.
Sep 20 08:43:29 stealth17-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
```

---

### Post by fjgaude on 2007-09-20
Could be a memory error, random. Or disk segment going bad... it could be anything.

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by ukripper on 2007-09-20
It is a wise idea to do fsck using LIVE CD. error seems to be on swap. definitely do fsck from Live CD

And from the log I can see you were running VMware which also takes alot of paging if your RAM is less could also be paging fault.

---

### Post by stealth17 on 2007-09-21
> **ukripper said:**
> It is a wise idea to do fsck using LIVE CD. error seems to be on swap. definitely do fsck from Live CD

And from the log I can see you were running VMware which also takes alot of paging if your RAM is less could also be paging fault.

When I restarted it ran one before it booted, do I have to use the Live CD?

---

### Post by ukripper on 2007-09-21
> **stealth17 said:**
> When I restarted it ran one before it booted, do I have to use the Live CD?

Don't run fsck while using filesystem. Live Cd is the best option. as it has already done it no point doing it again. if you get the same errors do it using Live CD

---

