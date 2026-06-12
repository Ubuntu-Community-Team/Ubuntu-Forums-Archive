---
title: "sudo fails and Kernel bug"
date: 2020-08-17
forum: General Help
---

### Post by hans12345 on 2020-08-17
I have my Ubuntu 20.04 failing after about an hour of use. It is not quite dead but not usable. It will not shutdown and has to be forcibly powered off and restarted. Then it works again for a while.

Initially my Internet connection dies. I have been poking around. I find the network-manager is not running. I try a sudo command but **sudo does not work**. It does not even ask for my password. No command starting with sudo works.

I look at the system log (sorry not attached here since I'm forced to report this on an old Win10 PC, which at least has Internet) and I see:
kernel: kernel BUG at mm/slub.c:306!

Any ideas? What should I be looking for? What can I post to make things clearer?

Help!

---

### Post by hans12345 on 2020-08-17
I have rebooted and am on the Ubuntu PC again. Now I can post the key part of the system log around the kernel bug :

```

08:19:14 kernel: Modules linked in: ccm intel_rapl_msr usblp mei_hdcp intel_rapl_common x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel crct10dif_pclmul snd_intel_dspcfg snd_hda_codec ghash_clmulni_intel snd_hda_core snd_hwdep ath9k_htc snd_pcm amdgpu ath9k_common snd_seq_midi snd_seq_midi_event aesni_intel ath9k_hw crypto_simd cryptd glue_helper ath intel_cstate snd_rawmidi intel_rapl_perf amd_iommu_v2 snd_seq mac80211 eeepc_wmi asus_wmi sparse_keymap input_leds wmi_bmof gpu_sched serio_raw snd_seq_device mxm_wmi ttm snd_timer drm_kms_helper snd i2c_algo_bit fb_sys_fops cfg80211 syscopyarea sysfillrect soundcore libarc4 sysimgblt mei_me mei mac_hid acpi_pad sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 uas usb_storage nvme ahci r8169 crc32_pclmul psmouse i2c_i801 nvme_core realtek libahci wmi video
08:19:14 kernel:  ret_from_fork+0x35/0x40
08:19:14 kernel: Call Trace:
08:19:14 kernel: CR2: 000055eb5f768978 CR3: 0000000318c0a005 CR4: 00000000003606e0
08:19:14 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
08:19:14 kernel: FS:  0000000000000000(0000) GS:ffff98eb66b00000(0000) knlGS:0000000000000000
08:19:14 kernel: R13: ffff98eb64c02e00 R14: ffffffff88518c35 R15: ffffae638050bd48
08:19:14 kernel: R10: ffff98eb66b29a00 R11: ffff98eb66b299e0 R12: fffffa3a50697800
08:19:14 kernel: RBP: ffffae638050bc70 R08: ffff98eb5a5e0600 R09: 0000000000000000
08:19:14 kernel: RDX: 000000000003ea42 RSI: 0000000000000246 RDI: ffff98eb5a5e0600
08:19:14 kernel: RAX: ffff98eb5a5e0600 RBX: ffff98eb5a5e0600 RCX: ffff98eb5a5e0600
08:19:14 kernel: RSP: 0018:ffffae638050bc50 EFLAGS: 00010246
08:19:14 kernel: Code: e7 e8 fe 68 fd ff e9 ef fe ff ff 4d 89 f1 41 b8 01 00 00 00 48 89 d9 48 89 da 4c 89 e6 4c 89 ef e8 9f fa ff ff e9 d0 fe ff ff <0f> 0b 48 8b 05 b1 ab 36 01 e9 ff fd ff ff 66 66 2e 0f 1f 84 00 00
08:19:14 kernel: RIP: 0010:kfree+0x236/0x250
08:19:14 kernel: Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
08:19:14 kernel: Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
08:19:14 kernel: CPU: 2 PID: 260 Comm: kworker/u8:4 Not tainted 5.4.0-42-generic #46-Ubuntu
08:19:14 kernel: invalid opcode: 0000 [#1] SMP PTI
08:19:14 kernel: kernel BUG at mm/slub.c:306!
08:19:14 kernel: ------------[ cut here ]------------
08:19:14 kernel: wlx74ea3a8f3e6d: deauthenticating from 8c:3b:ad:fc:81:66 by local choice (Reason: 3=DEAUTH_LEAVING)
08:19:14 kernel: usb 1-6: USB disconnect, device number 2

```

A further minor note. 
When I try to log off and power down, I am left with a black screen with "Ubuntu" written in large white letters at the bottom. This just stays until I hold the power switch off for a while.

---

### Post by hans12345 on 2020-08-18
I had a further crash today. This was a hard one. Screen just froze. Had to do a forced power off.

Key log files at the time of the crash (about 15.30):
```
Syslog:
Aug 18 14:30:36 Arctic systemd[1]: Started Run anacron jobs.
Aug 18 14:30:36 Arctic anacron[4645]: Anacron 2.3 started on 2020-08-18
Aug 18 14:30:36 Arctic anacron[4645]: Normal exit (0 jobs run)
Aug 18 14:30:36 Arctic systemd[1]: anacron.service: Succeeded.
Aug 18 15:01:50 Arctic systemd[1]: Starting Refresh fwupd metadata and update motd...
Aug 18 15:01:50 Arctic systemd[1]: fwupd-refresh.service: Succeeded.
Aug 18 15:01:50 Arctic systemd[1]: Finished Refresh fwupd metadata and update motd.
Aug 18 15:08:16 Arctic wpa_supplicant[982]: wlx74ea3a8f3e6d: WPA: Group rekeying completed with 8c:3b:ad:fc:81:66 [GTK=TKIP]
Aug 18 15:10:32 Arctic wpa_supplicant[982]: wlx74ea3a8f3e6d: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-74 noise=9999 txrate=243000
Aug 18 15:10:40 Arctic wpa_supplicant[982]: wlx74ea3a8f3e6d: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-66 noise=9999 txrate=270000
Aug 18 15:11:52 Arctic wpa_supplicant[982]: wlx74ea3a8f3e6d: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-60 noise=9999 txrate=300000
Aug 18 15:14:40 Arctic wpa_supplicant[982]: wlx74ea3a8f3e6d: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-54 noise=9999 txrate=243000
Aug 18 15:17:01 Arctic CRON[5012]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 18 15:30:01 Arctic CRON[5094]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
auth log:
Aug 18 14:17:01 Arctic CRON[4531]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 14:17:01 Arctic CRON[4531]: pam_unix(cron:session): session closed for user root
Aug 18 14:30:01 Arctic CRON[4640]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 14:30:01 Arctic CRON[4640]: pam_unix(cron:session): session closed for user root
Aug 18 15:17:01 Arctic CRON[5011]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 15:17:01 Arctic CRON[5011]: pam_unix(cron:session): session closed for user root
Aug 18 15:30:01 Arctic CRON[5093]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 15:30:01 Arctic CRON[5093]: pam_unix(cron:session): session closed for user root
kern log has nothing at the time of the crash
```

Your help and advice appreciated

---

### Post by Doug S on 2020-08-18
I wonder if [this]("https://bugzilla.kernel.org/show_bug.cgi?id=207703") is your issue?
The fix is already in the mainline kernels, but may not have worked its way back to Ubuntu kernel 5.4 yet. Seems to be in upstream 5.4.47
I did not look for a launchpad version of the bug report.

---

### Post by ActionParsnip on 2020-08-18
What happens when you use sudo? What is output in the terminal? Use a simple command like
```

sudo ls

```

---

### Post by hans12345 on 2020-08-18
Thanks Doug, thanks Action.

Action: that first partial crash I tried 'sudo ls' and got nothing, not even the request for the PW.

But today's freeze crash was quite different. The PC just froze. And the logs are different - no 'kernel bug'.

I am wondering if this is a HW problem? If it is, how can I track it down? Where should I be looking?

Thanks for your help.

---

### Post by TheFu on 2020-08-18
First, a lockup of the GUI isn't necessarily a system lockup.  Have you tried switching to a different console or ssh'ing into the system using a different machine? Do both of those fail?

As for HW issues, 
```
egrep -i 'err|warn' /var/log/*g
```
and check the **dmesg** output for errors and warnings too.  There's a way to do that with **journalctl**, but I don't use that.

The hardest things to troubleshoot are failing power supplies. Many PC shops will test a PSU for free. Just take it in.

Of course, it could be a kernel bug too.

Perhaps an overview of the hardware would help us? Run this **inxi -Fxxpzc0**
If the network isn't working, please use sneaker-net to copy the text output to a flash drive, then copy that from Windows to these forums and wrap it in 'code tags' using the Advanced Edit option.  Otherwise, it is just too hard to read the output.

---

### Post by Doug S on 2020-08-18
As a test, try [the mainline kernel]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9-rc1/").

---

### Post by hans12345 on 2020-08-19
Output from  inxi -Fxxxpzc0 (extra x option chosen from askubuntu advice):
```

System:    Kernel: 5.4.0-42-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.3 wm: gnome-shell 
           dm: GDM3 3.34.1 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: PRIME B250M-A v: Rev X.0x serial: <filter> UEFI [Legacy]: American Megatrends 
           v: 0614 date: 04/18/2017 
CPU:       Topology: Dual Core model: Intel Pentium G4560 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 27999 
           Speed: 800 MHz min/max: 800/3500 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: AMD Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X] vendor: Sapphire Limited driver: amdgpu 
           v: kernel bus ID: 01:00.0 chip ID: 1002:699f 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu compositor: gnome-shell resolution: 1920x1080~60Hz 
           OpenGL: renderer: Radeon RX550/550 Series (POLARIS12 DRM 3.35.0 5.4.0-42-generic LLVM 10.0.0) v: 4.6 Mesa 20.0.8 
           direct render: Yes 
Audio:     Device-1: Intel 200 Series PCH HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
           chip ID: 8086:a2f0 
           Device-2: AMD Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X] vendor: Sapphire Limited 
           driver: snd_hda_intel v: kernel bus ID: 01:00.1 chip ID: 1002:aae0 
           Sound Server: ALSA v: k5.4.0-42-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK driver: r8169 v: kernel port: d000 
           bus ID: 03:00.0 chip ID: 10ec:8168 
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
           Device-2: Qualcomm Atheros TP-Link TL-WN821N v3 / TL-WN822N v2 802.11n [Atheros AR7010+AR9287] type: USB 
           driver: ath9k_htc bus ID: 1-6:2 chip ID: 0cf3:7015 serial: <filter> 
           IF: wlx74ea3a8f3e6d state: up mac: <filter> 
Drives:    Local Storage: total: 1.57 TiB used: 265.87 GiB (16.5%) 
           ID-1: /dev/nvme0n1 vendor: Corsair model: Force MP510 size: 447.13 GiB speed: 31.6 Gb/s lanes: 4 serial: <filter> 
           rev: ECFM12.2 scheme: GPT 
           ID-2: /dev/sda vendor: Samsung model: SP2504C size: 232.89 GiB speed: 3.0 Gb/s serial: <filter> rev: 0-50 
           scheme: MBR 
           ID-3: /dev/sdb vendor: Western Digital model: WD10EZEX-08WN4A0 size: 931.51 GiB speed: 6.0 Gb/s rotation: 7200 rpm 
           serial: <filter> rev: 1A01 scheme: GPT 
Partition: ID-1: / size: 95.62 GiB used: 13.90 GiB (14.5%) fs: ext4 dev: /dev/nvme0n1p1 
           ID-2: /home size: 342.99 GiB used: 251.96 GiB (73.5%) fs: ext4 dev: /dev/nvme0n1p2 
           ID-3: /snap/chromium/1244 raw size: 158.4 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop2 
           ID-4: /snap/chromium/1260 raw size: 158.4 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop5 
           ID-5: /snap/core/9665 raw size: 97.0 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop10 
           ID-6: /snap/core/9804 raw size: 96.6 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop6 
           ID-7: /snap/core18/1880 raw size: 55.0 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop0 
           ID-8: /snap/core18/1885 raw size: 55.3 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop1 
           ID-9: /snap/firefox/392 raw size: 145.0 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop3 
           ID-10: /snap/firefox/398 raw size: 163.2 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop15 
           ID-11: /snap/gnome-3-28-1804/116 raw size: 160.2 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop4 
           ID-12: /snap/gnome-3-28-1804/128 raw size: 161.4 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop13 
           ID-13: /snap/gnome-3-34-1804/33 raw size: 255.6 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop12 
           ID-14: /snap/gnome-3-34-1804/36 raw size: 255.6 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop7 
           ID-15: /snap/gtk-common-themes/1502 raw size: 54.8 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop19 
           ID-16: /snap/gtk-common-themes/1506 raw size: 62.1 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop8 
           ID-17: /snap/signal-desktop/326 raw size: 114.2 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop9 
           ID-18: /snap/signal-desktop/327 raw size: 114.3 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop20 
           ID-19: /snap/skype/139 raw size: 177.2 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop11 
           ID-20: /snap/skype/143 raw size: 177.4 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop21 
           ID-21: /snap/snap-store/415 raw size: 43.2 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop18 
           ID-22: /snap/snap-store/467 raw size: 49.8 MiB size: <superuser/root required> used: <superuser/root required> 
           fs: squashfs dev: /dev/loop16 
           ID-23: /snap/speedy-duplicate-finder/26 raw size: 59.2 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop14 
           ID-24: /snap/speedy-duplicate-finder/27 raw size: 59.2 MiB size: <superuser/root required> 
           used: <superuser/root required> fs: squashfs dev: /dev/loop17 
           ID-25: swap-1 size: 3.23 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda6 
           ID-26: swap-2 size: 7.87 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sdb6 
Sensors:   System Temperatures: cpu: 46.0 C mobo: N/A gpu: amdgpu temp: 29 C 
           Fan Speeds (RPM): N/A gpu: amdgpu fan: 1167 
Info:      Processes: 268 Uptime: 1h 11m Memory: 15.58 GiB used: 4.69 GiB (30.1%) Init: systemd v: 245 runlevel: 5 Compilers: 
           gcc: 9.3.0 alt: 9 Shell: bash v: 5.0.17 running in: gnome-terminal inxi: 3.0.38 
```

---

### Post by hans12345 on 2020-08-19
3 errors in dmesg.0 (I cannot understand the layout timewise, so cannot link these to the time of the crash):
```

[    0.198709] kernel: acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.365961] kernel: RAS: Correctable Errors collector initialized.
[    2.279911] kernel: EXT4-fs (nvme0n1p1): re-mounted. Opts: errors=remount-ro

```

---

### Post by hans12345 on 2020-08-19
egrep output

There is nothing obvious here around 15.30 (15.36 is the reboot) on the 18th when the last crash happened:

```

syslog:
Aug 18 14:10:29 Arctic tracker-miner-f[2056]: Could not initialize currently active mount points: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 14:11:02 Arctic tracker-miner-f[2056]:   (Sparql buffer) Error in array-update: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 14:11:02 Arctic tracker-miner-f[2056]: Could not execute sparql: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 14:11:02 Arctic tracker-miner-f[2056]: Could not execute sparql: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Aug 18 15:36:52 Arctic kernel: [    0.198709] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Aug 18 15:36:52 Arctic systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.
Aug 18 15:36:52 Arctic kernel: [    0.365961] RAS: Correctable Errors collector initialized.
Aug 18 15:36:52 Arctic kernel: [    2.279911] EXT4-fs (nvme0n1p1): re-mounted. Opts: errors=remount-ro
Aug 18 15:36:52 Arctic thermald[981]: [WARN]22 CPUID levels; family:model:stepping 0x6:9e:9 (6:158:9)
Aug 18 15:36:52 Arctic thermald[981]: [WARN]Polling mode is enabled: 4
Aug 18 15:36:52 Arctic thermald[981]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Aug 18 15:36:52 Arctic thermald[981]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Aug 18 15:36:52 Arctic thermald[981]: [WARN]sysfs open failed
...

kern.log:
Aug 17 12:09:52 Arctic kernel: [ 5287.099837] audit: type=1400 audit(1597658992.780:4910): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/family/Documents/TEMP/OpenVPNLogErrors-Sue-May" pid=6088 comm="pool-soffice" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Aug 18 07:20:08 Arctic kernel: [    0.197242] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Aug 18 07:20:08 Arctic kernel: [    0.366039] RAS: Correctable Errors collector initialized.
Aug 18 07:20:08 Arctic kernel: [    2.195802] EXT4-fs (nvme0n1p1): re-mounted. Opts: errors=remount-ro
Aug 18 14:07:00 Arctic kernel: [    0.198005] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Aug 18 14:07:00 Arctic kernel: [    0.366470] RAS: Correctable Errors collector initialized.
Aug 18 14:07:00 Arctic kernel: [    2.220279] EXT4-fs (nvme0n1p1): re-mounted. Opts: errors=remount-ro
Aug 18 15:36:52 Arctic kernel: [    0.198709] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Aug 18 15:36:52 Arctic kernel: [    0.365961] RAS: Correctable Errors collector initialized.
Aug 18 15:36:52 Arctic kernel: [    2.279911] EXT4-fs (nvme0n1p1): re-mounted. Opts: errors=remount-ro
Aug 19 05:52:38 Arctic kernel: [    0.198335] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM

dmesg:
[    0.198709] kernel: acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.365961] kernel: RAS: Correctable Errors collector initialized.
[    2.279911] kernel: EXT4-fs (nvme0n1p1): re-mounted. Opts: errors=remount-ro


```

---

### Post by hans12345 on 2020-08-19
Thanks TheFu and Doug S for your input.
I have focused on the ideas of TheFu in my recent posts to see if there is something that I missed.

I no longer believe that this is "sudo fails and Kernel bug " problem.
Ideally the title should be changed.

As you can guess from the HW specs, this is a home-built system. It has been rock solid for years.
But there was one recent change. I upgraded the video card to a RX 550. I was under the impression that this upgrade preceded the crashes by some time but now I wonder. Did I overlook some earlier problems after the upgrade?
Power supply problems are always an issue with graphic card updates but the official power rating (Corsair VS 550W - or 550 watts) far exceeds what I need for this card.

So I am looking forward to new ideas.

Thanks !

---

### Post by TheFu on 2020-08-19
I don't see anything odd in any of the output related to a crash. Sorry.

I do see that both the wired and wifi are enabled. Why? Is this a router?  Probably only want 1 NIC enabled at a time.
[https://askubuntu.com/questions/1145738/osc-failed-ae-error-disabling-aspm](https://askubuntu.com/questions/1145738/osc-failed-ae-error-disabling-aspm) can cause system lockups.

---

### Post by hans12345 on 2020-08-20
> **TheFu said:**
> I don't see anything odd in any of the output related to a crash. Sorry.

I do see that both the wired and wifi are enabled. Why? Is this a router?  Probably only want 1 NIC enabled at a time.
[https://askubuntu.com/questions/1145738/osc-failed-ae-error-disabling-aspm](https://askubuntu.com/questions/1145738/osc-failed-ae-error-disabling-aspm) can cause system lockups.

Thanks for the observation.

Yes they are both enabled. I did not know this was bad.

I was switching between wifi and a powerline to see which was best (the powerline is faster but it has lots of lengthy interruptions) and I just left both on.

Back to the main problem. I imagine having both enabled is not causing my crashes?

Do you think I should be looking for a HW problem?

---

### Post by TheFu on 2020-08-20
> **hans12345 said:**
>  
Do you think I should be looking for a HW problem?

I think it would be very helpful if you answered the questions already asked.

---

### Post by hans12345 on 2020-08-20
Thanks TheFu, I'll go back and see what I missed.

In the meanwhile, I had another freeze at 13.28. Here are the main logs:

```

Syslog for system freeze at 13.28:

Aug 20 13:23:16 Arctic NetworkManager[944]: <info>  [1597922596.3491] manager: NetworkManager state is now CONNECTED_SITE
Aug 20 13:23:16 Arctic dbus-daemon[943]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.6' (uid=0 pid=944 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Aug 20 13:23:16 Arctic whoopsie[1747]: [13:23:16] Cannot reach: https://daisy.ubuntu.com
Aug 20 13:23:16 Arctic whoopsie[1747]: [13:23:16] offline
Aug 20 13:23:16 Arctic systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug 20 13:23:16 Arctic dbus-daemon[943]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 20 13:23:16 Arctic systemd[1]: Started Network Manager Script Dispatcher Service.
Aug 20 13:23:18 Arctic NetworkManager[944]: <info>  [1597922598.1475] manager: NetworkManager state is now CONNECTED_GLOBAL
Aug 20 13:23:18 Arctic whoopsie[1747]: [13:23:18] Cannot reach: https://daisy.ubuntu.com
Aug 20 13:23:18 Arctic whoopsie[1747]: [13:23:18] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Aug 20 13:23:18 Arctic whoopsie[1747]: [13:23:18] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Aug 20 13:23:18 Arctic whoopsie[1747]: [13:23:18] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Aug 20 13:23:19 Arctic whoopsie[1747]: [13:23:19] online
Aug 20 13:23:28 Arctic systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Aug 20 13:26:45 Arctic dbus-daemon[2145]: [session uid=1000 pid=2145] Activating via systemd: service name='org.freedesktop.Tracker1' unit='tracker-store.service' requested by ':1.1' (uid=1000 pid=2143 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
Aug 20 13:26:45 Arctic systemd[2128]: Starting Tracker metadata database store and lookup manager...
Aug 20 13:26:45 Arctic dbus-daemon[2145]: [session uid=1000 pid=2145] Successfully activated service 'org.freedesktop.Tracker1'
Aug 20 13:26:45 Arctic systemd[2128]: Started Tracker metadata database store and lookup manager.
Aug 20 13:26:46 Arctic dbus-daemon[2145]: [session uid=1000 pid=2145] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.1' (uid=1000 pid=2143 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
Aug 20 13:26:46 Arctic systemd[2128]: Starting Tracker metadata extractor...
Aug 20 13:26:46 Arctic tracker-extract[8858]: Set scheduler policy to SCHED_IDLE
Aug 20 13:26:46 Arctic tracker-extract[8858]: Setting priority nice level to 19
Aug 20 13:26:46 Arctic dbus-daemon[2145]: [session uid=1000 pid=2145] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
Aug 20 13:26:46 Arctic systemd[2128]: Started Tracker metadata extractor.
Aug 20 13:26:56 Arctic systemd[2128]: tracker-extract.service: Succeeded.
Aug 20 13:27:16 Arctic tracker-store[8850]: OK
Aug 20 13:27:16 Arctic systemd[2128]: tracker-store.service: Succeeded.
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Aug 20 13:32:25 Arctic systemd-modules-load[352]: Inserted module 'lp'

kern.log:

Aug 20 11:57:13 Arctic kernel: [14108.622260] ath: phy0: Short RX data len, dropping (dlen: 4)
Aug 20 12:27:14 Arctic kernel: [15908.639667] ath: phy0: Short RX data len, dropping (dlen: 4)
Aug 20 13:12:14 Arctic kernel: [18608.728995] ath: phy0: Short RX data len, dropping (dlen: 4)
Aug 20 13:12:14 Arctic kernel: [18608.760271] ath: phy0: Short RX data len, dropping (dlen: 4)
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Aug 20 13:32:25 Arctic kernel: [    0.000000] microcode: microcode updated early to revision 0xd6, date = 2020-04-23


```

---

### Post by TheFu on 2020-08-20
How many logs do you save? Hopefully, at least 3.  What's the same between each failure?
Should unplug the wifi and see if that stops the crashes.

---

### Post by hans12345 on 2020-08-21
Thanks TheFu

To my uneducated eye, there seems to be nothing much in common in the last few days logs.


About the double network connection (wifi and LAN powerline)

I have been looking at the "disabling ASPM" question.

My understanding of the post at:
[https://askubuntu.com/questions/1145738/osc-failed-ae-error-disabling-aspm](https://askubuntu.com/questions/1145738/osc-failed-ae-error-disabling-aspm)
is that doing this disable will not affect system stability, which however would be caused by forcing ASPM.

e.g. I have seen this Warning:
If pcie_aspm=force is set, hardware that does not support ASPM can cause the system to stop responding. Before setting pcie_aspm=force, ensure that all PCIe hardware on the system supports ASPM. 

But after yesterday's (20 Aug) crash I started a check. I looked at the Ubuntu GUI network status and it reported that the fixed network connection (via the powerline) was off.

Nevertheless, I have now disconnected the cable to the powerline and I hope this solves any confusion about how the PC is accessing the network.
(I prefer the wifi connection since the powerline has frequent outages)

This morning's boot (no powerline) still reports in syslog:
Aug 21 06:46:05 Arctic kernel: [    0.197017] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]
Aug 21 06:46:05 Arctic kernel: [    0.197052] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM

So it looks as if nothing has changed.

I shall report back if the crashes have gone (or indeed if they have not)

---

### Post by TheFu on 2020-08-21
I use powerline to connect between different floors. It works much better than wifi and never has "outages", so that is foreign to me.
In 2005-ish, I designed and helped deploy wifi to over 1200 locations.  That taught me to always avoid using wifi whenever possible. It is always a security risk and should never be used without a full VPN from the client out. Never trust just the encryption built into the wifi protocols. It cannot be trusted.  Every year, we learn about different problems with wifi security. Even the newest protocols have been hacked and remain unsecured today.

To the computer, there's no difference between wired and powerline ethernet. It doesn't know anything about powerline.

I haven't used a GUI to manage network connections on Linux in at least 10 yrs.  For wifi, I use a TUI, for wired, I use the config files in /etc/. Only portable systems use DHCP, with reservations. All the others use static IPs controlled by each server. DHCP servers fail sometimes and I've seen what happens to large networks when that happens - servers start dropping offline as they attempt to renew the connections and get current IPs/netmasks/gateways/DNS servers. Freshly booted systems don't join the network. It isn't pretty.  We all learn from our experiences.

---

### Post by hans12345 on 2020-08-22
A Kernel bug in another crash, but a 2 stage one. 

At 09.27 I lost the internet but the rest seemed OK.
At 09.30, whilst using the file manager to look at the logs, the system crashed

Note the "kernel BUG at mm/slub.c:306!" at 09.27

Syslog:
```

Aug 22 09:20:51 Arctic wpa_supplicant[977]: wlx74ea3a8f3e6d: CTRL-EVENT-BEACON-LOSS 
Aug 22 09:27:33 Arctic kernel: [ 3070.503979] usb 1-6: ath: firmware panic! exccause: 0x0000000d; pc: 0x0090ae81; badvaddr: 0x10ff4038.
Aug 22 09:27:33 Arctic kernel: [ 3070.626365] usb 1-6: USB disconnect, device number 2
Aug 22 09:27:33 Arctic kernel: [ 3070.642106] wlx74ea3a8f3e6d: deauthenticating from 8c:3b:ad:fc:81:66 by local choice (Reason: 3=DEAUTH_LEAVING)
Aug 22 09:27:33 Arctic kernel: [ 3070.906134] ------------[ cut here ]------------
Aug 22 09:27:33 Arctic kernel: [ 3070.906139] kernel BUG at mm/slub.c:306!
Aug 22 09:27:33 Arctic kernel: [ 3070.906154] invalid opcode: 0000 [#1] SMP PTI
Aug 22 09:27:33 Arctic kernel: [ 3070.906161] CPU: 2 PID: 262 Comm: kworker/u8:7 Not tainted 5.4.0-42-generic #46-Ubuntu
Aug 22 09:27:33 Arctic kernel: [ 3070.906164] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Aug 22 09:27:33 Arctic kernel: [ 3070.906180] Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906190] RIP: 0010:__slab_free+0x189/0x330
Aug 22 09:27:33 Arctic kernel: [ 3070.906195] Code: 00 48 89 c7 fa 66 0f 1f 44 00 00 f0 49 0f ba 2c 24 00 72 65 4d 3b 6c 24 20 74 11 49 0f ba 34 24 00 57 9d 0f 1f 44 00 00 eb 9f <0f> 0b 49 3b 5c 24 28 75 e8 48 8b 44 24 28 49 89 4c 24 28 49 89 44
Aug 22 09:27:33 Arctic kernel: [ 3070.906199] RSP: 0018:ffffb101c050bba0 EFLAGS: 00010246
Aug 22 09:27:33 Arctic kernel: [ 3070.906204] RAX: ffff931b230db800 RBX: 000000008010000b RCX: ffff931b230db800
Aug 22 09:27:33 Arctic kernel: [ 3070.906207] RDX: ffff931b230db800 RSI: ffffe597908c3680 RDI: ffff931b24c02e00
Aug 22 09:27:33 Arctic kernel: [ 3070.906210] RBP: ffffb101c050bc40 R08: 0000000000000001 R09: ffffffffba518c35
Aug 22 09:27:33 Arctic kernel: [ 3070.906213] R10: ffff931b230db800 R11: 0000000000000001 R12: ffffe597908c3680
Aug 22 09:27:33 Arctic kernel: [ 3070.906216] R13: ffff931b230db800 R14: ffff931b24c02e00 R15: ffffb101c050bd48
Aug 22 09:27:33 Arctic kernel: [ 3070.906221] FS:  0000000000000000(0000) GS:ffff931b26b00000(0000) knlGS:0000000000000000
Aug 22 09:27:33 Arctic kernel: [ 3070.906224] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 22 09:27:33 Arctic kernel: [ 3070.906227] CR2: 00007fa5530df000 CR3: 000000024500a002 CR4: 00000000003606e0
Aug 22 09:27:33 Arctic kernel: [ 3070.906230] Call Trace:
Aug 22 09:27:33 Arctic kernel: [ 3070.906243]  ? del_timer_sync+0x29/0x40
Aug 22 09:27:33 Arctic kernel: [ 3070.906250]  ? schedule_timeout+0x15a/0x2f0
Aug 22 09:27:33 Arctic kernel: [ 3070.906257]  ? skb_free_head+0x25/0x30
Aug 22 09:27:33 Arctic kernel: [ 3070.906261]  kfree+0x231/0x250
Aug 22 09:27:33 Arctic kernel: [ 3070.906266]  skb_free_head+0x25/0x30
Aug 22 09:27:33 Arctic kernel: [ 3070.906272]  skb_release_data+0x11d/0x180
Aug 22 09:27:33 Arctic kernel: [ 3070.906282]  ? ath9k_wmi_cmd+0x1a5/0x1c0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906287]  skb_release_all+0x26/0x30
Aug 22 09:27:33 Arctic kernel: [ 3070.906293]  kfree_skb+0x32/0xa0
Aug 22 09:27:33 Arctic kernel: [ 3070.906301]  ath9k_wmi_cmd+0x1a5/0x1c0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906311]  ath9k_regread+0x48/0x70 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906332]  ar9285_hw_pa_cal+0x317/0x520 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906348]  ar9002_hw_pa_cal+0x36/0x60 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906362]  ar9002_hw_calibrate+0x102/0x440 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906372]  ath9k_htc_ani_work+0x118/0x1a0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906379]  process_one_work+0x1eb/0x3b0
Aug 22 09:27:33 Arctic kernel: [ 3070.906385]  worker_thread+0x4d/0x400
Aug 22 09:27:33 Arctic kernel: [ 3070.906391]  kthread+0x104/0x140
Aug 22 09:27:33 Arctic kernel: [ 3070.906397]  ? process_one_work+0x3b0/0x3b0
Aug 22 09:27:33 Arctic kernel: [ 3070.906401]  ? kthread_park+0x90/0x90
Aug 22 09:27:33 Arctic kernel: [ 3070.906408]  ret_from_fork+0x35/0x40
Aug 22 09:27:33 Arctic kernel: [ 3070.906413] Modules linked in: ccm intel_rapl_msr mei_hdcp intel_rapl_common x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep ath9k_htc snd_pcm ath9k_common crct10dif_pclmul ghash_clmulni_intel ath9k_hw snd_seq_midi snd_seq_midi_event snd_rawmidi ath aesni_intel amdgpu crypto_simd mac80211 cryptd glue_helper intel_cstate snd_seq intel_rapl_perf amd_iommu_v2 snd_seq_device gpu_sched snd_timer cfg80211 ttm eeepc_wmi asus_wmi input_leds drm_kms_helper sparse_keymap wmi_bmof snd mxm_wmi libarc4 i2c_algo_bit serio_raw fb_sys_fops syscopyarea mei_me sysfillrect soundcore sysimgblt mei acpi_pad mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 nvme ahci r8169 crc32_pclmul psmouse nvme_core i2c_i801 realtek libahci wmi video
Aug 22 09:27:33 Arctic kernel: [ 3070.906482] ---[ end trace db8c2e15eab6e90f ]---
Aug 22 09:27:33 Arctic kernel: [ 3070.906487] RIP: 0010:__slab_free+0x189/0x330
Aug 22 09:27:33 Arctic kernel: [ 3070.906492] Code: 00 48 89 c7 fa 66 0f 1f 44 00 00 f0 49 0f ba 2c 24 00 72 65 4d 3b 6c 24 20 74 11 49 0f ba 34 24 00 57 9d 0f 1f 44 00 00 eb 9f <0f> 0b 49 3b 5c 24 28 75 e8 48 8b 44 24 28 49 89 4c 24 28 49 89 44
Aug 22 09:27:33 Arctic kernel: [ 3070.906495] RSP: 0018:ffffb101c050bba0 EFLAGS: 00010246
Aug 22 09:27:33 Arctic kernel: [ 3070.906499] RAX: ffff931b230db800 RBX: 000000008010000b RCX: ffff931b230db800
Aug 22 09:27:33 Arctic kernel: [ 3070.906502] RDX: ffff931b230db800 RSI: ffffe597908c3680 RDI: ffff931b24c02e00
Aug 22 09:27:33 Arctic kernel: [ 3070.906505] RBP: ffffb101c050bc40 R08: 0000000000000001 R09: ffffffffba518c35
Aug 22 09:27:33 Arctic kernel: [ 3070.906508] R10: ffff931b230db800 R11: 0000000000000001 R12: ffffe597908c3680
Aug 22 09:27:33 Arctic kernel: [ 3070.906511] R13: ffff931b230db800 R14: ffff931b24c02e00 R15: ffffb101c050bd48
Aug 22 09:27:33 Arctic kernel: [ 3070.906515] FS:  0000000000000000(0000) GS:ffff931b26b00000(0000) knlGS:0000000000000000
Aug 22 09:27:33 Arctic kernel: [ 3070.906518] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 22 09:27:33 Arctic kernel: [ 3070.906521] CR2: 00007fa5530df000 CR3: 000000024500a002 CR4: 00000000003606e0
Aug 22 09:22:13 Arctic wpa_supplicant[977]: wlx74ea3a8f3e6d: CTRL-EVENT-BEACON-LOSS 
Aug 22 09:29:12 Arctic gnome-shell[2508]: JS ERROR: TypeError: area is null#012padArea@resource:///org/gnome/shell/ui/workspace.js:1101:9#012_updateWindowPositions@resource:///org/gnome/shell/ui/workspace.js:1334:20#012_realRecalculateWindowPositions@resource:///org/gnome/shell/ui/workspace.js:1311:14#012_recalculateWindowPositions/this._positionWindowsId<@resource:///org/gnome/shell/ui/workspace.js:1286:18
Aug 22 09:29:18 Arctic dbus-daemon[2020]: [session uid=1000 pid=2020] Activating service name='org.gnome.Logs' requested by ':1.40' (uid=1000 pid=2508 comm="/usr/bin/gnome-shell " label="unconfined")
Aug 22 09:29:18 Arctic dbus-daemon[2020]: [session uid=1000 pid=2020] Successfully activated service 'org.gnome.Logs'
Aug 22 09:30:01 Arctic CRON[7720]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Aug 22 09:30:53 Arctic dbus-daemon[2020]: [session uid=1000 pid=2020] Activating service name='org.gnome.Nautilus' requested by ':1.40' (uid=1000 pid=2508 comm="/usr/bin/gnome-shell " label="unconfined")
Aug 22 09:30:53 Arctic dbus-daemon[2020]: [session uid=1000 pid=2020] Successfully activated service 'org.gnome.Nautilus'
Aug 22 09:30:53 Arctic dbus-daemon[941]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.137' (uid=1000 pid=7731 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Aug 22 09:30:53 Arctic systemd[1]: Starting Hostname Service...
Aug 22 09:31:38 Arctic systemd[1]: Started Run anacron jobs.
Aug 22 09:31:38 Arctic anacron[7761]: Anacron 2.3 started on 2020-08-22
Aug 22 09:31:38 Arctic anacron[7761]: Normal exit (0 jobs run)
Aug 22 09:31:38 Arctic systemd[1]: anacron.service: Succeeded.
Aug 22 09:32:23 Arctic systemd[1]: systemd-hostnamed.service: start operation timed out. Terminating.
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Aug 22 09:33:27 Arctic systemd-modules-load[355]: Inserted module 'lp'
Aug 22 09:33:27 Arctic systemd-modules-load[355]: Inserted module 'ppdev'

```

---

### Post by hans12345 on 2020-08-22
> **TheFu said:**
> I use powerline to connect between different floors. It works much better than wifi and never has "outages", so that is foreign to me.
In 2005-ish, I designed and helped deploy wifi to over 1200 locations.  That taught me to always avoid using wifi whenever possible. It is always a security risk and should never be used without a full VPN from the client out. Never trust just the encryption built into the wifi protocols. It cannot be trusted.  Every year, we learn about different problems with wifi security. Even the newest protocols have been hacked and remain unsecured today.

To the computer, there's no difference between wired and powerline ethernet. It doesn't know anything about powerline.

I haven't used a GUI to manage network connections on Linux in at least 10 yrs.  For wifi, I use a TUI, for wired, I use the config files in /etc/. Only portable systems use DHCP, with reservations. All the others use static IPs controlled by each server. DHCP servers fail sometimes and I've seen what happens to large networks when that happens - servers start dropping offline as they attempt to renew the connections and get current IPs/netmasks/gateways/DNS servers. Freshly booted systems don't join the network. It isn't pretty.  We all learn from our experiences.

Hi The Fu

I admire your professional approach. I am not at your level.
Of course a LAN is a LAN even if a powerline is present.
The house here is old and the wiring is a mess. I have 3 fuseboxes! I cannot track down the cause of the powerline problems.
I acknowledge the wifi security risk, Luckily I only have 2 neighbours in range and they are old folks.

As for the GUI, I try to use it for everything. I work very slowly with the terminal.

Thanks for your help

---

### Post by hans12345 on 2020-08-22
All the bad stuff seems to be at 09.27. It is strange that the GUI worked for a couple of minutes.
The kern.log at the time of the crash:
```

Aug 22 08:41:31 Arctic kernel: [  308.830746] ath: phy0: Short RX data len, dropping (dlen: 4)
Aug 22 09:27:33 Arctic kernel: [ 3070.503979] usb 1-6: ath: firmware panic! exccause: 0x0000000d; pc: 0x0090ae81; badvaddr: 0x10ff4038.
Aug 22 09:27:33 Arctic kernel: [ 3070.626365] usb 1-6: USB disconnect, device number 2
Aug 22 09:27:33 Arctic kernel: [ 3070.642106] wlx74ea3a8f3e6d: deauthenticating from 8c:3b:ad:fc:81:66 by local choice (Reason: 3=DEAUTH_LEAVING)
Aug 22 09:27:33 Arctic kernel: [ 3070.906134] ------------[ cut here ]------------
Aug 22 09:27:33 Arctic kernel: [ 3070.906139] kernel BUG at mm/slub.c:306!
Aug 22 09:27:33 Arctic kernel: [ 3070.906154] invalid opcode: 0000 [#1] SMP PTI
Aug 22 09:27:33 Arctic kernel: [ 3070.906161] CPU: 2 PID: 262 Comm: kworker/u8:7 Not tainted 5.4.0-42-generic #46-Ubuntu
Aug 22 09:27:33 Arctic kernel: [ 3070.906164] Hardware name: System manufacturer System Product Name/PRIME B250M-A, BIOS 0614 04/18/2017
Aug 22 09:27:33 Arctic kernel: [ 3070.906180] Workqueue: phy0 ath9k_htc_ani_work [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906190] RIP: 0010:__slab_free+0x189/0x330
Aug 22 09:27:33 Arctic kernel: [ 3070.906195] Code: 00 48 89 c7 fa 66 0f 1f 44 00 00 f0 49 0f ba 2c 24 00 72 65 4d 3b 6c 24 20 74 11 49 0f ba 34 24 00 57 9d 0f 1f 44 00 00 eb 9f <0f> 0b 49 3b 5c 24 28 75 e8 48 8b 44 24 28 49 89 4c 24 28 49 89 44
Aug 22 09:27:33 Arctic kernel: [ 3070.906199] RSP: 0018:ffffb101c050bba0 EFLAGS: 00010246
Aug 22 09:27:33 Arctic kernel: [ 3070.906204] RAX: ffff931b230db800 RBX: 000000008010000b RCX: ffff931b230db800
Aug 22 09:27:33 Arctic kernel: [ 3070.906207] RDX: ffff931b230db800 RSI: ffffe597908c3680 RDI: ffff931b24c02e00
Aug 22 09:27:33 Arctic kernel: [ 3070.906210] RBP: ffffb101c050bc40 R08: 0000000000000001 R09: ffffffffba518c35
Aug 22 09:27:33 Arctic kernel: [ 3070.906213] R10: ffff931b230db800 R11: 0000000000000001 R12: ffffe597908c3680
Aug 22 09:27:33 Arctic kernel: [ 3070.906216] R13: ffff931b230db800 R14: ffff931b24c02e00 R15: ffffb101c050bd48
Aug 22 09:27:33 Arctic kernel: [ 3070.906221] FS:  0000000000000000(0000) GS:ffff931b26b00000(0000) knlGS:0000000000000000
Aug 22 09:27:33 Arctic kernel: [ 3070.906224] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 22 09:27:33 Arctic kernel: [ 3070.906227] CR2: 00007fa5530df000 CR3: 000000024500a002 CR4: 00000000003606e0
Aug 22 09:27:33 Arctic kernel: [ 3070.906230] Call Trace:
Aug 22 09:27:33 Arctic kernel: [ 3070.906243]  ? del_timer_sync+0x29/0x40
Aug 22 09:27:33 Arctic kernel: [ 3070.906250]  ? schedule_timeout+0x15a/0x2f0
Aug 22 09:27:33 Arctic kernel: [ 3070.906257]  ? skb_free_head+0x25/0x30
Aug 22 09:27:33 Arctic kernel: [ 3070.906261]  kfree+0x231/0x250
Aug 22 09:27:33 Arctic kernel: [ 3070.906266]  skb_free_head+0x25/0x30
Aug 22 09:27:33 Arctic kernel: [ 3070.906272]  skb_release_data+0x11d/0x180
Aug 22 09:27:33 Arctic kernel: [ 3070.906282]  ? ath9k_wmi_cmd+0x1a5/0x1c0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906287]  skb_release_all+0x26/0x30
Aug 22 09:27:33 Arctic kernel: [ 3070.906293]  kfree_skb+0x32/0xa0
Aug 22 09:27:33 Arctic kernel: [ 3070.906301]  ath9k_wmi_cmd+0x1a5/0x1c0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906311]  ath9k_regread+0x48/0x70 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906332]  ar9285_hw_pa_cal+0x317/0x520 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906348]  ar9002_hw_pa_cal+0x36/0x60 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906362]  ar9002_hw_calibrate+0x102/0x440 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906372]  ath9k_htc_ani_work+0x118/0x1a0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906379]  process_one_work+0x1eb/0x3b0
Aug 22 09:27:33 Arctic kernel: [ 3070.906385]  worker_thread+0x4d/0x400
Aug 22 09:27:33 Arctic kernel: [ 3070.906391]  kthread+0x104/0x140
Aug 22 09:27:33 Arctic kernel: [ 3070.906397]  ? process_one_work+0x3b0/0x3b0
Aug 22 09:27:33 Arctic kernel: [ 3070.906401]  ? kthread_park+0x90/0x90
Aug 22 09:27:33 Arctic kernel: [ 3070.906408]  ret_from_fork+0x35/0x40
Aug 22 09:27:33 Arctic kernel: [ 3070.906413] Modules linked in: ccm intel_rapl_msr mei_hdcp intel_rapl_common x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep ath9k_htc snd_pcm ath9k_common crct10dif_pclmul ghash_clmulni_intel ath9k_hw snd_seq_midi snd_seq_midi_event snd_rawmidi ath aesni_intel amdgpu crypto_simd mac80211 cryptd glue_helper intel_cstate snd_seq intel_rapl_perf amd_iommu_v2 snd_seq_device gpu_sched snd_timer cfg80211 ttm eeepc_wmi asus_wmi input_leds drm_kms_helper sparse_keymap wmi_bmof snd mxm_wmi libarc4 i2c_algo_bit serio_raw fb_sys_fops syscopyarea mei_me sysfillrect soundcore sysimgblt mei acpi_pad mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 nvme ahci r8169 crc32_pclmul psmouse nvme_core i2c_i801 realtek libahci wmi video
Aug 22 09:27:33 Arctic kernel: [ 3070.906482] ---[ end trace db8c2e15eab6e90f ]---
Aug 22 09:27:33 Arctic kernel: [ 3070.906487] RIP: 0010:__slab_free+0x189/0x330
Aug 22 09:27:33 Arctic kernel: [ 3070.906492] Code: 00 48 89 c7 fa 66 0f 1f 44 00 00 f0 49 0f ba 2c 24 00 72 65 4d 3b 6c 24 20 74 11 49 0f ba 34 24 00 57 9d 0f 1f 44 00 00 eb 9f <0f> 0b 49 3b 5c 24 28 75 e8 48 8b 44 24 28 49 89 4c 24 28 49 89 44
Aug 22 09:27:33 Arctic kernel: [ 3070.906495] RSP: 0018:ffffb101c050bba0 EFLAGS: 00010246
Aug 22 09:27:33 Arctic kernel: [ 3070.906499] RAX: ffff931b230db800 RBX: 000000008010000b RCX: ffff931b230db800
Aug 22 09:27:33 Arctic kernel: [ 3070.906502] RDX: ffff931b230db800 RSI: ffffe597908c3680 RDI: ffff931b24c02e00
Aug 22 09:27:33 Arctic kernel: [ 3070.906505] RBP: ffffb101c050bc40 R08: 0000000000000001 R09: ffffffffba518c35
Aug 22 09:27:33 Arctic kernel: [ 3070.906508] R10: ffff931b230db800 R11: 0000000000000001 R12: ffffe597908c3680
Aug 22 09:27:33 Arctic kernel: [ 3070.906511] R13: ffff931b230db800 R14: ffff931b24c02e00 R15: ffffb101c050bd48
Aug 22 09:27:33 Arctic kernel: [ 3070.906515] FS:  0000000000000000(0000) GS:ffff931b26b00000(0000) knlGS:0000000000000000
Aug 22 09:27:33 Arctic kernel: [ 3070.906518] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 22 09:27:33 Arctic kernel: [ 3070.906521] CR2: 00007fa5530df000 CR3: 000000024500a002 CR4: 00000000003606e0
Aug 22 09:33:27 Arctic kernel: [    0.000000] microcode: microcode updated early to revision 0xd6, date = 2020-04-23



```

---

### Post by TheFu on 2020-08-22
Seems clear.  The problem is with a USB device using the ath9k driver.
```
           Device-2: Qualcomm Atheros TP-Link TL-WN821N v3 / TL-WN822N v2 802.11n [Atheros AR7010+AR9287] type: USB 
           driver: ath9k_htc bus ID: 1-6:2 chip ID: 0cf3:7015 serial: <filter> 
           IF: wlx74ea3a8f3e6d state: up mac: <filter>
```
That is one of the problems. We don't know if it is the only problem.

---

### Post by Doug S on 2020-08-22
Did you ever try the mainline kernel? Your issue sure sounds like that bug report I referred you to earlier.

---

### Post by TheFu on 2020-08-22
> **Doug S said:**
> Did you ever try the mainline kernel? Your issue sure sounds like that bug report I referred you to earlier.
Sure does.
> For the record, the patch was merged to v5.4.47 (and other newer kernels)
5.4.0-42-generic is the current 20.04 default kernel, so going out of the way to get a newer one will be needed to use that wifi usb device.

---

### Post by hans12345 on 2020-08-23
> **Doug S said:**
> Did you ever try the mainline kernel? Your issue sure sounds like that bug report I referred you to earlier.

Thanks Doug S

I noted your proposal but for me it looks a bit heavy so I was exploring other options first.

See my next post for these steps.

---

### Post by hans12345 on 2020-08-23
> **TheFu said:**
> Seems clear.  The problem is which a USB device using the ath9k driver.
```
           Device-2: Qualcomm Atheros TP-Link TL-WN821N v3 / TL-WN822N v2 802.11n [Atheros AR7010+AR9287] type: USB 
           driver: ath9k_htc bus ID: 1-6:2 chip ID: 0cf3:7015 serial: <filter> 
           IF: wlx74ea3a8f3e6d state: up mac: <filter>
```
That is one of the problems. We don't know if it is the only problem.

Thanks TheFu

OK, let me take these steps:

- switch back to the LAN (powerline) connection
- upgrade to the 20.04.1 point release (for some reason I missed the release announcement)

Edit: Whoops - it seems that I have the point release already !

---

### Post by Doug S on 2020-08-23
> **hans12345 said:**
> I noted your proposal but for me it looks a bit heavy so I was exploring other options first.It is actually pretty trivial to try, but O.K. Watch for kernel 5.4.0-44.48 (= mainline 5.4.55), which has been in proposed since August 10th, and so should be out soon. It will have the fix.

---

### Post by hans12345 on 2020-08-24
24 hours and no crash.

Can my problems be caused by a rogue wifi USB stick?

For the record it is a TP-Link TL-WN821N

---

### Post by hans12345 on 2020-08-24
Hi Doug S
This is what I have:
cat /proc/version_signature
	Ubuntu 5.4.0-42.46-generic 5.4.44
and this is what you suggest?
       linux-generic-hwe-20.04_5.4.0.44.48_amd64.deb 	5.4.0.44.48 	amd64 	Ubuntu Proposed Main Official

---

### Post by TheFu on 2020-08-24
```
Aug 22 09:27:33 Arctic kernel: [ 3070.906282]  ? ath9k_wmi_cmd+0x1a5/0x1c0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906287]  skb_release_all+0x26/0x30
Aug 22 09:27:33 Arctic kernel: [ 3070.906293]  kfree_skb+0x32/0xa0
Aug 22 09:27:33 Arctic kernel: [ 3070.906301]  ath9k_wmi_cmd+0x1a5/0x1c0 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906311]  ath9k_regread+0x48/0x70 [ath9k_htc]
Aug 22 09:27:33 Arctic kernel: [ 3070.906332]  ar9285_hw_pa_cal+0x317/0x520 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906348]  ar9002_hw_pa_cal+0x36/0x60 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906362]  ar9002_hw_calibrate+0x102/0x440 [ath9k_hw]
Aug 22 09:27:33 Arctic kernel: [ 3070.906372]  ath9k_htc_ani_work+0x118/0x1a0 [ath9k_htc]
```
Is the crash.
ath9k is the driver for that wifi USB device.  So, yes, the driver or kernel has a bug that is causing the crash.  Drivers are loaded into the kernel for performance reasons, but a mistake that bring down the entire machine.

There could be other issues in other drivers, but this is certainly one.  From memory, the bug link above says the kernel is accessing the driver memory that has been freed already. Usually, kernel code wouldn't be specialized for loading, using, unloading and driver, so any problem for this device would be expected to impact every other similar device too. That doesn't appear to be the situations, so I'm strongly guessing the problem is in the driver software and the kernel you have just happens to do things in a way that causes this bug to crash the system.

Those are my guesses. I could be wrong. My memory could be off, but the fix is a newer kernel which seems to be available, just not in the distribution yet.

---

### Post by Doug S on 2020-08-24
> **hans12345 said:**
> 
and this is what you suggest?
       linux-generic-hwe-20.04_5.4.0.44.48_amd64.deb 	5.4.0.44.48 	amd64 	Ubuntu Proposed Main OfficialYes.

---

### Post by hans12345 on 2020-08-26
Still no new crash !

---

### Post by TheFu on 2020-08-26
> **hans12345 said:**
> Still no new crash !

Seems solved. Please use the "thread tools" button near the top to mark it that way.

---

### Post by hans12345 on 2020-08-29
> **TheFu said:**
> Seems solved. Please use the "thread tools" button near the top to mark it that way.

Yes, it is fixed.

Thanks TheFu, I would never have found the cause of the problem without your help.

---

