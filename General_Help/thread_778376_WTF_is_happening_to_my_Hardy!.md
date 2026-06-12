---
title: "WTF is happening to my Hardy?!"
date: 2008-05-02
forum: General Help
---

### Post by FLCLFan on 2008-05-02
This has been going on since I installed Hardy (x64).

```
May  1 22:11:45 eli-desktop kernel: [12220.808424] PGD 203067 PUD 207063 PMD 0 
May  1 22:11:45 eli-desktop kernel: [12220.808429] CPU 0 
May  1 22:11:45 eli-desktop kernel: [12220.808430] Modules linked in: ipv6 af_packet rfcomm l2cap bluetooth ppdev cpufreq_stats cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_ondemand freq_table container dock video output sbs sbshc battery iptable_filter ip_tables x_tables ac sbp2 lp uinput parport_pc parport joydev evdev snd_usb_audio snd_usb_lib snd_hwdep fglrx(P) snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi pcspkr snd_seq_midi_event snd_seq snd_timer snd_seq_device button k8temp snd soundcore snd_page_alloc shpchp pci_hotplug i2c_nforce2 i2c_core ext3 jbd mbcache sd_mod sg sr_mod cdrom ata_generic usbhid hid pata_acpi floppy ohci1394 r8169 ieee1394 sata_nv pata_amd libata scsi_mod forcedeth ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
May  1 22:11:45 eli-desktop kernel: [12220.808467] Pid: 7027, comm: firefox Tainted: P        2.6.24-16-generic #1
May  1 22:11:45 eli-desktop kernel: [12220.808469] RIP: 0010:[__link_path_walk+0x784/0xe90]  [__link_path_walk+0x784/0xe90] __link_path_walk+0x784/0xe90
May  1 22:11:45 eli-desktop kernel: [12220.808472] RSP: 0018:ffff81003b213c58  EFLAGS: 00010286
May  1 22:11:45 eli-desktop kernel: [12220.808474] RAX: ffffffffa81b3860 RBX: ffff8100098ab6c8 RCX: 0000000000000000
May  1 22:11:45 eli-desktop kernel: [12220.808475] RDX: ffff810009a055c8 RSI: ffff810009a055b0 RDI: ffff810009a055b0
May  1 22:11:45 eli-desktop kernel: [12220.808477] RBP: ffff81003b213c78 R08: 0000000000000000 R09: 0000000000000000
May  1 22:11:45 eli-desktop kernel: [12220.808479] R10: 0000000000000000 R11: ffffffff8032d060 R12: 0000000000000000
May  1 22:11:45 eli-desktop kernel: [12220.808481] R13: ffff81003b213ea8 R14: ffff8100375b0000 R15: ffff8100375b0000
May  1 22:11:45 eli-desktop kernel: [12220.808483] FS:  00007fab20ec16f0(0000) GS:ffffffff805b0000(0000) knlGS:0000000000000000
May  1 22:11:45 eli-desktop kernel: [12220.808485] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May  1 22:11:45 eli-desktop kernel: [12220.808486] CR2: ffffffffa81b38b0 CR3: 00000000099af000 CR4: 00000000000006e0
May  1 22:11:45 eli-desktop kernel: [12220.808488] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May  1 22:11:45 eli-desktop kernel: [12220.808490] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May  1 22:11:45 eli-desktop kernel: [12220.808492] Process firefox (pid: 7027, threadinfo ffff81003b212000, task ffff810015b71740)
May  1 22:11:45 eli-desktop kernel: [12220.808493] Stack:  ffff81003b213eb0 0000010100000001 0000000000000000 fffffff51f428b00
May  1 22:11:45 eli-desktop kernel: [12220.808497]  0000000c2474a5c3 ffff8100375b001f ffff81003d27ac00 ffff810009a055b0
May  1 22:11:45 eli-desktop kernel: [12220.808500]  0000001000000003 ffff81003b213ea8 ffff81003d27ac00 ffff81003eb218f0
May  1 22:11:45 eli-desktop kernel: [12220.808502] Call Trace:
May  1 22:11:45 eli-desktop kernel: [12220.808512]  [link_path_walk+0x5b/0x100] link_path_walk+0x5b/0x100
May  1 22:11:45 eli-desktop kernel: [12220.808523]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May  1 22:11:45 eli-desktop kernel: [12220.808526]  [__slab_alloc+0x158/0x400] __slab_alloc+0x158/0x400
May  1 22:11:45 eli-desktop kernel: [12220.808529]  [get_empty_filp+0x31/0x150] get_empty_filp+0x31/0x150
May  1 22:11:45 eli-desktop kernel: [12220.808534]  [do_path_lookup+0x8a/0x250] do_path_lookup+0x8a/0x250
May  1 22:11:45 eli-desktop kernel: [12220.808540]  [__path_lookup_intent_open+0x6a/0xd0] __path_lookup_intent_open+0x6a/0xd0
May  1 22:11:45 eli-desktop kernel: [12220.808546]  [open_namei+0x89/0x710] open_namei+0x89/0x710
May  1 22:11:45 eli-desktop kernel: [12220.808553]  [_atomic_dec_and_lock+0x48/0x70] _atomic_dec_and_lock+0x48/0x70
May  1 22:11:45 eli-desktop kernel: [12220.808559]  [do_filp_open+0x1c/0x50] do_filp_open+0x1c/0x50
May  1 22:11:45 eli-desktop kernel: [12220.808568]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
May  1 22:11:45 eli-desktop kernel: [12220.808574]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
May  1 22:11:45 eli-desktop kernel: [12220.808579]  [system_call+0x7e/0x83] system_call+0x7e/0x83
May  1 22:11:45 eli-desktop kernel: [12220.808588] 
May  1 22:11:45 eli-desktop kernel: [12220.808588] 
May  1 22:11:45 eli-desktop kernel: [12220.808589] Code: 48 83 78 50 00 0f 84 61 03 00 00 65 48 8b 04 25 00 00 00 00 
May  1 22:11:45 eli-desktop kernel: [12220.808597]  RSP <ffff81003b213c58>
May  1 22:11:45 eli-desktop kernel: [12220.808602] ---[ end trace 78f7703d3e97beec ]---
May  1 22:14:43 eli-desktop kernel: [12398.949517] tracker-extract[9309]: segfault at 7f1a88b62ba8 rip 7f1a8a5eb46e rsp 7fff927fbb40 error 6
May  1 22:15:09 eli-desktop kernel: [12424.866279] firefox[9314]: segfault at 7f125c074ba8 rip 7f125c3b40d6 rsp 7fff645c4a70 error 6
May  1 22:15:24 eli-desktop kernel: [12440.449237] gnome-system-mo[9316]: segfault at 7f097d3edba8 rip 7f09817600d6 rsp 7fff89972e20 error 6
May  1 22:15:46 eli-desktop kernel: [12462.439601] firefox[9318]: segfault at 7f190d909ba8 rip 7f190dc490d6 rsp 7fff15e5c300 error 6
May  1 22:15:51 eli-desktop kernel: [12467.259853] firefox-2-bin[9336]: segfault at 7f334d2e3ba8 rip 7f334ed710d6 rsp 7fff56f821a0 error 6
May  1 22:16:01 eli-desktop kernel: [12476.541966] nautilus[9338]: segfault at 7f4115330ba8 rip 7f411e5050d6 rsp 7fff26715bc0 error 6
```

I get that initial error chain and then every program I try to open segfaults.

Can someone please tell me why this is happening?

Thank you.

---

### Post by tamoneya on 2008-05-02
```
Pid: 7027, comm: firefox Tainted: P 
```Looks to me like firefox is the culprit.  See what happens if you reinstall firefox through the recovery option in GRUB.

---

### Post by FLCLFan on 2008-05-02
I can boot just fine. I just went into synaptic and reinstalled firefox. I dont think is going to help though. When i first installed hardy this happened, then i reinstalled it and its happening again.

---

### Post by rmtatum on 2008-05-02
Your hard drive could be failing.

Install [smartmontools]("http://smartmontools.sourceforge.net/")
```
sudo aptitude install smartmontools
```

Post the results of:
```
sudo smartctl -HA /dev/[replace this with your hard drive's device node]
```

---

### Post by FLCLFan on 2008-05-02
Here it is:
```
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   060   050   006    Pre-fail  Always       -       128543778
  3 Spin_Up_Time            0x0003   096   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1135
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       25923134996
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       3340
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1585
194 Temperature_Celsius     0x0022   027   040   000    Old_age   Always       -       27 (Lifetime Min/Max 0/12)
195 Hardware_ECC_Recovered  0x001a   060   050   000    Old_age   Always       -       128543778
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

```

---

### Post by jimv on 2008-05-02
Oh my God, you've triggered the apocalypse!

---

### Post by Zorael on 2008-05-02
Make sure to pick **complete removal** (also called **purge**) when uninstalling Firefox.
```
$ sudo aptitude purge firefox flashplugin-nonfree
$ sudo aptitude update
$ sudo aptitude clean
sudo aptitude install firefox flashplugin-nonfree
```
Of course, omit flashplugin-nonfree if you don't want flash. I included it just in case, since I'm evil and inconsiderate.

---

### Post by FLCLFan on 2008-05-02
Okay, i just did that. Now im going to wait and see what happens.

If i dont see the errors then you win, if i do then you Fail!

Time to wait.

---

### Post by carlhako on 2008-05-02
Your output from smartctl doesnt look too good to me. when i compare it to one of my drives

YOURS
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   060   050   006    Pre-fail  Always       -       128543778
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       25923134996
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       3340
194 Temperature_Celsius     0x0022   027   040   000    Old_age   Always       -       27 (Lifetime Min/Max 0/12)
195 Hardware_ECC_Recovered  0x001a   060   050   000    Old_age   Always       -       128543778

```

Can see your drive is fairly new all my drives all have a 0 for those spots even some of my older drives 25000 hrs of running time no errors.

Maybe someone knows a bit more about these type of errors they may meen nothing seems like a hell of alot

---

### Post by FLCLFan on 2008-05-02
OMG I cant take it! ubuntu keeps crashing and freezing. I give up with it.

---

### Post by rmtatum on 2008-05-03
I'm not sure what the problem is.  Try creating a new user and logging in with that user.  If the error still occurs, you could reinstall Ubuntu.

---

### Post by FLCLFan on 2008-05-05
Okay, after a few more reinstalls I have finally found the sources of my problems.

It seems that FGLRX is the source of most of the problems. In addition, Pulseaudio is the second source for some of the problems I have been having. So I have removed FGLRX and i have switched to ALSA and my problems are gone :)

---

### Post by fmartinez on 2008-05-05
> **FLCLFan said:**
> Okay, after a few more reinstalls I have finally found the sources of my problems.

It seems that FGLRX is the source of most of the problems. In addition, Pulseaudio is the second source for some of the problems I have been having. So I have removed FGLRX and i have switched to ALSA and my problems are gone :)

WAY TO HANG IN THERE! THOUGHT WE LOST YOU FOR A MOMENT THERE!

---

### Post by FLCLFan on 2008-05-06
lol. I am way to modivated to give up on my favorite OS :D

But if i did not find wat was causing the problems i would have just went back to gutsy.

---

### Post by rmtatum on 2008-05-07
Glad that you were able to solve your problems.  You could also file a bug report describing your problems with FGLRX and PulseAudio.

---

