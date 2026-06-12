---
title: "Firefox crash takes kernel with it?"
date: 2006-09-14
forum: General Help
---

### Post by Grey on 2006-09-14
Okay, I was typing this in Firefox, when it crashed AGAIN.  So here goes again, so sorry, it's the abbreviated version this time.

My girlfriend's computer is having issues.  Firefox crashes many times in a day.  X crashes about once a day.  The most recent crash resulted in a kernel panic of sorts.  She recently upgraded from an Athlon 64 to an Athlon 64x2.  All other parts are the same and Linux hasn't been modified, aside from daily updates.  Windows likes to crash, but then again, it always did.

I was using the computer when the most recent crash occurred.  I was browsing the web with firefox, playing music with xmms, and browsing files with Nautilus.  Firefox stopped responding, so I tried closing it.  When presented with the "this program is not responding" window, I closed it.  CPU usage went to 100%, and I tried to play a new song via nautilus.  Nautilus stopped responding, as did the gnome-panel and desktop.  I switched to a terminal I had open, and typed "killall firefox-bin".  After that, the system locked up hard.  Here's the log of the event:

```

Sep 14 02:01:24 localhost kernel: [17209891.368000] Unable to handle kernel NULL pointer dereference at virtual address 000000b4
Sep 14 02:01:24 localhost kernel: [17209891.368000]  printing eip:
Sep 14 02:01:24 localhost kernel: [17209891.368000] c015dc12
Sep 14 02:01:24 localhost kernel: [17209891.368000] *pde = 00000000
Sep 14 02:01:24 localhost kernel: [17209891.368000] Oops: 0000 [#1]
Sep 14 02:01:24 localhost kernel: [17209891.368000] PREEMPT SMP
Sep 14 02:01:24 localhost kernel: [17209891.368000] Modules linked in: nfsd exportfs lockd sunrpc isofs udf rfcomm l2cap bluetooth ipv6 fglrx ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec nls_cp437 ntfs md_mod dm_mod af_packet sr_mod sbp2 parport_pc lp parport ide_disk rsrc_nonstatic pcmcia_core snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq snd_via82xx gameport snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_mpu401_uart tsdev snd_rawmidi snd_seq_device pcspkr floppy snd usbhid soundcore i2c_viapro psmouse shpchp pci_hotplug i2c_core serio_raw sk98lin skge amd64_agp agpgart sg evdev ext3 jbd ide_generic ehci_hcd uhci_hcd ohci1394 ieee1394 usbcore ide_cd cdrom via82cxxx generic sd_mod sata_via libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit s
Sep 14 02:01:24 localhost kernel: ftcursor
Sep 14 02:01:24 localhost kernel: [17209891.368000] CPU:    1
Sep 14 02:01:24 localhost kernel: [17209891.368000] EIP:    0060:[vma_prio_tree_remove+34/288]    Tainted: P      VLI
Sep 14 02:01:24 localhost kernel: [17209891.368000] EFLAGS: 00210202   (2.6.15-26-k7)
Sep 14 02:01:24 localhost kernel: [17209891.368000] EIP is at vma_prio_tree_remove+0x22/0x120
Sep 14 02:01:24 localhost kernel: [17209891.368000] eax: dfd55c64   ebx: 00000080   ecx: f725ecc0   edx: dfd55c48
Sep 14 02:01:24 localhost kernel: [17209891.368000] esi: f51cab74   edi: f725ecc0   ebp: dfd55c64   esp: caf69de8
Sep 14 02:01:24 localhost kernel: [17209891.368000] ds: 007b   es: 007b   ss: 0068
Sep 14 02:01:24 localhost kernel: [17209891.368000] Process firefox-bin (pid: 22117, threadinfo=caf68000 task=e22a7030)
Sep 14 02:01:24 localhost kernel: [17209891.368000] Stack: 00200282 ead2bad8 00000000 dfd55c48 dfd55c74 f725ecc0 f51cab74 c016324e
Sep 14 02:01:24 localhost kernel: [17209891.368000]        f51cab74 dfd55c64 dfd55c48 f51ca85c f51cab74 b328d000 00000000 c015f714
Sep 14 02:01:24 localhost kernel: [17209891.368000]        f51cab74 08048000 09494000 00000000 b328d000 caf69e6c d7f1fa6c f7be83c0
Sep 14 02:01:24 localhost kernel: [17209891.368000] Call Trace:
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [unlink_file_vma+62/112] unlink_file_vma+0x3e/0x70
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [free_pgtables+148/176] free_pgtables+0x94/0xb0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [exit_mmap+186/320] exit_mmap+0xba/0x140
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [mmput+56/160] mmput+0x38/0xa0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_exit+224/1056] do_exit+0xe0/0x420
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_group_exit+64/176] do_group_exit+0x40/0xb0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [get_signal_to_deliver+551/832] get_signal_to_deliver+0x227/0x340
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_signal+111/384] do_signal+0x6f/0x180
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [default_wake_function+0/32] default_wake_function+0x0/0x20
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_futex+116/192] do_futex+0x74/0xc0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [sys_futex+102/304] sys_futex+0x66/0x130
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_notify_resume+40/56] do_notify_resume+0x28/0x38
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [work_notifysig+19/25] work_notifysig+0x13/0x19
Sep 14 02:01:24 localhost kernel: [17209891.368000] Code: 00 00 00 8d bf 00 00 00 00 83 ec 1c 89 74 24 10 8b 74 24 20 89 6c 24 18 89 5c 24 0c 89 7c 24 14 8b 6c 24 24 8b 5e 34 85 db 74 62 <3b> 73 34 0f 85 df 00 00 00 8b 56 30 85 d2 0f 84 a2 00 00 00 8b
Sep 14 02:01:24 localhost kernel: [17209891.368000]  <1>Fixing recursive fault but reboot is needed!
Sep 14 02:01:24 localhost kernel: [17209891.368000] scheduling while atomic: firefox-bin/0x00000002/22117
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [schedule+2461/3360] schedule+0x99d/0xd20
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_exit+926/1056] do_exit+0x39e/0x420
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [die+395/400] die+0x18b/0x190
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_page_fault+0/1582] do_page_fault+0x0/0x62e
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_page_fault+891/1582] do_page_fault+0x37b/0x62e
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [__pagevec_free+50/80] __pagevec_free+0x32/0x50
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_page_fault+0/1582] do_page_fault+0x0/0x62e
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [error_code+79/84] error_code+0x4f/0x54
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [vma_prio_tree_remove+34/288] vma_prio_tree_remove+0x22/0x120
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [unlink_file_vma+62/112] unlink_file_vma+0x3e/0x70
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [free_pgtables+148/176] free_pgtables+0x94/0xb0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [exit_mmap+186/320] exit_mmap+0xba/0x140
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [mmput+56/160] mmput+0x38/0xa0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_exit+224/1056] do_exit+0xe0/0x420
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_group_exit+64/176] do_group_exit+0x40/0xb0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [get_signal_to_deliver+551/832] get_signal_to_deliver+0x227/0x340
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_signal+111/384] do_signal+0x6f/0x180
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [default_wake_function+0/32] default_wake_function+0x0/0x20
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_futex+116/192] do_futex+0x74/0xc0
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [sys_futex+102/304] sys_futex+0x66/0x130
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [do_notify_resume+40/56] do_notify_resume+0x28/0x38
Sep 14 02:01:24 localhost kernel: [17209891.368000]  [work_notifysig+19/25] work_notifysig+0x13/0x19

```

My question is... what does this mean, and what can I do to fix it?  Should I file a bug?

EDIT:
And as I finished this up, and was browsing the forums, X crashed for the second time in an hour.  I got this message in the X log:

```
AUDIT: Thu Sep 14 02:37:47 2006: 6799 X: client 1 rejected from local host
```

EDIT2:
Syslog says this, right BEFORE the X log:
```

Sep 14 02:37:44 localhost gdm[4765]: Error reinitilizing server
Sep 14 02:37:45 localhost kernel: [17181507.676000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
Sep 14 02:37:46 localhost kernel: [17181508.248000] [fglrx] AGP detected, AgpState   = 0x1f000a0b (hardware caps of chipset)
Sep 14 02:37:46 localhost kernel: [17181508.252000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Sep 14 02:37:46 localhost kernel: [17181508.252000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Sep 14 02:37:46 localhost kernel: [17181508.252000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Sep 14 02:37:46 localhost kernel: [17181508.252000] [fglrx] AGP enabled,  AgpCommand = 0x1f000302 (selected caps)
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] total      GART = 268435456
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] free       GART = 252440576
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] max single GART = 252440576
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] total      LFB  = 126873600
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] free       LFB  = 116387840
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] max single LFB  = 116387840
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] total      Inv  = 0
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] free       Inv  = 0
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] max single Inv  = 0
Sep 14 02:37:46 localhost kernel: [17181508.260000] [fglrx] total      TIM  = 0

```

EDIT3:

Looking further into this, (I've been googling), I'm not the only one to have these problems, but the previous thread has gone unanswered.

[http://ubuntuforums.org/showthread.php?t=193670](http://ubuntuforums.org/showthread.php?t=193670)

---

