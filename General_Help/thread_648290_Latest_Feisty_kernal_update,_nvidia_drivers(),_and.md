---
title: "Latest Feisty kernal update, nvidia drivers(?), and unusual crashes/freezes"
date: 2007-12-23
forum: General Help
---

### Post by oscarsfriend on 2007-12-23
Hi,

For the last few days my system has been unusually unstable.  The first time I noticed this was when I ran Tremulous (3D game), and it froze on a blank screen.  Logging out and restarting the X server did nothing to solve the problem, it needed a complete reboot and then Tremulous was fine. 

Today I was watching a recording on MythTV (while it was still recording), and was dropped out back to the menu before the program had finished.  When I tried to continue watching, my system froze but I was able to restart the X server.  However, MythTV had stopped recording, and I was unable to start any application (e.g. firefox would not load from clicking its icon or running from the terminal).  When I tried to reboot my system hung at the stage where it unmounts the filesystem.  (Note: I have MythTV set to use OpenGL somehow during playback.)

Since the last kernel update I have noticed strange glitches when the screen changes (e.g. going from desktop to tremulous, or restarting X.) -- one or two horizontal line of pixels, about 100-200 pixels long.  So I'm wondering if it is to do with the nvidia drivers (from nvidia's website), which are compiled against the kernel.  I didn't recompile them after the update because it was only a minor change, and it has worked fine in the past.  After reinstalling the drivers I no longer get the glitching.  So I'm wondering if this could be the problem.  Any ideas?  [EDIT: Actually, now that I've checked again ,there is still the occasional glitch, but it seemed to be doing it all the time since the update.]

I did also update Myth shortly after the kernel update, but I **think** the first crash happened before I did this, but I am not certain.  Has anyone else experienced similar problems recently, or in similar circumstances.

---

### Post by oscarsfriend on 2007-12-23
OK, this is from /var/log/messages around (at?) the last time things went all wobbly.  Can anyone figure out what is happening from this?

```

Dec 23 15:28:51 192 kernel: [ 7272.336924] PGD 0
Dec 23 15:28:51 192 kernel: [ 7272.336928] CPU 0
Dec 23 15:28:51 192 kernel: [ 7272.336930] Modules linked in: bluetooth ppdev powernow_k8 cpufr
eq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table cpufreq_powersave s
ony_acpi tc1100_wmi pcc_acpi dev_acpi asus_acpi container video sbs dock battery button backlig
ht ac i2c_ec ipv6 cx22702 cx88_dvb cx88_vp3054_i2c dvb_pll video_buf_dvb dvb_core sbp2 parport_
pc lp parport fuse snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy
snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event nvidia(P) cx8800 cx8802 cx88xx snd_seq
pcspkr k8temp serio_raw ir_common compat_ioctl32 af_packet psmouse i2c_algo_bit tveeprom btcx_r
isc video_buf videodev v4l2_common v4l1_compat i2c_core snd_timer snd_seq_device shpchp pci_hot
plug snd soundcore snd_page_alloc tsdev evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom sata_nv a
hci ata_generic libata scsi_mod amd74xx floppy forcedeth ohci1394 ieee1394 generic ehci_hcd ohc
i_hcd usbcore thermal processor fan dm_mod fbcon tileblit font bitblit so
Dec 23 15:28:51 192 kernel: tcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commonc
ap
Dec 23 15:28:51 192 kernel: [ 7272.336974] Pid: 233, comm: kswapd0 Tainted: P      2.6.20-16-ge
neric #2
Dec 23 15:28:51 192 kernel: [ 7272.336977] RIP: 0010:[_end+129598927/2130485360]  [_end+1295989
27/2130485360] :ext3:ext3_clear_inode+0x2f/0xd0
Dec 23 15:28:51 192 kernel: [ 7272.336987] RSP: 0018:ffff8100378e7d10  EFLAGS: 00010287
Dec 23 15:28:51 192 kernel: [ 7272.336990] RAX: ffffffff881ce530 RBX: ffff810028cd4150 RCX: fff
f81000000c000
Dec 23 15:28:51 192 kernel: [ 7272.336993] RDX: ffffffff881d0300 RSI: ffff810028cd5ca8 RDI: fff
ffbffffffffff
Dec 23 15:28:51 192 kernel: [ 7272.336996] RBP: ffff810028cd4088 R08: 0000000000000000 R09: fff
f8100378e7da0
Dec 23 15:28:51 192 kernel: [ 7272.336999] R10: 28f5c28f5c28f5c3 R11: ffffffff881ce510 R12: 000
0000000000000
Dec 23 15:28:51 192 kernel: [ 7272.337002] R13: 0000000000000028 R14: 0000000000000080 R15: 000
0000000000000
Dec 23 15:28:51 192 kernel: [ 7272.337005] FS:  000000004c81a940(0000) GS:ffffffff8054e000(0000
) knlGS:00000000f75bcb10
Dec 23 15:28:51 192 kernel: [ 7272.337007] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Dec 23 15:28:51 192 kernel: [ 7272.337010] CR2: fffffbffffffffff CR3: 000000005dd3c000 CR4: 000
00000000006e0
Dec 23 15:28:51 192 kernel: [ 7272.337013] Process kswapd0 (pid: 233, threadinfo ffff8100378e60
00, task ffff81006ccca0c0)
Dec 23 15:28:51 192 kernel: [ 7272.337015] Stack:  ffff810028cd4150 ffff810028cd4150 ffff810037
8e7d70 ffffffff80223c1e
Dec 23 15:28:51 192 kernel: [ 7272.337021]  ffff810028cd4160 ffffffff80236408 ffff81006f8b7ab8
ffff810028ce4488
Dec 23 15:28:51 192 kernel: [ 7272.337025]  0000000000000080 0000000000000080 ffff8100378e7d70
ffffffff8022ec39
Dec 23 15:28:51 192 kernel: [ 7272.337029] Call Trace:
Dec 23 15:28:51 192 kernel: [ 7272.337037]  [clear_inode+206/304] clear_inode+0xce/0x130
Dec 23 15:28:51 192 kernel: [ 7272.337042]  [dispose_list+104/272] dispose_list+0x68/0x110
Dec 23 15:28:51 192 kernel: [ 7272.337048]  [shrink_icache_memory+537/624] shrink_icache_memory
+0x219/0x270
Dec 23 15:28:51 192 kernel: [ 7272.337057]  [shrink_slab+279/400] shrink_slab+0x117/0x190
Dec 23 15:28:51 192 kernel: [ 7272.337066]  [kswapd+908/1264] kswapd+0x38c/0x4f0
Dec 23 15:28:51 192 kernel: [ 7272.337077]  [autoremove_wake_function+0/48] autoremove_wake_fun
ction+0x0/0x30
Dec 23 15:28:51 192 kernel: [ 7272.337089]  [kswapd+0/1264] kswapd+0x0/0x4f0
Dec 23 15:28:51 192 kernel: [ 7272.337092]  [keventd_create_kthread+0/144] keventd_create_kthre
ad+0x0/0x90
Dec 23 15:28:51 192 kernel: [ 7272.337096]  [kthread+217/288] kthread+0xd9/0x120
Dec 23 15:28:51 192 kernel: [ 7272.337104]  [child_rip+10/18] child_rip+0xa/0x12
Dec 23 15:28:51 192 kernel: [ 7272.337108]  [keventd_create_kthread+0/144] keventd_create_kthre
ad+0x0/0x90
Dec 23 15:28:51 192 kernel: [ 7272.337114]  [physflat_send_IPI_mask+0/128] physflat_send_IPI_ma
sk+0x0/0x80
Dec 23 15:28:51 192 kernel: [ 7272.337122]  [kthread+0/288] kthread+0x0/0x120
Dec 23 15:28:51 192 kernel: [ 7272.337126]  [child_rip+0/18] child_rip+0x0/0x12
Dec 23 15:28:51 192 kernel: [ 7272.337130]
Dec 23 15:28:51 192 kernel: [ 7272.337131]
Dec 23 15:28:51 192 kernel: [ 7272.337131] Code: f0 ff 0f 0f 94 c0 84 c0 74 07 e8 a2 c7 03 f8 6
6 90 48 c7 43
Dec 23 15:28:51 192 kernel: [ 7272.337148]  RSP <ffff8100378e7d10>

```

---

### Post by oscarsfriend on 2007-12-23
Anyone?  Also, /var/log/syslog has a similar error message, except at the start it has this:

```

Dec 23 15:28:51 192 kernel: [ 7272.336903] Unable to handle kernel paging request at fffffbffff
ffffff RIP:
Dec 23 15:28:51 192 kernel: [ 7272.336908]  [_end+129598927/2130485360] :ext3:ext3_clear_inode+
0x2f/0xd0
Dec 23 15:28:51 192 kernel: [ 7272.336924] PGD 0
Dec 23 15:28:51 192 kernel: [ 7272.336926] Oops: 0002 [1] SMP
Dec 23 15:28:51 192 kernel: [ 7272.336928] CPU 0
[. . . Rest as before, I think]

```

---

### Post by oscarsfriend on 2007-12-23
bump

---

### Post by oscarsfriend on 2007-12-23
one more bump for now

---

### Post by oscarsfriend on 2007-12-23
one last bump for the day.  Anyone?

I can see the problem is a kernel oops, but I want to figure out what is causing it.  I ran memtest for a while, and everything seemed to check out.  Also, my system logs indicate that I have only had one kernel oops, so presumably the first time I had the problem it wasn't so bad.

---

### Post by StephX on 2007-12-23
i really have no idea if my problems have the same root as your issues, but after doing an update two nights ago my computer no longer boots correctly (it gets stuck in grub>), and so now i'm simply doing a reinstall.

---

### Post by oscarsfriend on 2007-12-23
This sounds like your menu.lst file has been overwritten during the kernel upgrade, you should be able to restore a backup (/boot/grub/menu.lst~) or manually reconfigure it.  Use a live CD if you have to.

Edit: see here for more info: [http://ubuntuforums.org/showthread.php?t=648377](http://ubuntuforums.org/showthread.php?t=648377)

---

### Post by StephX on 2007-12-23
thanks for the tip, the menu.lst was still there and looked to be in good condition, it just seemed like grub was 'seeing' it for some reason. but anyway, i've just finished a reinstall so that really doesn't matter anymore.

---

### Post by oscarsfriend on 2007-12-24
bump

---

### Post by oscarsfriend on 2007-12-24
bump.

Also, I remembered what I was doing the first time I had the crash.  I was watching an ISO of DVD with kaffeine, and it crashed after going through the menus to the main menu.  I have kaffeine (which uses xine) configured to use the opengl driver.  After that failed, I then tried to run tremulous, and got the blank screen.

---

### Post by oscarsfriend on 2007-12-24
Maybe Santa can help me?

---

