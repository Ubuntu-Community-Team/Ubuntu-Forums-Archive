---
title: "skge kernel module crash"
date: 2008-04-14
forum: General Help
---

### Post by wildmage on 2008-04-14
2 days ago I upgraded my desktop from Feisty to Gutsy 7.10.  Performance was a bit faster in Feisty, but I'm not complaining too much.  However, starting last night, my whole machine crashes shortly after it brings up the graphical login screen.

I was only able to boot safely after starting up via recovery mode and setting init level 4.

Going into the kernel messages, I can see that the kernel crashed in the skge.c module.  The following is some system info and the error message snipped from the syslog:

```
wildmage@wildmage-desktop:~$ uname -a
Linux wildmage-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

```

Apr 14 07:15:58 wildmage-desktop kernel: [   76.731111] ------------[ cut here ]------------
Apr 14 07:15:58 wildmage-desktop kernel: [   76.731172] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/skge.c:2518!
Apr 14 07:15:58 wildmage-desktop kernel: [   76.731237] invalid opcode: 0000 [#1]
Apr 14 07:15:58 wildmage-desktop kernel: [   76.731293] SMP 
Apr 14 07:15:58 wildmage-desktop kernel: [   76.731449] Modules linked in: af_packet binfmt_misc rfcomm l2cap bluetooth ppdev ipv6 cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table button sbs video container ac dock battery sbp2 lp snd_usb_audio snd_via82xx_modem parport_pc parport snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_pcm usbhid hid snd_seq_oss snd_mpu401_uart serio_raw gspca pcspkr psmouse snd_seq_midi snd_seq_midi_event videodev v4l2_common v4l1_compat k8temp snd_usb_lib snd_hwdep i2c_viapro snd_rawmidi snd_seq snd_timer snd_seq_device nvidia(P) snd soundcore snd_page_alloc i2c_core shpchp pci_hotplug amd64_agp agpgart evdev ide_cd cdrom ide_disk via82cxxx ide_core ext3 jbd mbcache sg sd_mod floppy ehci_hcd uhci_hcd usbcore ata_generic sata_via skge sata_promise libata scsi_mod ohci1394 ieee1394 thermal processor fan fuse apparmor commoncap
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736432] CPU:    0
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736433] EIP:    0060:[<f8895d5d>]    Tainted: P       VLI
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736434] EFLAGS: 00010206   (2.6.22-14-generic #1)
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736642] EIP is at skge_up+0x81d/0x830 [skge]
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736712] eax: f6cec000   ebx: 00000000   ecx: 36c88000   edx: f88a8420
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736784] esi: dfe3e500   edi: 00000000   ebp: dfe3e000   esp: ef62fe64
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736856] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736926] Process ifconfig (pid: 5946, ti=ef62e000 task=f1bd0f90 task.ti=ef62e000)
Apr 14 07:15:58 wildmage-desktop kernel: [   76.736998] Stack: 00004000 dfe3e000 00000003 0bfde002 f88a8f04 c197226c 00004000 00000000 
Apr 14 07:15:58 wildmage-desktop kernel: [   76.737540]        00000000 dfe3e580 00000000 c1972240 00000000 00000000 f6c8c000 f6c88000 
Apr 14 07:15:58 wildmage-desktop kernel: [   76.738083]        dfe3e198 00002888 00002800 00000f00 dfe3e500 00000000 00000000 00005000 
Apr 14 07:15:58 wildmage-desktop kernel: [   76.738625] Call Trace:
Apr 14 07:15:58 wildmage-desktop kernel: [   76.738834]  [<f88973a5>] skge_change_mtu+0x55/0x70 [skge]
Apr 14 07:15:58 wildmage-desktop kernel: [   76.738969]  [dev_set_mtu+49/96] dev_set_mtu+0x31/0x60
Apr 14 07:15:58 wildmage-desktop kernel: [   76.739092]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr 14 07:15:58 wildmage-desktop kernel: [   76.739213]  [dev_ioctl+534/832] dev_ioctl+0x216/0x340
Apr 14 07:15:58 wildmage-desktop kernel: [   76.739389]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210
Apr 14 07:15:58 wildmage-desktop kernel: [   76.739513]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr 14 07:15:58 wildmage-desktop kernel: [   76.739642]  [do_ioctl+43/192] do_ioctl+0x2b/0xc0
Apr 14 07:15:58 wildmage-desktop kernel: [   76.739764]  [do_page_fault+905/1680] do_page_fault+0x389/0x690
Apr 14 07:15:58 wildmage-desktop kernel: [   76.739890]  [sys_socket+41/80] sys_socket+0x29/0x50
Apr 14 07:15:58 wildmage-desktop kernel: [   76.740022]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Apr 14 07:15:58 wildmage-desktop kernel: [   76.740158]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Apr 14 07:15:58 wildmage-desktop kernel: [   76.740292]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Apr 14 07:15:58 wildmage-desktop kernel: [   76.740463]  =======================
Apr 14 07:15:58 wildmage-desktop kernel: [   76.740530] Code: 0d 00 02 00 02 89 82 5c 01 00 00 e9 e8 fa ff ff 0f 0b eb fe 8b 54 24 30 89 c8 e8 2f f0 ff ff e9 d8 fd ff ff b1 8f e9 4e ff ff ff <0f> 0b 90 eb fd 8d b4 26 00 00 00 00 8d bc 27 00 00 00 00 55 89 
Apr 14 07:15:58 wildmage-desktop kernel: [   76.743946] EIP: [<f8895d5d>] skge_up+0x81d/0x830 [skge] SS:ESP 0068:ef62fe64
Apr 14 07:16:01 wildmage-desktop kernel: [   79.943033] skge eth0: Link is up at 1000 Mbps, full duplex, flow control both

```

Any help on resolving this kernel module problem would be very helpful and greatly appreciated!  :)

Jacob

---

