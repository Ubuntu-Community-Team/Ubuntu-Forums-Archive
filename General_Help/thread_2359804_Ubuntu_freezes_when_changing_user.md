---
title: "Ubuntu freezes when changing user"
date: 2017-04-27
forum: General Help
---

### Post by mexp on 2017-04-27
I have an office computer with two users, and often when either of the users has left the computer to lock the screen automatically, system freezes when trying to change user when logging in again. I then need to do a hard restart to be able to continue. I can't even exit the graphical interface by ctrl+alt+F1. Mouse moves, but clicks do not register. The power settings has been set to Do not suspend.

Where to look for solutions to this annoying problem? 

It's pretty much pristine and up to date installation of Ubuntu 16.04 on a HP 8200 Desktop PC (Intel® Core&#8482; i5-2400 CPU @ 3.10GHz × 4)

---

### Post by mexp on 2017-05-31
How is this possible..? This question has been here for four weeks, and the stats show that no-one has even viewed it???

---

### Post by VMC on 2017-05-31
Have you looked at the log files after re-booting from a hard restart? I had something similar using gnome.

---

### Post by mexp on 2017-05-31
What should I look for?

---

### Post by deadflowr on 2017-05-31
> **mexp said:**
> How is this possible..? This question has been here for four weeks, and the stats show that no-one has even viewed it???

View count is busted.

That said, seems like something like this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1247189]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1247189")
Though i have my doubts if anything you can mine out of that bug report would be of help.

---

### Post by VMC on 2017-05-31
Look for something in regards to your graphics chip. I noticed your system has Intel graphics.
Without any crash reports to view, look for something suspicious in graphics area. ("/var/log/syslog, etc")

---

### Post by mexp on 2017-06-21
For long time, it was working ok, but just now it froze again.

This is from the syslog, is it related & revealing anything?

Jun 21 09:18:16 hp-8200 kernel: [24407.576666] usblp 1-1.5:1.0: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x0985 pid 0x0045
Jun 21 09:25:06 hp-8200 lightdm[938]: Stopping PAM conversation, interaction requested but not supported
Jun 21 09:25:07 hp-8200 kernel: [24818.423131] ------------[ cut here ]------------
Jun 21 09:25:07 hp-8200 kernel: [24818.423156] WARNING: CPU: 0 PID: 1450 at /build/linux-As38az/linux-4.4.0/drivers/gpu/drm/drm_irq.c:1326 drm_wait_one_vblank+0x1b5/0x1c0 [drm]()
Jun 21 09:25:07 hp-8200 kernel: [24818.423157] vblank wait timed out on crtc 0
Jun 21 09:25:07 hp-8200 kernel: [24818.423195] Modules linked in: usblp joydev input_leds hp_wmi sparse_keymap gpio_ich hid_generic intel_rapl x86_pkg_temp_thermal intel_powerclamp snd_hda_codec_hdmi coretemp snd_hda_codec_realtek kvm snd_hda_codec_generic snd_hda_intel irqbypass snd_hda_codec snd_hda_core crct10dif_pclmul snd_hwdep crc32_pclmul snd_pcm ghash_clmulni_intel aesni_intel aes_x86_64 snd_seq_midi lrw snd_seq_midi_event gf128mul glue_helper snd_rawmidi ablk_helper cryptd snd_seq snd_seq_device snd_timer snd soundcore usbhid serio_raw mei_me hid mei shpchp lpc_ich 8250_fintek tpm_infineon mac_hid parport_pc ppdev lp parport autofs4 i915 video i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt psmouse fb_sys_fops e1000e ahcJun 21 09:26:02 hp-8200 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="731" x-info="http://www.rsyslog.com"] start
Jun 21 09:26:02 hp-8200 rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try [http://www.rsyslog.com/e/2222](http://www.rsyslog.com/e/2222) ]
Jun 21 09:26:02 hp-8200 rsyslogd: rsyslogd's groupid changed to 108

---

### Post by mexp on 2017-06-27
Here's another freeze:

```
Jun 27 16:24:17 hp-8200 kernel: [169634.922854] ------------[ cut here ]------------
Jun 27 16:24:17 hp-8200 kernel: [169634.922881] WARNING: CPU: 3 PID: 22347 at /build/linux-As38az/linux-4.4.0/drivers/gpu/drm/drm_irq.c:1326 drm_wait_one_vblank+0x1b5/0x1c0 [drm]()
Jun 27 16:24:17 hp-8200 kernel: [169634.922883] vblank wait timed out on crtc 0
Jun 27 16:24:17 hp-8200 kernel: [169634.922885] Modules linked in: usblp joydev input_leds hp_wmi sparse_keymap gpio_ich intel_rapl snd_hda_codec_hdmi x86_pkg_temp_thermal intel_powerclamp snd_hda_codec_realtek snd_hda_codec_generic coretemp snd_hda_intel snd_hda_codec kvm snd_hda_core snd_hwdep irqbypass snd_pcm crct10dif_pclmul crc32_pclmul snd_seq_midi ghash_clmulni_intel snd_seq_midi_event snd_rawmidi aesni_intel aes_x86_64 lrw snd_seq gf128mul glue_helper ablk_helper cryptd snd_seq_device snd_timer snd serio_raw soundcore mei_me mei shpchp lpc_ich tpm_infineon 8250_fintek mac_hid hid_generic usbhid hid parport_pc ppdev lp parport autofs4 i915 video i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt psmouse fb_sys_fops ahci e1000e drm libahci ptp pps_core wmi fjes
Jun 27 16:24:17 hp-8200 kernel: [169634.922940] CPU: 3 PID: 22347 Comm: Xorg Tainted: G        W       4.4.0-79-generic #100-Ubuntu
Jun 27 16:24:17 hp-8200 kernel: [169634.922942] Hardware name: Hewlett-Packard HP Compaq 8200 Elite SFF/1495, BIOS J01 v02.09 07/01/2011
Jun 27 16:24:17 hp-8200 kernel: [169634.922945]  0000000000000286 00000000ef156e63 ffff880127a3fb08 ffffffff813f94d3
Jun 27 16:24:17 hp-8200 kernel: [169634.922948]  ffff880127a3fb50 ffffffffc006fb38 ffff880127a3fb40 ffffffff81081322
Jun 27 16:24:17 hp-8200 kernel: [169634.922951]  ffff88012795c800 0000000000000000 0000000000000000 00000000003aa637
Jun 27 16:24:17 hp-8200 kernel: [169634.922955] Call Trace:
Jun 27 16:24:17 hp-8200 kernel: [169634.922961]  [<ffffffff813f94d3>] dump_stack+0x63/0x90
Jun 27 16:24:17 hp-8200 kernel: [169634.922966]  [<ffffffff81081322>] warn_slowpath_common+0x82/0xc0
Jun 27 16:24:17 hp-8200 kernel: [169634.922970]  [<ffffffff810813bc>] warn_slowpath_fmt+0x5c/0x80
Jun 27 16:24:17 hp-8200 kernel: [169634.922975]  [<ffffffff810c3e95>] ? finish_wait+0x55/0x70
Jun 27 16:24:17 hp-8200 kernel: [169634.922989]  [<ffffffffc003f2b5>] drm_wait_one_vblank+0x1b5/0x1c0 [drm]
Jun 27 16:24:17 hp-8200 kernel: [169634.922993]  [<ffffffff810c4330>] ? wake_atomic_t_function+0x60/0x60
Jun 27 16:24:17 hp-8200 kernel: [169634.923029]  [<ffffffffc021ed7a>] intel_atomic_commit+0x43a/0x6f0 [i915]
Jun 27 16:24:17 hp-8200 kernel: [169634.923050]  [<ffffffffc0059037>] drm_atomic_commit+0x37/0x60 [drm]
Jun 27 16:24:17 hp-8200 kernel: [169634.923061]  [<ffffffffc0161dc6>] drm_atomic_helper_set_config+0x76/0xb0 [drm_kms_helper]
Jun 27 16:24:17 hp-8200 kernel: [169634.923078]  [<ffffffffc0047e12>] drm_mode_set_config_internal+0x62/0x100 [drm]
Jun 27 16:24:17 hp-8200 kernel: [169634.923095]  [<ffffffffc004c46c>] drm_mode_setcrtc+0x3cc/0x4f0 [drm]
Jun 27 16:24:17 hp-8200 kernel: [169634.923110]  [<ffffffffc003d722>] drm_ioctl+0x152/0x540 [drm]
Jun 27 16:24:17 hp-8200 kernel: [169634.923124]  [<ffffffffc004c0a0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
Jun 27 16:24:17 hp-8200 kernel: [169634.923129]  [<ffffffff8122308f>] do_vfs_ioctl+0x29f/0x490
Jun 27 16:24:17 hp-8200 kernel: [169634.923133]  [<ffffffff8108e5d1>] ? __set_task_blocked+0x41/0xa0
Jun 27 16:24:17 hp-8200 kernel: [169634.923137]  [<ffffffff81090f66>] ? __set_current_blocked+0x36/0x60
Jun 27 16:24:17 hp-8200 kernel: [169634.923140]  [<ffffffff812232f9>] SyS_ioctl+0x79/0x90
Jun 27 16:24:17 hp-8200 kernel: [169634.923143]  [<ffffffff8109121e>] ? SyS_rt_sigprocmask+0x8e/0xc0
Jun 27 16:24:17 hp-8200 kernel: [169634.923147]  [<ffffffff81840a72>] entry_SYSCALL_64_fastpath+0x16/0x71
Jun 27 16:24:17 hp-8200 kernel: [169634.923150] ---[ end trace bc85485a839b8a0e ]---
```

---

### Post by mexp on 2018-06-19
Hi folks,

This is still happening on this same PC... I haven't been able to figure out why it's freezing. 

Any ideas that I could look into?

---

