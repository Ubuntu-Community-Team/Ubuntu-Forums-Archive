---
title: "Screensaver kills my USB?"
date: 2007-06-04
forum: General Help
---

### Post by dj_flx on 2007-06-04
I'm running Xubuntu but this has been going on since I was even running Gnome/Ubuntu back to 5.x. I just upgraded and the screensaver was turned back on so this came back up.

If I leave the screensaver running for too long (so far it has to be at least half an hour, I haven't been able to find the lower limit yet) my USB mouse dies. It's an infrared, so I can see that the light is off when I pick it up. Unplugging it and plugging it back in doesn't being it back... The keyboard still works, though, it's on an extra PCI USB card I have on the machine (it got switched with my camera USB cord so I found that this card doesn't die, by accident).

I have power management turned off. Screen isn't set to lock for password.

I was messing with the screensaver control panel, and the mouse died when I tried to change the blank timeout; I had a terminal open  and I saw that syslog spit this out:

```
Jun  4 01:34:31 localhost kernel: [17181919.244000] uhci_hcd 0000:00:14.3: host system error, PCI problems?
Jun  4 01:34:31 localhost kernel: [17181919.244000] uhci_hcd 0000:00:14.3: host controller halted, very bad!
Jun  4 01:34:31 localhost kernel: [17181919.244000] uhci_hcd 0000:00:14.3: HC died; cleaning up
Jun  4 01:34:31 localhost kernel: [17181919.244000] usb 2-1: USB disconnect, address 2
Jun  4 01:34:31 localhost kernel: [17181919.248000] usb 2-2: USB disconnect, address 4
Jun  4 01:34:31 localhost kernel: [17181919.252000] drivers/usb/net/atmel/at76c503-fw_skel.c: wlan0 disconnecting
Jun  4 01:34:31 localhost kernel: [17181919.252000] drivers/usb/net/atmel/at76c503.c: at76c503_delete_device: rtnl_lock already taken
Jun  4 01:34:31 localhost kernel: [17181919.280000] ------------[ cut here ]------------
Jun  4 01:34:31 localhost kernel: [17181919.280000] kernel BUG at net/core/dev.c:3134!
Jun  4 01:34:31 localhost kernel: [17181919.280000] invalid opcode: 0000 [#1]
Jun  4 01:34:31 localhost kernel: [17181919.280000] SMP 
Jun  4 01:34:31 localhost kernel: [17181919.280000] Modules linked in: binfmt_misc appletalk cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi ipv6 af_packet md_mod dm_mod ide_floppy lp at76c503_rfmd at76c503 at76_usbdfu snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq tsdev evdev nvidia serio_raw sg snd_via82xx gameport floppy snd_ac97_codec snd_ac97_bus psmouse snd_pcm_oss snd_mixer_oss via_agp pcspkr snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device agpgart snd soundcore via686a i2c_isa i2c_viapro tulip i2c_core shpchp pci_hotplug parport_pc parport ext3 jbd usbhid sd_mod ohci_hcd uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk via82cxxx generic aic7xxx scsi_transport_spi scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Jun  4 01:34:31 localhost kernel: [17181919.280000] CPU:    0
Jun  4 01:34:31 localhost dhclient: receive_packet failed on wlan0: Network is down
Jun  4 01:34:31 localhost kernel: [17181919.280000] EIP:    0060:[free_netdev+58/80]    Tainted: P S    VLI
Jun  4 01:34:31 localhost kernel: [17181919.280000] EFLAGS: 00010297   (2.6.17-11-generic #2) 
Jun  4 01:34:31 localhost kernel: [17181919.280000] EIP is at free_netdev+0x3a/0x50
Jun  4 01:34:31 localhost kernel: [17181919.280000] eax: 00000002   ebx: d35f4400   ecx: 00000000   edx: d35f4000
Jun  4 01:34:31 localhost kernel: [17181919.280000] esi: d35f45e4   edi: 000000a0   ebp: d35f45e0   esp: d7b4fe60
Jun  4 01:34:31 localhost kernel: [17181919.280000] ds: 007b   es: 007b   ss: 0068
Jun  4 01:34:31 localhost kernel: [17181919.280000] Process khubd (pid: 1846, threadinfo=d7b4e000 task=d7f8d030)
Jun  4 01:34:31 localhost kernel: [17181919.280000] Stack: d8b1b517 d8b237a8 d8b20168 d8b1fc63 00000296 d35f4400 d8a591a0 d8a591c8 
Jun  4 01:34:31 localhost kernel: [17181919.280000]        d6584414 d35f4400 d8a591a0 d8a591c8 d6584414 d8a58036 d8a584b4 d8a581b4 
Jun  4 01:34:31 localhost kernel: [17181919.280000]        d35f4000 d6584400 d8917994 d658448c d6584414 c024605b d6584414 d6584414 
Jun  4 01:34:31 localhost kernel: [17181919.280000] Call Trace:
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <d8b1b517> at76c503_delete_device+0x187/0x2c0 [at76c503]  <d8a58036> at76c50x_disconnect+0x36/0x50 [at76c503_rfmd]
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <d8917994> usb_unbind_interface+0x34/0x70 [usbcore]  <c024605b> __device_release_driver+0x5b/0xa0
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <c024631c> device_release_driver+0x1c/0x30  <c0245887> bus_remove_device+0x77/0x90
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <c02448f5> device_del+0x35/0x70  <d8915bc6> usb_disable_device+0x86/0xe0 [usbcore]
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <d8911927> usb_disconnect+0x97/0xf0 [usbcore]  <d89119c6> hub_pre_reset+0x46/0x80 [usbcore]
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <d8912aa5> hub_thread+0x395/0xc80 [usbcore]  <c0136180> autoremove_wake_function+0x0/0x50
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <d8912710> hub_thread+0x0/0xc80 [usbcore]  <c0135f8b> kthread+0xab/0xe0
Jun  4 01:34:31 localhost kernel: [17181919.280000]  <c0135ee0> kthread+0x0/0xe0  <c0101005> kernel_thread_helper+0x5/0x10
Jun  4 01:34:31 localhost kernel: [17181919.280000] Code: 64 29 c2 89 d0 e9 d7 5e ef ff 8d b4 26 00 00 00 00 83 f8 03 75 15 c7 82 94 02 00 00 04 00 00 00 8d 82 f0 02 00 00 e9 36 63 fd ff <0f> 0b 3e 0c c4 d1 30 c0 eb e1 8d b6 00 00 00 00 8d bf 00 00 00 
Jun  4 01:34:31 localhost kernel: [17181919.280000] EIP: [free_netdev+58/80] free_netdev+0x3a/0x50 SS:ESP 0068:d7b4fe60
```

I don't know what that means except for the "died" and "very bad" parts...

I can just leave the screensaver shut off, but it annoys me that I don't know what the problem is here.

---

