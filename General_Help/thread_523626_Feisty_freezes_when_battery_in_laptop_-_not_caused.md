---
title: "Feisty freezes when battery in laptop - not caused by laptop_mode"
date: 2007-08-12
forum: General Help
---

### Post by TwanGoosen on 2007-08-12
Hi,
Here's a follow-up on [this post]("http://ubuntuforums.org/showthread.php?p=3170521"), if that's okay.
The problem is as follows: whenever I boot my notebook (Acer Travelmate 2310; Feisty, recently installed, no kernel updates) with its **battery inserted** (but still attached to power socket), the system freezes at random time. This does not occur when the battery is not inserted. 

What happens is the following: 
First the keyboard gets irresponsive, then the mouse buttons and finally no input seems to be processed anymore. The system as a whole does not seem to hang. Right before the keyboard gets irresponsive, a list of kernel messages is printed in the terminal. From kernel.log:

> 
ug 12 11:29:02 acer kernel: [  678.964000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Aug 12 11:29:03 acer kernel: [  679.732000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000085
Aug 12 11:29:03 acer kernel: [  679.732000]  printing eip:
Aug 12 11:29:03 acer kernel: [  679.732000] c01ed01a
Aug 12 11:29:03 acer kernel: [  679.732000] *pde = 00000000
Aug 12 11:29:03 acer kernel: [  679.732000] Oops: 0000 [#1]
Aug 12 11:29:03 acer kernel: [  679.732000] SMP 
Aug 12 11:29:03 acer kernel: [  679.732000] Modules linked in: sg sd_mod usb_storage libusual isofs udf binfmt_misc rfcomm l2cap bluetooth ppdev sony_acpi tc1100_wmi pcc_acpi dev_acpi button sbs dock asus_acpi video container backlight battery i2c_ec ac nls_iso8859_1 nls_cp437 vfat fat ipv6 parport_pc lp parport fuse joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm pcmcia snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw psmouse snd soundcore pcspkr snd_page_alloc yenta_socket rsrc_nonstatic pcmcia_core ath_pci wlan ath_hal(P) sis_agp af_packet agpgart i2c_sis96x i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod generic sis900 mii ehci_hcd ohci_hcd usbcore sis5513 thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Aug 12 11:29:03 acer kernel: [  679.732000] CPU:    0
Aug 12 11:29:03 acer kernel: [  679.732000] EIP:    0060:[idr_get_new_above_int+74/624]    Tainted: P      VLI
Aug 12 11:29:03 acer kernel: [  679.732000] EFLAGS: 00010293   (2.6.20-16-generic #2)
Aug 12 11:29:03 acer kernel: [  679.732000] EIP is at idr_get_new_above_int+0x4a/0x270
Aug 12 11:29:03 acer kernel: [  679.732000] eax: 00000001   ebx: 00000000   ecx: 00000000   edx: dff2d550
Aug 12 11:29:03 acer kernel: [  679.732000] esi: 00000000   edi: 00000001   ebp: f0f08dd0   esp: f08d5ec8
Aug 12 11:29:03 acer kernel: [  679.732000] ds: 007b   es: 007b   ss: 0068
Aug 12 11:29:03 acer kernel: [  679.732000] Process nautilus (pid: 5115, ti=f08d4000 task=ec88a030 task.ti=f08d4000)
Aug 12 11:29:03 acer kernel: [  679.732000] Stack: df94c800 df94df40 dff2d550 f0f08dc0 00000040 00000009 0000001d 00000001 
Aug 12 11:29:03 acer kernel: [  679.732000]        dd26601c 00000246 000000d0 00000286 c01ecdbb f0f08dc0 000000d0 f0f08dc0 
Aug 12 11:29:03 acer kernel: [  679.732000]        dff2d550 ffffffea f35cf2b8 c01ed275 c01a03aa dff2d56c f35cf3dc f0f08dd4 
Aug 12 11:29:03 acer kernel: [  679.732000] Call Trace:
Aug 12 11:29:03 acer kernel: [  679.732000]  [free_layer+43/80] free_layer+0x2b/0x50
Aug 12 11:29:03 acer kernel: [  679.732000]  [idr_get_new_above+5/48] idr_get_new_above+0x5/0x30
Aug 12 11:29:03 acer kernel: [  679.732000]  [inotify_add_watch+106/256] inotify_add_watch+0x6a/0x100
Aug 12 11:29:03 acer kernel: [  679.732000]  [sys_inotify_add_watch+321/352] sys_inotify_add_watch+0x141/0x160
Aug 12 11:29:03 acer kernel: [  679.732000]  [sys_stat64+30/48] sys_stat64+0x1e/0x30
Aug 12 11:29:03 acer kernel: [  679.732000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Aug 12 11:29:03 acer kernel: [  679.732000]  [xfrm_state_find+979/1392] xfrm_state_find+0x3d3/0x570
Aug 12 11:29:03 acer kernel: [  679.732000]  =======================
Aug 12 11:29:03 acer kernel: [  679.732000] Code: 84 28 02 00 00 8b 6c 24 0c 8d 34 9b 83 c5 10 eb 06 83 c3 01 83 c6 05 83 fb 05 77 48 b8 01 00 00 00 89 f1 d3 e0 3b 44 24 14 7f 39 <8b> 87 84 00 00 00 85 c0 74 dc 8b 44 24 0c e8 b3 fd ff ff 85 c0 
Aug 12 11:29:03 acer kernel: [  679.732000] EIP: [idr_get_new_above_int+74/624] idr_get_new_above_int+0x4a/0x270 SS:ESP 0068:f08d5ec8
Aug 12 11:29:32 acer kernel: [  679.732000]  ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Aug 12 11:30:02 acer kernel: [  739.008000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Aug 12 11:30:02 acer kernel: [  739.008000] ------------[ cut here ]------------
Aug 12 11:30:02 acer kernel: [  739.008000] kernel BUG at mm/slab.c:597!
Aug 12 11:30:02 acer kernel: [  739.008000] invalid opcode: 0000 [#2]
Aug 12 11:30:02 acer kernel: [  739.008000] SMP 
Aug 12 11:30:02 acer kernel: [  739.008000] Modules linked in: sg sd_mod usb_storage libusual isofs udf binfmt_misc rfcomm l2cap bluetooth ppdev sony_acpi tc1100_wmi pcc_acpi dev_acpi button sbs dock asus_acpi video container backlight battery i2c_ec ac nls_iso8859_1 nls_cp437 vfat fat ipv6 parport_pc lp parport fuse joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm pcmcia snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw psmouse snd soundcore pcspkr snd_page_alloc yenta_socket rsrc_nonstatic pcmcia_core ath_pci wlan ath_hal(P) sis_agp af_packet agpgart i2c_sis96x i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod generic sis900 mii ehci_hcd ohci_hcd usbcore sis5513 thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Aug 12 11:30:02 acer kernel: [  739.008000] CPU:    0
Aug 12 11:30:02 acer kernel: [  739.008000] EIP:    0060:[kfree+122/128]    Tainted: P      VLI
Aug 12 11:30:02 acer kernel: [  739.008000] EFLAGS: 00010046   (2.6.20-16-generic #2)
Aug 12 11:30:02 acer kernel: [  739.008000] EIP is at kfree+0x7a/0x80
Aug 12 11:30:02 acer kernel: [  739.008000] eax: 00000000   ebx: edd27f60   ecx: f60535a0   edx: c1800000
Aug 12 11:30:02 acer kernel: [  739.008000] esi: 00000001   edi: 00000202   ebp: 00000400   esp: edd27f30
Aug 12 11:30:02 acer kernel: [  739.008000] ds: 007b   es: 007b   ss: 0068
Aug 12 11:30:02 acer kernel: [  739.008000] Process hald (pid: 4492, ti=edd26000 task=f25e9a90 task.ti=edd26000)
Aug 12 11:30:02 acer kernel: [  739.008000] Stack: edd27f60 e204f440 00000001 c0190cce 00000400 080860e0 e1381d40 e204f460 
Aug 12 11:30:02 acer kernel: [  739.008000]        00000000 00000000 c1b4c900 00000000 00000000 00000000 e1381d40 080860e0 
Aug 12 11:30:02 acer kernel: [  739.008000]        edd27fa0 00000400 c0176e3c edd27fa0 c1b4c934 c0190c40 e1381d40 fffffff7 
Aug 12 11:30:02 acer kernel: [  739.008000] Call Trace:
Aug 12 11:30:02 acer kernel: [  739.008000]  [seq_read+142/672] seq_read+0x8e/0x2a0
Aug 12 11:30:02 acer kernel: [  739.008000]  [vfs_read+188/400] vfs_read+0xbc/0x190
Aug 12 11:30:02 acer kernel: [  739.008000]  [seq_read+0/672] seq_read+0x0/0x2a0
Aug 12 11:30:02 acer kernel: [  739.008000]  [sys_read+65/112] sys_read+0x41/0x70
Aug 12 11:30:02 acer kernel: [  739.008000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Aug 12 11:30:02 acer kernel: [  739.008000]  [xfrm_state_find+979/1392] xfrm_state_find+0x3d3/0x570
Aug 12 11:30:02 acer kernel: [  739.008000]  =======================
Aug 12 11:30:02 acer kernel: [  739.008000] Code: 89 74 83 14 83 c0 01 89 03 89 f8 50 9d 90 8d b4 26 00 00 00 00 5b 5e 5f c3 8b 52 0c eb c9 89 c8 89 da e8 9a fe ff ff 8b 03 eb d5 <0f> 0b eb fe 66 90 57 89 d7 8d 92 00 00 00 40 89 c1 c1 ea 0c c1 
Aug 12 11:30:02 acer kernel: [  739.008000] EIP: [kfree+122/128] kfree+0x7a/0x80 SS:ESP 0068:edd27f30
Aug 12 11:30:02 acer kernel: [  739.008000]  <0>------------[ cut here ]------------
Aug 12 11:30:02 acer kernel: [  739.008000] kernel BUG at mm/slab.c:597!
Aug 12 11:30:02 acer kernel: [  739.008000] invalid opcode: 0000 [#3]
Aug 12 11:30:02 acer kernel: [  739.008000] SMP 
Aug 12 11:30:02 acer kernel: [  739.008000] Modules linked in: sg sd_mod usb_storage libusual isofs udf binfmt_misc rfcomm l2cap bluetooth ppdev sony_acpi tc1100_wmi pcc_acpi dev_acpi button sbs dock asus_acpi video container backlight battery i2c_ec ac nls_iso8859_1 nls_cp437 vfat fat ipv6 parport_pc lp parport fuse joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm pcmcia snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw psmouse snd soundcore pcspkr snd_page_alloc yenta_socket rsrc_nonstatic pcmcia_core ath_pci wlan ath_hal(P) sis_agp af_packet agpgart i2c_sis96x i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk pata_sis ata_generic libata scsi_mod generic sis900 mii ehci_hcd ohci_hcd usbcore sis5513 thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Aug 12 11:30:02 acer kernel: [  739.008000] CPU:    0
Aug 12 11:30:02 acer kernel: [  739.008000] EIP:    0060:[kfree+122/128]    Tainted: P      VLI
Aug 12 11:30:02 acer kernel: [  739.008000] EFLAGS: 00010046   (2.6.20-16-generic #2)
Aug 12 11:30:02 acer kernel: [  739.008000] EIP is at kfree+0x7a/0x80
Aug 12 11:30:02 acer kernel: [  739.008000] eax: 00000000   ebx: e204f440   ecx: e204f440   edx: c1800000
Aug 12 11:30:02 acer kernel: [  739.008000] esi: 00000001   edi: 00000202   ebp: eedf00d8   esp: edd27d54
Aug 12 11:30:02 acer kernel: [  739.008000] ds: 007b   es: 007b   ss: 0068
Aug 12 11:30:02 acer kernel: [  739.008000] Process hald (pid: 4492, ti=edd26000 task=f25e9a90 task.ti=edd26000)
Aug 12 11:30:02 acer kernel: [  739.008000] Stack: e204f440 f60535a0 df2777c8 c019058b 00000010 c01905f5 00000010 e1381d40 
Aug 12 11:30:02 acer kernel: [  739.008000]        c0177757 00000000 00000000 df2777c8 df947140 eedf00d8 e1381d40 dfe16840 
Aug 12 11:30:02 acer kernel: [  739.008000]        00000000 dfe16840 c0174af7 edd27da8 00000001 dfe16848 00000000 c01281af 
Aug 12 11:30:02 acer kernel: [  739.008000] Call Trace:
Aug 12 11:30:02 acer kernel: [  739.008000]  [seq_release+11/32] seq_release+0xb/0x20
Aug 12 11:30:02 acer kernel: [  739.008000]  [single_release+21/48] single_release+0x15/0x30
Aug 12 11:30:02 acer kernel: [  739.008000]  [__fput+167/400] __fput+0xa7/0x190
Aug 12 11:30:02 acer kernel: [  739.008000]  [filp_close+71/128] filp_close+0x47/0x80
Aug 12 11:30:02 acer kernel: [  739.008000]  [put_files_struct+143/176] put_files_struct+0x8f/0xb0
Aug 12 11:30:02 acer kernel: [  739.008000]  [do_exit+308/2048] do_exit+0x134/0x800
Aug 12 11:30:02 acer kernel: [  739.008000]  [printk+27/32] printk+0x1b/0x20
Aug 12 11:30:02 acer kernel: [  739.008000]  [show_stack+0/64] show_stack+0x0/0x40
Aug 12 11:30:02 acer kernel: [  739.008000]  [do_invalid_op+0/176] do_invalid_op+0x0/0xb0
Aug 12 11:30:02 acer kernel: [  739.008000]  [do_invalid_op+162/176] do_invalid_op+0xa2/0xb0
Aug 12 11:30:02 acer kernel: [  739.008000]  [kfree+122/128] kfree+0x7a/0x80
Aug 12 11:30:02 acer kernel: [  739.008000]  [printk+27/32] printk+0x1b/0x20
Aug 12 11:30:02 acer kernel: [  739.008000]  [acpi_os_vprintf+37/40] acpi_os_vprintf+0x25/0x28
Aug 12 11:30:02 acer kernel: [  739.008000]  [error_code+124/144] error_code+0x7c/0x90
Aug 12 11:30:02 acer kernel: [  739.008000]  [kfree+122/128] kfree+0x7a/0x80
Aug 12 11:30:02 acer kernel: [  739.008000]  [seq_read+142/672] seq_read+0x8e/0x2a0
Aug 12 11:30:02 acer kernel: [  739.008000]  [vfs_read+188/400] vfs_read+0xbc/0x190
Aug 12 11:30:02 acer kernel: [  739.008000]  [seq_read+0/672] seq_read+0x0/0x2a0
Aug 12 11:30:02 acer kernel: [  739.008000]  [sys_read+65/112] sys_read+0x41/0x70
Aug 12 11:30:02 acer kernel: [  739.008000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Aug 12 11:30:02 acer kernel: [  739.008000]  [xfrm_state_find+979/1392] xfrm_state_find+0x3d3/0x570
Aug 12 11:30:02 acer kernel: [  739.008000]  =======================
Aug 12 11:30:02 acer kernel: [  739.008000] Code: 89 74 83 14 83 c0 01 89 03 89 f8 50 9d 90 8d b4 26 00 00 00 00 5b 5e 5f c3 8b 52 0c eb c9 89 c8 89 da e8 9a fe ff ff 8b 03 eb d5 <0f> 0b eb fe 66 90 57 89 d7 8d 92 00 00 00 40 89 c1 c1 ea 0c c1 
Aug 12 11:30:02 acer kernel: [  739.008000] EIP: [kfree+122/128] kfree+0x7a/0x80 SS:ESP 0068:edd27d54
Aug 12 11:30:02 acer kernel: [  739.008000]  <1>Fixing recursive fault but reboot is needed!


I also get:

> 
Aug 12 11:19:32 acer kernel: [  108.696000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Aug 12 11:20:02 acer kernel: [  138.720000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Aug 12 11:20:32 acer kernel: [  168.724000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Aug 12 11:21:02 acer kernel: [  198.724000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
Aug 12 11:21:32 acer kernel: [  228.764000] ACPI Exception (acpi_battery-0217): AE_SUPPORT, Extracting _BST [20060707]
...


which seems to be related. 

It is not quit [bug 12483](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/12483), since the freezes keep occurring even though I disabled laptop_mode. 

Any thoughts on how to solve this?
Twan Goosen

---

### Post by TwanGoosen on 2007-08-13
When I boot with acpi=off, the freezes disappear, as expected. Is there way to turn off **only** the battery part of acpi? As I really like to put my laptop into standby or hibernate mode!

---

### Post by TwanGoosen on 2007-08-13
upgraded kernel to 2.6.22-9-generic, still freezes with acpi=on.

---

### Post by TwanGoosen on 2007-08-13
I blacklisted battery.ko (added 'blacklist battery' to /etc/modprobe.d/blacklist) and it seems that the freezes don't occur anymore. Now my WiFi is not working, might be related?

---

