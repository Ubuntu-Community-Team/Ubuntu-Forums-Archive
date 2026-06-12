---
title: "dvb-utils' scan causes hardlock (hauppauge nova-t usb2 stick)"
date: 2007-01-27
forum: General Help
---

### Post by neocookie on 2007-01-27
Hi all

I'm installing mythtv on my laptop. Everything's on, I've managed to get my Hauppauge WinTV Nova-T USB2 Stick installed, configured, and working. Or so I thought.

When I use dvb-utils to scan for channels from my local transponder (Emley moor, uk) it runs for about 30 seconds before I get a hardlock.

I can view tv through xine fine, and because its a hardlock i can't find out what might be the cause.

Can anyone help?

---

### Post by neocookie on 2007-01-27
I've managed to get some output from dmesg by scanning for channels through mythtv. Here's the output:
```
Message from syslogd@iyoti at Sat Jan 27 17:45:46 2007 ...
iyoti kernel: [17180473.308000] Oops: 0002 [#1]

Message from syslogd@iyoti at Sat Jan 27 17:45:46 2007 ...
iyoti 
Message from syslogd@iyoti at Sat Jan 27 17:45:46 2007 ...
iyoti kernel: [17180473.308000] CPU:    0

Message from syslogd@iyoti at Sat Jan 27 17:45:46 2007 ...
iyoti kernel: [17180473.308000] EIP is at dvb_frontend_release+0x37/0x90 [dvb_core]

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] eax: 00024df7   ebx: e8110031   ecx: f8aaa670   edx: dda36600

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] esi: dda36600   edi: 00000000   ebp: e73e125c   esp: cedd9e00

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] Process mythtv-setup (pid: 5766, threadinfo=cedd8000 task=ce4c6560)
kernel: [17180473.308000] SMP 

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] Stack: 00000000 e73e1384 00000008 dda36600 ecbda8d0 e73e125c c016b95b 00000000 

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]        ecbda8d0 dfff60c0 e73e125c dda36600 00000000 dfca8240 00000000 c0168b27 

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]        00000000 0000003f d8435d00 00000000 c0124458 dfca8240 00000034 dfca8240 

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] Call Trace:

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]  <c016b95b> __fput+0x9b/0x1a0  <c0168b27> filp_close+0x47/0x80

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]  <c0124458> put_files_struct+0x98/0xc0  <c012560c> do_exit+0x11c/0x840

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]  <c0125d67> do_group_exit+0x37/0x80  <c012e751> get_signal_to_deliver+0x281/0x3f0

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]  <c02dbd00> do_page_fault+0x0/0x6f0  <c010266b> do_notify_resume+0x8b/0x6c0

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]  <c0139440> hrtimer_run_queues+0xc0/0x150  <c011cdf8> __wake_up+0x38/0x50

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]  <c02dbe02> do_page_fault+0x102/0x6f0  <c02dbd00> do_page_fault+0x0/0x6f0

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000]  <c01030be> work_notifysig+0x13/0x25 

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] Code: 14 89 c5 89 5c 24 08 89 7c 24 10 8b 42 78 8b 58 28 a1 90 8c ab f8 8b bb d8 01 00 00 85 c0 75 44 f6 46 18 03 74 0b a1 00 04 3e c0 <89> 87 c0 01 00 00 8b 8b 08 01 00 00 85 c9 74 06 31 d2 89 d8 ff 

Message from syslogd@iyoti at Sat Jan 27 17:45:47 2007 ...
iyoti kernel: [17180473.308000] EIP: [pg0+945874599/1068901376] dvb_frontend_release+0x37/0x90 [dvb_core] SS:ESP 0068:cedd9e00
```

I've absolutely no idea whether this is helpful or not, but its the only error message i got when it bombed out.

---

### Post by neocookie on 2007-01-27
Scratch that last one - got a better response from dmesg:

```
[17179785.236000] BUG: unable to handle kernel NULL pointer dereference at virtual address 000001dc
[17179785.236000]  printing eip:
[17179785.236000] f8aa8692
[17179785.236000] *pde = 00000000
[17179785.236000] Oops: 0000 [#1]
[17179785.236000] SMP 
[17179785.236000] Modules linked in: binfmt_misc mt2060 rfcomm dvb_usb_dib0700 l2cap bluetooth vmnet vmmon ipv6 fglrx powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac af_packet deflate zlib_deflate twofish serpent aes blowfish des sha256 sha1 crypto_null af_key ndiswrapper dvb_usb_nova_t_usb2 dvb_usb_dibusb_mc dvb_usb_dibusb_mb dib3000mb dvb_usb_dibusb_common dib3000mc dvb_usb dvb_pll dib7000p dib7000m dibx000_common dst dvb_core bt878 bttv video_buf ir_common compat_ioctl32 i2c_algo_bit btcx_risc tveeprom i2c_core videodev v4l2_common v4l1_compat parport_pc lp parport joydev tsdev snd_atiixp_modem snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq psmouse serio_raw evdev snd_atiixp snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer 8139cp 8139too mii shpchp pci_hotplug snd_seq_device snd soundcore snd_page_alloc ati_agp agpgart pcspkr ext3 jbd ehci_hcd ohci_hcd usbcore ide_generic ide_cd cdrom ide_disk generic atiixp thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[17179785.236000] CPU:    0
[17179785.236000] EIP:    0060:[<f8aa8692>]    Tainted: P      VLI
[17179785.236000] EFLAGS: 00210286   (2.6.17-10-generic #2) 
[17179785.236000] EIP is at dvb_frontend_release+0x22/0x90 [dvb_core]
[17179785.236000] eax: 00000000   ebx: 00000004   ecx: f8aa8670   edx: ebdb70c0
[17179785.236000] esi: ebdb70c0   edi: e4380d74   ebp: e4382e80   esp: e73c3e00
[17179785.236000] ds: 007b   es: 007b   ss: 0068
[17179785.236000] Process mythtv-setup (pid: 5412, threadinfo=e73c2000 task=f1018a90)
[17179785.236000] Stack: 00000000 e4382fa8 00000008 ebdb70c0 e4380d74 e4382e80 c016b95b 00000000 
[17179785.236000]        e4380d74 dfa660c0 e4382e80 ebdb70c0 00000000 dff86b40 00000000 c0168b27 
[17179785.236000]        00000000 0000003f e40ba5c0 00000000 c0124458 dff86b40 00000034 dff86b40 
[17179785.236000] Call Trace:
[17179785.236000]  <c016b95b> __fput+0x9b/0x1a0  <c0168b27> filp_close+0x47/0x80
[17179785.236000]  <c0124458> put_files_struct+0x98/0xc0  <c012560c> do_exit+0x11c/0x840
[17179785.236000]  <c0125d67> do_group_exit+0x37/0x80  <c012e751> get_signal_to_deliver+0x281/0x3f0
[17179785.236000]  <c02dbd00> do_page_fault+0x0/0x6f0  <c010266b> do_notify_resume+0x8b/0x6c0
[17179785.236000]  <c011cdf8> __wake_up+0x38/0x50  <c02dbe02> do_page_fault+0x102/0x6f0
[17179785.236000]  <c02dbd00> do_page_fault+0x0/0x6f0  <c01030be> work_notifysig+0x13/0x25
[17179785.236000] Code: 89 f6 8d bc 27 00 00 00 00 83 ec 18 89 74 24 0c 89 d6 89 6c 24 14 89 c5 89 5c 24 08 89 7c 24 10 8b 42 78 8b 58 28 a1 90 6c ab f8 <8b> bb d8 01 00 00 85 c0 75 44 f6 46 18 03 74 0b a1 00 04 3e c0 
[17179785.236000] EIP: [<f8aa8692>] dvb_frontend_release+0x22/0x90 [dvb_core] SS:ESP 0068:e73c3e00
[17179785.236000]  <1>Fixing recursive fault but reboot is needed!

```

---

### Post by neocookie on 2007-01-29
I think I've sorted it. I noticed that when I restarted my laptop, I could do a dvb-utils `scan` once. Second time, I'd get a hardlock.

In mythtv, I told it to use quite a long delay between scans, then after a restart used it to scan for channels. It worked first time, so I saved the changes and its been running fine since.

---

