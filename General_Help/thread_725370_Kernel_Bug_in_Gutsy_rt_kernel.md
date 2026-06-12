---
title: "Kernel Bug in Gutsy rt kernel"
date: 2008-03-15
forum: General Help
---

### Post by raffytaffy on 2008-03-15
Getting strange lock ups to the point I have to reboot the system. I have traced the problem to this in the log.> Mar 15 15:57:31 equinox2 kernel: [17401.886775] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/net/core/skbuff.c:1359!

Any help is appreciated.
> Mar 15 13:12:10 equinox2 kernel: [ 7492.541174] sd 7:0:0:0: Attached scsi generic sg5 type 0
Mar 15 15:57:31 equinox2 kernel: [17401.886768] ------------[ cut here ]------------
Mar 15 15:57:31 equinox2 kernel: [17401.886775] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/net/core/skbuff.c:1359!
Mar 15 15:57:31 equinox2 kernel: [17401.886779] invalid opcode: 0000 [#1]
Mar 15 15:57:31 equinox2 kernel: [17401.886781] PREEMPT SMP 
Mar 15 15:57:31 equinox2 kernel: [17401.886783] Modules linked in: nfnetlink_queue binfmt_misc ipt_REJECT xt_mark xt_tcpudp xt_state xt_NFQUEUE ppdev cpufreq_conservative cpufreq_powersave cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table video ac container sbs dock button battery nls_iso8859_1 nls_cp437 vfat fat it87 hwmon_vid i2c_isa eeprom sbp2 lp snd_cmipci gameport snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib snd_hwdep snd_mpu401_uart snd_seq_dummy af_packet snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer nvidia(P) snd_seq_device snd xpad agpgart soundcore parport_pc parport k8temp pcspkr shpchp pci_hotplug i2c_nforce2 i2c_core evdev joydev iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nfnetlink iptable_mangle iptable_filter ip_tables x_tables usb_storage libusual ext3 jbd mbcache ide_disk sg sd_mod usbhid hid sr_mod cdrom ata_generic ohci1394 ieee1394 tg3 floppy ohci_hcd ehci_hcd amd74xx ide_core usbcore sata_nv libata scsi_mod thermal processor fan f
Mar 15 15:57:31 equinox2 kernel: se apparmor commoncap

---

