---
title: "Ubuntu 14.04 complete system freeze"
date: 2015-04-22
forum: General Help
---

### Post by NaneK on 2015-04-22
Hello everybody,

I have been using Ubuntu for a long time. I dualbooted with Windows. While I was dualbooting I hadn't any problem at all.
About week ago I wiped out my Windows, a freshly installed Ubuntu as my main OS.

It runs perfectly, even better than Windows 7. My laptop is way less hotter now, acctualy its cold now xD
But last night I had a problem. I was listening to the music, chating via ChatCrypt, browsing with the Firefox and I was writing some text in Gedit (large text).
And then it hit me. The whole system frooze. Nothing was responsive, I could not even enter TTY. I could just move mouse around for a few seconds and then he disappeared too. It's like I opened screenshot picture, and tried to click on the icons on that picture.
Music was still playing, but the replies from the chat weren't comming. Then after a minut in has unfroozen. But then it run everything that I tried to run via keyboard shortcuts while froozen (opened Ubuntu dash - close it, opened TTY, locked screen - machine did it all right after it unfrooze).

This never heppend on my Windows eariler, and did not heppend on Ubuntu while I was dualbooting.
It just can't be hardware related, cuz, as I were saying, it never happend on Windows. Do not get me wrong - I had Windows freeze also, but never on this laptop.

Below you can have a look at my syslog. The frooze happend somewhere from 20h to 20:30h, can't remeber right time. I would be greatfull if you could see is there something unusal in that period od time.

```
Apr 21 19:15:20 Nuju kernel: [ 8625.499503] psmouse serio4: Touchpad at isa0060/serio4/input0 - driver resynced.
Apr 21 19:17:01 Nuju CRON[5769]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 21 19:24:05 Nuju kernel: [ 9151.736897] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
Apr 21 19:24:05 Nuju kernel: [ 9151.747530] psmouse serio4: Touchpad at isa0060/serio4/input0 - driver resynced.
Apr 21 19:36:05 Nuju kernel: [ 9872.389716] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
Apr 21 19:36:05 Nuju kernel: [ 9872.400304] psmouse serio4: Touchpad at isa0060/serio4/input0 - driver resynced.
Apr 21 19:59:17 Nuju wpa_supplicant[914]: message repeated 95 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 21 19:59:19 Nuju wpa_supplicant[914]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Apr 21 20:01:17 Nuju wpa_supplicant[914]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 20:09:21 Nuju dbus[680]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr 21 20:09:21 Nuju dbus[680]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr 21 20:09:21 Nuju kernel: [11870.158955] systemd-hostnamed[7954]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Apr 21 20:13:22 Nuju kernel: [12111.416291] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
Apr 21 20:13:22 Nuju kernel: [12111.450616] psmouse serio4: Touchpad at isa0060/serio4/input0 - driver resynced.
Apr 21 20:17:01 Nuju CRON[8486]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 21 20:19:03 Nuju kernel: [12452.954924] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
Apr 21 20:19:03 Nuju kernel: [12452.974573] psmouse serio4: Touchpad at isa0060/serio4/input0 - driver resynced.
Apr 21 20:20:21 Nuju dbus[680]: [system] Activating service name='org.debian.apt' (using servicehelper)
Apr 21 20:20:22 Nuju AptDaemon: INFO: Initializing daemon
Apr 21 20:20:22 Nuju dbus[680]: [system] Successfully activated service 'org.debian.apt'
Apr 21 20:20:22 Nuju AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Apr 21 20:30:22 Nuju AptDaemon: INFO: Quitting due to inactivity
Apr 21 20:30:22 Nuju AptDaemon: INFO: Quitting was requested
Apr 21 20:34:31 Nuju dbus[680]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr 21 20:34:31 Nuju dbus[680]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr 21 20:34:31 Nuju kernel: [13381.599826] systemd-hostnamed[9269]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

I am using Ubuntu 14.04 LTS 64bit with all updates installed.
Please help me beacuse I almost lost a very important work. I was thinking about restarting laptop or not, but I decided to wait a bit, beacuse I just couldn't lost the text I was working on. So the restart or RESUIB was not an option.

Thanks, cheers!

---

### Post by dino99 on 2015-04-22
That is sometimes also happening to me, but im mainly able to kill the wrong process via system-monitor
Syslog might have logged something about that 

Are you using some 'instable' app/lib from third party/ppa ?

---

### Post by NaneK on 2015-04-22
> **9d9 said:**
> That is sometimes also happening to me, but im mainly able to kill the wrong process via system-monitor
Syslog might have logged something about that 

Are you using some 'instable' app/lib from third party/ppa ?

Yes usualy when just some program stucks I use system monitor. But this time the whole comupter hangs.
I use only one PPA - atareao. It's for the My Weather Indicator. Also I use Bumblebee for my Optimus technology, but I use just Intel GPU, and almost never Nvidia, since I do light computing. So Nvidia is turned off 99.9% of the time.

---

### Post by NaneK on 2015-05-26
Sorry for double post, and old topic refresh, but I still have problems with system freeze.
It happend a few moments ago.

The system has freezen at 23:14h. After 5 minutes (23:19h) it started working. Music was playing in background but I had no controls over anything on system. Buttons, touchpad, function keys nothing was working. 

This is syslog for that period of 5 minutes while system was not usable.

```
May 26 23:14:23 Nuju kernel: [14328.278224] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
May 26 23:14:23 Nuju kernel: [14328.289438] psmouse serio4: Touchpad at isa0060/serio4/input0 - driver resynced.
May 26 23:15:28 Nuju wpa_supplicant[1090]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 26 23:17:01 Nuju CRON[16015]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 26 23:17:28 Nuju wpa_supplicant[1090]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 26 23:17:29 Nuju wpa_supplicant[1090]: nl80211: send_and_recv->nl_recvmsgs failed: -33
May 26 23:18:16 Nuju kernel: [14562.039336] pci_bus 0000:01: Allocating resources
May 26 23:18:16 Nuju kernel: [14562.039367] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:16 Nuju kernel: [14562.039404] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:16 Nuju kernel: [14562.040848] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:16 Nuju kernel: [14562.040878] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:16 Nuju kernel: [14562.041154] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:16 Nuju kernel: [14562.041180] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:16 Nuju kernel: [14562.041500] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:16 Nuju kernel: [14562.041524] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:16 Nuju kernel: [14562.041825] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:16 Nuju kernel: [14562.041848] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:16 Nuju kernel: [14562.042724] pci_bus 0000:02: Allocating resources
May 26 23:18:16 Nuju kernel: [14562.042755] pci_bus 0000:03: Allocating resources
May 26 23:18:16 Nuju kernel: [14562.042789] pci_bus 0000:04: Allocating resources
May 26 23:18:16 Nuju kernel: [14562.042824] pci_bus 0000:05: Allocating resources
May 26 23:18:16 Nuju kernel: [14562.042890] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:16 Nuju kernel: [14562.042915] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:16 Nuju kernel: [14562.043452] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:16 Nuju kernel: [14562.043476] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:18 Nuju kernel: [14563.288608] pci_bus 0000:01: Allocating resources
May 26 23:18:18 Nuju kernel: [14563.288635] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:18 Nuju kernel: [14563.288668] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:18 Nuju kernel: [14563.289960] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:18 Nuju kernel: [14563.289987] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:18 Nuju kernel: [14563.290240] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:18 Nuju kernel: [14563.290263] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:18 Nuju kernel: [14563.290554] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:18 Nuju kernel: [14563.290576] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:18 Nuju kernel: [14563.290851] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:18 Nuju kernel: [14563.290872] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:18 Nuju kernel: [14563.291645] pci_bus 0000:02: Allocating resources
May 26 23:18:18 Nuju kernel: [14563.291673] pci_bus 0000:03: Allocating resources
May 26 23:18:18 Nuju kernel: [14563.291705] pci_bus 0000:04: Allocating resources
May 26 23:18:18 Nuju kernel: [14563.291738] pci_bus 0000:05: Allocating resources
May 26 23:18:18 Nuju kernel: [14563.291898] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:18 Nuju kernel: [14563.291923] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:18 Nuju kernel: [14563.292496] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:18 Nuju kernel: [14563.292521] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:27 Nuju kernel: [14572.826561] pci_bus 0000:01: Allocating resources
May 26 23:18:27 Nuju kernel: [14572.826592] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:27 Nuju kernel: [14572.826630] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:27 Nuju kernel: [14572.828068] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:27 Nuju kernel: [14572.828097] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:27 Nuju kernel: [14572.828374] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:27 Nuju kernel: [14572.828407] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:27 Nuju kernel: [14572.828732] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:27 Nuju kernel: [14572.828757] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:27 Nuju kernel: [14572.829055] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:27 Nuju kernel: [14572.829079] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:27 Nuju kernel: [14572.829946] pci_bus 0000:02: Allocating resources
May 26 23:18:27 Nuju kernel: [14572.829975] pci_bus 0000:03: Allocating resources
May 26 23:18:27 Nuju kernel: [14572.830008] pci_bus 0000:04: Allocating resources
May 26 23:18:27 Nuju kernel: [14572.830042] pci_bus 0000:05: Allocating resources
May 26 23:18:27 Nuju kernel: [14572.830106] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:27 Nuju kernel: [14572.830128] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:27 Nuju kernel: [14572.830620] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:27 Nuju kernel: [14572.830641] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:37 Nuju kernel: [14582.732932] pci_bus 0000:01: Allocating resources
May 26 23:18:37 Nuju kernel: [14582.732959] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:37 Nuju kernel: [14582.732992] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:37 Nuju kernel: [14582.734282] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:37 Nuju kernel: [14582.734309] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:37 Nuju kernel: [14582.734563] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:37 Nuju kernel: [14582.734586] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:37 Nuju kernel: [14582.734879] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:37 Nuju kernel: [14582.734900] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:37 Nuju kernel: [14582.735177] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:37 Nuju kernel: [14582.735198] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:37 Nuju kernel: [14582.735956] pci_bus 0000:02: Allocating resources
May 26 23:18:37 Nuju kernel: [14582.735984] pci_bus 0000:03: Allocating resources
May 26 23:18:37 Nuju kernel: [14582.736016] pci_bus 0000:04: Allocating resources
May 26 23:18:37 Nuju kernel: [14582.736049] pci_bus 0000:05: Allocating resources
May 26 23:18:37 Nuju kernel: [14582.736214] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:37 Nuju kernel: [14582.736244] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:37 Nuju kernel: [14582.736697] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
May 26 23:18:37 Nuju kernel: [14582.736718] pci 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:01.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
May 26 23:18:49 Nuju kernel: [14594.824843] ------------[ cut here ]------------
May 26 23:18:49 Nuju kernel: [14594.824917] WARNING: CPU: 0 PID: 1116 at /build/buildd/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
May 26 23:18:49 Nuju kernel: [14594.824922] Modules linked in: bbswitch(OE) ctr ccm bnep rfcomm binfmt_misc uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev arc4 media ath9k ath9k_common ath9k_hw ath snd_hda_codec_hdmi mac80211 snd_hda_codec_realtek snd_hda_codec_generic cfg80211 snd_hda_intel snd_hda_controller i915 snd_hda_codec snd_hwdep snd_pcm asus_nb_wmi intel_rapl x86_pkg_temp_thermal intel_powerclamp asus_wmi mxm_wmi sparse_keymap coretemp snd_seq_midi snd_seq_midi_event crct10dif_pclmul crc32_pclmul snd_rawmidi snd_seq ghash_clmulni_intel snd_seq_device snd_timer cryptd snd parport_pc ppdev ath3k btusb joydev lp serio_raw soundcore lpc_ich mei_me bluetooth drm_kms_helper drm mei parport 6lowpan_iphc wmi shpchp i2c_algo_bit mac_hid video psmouse ahci libahci atl1c
May 26 23:18:49 Nuju kernel: [14594.825038] CPU: 0 PID: 1116 Comm: Xorg Tainted: G           OE 3.16.0-38-generic #52~14.04.1-Ubuntu
May 26 23:18:49 Nuju kernel: [14594.825043] Hardware name: ASUSTeK Computer Inc. K53SD/K53SD, BIOS K53SD.205 03/06/2012
May 26 23:18:49 Nuju kernel: [14594.825047]  0000000000000009 ffff88009457fbf0 ffffffff8176534f 0000000000000000
May 26 23:18:49 Nuju kernel: [14594.825054]  ffff88009457fc28 ffffffff8106dd9d 0000000000000000 ffff8800970fe000
May 26 23:18:49 Nuju kernel: [14594.825061]  ffff880144c28238 ffff8800987ad800 ffff8800987ad800 ffff88009457fc38
May 26 23:18:49 Nuju kernel: [14594.825068] Call Trace:
May 26 23:18:49 Nuju kernel: [14594.825083]  [<ffffffff8176534f>] dump_stack+0x45/0x56
May 26 23:18:49 Nuju kernel: [14594.825094]  [<ffffffff8106dd9d>] warn_slowpath_common+0x7d/0xa0
May 26 23:18:49 Nuju kernel: [14594.825102]  [<ffffffff8106de7a>] warn_slowpath_null+0x1a/0x20
May 26 23:18:49 Nuju kernel: [14594.825147]  [<ffffffffc04f9ab1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
May 26 23:18:49 Nuju kernel: [14594.825159]  [<ffffffff810b4e70>] ? prepare_to_wait_event+0x100/0x100
May 26 23:18:49 Nuju kernel: [14594.825198]  [<ffffffffc04fc573>] intel_crtc_disable_planes+0x33/0x1c0 [i915]
May 26 23:18:49 Nuju kernel: [14594.825232]  [<ffffffffc04fcb3d>] ironlake_crtc_disable+0x4d/0x920 [i915]
May 26 23:18:49 Nuju kernel: [14594.825284]  [<ffffffffc02d6ae3>] ? drm_modeset_lock+0x33/0xe0 [drm]
May 26 23:18:49 Nuju kernel: [14594.825295]  [<ffffffff8176be52>] ? mutex_lock+0x12/0x2f
May 26 23:18:49 Nuju kernel: [14594.825334]  [<ffffffffc04fde77>] intel_crtc_update_dpms+0x67/0xa0 [i915]
May 26 23:18:49 Nuju kernel: [14594.825370]  [<ffffffffc0502339>] intel_connector_dpms+0x59/0x70 [i915]
May 26 23:18:49 Nuju kernel: [14594.825413]  [<ffffffffc02cd9cf>] drm_mode_obj_set_property_ioctl+0x39f/0x3b0 [drm]
May 26 23:18:49 Nuju kernel: [14594.825449]  [<ffffffffc02cda10>] drm_mode_connector_property_set_ioctl+0x30/0x40 [drm]
May 26 23:18:49 Nuju kernel: [14594.825476]  [<ffffffffc02bc9ec>] drm_ioctl+0x1ec/0x660 [drm]
May 26 23:18:49 Nuju kernel: [14594.825493]  [<ffffffff810a60a8>] ? __enqueue_entity+0x78/0x80
May 26 23:18:49 Nuju kernel: [14594.825503]  [<ffffffff8101db46>] ? __switch_to_xtra+0x136/0x170
May 26 23:18:49 Nuju kernel: [14594.825512]  [<ffffffff811e7360>] do_vfs_ioctl+0x2e0/0x4c0
May 26 23:18:49 Nuju kernel: [14594.825520]  [<ffffffff8176958f>] ? __schedule+0x35f/0x7a0
May 26 23:18:49 Nuju kernel: [14594.825527]  [<ffffffff811e75c1>] SyS_ioctl+0x81/0xa0
May 26 23:18:49 Nuju kernel: [14594.825533]  [<ffffffff811e95f5>] ? SyS_poll+0x65/0x100
May 26 23:18:49 Nuju kernel: [14594.825541]  [<ffffffff8176da4d>] system_call_fastpath+0x1a/0x1f
May 26 23:18:49 Nuju kernel: [14594.825547] ---[ end trace d178b86865d891c0 ]---
May 26 23:19:04 Nuju dbus[690]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
May 26 23:19:04 Nuju kernel: [14609.931985] systemd-hostnamed[16049]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
May 26 23:19:04 Nuju dbus[690]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 26 23:19:28 Nuju wpa_supplicant[1090]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 26 23:19:53 Nuju kernel: [14658.521545] init: tty4 main process ended, respawning
```

---

### Post by NaneK on 2015-08-11
Sorry for refresh of old topic, but I found out why my comupter had freezen. I am posting it below so it may help somebody.

Every single time when this happend (total freeze), I was listening music or (more often) the radio via Rhythmbox. I stopped using Rhythmbox and tried listening music via Totem (Videos now). Since May 26, untill today I didn't have a single freeze. Today I tried Rhythmbox (radio) again, and it freezed in a few minutes just like before. So for me Rhythmbox caused the problem of freezing the comupter. I stopped using it, and I now play my music via Totem, and I prefer it since it is simple.

What caused Rhythmbox to act funny, I do not know.

---

