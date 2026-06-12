---
title: "kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/kernel/futex.c:1047!"
date: 2007-12-26
forum: General Help
---

### Post by khughitt on 2007-12-26
Hello,

I was trying to diagnose why my system recently froze up in the middle of surfing the web, and when I checked the logs for about that time, I came across this under syslog:

> 
Dec 26 07:29:22 Desktop kernel: [ 1160.347584] ------------[ cut here ]------------
Dec 26 07:29:22 Desktop kernel: [ 1160.347594] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/kernel/futex.c:1047!
Dec 26 07:29:22 Desktop kernel: [ 1160.347600] invalid opcode: 0000 [#1]
Dec 26 07:29:22 Desktop kernel: [ 1160.347603] SMP 
Dec 26 07:29:22 Desktop kernel: [ 1160.347608] Modules linked in: ipv6 af_packet fglrx(P) speedstep_lib cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_userspace battery sbp2 lp snd_intel8x0 snd_ac97_codec ac97_bus snd_seq_dummy snd_seq_oss snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_midi snd_seq_midi_event snd_rawmidi snd_hwdep wlan_scan_sta parport_pc ath_rate_sample snd_seq snd_timer snd_seq_device parport snd soundcore ath_pci wlan xpad pcspkr ath_hal(P) snd_page_alloc i82875p_edac serio_raw psmouse edac_mc iTCO_wdt iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev ext3 jbd mbcache usbhid hid sg sd_mod sr_mod cdrom ata_generic floppy sata_promise ohci1394 ehci_hcd e1000 ieee1394 uhci_hcd usbcore ata_piix libata scsi_mod thermal processor fan fuse apparmor commoncap
Dec 26 07:29:22 Desktop kernel: [ 1160.347737] CPU:    0
Dec 26 07:29:22 Desktop kernel: [ 1160.347739] EIP:    0060:[unqueue_me+97/144]    Tainted: P       VLI
Dec 26 07:29:22 Desktop kernel: [ 1160.347742] EFLAGS: 00010206   (2.6.22-14-generic #1)
Dec 26 07:29:22 Desktop kernel: [ 1160.347753] EIP is at unqueue_me+0x61/0x90
Dec 26 07:29:22 Desktop kernel: [ 1160.347758] eax: 00020000   ebx: c0491248   ecx: c0491254   edx: c0491254
Dec 26 07:29:22 Desktop kernel: [ 1160.347764] esi: eda19e88   edi: ee29e3b4   ebp: ee6859f0   esp: eda19e18
Dec 26 07:29:22 Desktop kernel: [ 1160.347769] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Dec 26 07:29:22 Desktop kernel: [ 1160.347775] Process swiftweasel-bin (pid: 7344, ti=eda18000 task=ee6859f0 task.ti=eda18000)
Dec 26 07:29:22 Desktop kernel: [ 1160.347780] Stack: 00000282 eda19e40 aacff308 ee29e3b4 00000000 aacff308 c014651d 00000000 
Dec 26 07:29:22 Desktop kernel: [ 1160.347796]        00000001 00000001 c2010ac0 00000000 00000000 99d78996 00000102 c013ede0 
Dec 26 07:29:22 Desktop kernel: [ 1160.347811]        c2010a38 00000000 00000002 eda19e64 eda19e64 c01464e4 66697773 61657774 
Dec 26 07:29:22 Desktop kernel: [ 1160.347826] Call Trace:
Dec 26 07:29:22 Desktop kernel: [ 1160.347846]  [futex_wait+557/784] futex_wait+0x22d/0x310
Dec 26 07:29:22 Desktop kernel: [ 1160.347873]  [hrtimer_wakeup+0/32] hrtimer_wakeup+0x0/0x20
Dec 26 07:29:22 Desktop kernel: [ 1160.347892]  [futex_wait+500/784] futex_wait+0x1f4/0x310
Dec 26 07:29:22 Desktop kernel: [ 1160.347956]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Dec 26 07:29:22 Desktop kernel: [ 1160.347979]  [do_futex+511/3040] do_futex+0x1ff/0xbe0
Dec 26 07:29:22 Desktop kernel: [ 1160.347989]  [lapic_next_event+12/16] lapic_next_event+0xc/0x10
Dec 26 07:29:22 Desktop kernel: [ 1160.347998]  [clockevents_program_event+136/256] clockevents_program_event+0x88/0x100
Dec 26 07:29:22 Desktop kernel: [ 1160.348018]  [run_timer_softirq+347/448] run_timer_softirq+0x15b/0x1c0
Dec 26 07:29:22 Desktop kernel: [ 1160.348026]  [process_timeout+0/16] process_timeout+0x0/0x10
Dec 26 07:29:22 Desktop kernel: [ 1160.348040]  [process_timeout+0/16] process_timeout+0x0/0x10
Dec 26 07:29:22 Desktop kernel: [ 1160.348064]  [getnstimeofday+54/208] getnstimeofday+0x36/0xd0
Dec 26 07:29:22 Desktop kernel: [ 1160.348083]  [ktime_get_ts+22/80] ktime_get_ts+0x16/0x50
Dec 26 07:29:22 Desktop kernel: [ 1160.348104]  [sys_futex+151/256] sys_futex+0x97/0x100
Dec 26 07:29:22 Desktop kernel: [ 1160.348144]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Dec 26 07:29:22 Desktop kernel: [ 1160.348197]  =======================


Can anyone tell if this is the cause of the system freeze, and if so, should I submit it to launchpad? I'm running Ubuntu 7.10 with Compiz Fusion. Any input would be appreciated. 

Thanks!

---

### Post by khughitt on 2007-12-29
*bump* ... anybody?

---

