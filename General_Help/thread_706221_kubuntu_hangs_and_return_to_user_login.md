---
title: "kubuntu hangs and return to user login"
date: 2008-02-24
forum: General Help
---

### Post by dimebagbarrett on 2008-02-24
hi, i had this problem some minute ago, this is the first time my kubuntu does this (hangin and returning to user login gui )
This is my dmesg output, if anyone knows what is this and know how resolve...

Sorry for my english :)


[19915.118421] BUG: unable to handle kernel NULL pointer dereference at virtual
address 00000336
[19915.118526]  printing eip:
[19915.118573] c0139046
[19915.118574] *pde = 00000000
[19915.118623] Oops: 0000 [#1]
[19915.118669] SMP
[19915.118804] Modules linked in: ipv6 af_packet rfcomm l2cap bluetooth fglrx(P)
 ppdev cpufreq_powersave cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_t
able cpufreq_conservative video sbs ac container dock button battery lp loop snd
_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_m
idi snd_rawmidi xpad snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse
 parport_pc parport serio_raw snd soundcore snd_page_alloc pcspkr i2c_viapro i2c
_core shpchp pci_hotplug via_agp agpgart joydev evdev ext3 jbd mbcache ide_cd cd
rom ide_disk usbhid hid via82cxxx ide_core via_rhine floppy ehci_hcd ata_generic
 sata_via libata scsi_mod 8139too mii uhci_hcd usbcore thermal processor fan fus
e apparmor commoncap
[19915.122562] CPU:    0
[19915.122563] EIP:    0060:[<c0139046>]    Tainted: P       VLI
[19915.122564] EFLAGS: 00210206   (2.6.22-14-generic #1)
[19915.122726] EIP is at put_pid+0x6/0x30
[19915.122779] eax: 00000336   ebx: 00000008   ecx: 00000002   edx: 00000336
[19915.122834] esi: ccf0c9c0   edi: df817990   ebp: c2bc71a8   esp: dd7b7e24
[19915.122889] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
[19915.122944] Process ktorrent (pid: 6733, ti=dd7b6000 task=c3cec000 task.ti=dd
7b6000)
[19915.122999] Stack: c0181702 00000000 00000000 df817990 dfffae00 c2bc71a8 ccf0
c9c0 e495f600
[19915.123468]        00000000 e495f600 c017ea97 dd7b00d8 00000001 f791cc40 0000
0003 c012a3df
[19915.123940]        000001fc e495f600 c3cec000 00000001 c3cec4b4 c012b641 0077
0074 00001a4d
[19915.124423] Call Trace:
[19915.124522]  [<c0181702>] __fput+0xf2/0x1a0
[19915.124639]  [<c017ea97>] filp_close+0x47/0x80
[19915.124744]  [<c012a3df>] put_files_struct+0x8f/0xb0
[19915.124850]  [<c012b641>] do_exit+0x151/0x810
[19915.124954]  [<c0132320>] __dequeue_signal+0x10/0x160
[19915.125060]  [<c013204b>] recalc_sigpending+0xb/0x20
[19915.125163]  [<c012bd26>] do_group_exit+0x26/0x80
[19915.125265]  [<c0134368>] get_signal_to_deliver+0x298/0x410
[19915.125372]  [<c01037d3>] do_notify_resume+0x93/0x720
[19915.125472]  [<c012d6b2>] __do_softirq+0x82/0x110
[19915.125590]  [<c0140e56>] getnstimeofday+0x36/0xd0
[19915.125693]  [<c013eeb6>] ktime_get_ts+0x16/0x50
[19915.125798]  [<c01475e7>] sys_futex+0x97/0x100
[19915.125911]  [<c010432e>] work_notifysig+0x13/0x25
[19915.126018]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[19915.126124]  =======================
[19915.126175] Code: c0 74 ea ba 00 80 00 00 e8 18 53 0c 00 3d ff 7f 00 00 77 d9                                                                                                    8d 1c 30 85 db 7f 90 89 e8 5b 5e 5f 5d c3 8d 76 00 85 c0 89 c2 74 1a <83> 38 01                                                                                                    74 0a f0 ff 08 0f 94 c0 84 c0 74 0b a1 5c 08 47 c0 e9
[19915.129112] EIP: [<c0139046>] put_pid+0x6/0x30 SS:ESP 0068:dd7b7e24
[19915.129385] Fixing recursive fault but reboot is needed!
[19918.438075] [fglrx] PCIe has already been initialized. Reinitializing ...
[19918.469231] [fglrx] total      GART = 134217728
[19918.469241] [fglrx] free       GART = 118226944
[19918.469244] [fglrx] max single GART = 118226944
[19918.469246] [fglrx] total      LFB  = 268304384
[19918.469247] [fglrx] free       LFB  = 250474496
[19918.469249] [fglrx] max single LFB  = 250474496
[19918.469251] [fglrx] total      Inv  = 0
[19918.469253] [fglrx] free       Inv  = 0
[19918.469254] [fglrx] max single Inv  = 0
[19918.469256] [fglrx] total      TIM  = 0

---

### Post by pointone on 2008-02-24
If this is the first time it has happened, just reboot and see if it happens again. It could've just been a random error.

---

