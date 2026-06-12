---
title: "Ubuntu 7.04 locks up... sorta *invalid opcode kernel messages*"
date: 2007-07-08
forum: General Help
---

### Post by SupaRice on 2007-07-08
So, after a while of running my machine will stop responding to keyboard input, but everything else seems to work fine.  Even the mouse works, and after I ssh into the console and kill the process for my screen saver I can click around in X on the box.  I at first thought it might be a problem with hardware, so I replaced the keyboard but it still happens.  And then I happened to have a terminal window open during the problem, from which I captured the following messages with the mouse.

What the heck is going on?

```
fs01 kernel: [ 7787.063547] ------------[ cut here ]------------

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063560] invalid opcode: 0000 [#1]

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063562] SMP

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063661] CPU:    0

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063662] EIP:    0060:[free_block+291/304]    Tainted: P      VLI

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063664] EFLAGS: 00010002   (2.6.20-16-generic #2)

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063676] EIP is at free_block+0x123/0x130

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063679] eax: 8000082c   ebx: dfff6c14   ecx: ffffffff   edx: c17fffe0

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063683] esi: dfff6c00   edi: 00000004   ebp: dfff6c14   esp: df871f00

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063686] ds: 007b   es: 007b   ss: 0068

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063689] Process events/0 (pid: 5, ti=df870000 task=df867560 task.ti=df870000)

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063691] Stack: 00000000 00000000 00000004 dffff1c0 00000000 dfff6c14 dfff6c00 00000004

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063699]        dfffd140 c01728bf 00000000 dffff1c0 dfffd140 dffff1c0 c200d900 00000292

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063707]        c0173e41 00000000 00000000 c200d904 c20db5c0 c0137314 00000000 c20db5d4

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063714] Call Trace:

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063741]  [drain_array+95/208] drain_array+0x5f/0xd0

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063762]  [cache_reap+129/320] cache_reap+0x81/0x140

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063778]  [run_workqueue+148/320] run_workqueue+0x94/0x140

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063802]  [cache_reap+0/320] cache_reap+0x0/0x140

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063817]  [worker_thread+327/368] worker_thread+0x147/0x170

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063840]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063864]  [worker_thread+0/368] worker_thread+0x0/0x170

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063868]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063879]  [kthread+0/240] kthread+0x0/0xf0

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063891]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063914]  =======================

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063916] Code: 2b 42 3c 89 f2 89 47 18 8b 44 24 0c e8 77 fe ff ff e9 2f ff ff ff 83 c4 14 5b 5e 5f 5d c3 8b 52 0c 8b 02 84 c0 0f 88 5a ff ff ff <0f> 0b eb fe 89 f6 8d bc 27 00 00 00 00 83
ec 18 85 c9 89 74 24

Message from syslogd@fs01 at Fri Jul  6 10:48:48 2007 ...
fs01 kernel: [ 7787.063956] EIP: [free_block+291/304] free_block+0x123/0x130 SS:ESP 0068:df871f00

```

dmesg gives this output:

```
[21802.770372] ------------[ cut here ]------------
[21802.770383] kernel BUG at mm/slab.c:610!
[21802.770386] invalid opcode: 0000 [#1]
[21802.770388] SMP
[21802.770391] Modules linked in: isofs vmnet(P) vmmon(P) binfmt_misc rfcomm l2cap bluetooth ppdev ipv6 af_packet fglrx(P) speedstep_lib cpufreq_ondemand cpufreq_stats freq_table cpufreq_powersave cpufreq_userspace cpufreq_conservative dev_acpi tc1100_wmi sony_acpi pcc_acpi button sbs ac container battery dock video i2c_ec i2c_core asus_acpi backlight lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device parport_pc snd soundcore sis_agp snd_page_alloc serio_raw psmouse agpgart parport pcspkr shpchp pci_hotplug tsdev evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom ide_disk sata_sis pata_sis floppy ehci_hcd 3c59x ata_generic libata scsi_mod sis900 mii ohci_hcd usbcore sis5513 generic raid1 raid0 md_mod thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[21802.770487] CPU:    0
[21802.770488] EIP:    0060:[<c0172853>]    Tainted: P      VLI
[21802.770490] EFLAGS: 00010046   (2.6.20-16-generic #2)
[21802.770501] EIP is at free_block+0x123/0x130
[21802.770505] eax: 80000000   ebx: dfff6c14   ecx: ffffffff   edx: c17fffe0
[21802.770508] esi: dfff6c00   edi: 00000018   ebp: dfff6c14   esp: df871f00
[21802.770511] ds: 007b   es: 007b   ss: 0068
[21802.770514] Process events/0 (pid: 5, ti=df870000 task=df867560 task.ti=df870000)
[21802.770517] Stack: 00000000 00000000 00000018 dffff1c0 00000000 dfff6c14 dfff6c00 00000018
[21802.770525]        dfffd140 c01728bf 00000000 dffff1c0 dfffd140 dffff1c0 c200d900 00000292
[21802.770533]        c0173e41 00000000 00000000 c200d904 c20db5c0 c0137314 00000000 c20db5d4
[21802.770541] Call Trace:
[21802.770568]  [<c01728bf>] drain_array+0x5f/0xd0
[21802.770589]  [<c0173e41>] cache_reap+0x81/0x140
[21802.770605]  [<c0137314>] run_workqueue+0x94/0x140
[21802.770629]  [<c0173dc0>] cache_reap+0x0/0x140
[21802.770644]  [<c0137d97>] worker_thread+0x147/0x170
[21802.770666]  [<c0120b40>] default_wake_function+0x0/0x10
[21802.770691]  [<c0137c50>] worker_thread+0x0/0x170
[21802.770695]  [<c013ac4a>] kthread+0xba/0xf0
[21802.770706]  [<c013ab90>] kthread+0x0/0xf0
[21802.770719]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[21802.770741]  =======================
[21802.770742] Code: 2b 42 3c 89 f2 89 47 18 8b 44 24 0c e8 77 fe ff ff e9 2f ff ff ff 83 c4 14 5b 5e 5f 5d c3 8b 52 0c 8b 02 84 c0 0f 88 5a ff ff ff <0f> 0b eb fe 89 f6 8d bc 27 00 00 00 00 83 ec 18 85 c9 89 74 24
[21802.770785] EIP: [<c0172853>] free_block+0x123/0x130 SS:ESP 0068:df871f00
[21802.770791]

```

---

### Post by AlexThomson_NZ on 2007-07-08
It looks to my untrained eye that there is a bug (in slab?) that is causing the kernel to try to run commands that aren't commands (like jumping off the end of a program...)

[21802.770386] invalid opcode: 0000 [#1]

Try to replicate as simply as possible if you can.  Point it out to the lkml, although they may not be interested if you have a tainted kernel (ie. closed source gfx drivers, etc.)

---

### Post by SupaRice on 2007-07-08
lkml ?  Sorry, I don't know who that is.  I am running the ATI restricted drivers, but I've run them previously without problem.

---

### Post by AlexThomson_NZ on 2007-07-08
Sorry, lkml = linux kernel mailing list.

They probably don't want to know though as you are using restricted drivers (even if they have been running fine 24/7 for the last 10 years).  If you can replicate it though using an 'official' kernel go ahead.

(This isn't a political thing, but it can take a long time to hunt down bugs as it is without throwing closed-source 3rd party code into the mix- so I hope you can understand why they might be a bit precious about it)

Have you tried googling to see if anyone else has had similar problems?

---

### Post by SupaRice on 2007-07-19
Well, I ended up not being able to mess with it for a few days.  Then when I went to investigate the issue further there were some software updates in update manager.  I ran those (don't recall what they were :lol: )  and now it's fine!


I love it when problems "fix themselves"!
:guitar:

---

