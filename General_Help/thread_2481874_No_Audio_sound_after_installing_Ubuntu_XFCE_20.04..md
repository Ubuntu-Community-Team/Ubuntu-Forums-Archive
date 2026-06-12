---
title: "No Audio sound after installing Ubuntu XFCE 20.04.1"
date: 2022-12-11
forum: General Help
---

### Post by surendra-mum on 2022-12-11
Have tried all the sources available on various sites but unable to fix the sound issue.

locus@locus-fuss:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy

locus@locus-fuss:~$ uname -r
5.15.0-56-generic

locus@locus-fuss:~$ dpkg --list | grep linux-image
ii  linux-image-5.15.0-43-generic              5.15.0-43.46                               amd64        Signed kernel image generic
ii  linux-image-5.15.0-56-generic              5.15.0-56.62                               amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04              5.15.0.56.54                               amd64        Generic Linux kernel image

                       [LEFT] locus@locus-fuss:~$ **lspci -nv**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:00.0 0600: 8086:9b63 (rev 03)[/LEFT]
 [LEFT]     DeviceName: Onboard - Other[/LEFT]
 [LEFT]     Subsystem: 1458:5000[/LEFT]
 [LEFT]     Flags: bus master, fast devsel, latency 0[/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: skl_uncore[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:02.0 0300: 8086:9bc8 (rev 03) (prog-if 00 [VGA controller])[/LEFT]
 [LEFT]     DeviceName: Onboard - Video[/LEFT]
 [LEFT]     Subsystem: 1458:d000[/LEFT]
 [LEFT]     Flags: bus master, fast devsel, latency 0, IRQ 127[/LEFT]
 [LEFT]     Memory at 50000000 (64-bit, non-prefetchable) [size=16M][/LEFT]
 [LEFT]     Memory at 40000000 (64-bit, prefetchable) [size=256M][/LEFT]
 [LEFT]     I/O ports at 3000 [size=64][/LEFT]
 [LEFT]     Expansion ROM at 000c0000 [virtual] [disabled] [size=128K][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: i915[/LEFT]
 [LEFT]     Kernel modules: i915[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:14.0 0c03: 8086:43ed (rev 11) (prog-if 30 [XHCI])[/LEFT]
 [LEFT]     DeviceName: Onboard - Other[/LEFT]
 [LEFT]     Subsystem: 1458:5007[/LEFT]
 [LEFT]     Flags: bus master, medium devsel, latency 0, IRQ 125[/LEFT]
 [LEFT]     Memory at 51120000 (64-bit, non-prefetchable) [size=64K][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: xhci_hcd[/LEFT]
 [LEFT]     Kernel modules: xhci_pci[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:14.2 0500: 8086:43ef (rev 11)[/LEFT]
 [LEFT]     DeviceName: Onboard - Other[/LEFT]
 [LEFT]     Flags: fast devsel[/LEFT]
 [LEFT]     Memory at 51134000 (64-bit, non-prefetchable) [disabled] [size=16K][/LEFT]
 [LEFT]     Memory at 5113e000 (64-bit, non-prefetchable) [disabled] [size=4K][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:16.0 0780: 8086:43e0 (rev 11)[/LEFT]
 [LEFT]     DeviceName: Onboard - Other[/LEFT]
 [LEFT]     Subsystem: 1458:1c3a[/LEFT]
 [LEFT]     Flags: bus master, fast devsel, latency 0, IRQ 126[/LEFT]
 [LEFT]     Memory at 5113d000 (64-bit, non-prefetchable) [size=4K][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: mei_me[/LEFT]
 [LEFT]     Kernel modules: mei_me[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:17.0 0106: 8086:43d2 (rev 11) (prog-if 01 [AHCI 1.0])[/LEFT]
 [LEFT]     DeviceName: Onboard - SATA[/LEFT]
 [LEFT]     Subsystem: 1458:b005[/LEFT]
 [LEFT]     Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 123[/LEFT]
 [LEFT]     Memory at 51138000 (32-bit, non-prefetchable) [size=8K][/LEFT]
 [LEFT]     Memory at 5113c000 (32-bit, non-prefetchable) [size=256][/LEFT]
 [LEFT]     I/O ports at 3090 [size=8][/LEFT]
 [LEFT]     I/O ports at 3080 [size=4][/LEFT]
 [LEFT]     I/O ports at 3060 [size=32][/LEFT]
 [LEFT]     Memory at 5113b000 (32-bit, non-prefetchable) [size=2K][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: ahci[/LEFT]
 [LEFT]     Kernel modules: ahci[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:1c.0 0604: 8086:43bc (rev 11) (prog-if 00 [Normal decode])[/LEFT]
 [LEFT]     Flags: bus master, fast devsel, latency 0, IRQ 122[/LEFT]
 [LEFT]     Bus: primary=00, secondary=01, subordinate=01, sec-latency=0[/LEFT]
 [LEFT]     I/O behind bridge: 00004000-00004fff [size=4K][/LEFT]
 [LEFT]     Memory behind bridge: 3f800000-3f9fffff [size=2M][/LEFT]
 [LEFT]     Prefetchable memory behind bridge: 000000003fa00000-000000003fbfffff [size=2M][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: pcieport[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:1f.0 0601: 8086:4388 (rev 11)[/LEFT]
 [LEFT]     DeviceName: Onboard - Other[/LEFT]
 [LEFT]     Subsystem: 1458:5001[/LEFT]
 [LEFT]     Flags: bus master, fast devsel, latency 0[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:1f.3 0403: 8086:f0c8 (rev 11)[/LEFT]
 [LEFT]     **DeviceName: Onboard - Sound**[/LEFT]
 [LEFT]     Subsystem: 1458:a194[/LEFT]
 [LEFT]     Flags: bus master, fast devsel, latency 32, IRQ 128[/LEFT]
 [LEFT]     Memory at 51130000 (64-bit, non-prefetchable) [size=16K][/LEFT]
 [LEFT]     Memory at 51000000 (64-bit, non-prefetchable) [size=1M][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: snd_hda_intel[/LEFT]
 [LEFT]     Kernel modules: snd_hda_intel[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:1f.4 0c05: 8086:43a3 (rev 11)[/LEFT]
 [LEFT]     DeviceName: Onboard - Other[/LEFT]
 [LEFT]     Subsystem: 1458:5001[/LEFT]
 [LEFT]     Flags: medium devsel, IRQ 16[/LEFT]
 [LEFT]     Memory at 5113a000 (64-bit, non-prefetchable) [size=256][/LEFT]
 [LEFT]     I/O ports at efa0 [size=32][/LEFT]
 [LEFT]     Kernel driver in use: i801_smbus[/LEFT]
 [LEFT]     Kernel modules: i2c_i801[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:1f.5 0c80: 8086:43a4 (rev 11)[/LEFT]
 [LEFT]     DeviceName: Onboard - Other[/LEFT]
 [LEFT]     Flags: fast devsel[/LEFT]
 [LEFT]     Memory at 3fc00000 (32-bit, non-prefetchable) [size=4K][/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:1f.6 0200: 8086:15fa (rev 11)[/LEFT]
 [LEFT]     DeviceName: Onboard - Ethernet[/LEFT]
 [LEFT]     Subsystem: 8086:0000[/LEFT]
 [LEFT]     Flags: bus master, fast devsel, latency 0, IRQ 124[/LEFT]
 [LEFT]     Memory at 51100000 (32-bit, non-prefetchable) [size=128K][/LEFT]
 [LEFT]     Capabilities: <access denied>[/LEFT]
 [LEFT]     Kernel driver in use: e1000e[/LEFT]
 [LEFT]     Kernel modules: e1000e[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] locus@locus-fuss:~$ **lsmod|grep snd**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] snd_usb_audio         356352  0[/LEFT]
 [LEFT] snd_usbmidi_lib        45056  1 snd_usb_audio[/LEFT]
 [LEFT] snd_seq_midi           20480  0[/LEFT]
 [LEFT] snd_seq_midi_event     16384  1 snd_seq_midi[/LEFT]
 [LEFT] snd_seq                77824  2 snd_seq_midi,snd_seq_midi_event[/LEFT]
 [LEFT] snd_rawmidi            49152  2 snd_seq_midi,snd_usbmidi_lib[/LEFT]
 [LEFT] snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi[/LEFT]
 [LEFT] mc                     65536  1 snd_usb_audio[/LEFT]
 [LEFT] snd_hda_codec_hdmi     77824  0[/LEFT]
 [LEFT] snd_hda_codec_realtek   159744  0[/LEFT]
 [LEFT] snd_hda_codec_generic   102400  3 snd_hda_codec_realtek[/LEFT]
 [LEFT] ledtrig_audio          16384  1 snd_hda_codec_generic[/LEFT]
 [LEFT] snd_hda_intel          53248  3[/LEFT]
 [LEFT] snd_intel_dspcfg       28672  1 snd_hda_intel[/LEFT]
 [LEFT] snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg[/LEFT]
 [LEFT] snd_hda_codec         163840  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek[/LEFT]
 [LEFT] snd_hda_core          110592  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek[/LEFT]
 [LEFT] snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec[/LEFT]
 [LEFT] snd_pcm               143360  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core[/LEFT]
 [LEFT] snd_timer              40960  2 snd_seq,snd_pcm[/LEFT]
 [LEFT] snd                   106496  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi[/LEFT]
 [LEFT] soundcore              16384  1 snd[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] locus@locus-fuss:~$ **cat /proc/asound/version**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] **Advanced Linux Sound Architecture Driver Version k5.15.0-56-generic.**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] locus@locus-fuss:~$ **cat /proc/asound/card0/codec#0**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] Codec: Realtek Generic[/LEFT]
 [LEFT] Address: 0[/LEFT]
 [LEFT] AFG Function Id: 0x1 (unsol 1)[/LEFT]
 [LEFT] Vendor Id: 0x10ec0897[/LEFT]
 [LEFT] Subsystem Id: 0x1458a194[/LEFT]
 [LEFT] Revision Id: 0x100402[/LEFT]
 [LEFT] No Modem Function Group found[/LEFT]
 [LEFT] Default PCM:[/LEFT]
 [LEFT]     rates [0x5f0]: 32000 44100 48000 88200 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT] Default Amp-In caps: N/A[/LEFT]
 [LEFT] Default Amp-Out caps: N/A[/LEFT]
 [LEFT] State of AFG node 0x01:[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 CLKSTOP EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] GPIO: io=5, o=0, i=0, unsolicited=1, wake=0[/LEFT]
 [LEFT]   IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0[/LEFT]
 [LEFT]   IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0[/LEFT]
 [LEFT]   IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0[/LEFT]
 [LEFT]   IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0[/LEFT]
 [LEFT]   IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0[/LEFT]
 [LEFT] Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out[/LEFT]
 [LEFT]   Control: name="Front Playback Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Device: name="Generic Analog", type="Audio", device=0[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0[/LEFT]
 [LEFT]   Amp-Out vals:  [0x57 0x57][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out[/LEFT]
 [LEFT]   Control: name="Surround Playback Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0[/LEFT]
 [LEFT]   Amp-Out vals:  [0x00 0x00][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out[/LEFT]
 [LEFT]   Control: name="Center Playback Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=1, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Control: name="LFE Playback Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=2, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0[/LEFT]
 [LEFT]   Amp-Out vals:  [0x00 0x00][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out[/LEFT]
 [LEFT]   Control: name="Headphone Playback Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0[/LEFT]
 [LEFT]   Amp-Out vals:  [0x57 0x57][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital[/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   Digital:[/LEFT]
 [LEFT]   Digital category: 0x0[/LEFT]
 [LEFT]   IEC Coding Type: 0x0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x5f0]: 32000 44100 48000 88200 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x07 [Audio Input] wcaps 0x10051b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x97 0x97][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   SDI-Select: 0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x12[/LEFT]
 [LEFT] Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In[/LEFT]
 [LEFT]   Control: name="Capture Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=In, idx=0, ofs=0[/LEFT]
 [LEFT]   Control: name="Capture Switch", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=In, idx=0, ofs=0[/LEFT]
 [LEFT]   Device: name="Generic Analog", type="Audio", device=0[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x3f 0x3f][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   SDI-Select: 0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x23[/LEFT]
 [LEFT] Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In[/LEFT]
 [LEFT]   Control: name="Capture Volume", index=1, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=In, idx=0, ofs=0[/LEFT]
 [LEFT]   Control: name="Capture Switch", index=1, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=In, idx=0, ofs=0[/LEFT]
 [LEFT]   Device: name="Generic Alt Analog", type="Audio", device=2[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0xbf 0xbf][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   SDI-Select: 0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x22[/LEFT]
 [LEFT] Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital[/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   SDI-Select: 0[/LEFT]
 [LEFT]   Digital:[/LEFT]
 [LEFT]   Digital category: 0x0[/LEFT]
 [LEFT]   IEC Coding Type: 0x0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x1f[/LEFT]
 [LEFT] Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97][/LEFT]
 [LEFT]   Connection: 10[/LEFT]
 [LEFT]      0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17[/LEFT]
 [LEFT] Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00] [0x80 0x80][/LEFT]
 [LEFT]   Connection: 2[/LEFT]
 [LEFT]      0x02 0x0b[/LEFT]
 [LEFT] Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00] [0x80 0x80][/LEFT]
 [LEFT]   Connection: 2[/LEFT]
 [LEFT]      0x03 0x0b[/LEFT]
 [LEFT] Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x80 0x80] [0x80 0x80][/LEFT]
 [LEFT]   Connection: 2[/LEFT]
 [LEFT]      0x04 0x0b[/LEFT]
 [LEFT] Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00] [0x80 0x80][/LEFT]
 [LEFT]   Connection: 2[/LEFT]
 [LEFT]      0x05 0x0b[/LEFT]
 [LEFT] Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital[/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   Digital:[/LEFT]
 [LEFT]   Digital category: 0x0[/LEFT]
 [LEFT]   IEC Coding Type: 0x0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x5f0]: 32000 44100 48000 88200 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital[/LEFT]
 [LEFT]   Pincap 0x00000010: OUT[/LEFT]
 [LEFT]   Pin Default 0x4037c040: [N/A] CD at Ext N/A[/LEFT]
 [LEFT]     Conn = Analog, Color = UNKNOWN[/LEFT]
 [LEFT]     DefAssociation = 0x4, Sequence = 0x0[/LEFT]
 [LEFT]   Pin-ctls: 0x40: OUT[/LEFT]
 [LEFT]   Unsolicited: tag=00, enabled=0[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x10[/LEFT]
 [LEFT] Node 0x12 [Pin Complex] wcaps 0x400401: Stereo[/LEFT]
 [LEFT]   Pincap 0x00000020: IN[/LEFT]
 [LEFT]   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Black[/LEFT]
 [LEFT]     DefAssociation = 0xf, Sequence = 0x0[/LEFT]
 [LEFT]     Misc = NO_PRESENCE[/LEFT]
 [LEFT]   Pin-ctls: 0x00:[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono[/LEFT]
 [LEFT] Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out[/LEFT]
 [LEFT]   Control: name="Front Playback Switch", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x80 0x80][/LEFT]
 [LEFT]   Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger[/LEFT]
 [LEFT]   EAPD 0x2: EAPD[/LEFT]
 [LEFT]   Pin Default 0x01014010: [Jack] Line Out at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Green[/LEFT]
 [LEFT]     DefAssociation = 0x1, Sequence = 0x0[/LEFT]
 [LEFT]   Pin-ctls: 0x40: OUT[/LEFT]
 [LEFT]   Unsolicited: tag=05, enabled=1[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x0c[/LEFT]
 [LEFT] Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x80 0x80][/LEFT]
 [LEFT]   Pincap 0x00000036: IN OUT Detect Trigger[/LEFT]
 [LEFT]   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Black[/LEFT]
 [LEFT]     DefAssociation = 0xf, Sequence = 0x0[/LEFT]
 [LEFT]     Misc = NO_PRESENCE[/LEFT]
 [LEFT]   Pin-ctls: 0x20: IN[/LEFT]
 [LEFT]   Unsolicited: tag=00, enabled=0[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x0d[/LEFT]
 [LEFT] Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x80 0x80][/LEFT]
 [LEFT]   Pincap 0x00000036: IN OUT Detect Trigger[/LEFT]
 [LEFT]   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Black[/LEFT]
 [LEFT]     DefAssociation = 0xf, Sequence = 0x0[/LEFT]
 [LEFT]     Misc = NO_PRESENCE[/LEFT]
 [LEFT]   Pin-ctls: 0x20: IN[/LEFT]
 [LEFT]   Unsolicited: tag=00, enabled=0[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x0e[/LEFT]
 [LEFT] Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x80 0x80][/LEFT]
 [LEFT]   Pincap 0x00000036: IN OUT Detect Trigger[/LEFT]
 [LEFT]   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Black[/LEFT]
 [LEFT]     DefAssociation = 0xf, Sequence = 0x0[/LEFT]
 [LEFT]     Misc = NO_PRESENCE[/LEFT]
 [LEFT]   Pin-ctls: 0x20: IN[/LEFT]
 [LEFT]   Unsolicited: tag=00, enabled=0[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x0f[/LEFT]
 [LEFT] Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out[/LEFT]
 [LEFT]   Control: name="Center Playback Switch", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=1, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Control: name="LFE Playback Switch", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=2, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Control: name="Rear Mic Boost Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=In, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00][/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x80 0x80][/LEFT]
 [LEFT]   Pincap 0x00003736: IN OUT Detect Trigger[/LEFT]
 [LEFT]     Vref caps: HIZ 50 GRD 80 100[/LEFT]
 [LEFT]   Pin Default 0x01a19030: [Jack] Mic at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Pink[/LEFT]
 [LEFT]     DefAssociation = 0x3, Sequence = 0x0[/LEFT]
 [LEFT]   Pin-ctls: 0x24: IN VREF_80[/LEFT]
 [LEFT]   Unsolicited: tag=03, enabled=1[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 5[/LEFT]
 [LEFT]      0x0c* 0x0d 0x0e 0x0f 0x26[/LEFT]
 [LEFT] Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out[/LEFT]
 [LEFT]   Control: name="Front Mic Boost Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=In, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00][/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x80 0x80][/LEFT]
 [LEFT]   Pincap 0x0000373e: IN OUT HP Detect Trigger[/LEFT]
 [LEFT]     Vref caps: HIZ 50 GRD 80 100[/LEFT]
 [LEFT]   Pin Default 0x02a19040: [Jack] Mic at Ext Front[/LEFT]
 [LEFT]     Conn = 1/8, Color = Pink[/LEFT]
 [LEFT]     DefAssociation = 0x4, Sequence = 0x0[/LEFT]
 [LEFT]   Pin-ctls: 0x24: IN VREF_80[/LEFT]
 [LEFT]   Unsolicited: tag=02, enabled=1[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 5[/LEFT]
 [LEFT]      0x0c* 0x0d 0x0e 0x0f 0x26[/LEFT]
 [LEFT] Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out[/LEFT]
 [LEFT]   Control: name="Surround Playback Switch", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Control: name="Line Boost Volume", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=In, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00][/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x80 0x80][/LEFT]
 [LEFT]   Pincap 0x00003736: IN OUT Detect Trigger[/LEFT]
 [LEFT]     Vref caps: HIZ 50 GRD 80 100[/LEFT]
 [LEFT]   Pin Default 0x0181303f: [Jack] Line In at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Blue[/LEFT]
 [LEFT]     DefAssociation = 0x3, Sequence = 0xf[/LEFT]
 [LEFT]   Pin-ctls: 0x40: OUT VREF_HIZ[/LEFT]
 [LEFT]   Unsolicited: tag=04, enabled=1[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 5[/LEFT]
 [LEFT]      0x0c 0x0d* 0x0e 0x0f 0x26[/LEFT]
 [LEFT] Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out[/LEFT]
 [LEFT]   Control: name="Headphone Playback Switch", index=0, device=0[/LEFT]
 [LEFT]     ControlAmp: chs=3, dir=Out, idx=0, ofs=0[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00][/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-Out vals:  [0x00 0x00][/LEFT]
 [LEFT]   Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger[/LEFT]
 [LEFT]     Vref caps: HIZ 50 GRD 80 100[/LEFT]
 [LEFT]   EAPD 0x2: EAPD[/LEFT]
 [LEFT]   Pin Default 0x02214020: [Jack] HP Out at Ext Front[/LEFT]
 [LEFT]     Conn = 1/8, Color = Green[/LEFT]
 [LEFT]     DefAssociation = 0x2, Sequence = 0x0[/LEFT]
 [LEFT]   Pin-ctls: 0xc0: OUT HP VREF_HIZ[/LEFT]
 [LEFT]   Unsolicited: tag=01, enabled=1[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 5[/LEFT]
 [LEFT]      0x0c 0x0d 0x0e 0x0f* 0x26[/LEFT]
 [LEFT] Node 0x1c [Pin Complex] wcaps 0x400481: Stereo[/LEFT]
 [LEFT]   Pincap 0x00000020: IN[/LEFT]
 [LEFT]   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Black[/LEFT]
 [LEFT]     DefAssociation = 0xf, Sequence = 0x0[/LEFT]
 [LEFT]     Misc = NO_PRESENCE[/LEFT]
 [LEFT]   Pin-ctls: 0x20: IN[/LEFT]
 [LEFT]   Unsolicited: tag=00, enabled=0[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0, Setting-reset[/LEFT]
 [LEFT] Node 0x1d [Pin Complex] wcaps 0x400400: Mono[/LEFT]
 [LEFT]   Pincap 0x00000020: IN[/LEFT]
 [LEFT]   Pin Default 0x4035c641: [N/A] CD at Ext N/A[/LEFT]
 [LEFT]     Conn = Optical, Color = UNKNOWN[/LEFT]
 [LEFT]     DefAssociation = 0x4, Sequence = 0x1[/LEFT]
 [LEFT]   Pin-ctls: 0x20: IN[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital[/LEFT]
 [LEFT]   Pincap 0x00000010: OUT[/LEFT]
 [LEFT]   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Black[/LEFT]
 [LEFT]     DefAssociation = 0xf, Sequence = 0x0[/LEFT]
 [LEFT]     Misc = NO_PRESENCE[/LEFT]
 [LEFT]   Pin-ctls: 0x40: OUT[/LEFT]
 [LEFT]   Unsolicited: tag=00, enabled=0[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT]   Connection: 1[/LEFT]
 [LEFT]      0x06[/LEFT]
 [LEFT] Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital[/LEFT]
 [LEFT]   Pincap 0x00000020: IN[/LEFT]
 [LEFT]   Pin Default 0x411111f0: [N/A] Speaker at Ext Rear[/LEFT]
 [LEFT]     Conn = 1/8, Color = Black[/LEFT]
 [LEFT]     DefAssociation = 0xf, Sequence = 0x0[/LEFT]
 [LEFT]     Misc = NO_PRESENCE[/LEFT]
 [LEFT]   Pin-ctls: 0x20: IN[/LEFT]
 [LEFT]   Unsolicited: tag=00, enabled=0[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono[/LEFT]
 [LEFT]   Processing caps: benign=0, ncoeff=142[/LEFT]
 [LEFT] Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono[/LEFT]
 [LEFT] Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80][/LEFT]
 [LEFT]   Connection: 12[/LEFT]
 [LEFT]      0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12[/LEFT]
 [LEFT] Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80][/LEFT]
 [LEFT]   Connection: 11[/LEFT]
 [LEFT]      0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b[/LEFT]
 [LEFT] Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono[/LEFT]
 [LEFT] Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out[/LEFT]
 [LEFT]   Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0[/LEFT]
 [LEFT]   Amp-Out vals:  [0x57 0x57][/LEFT]
 [LEFT]   Converter: stream=0, channel=0[/LEFT]
 [LEFT]   PCM:[/LEFT]
 [LEFT]     rates [0x560]: 44100 48000 96000 192000[/LEFT]
 [LEFT]     bits [0xe]: 16 20 24[/LEFT]
 [LEFT]     formats [0x1]: PCM[/LEFT]
 [LEFT]   Power states:  D0 D1 D2 D3 EPSS[/LEFT]
 [LEFT]   Power: setting=D0, actual=D0[/LEFT]
 [LEFT] Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In[/LEFT]
 [LEFT]   Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1[/LEFT]
 [LEFT]   Amp-In vals:  [0x00 0x00] [0x80 0x80][/LEFT]
 [LEFT]   Connection: 2[/LEFT]
 [LEFT]      0x25 0x0b[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] locus@locus-fuss:~$ **aplay -l**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] **** List of PLAYBACK Hardware Devices ****[/LEFT]
 [LEFT] card 0: PCH [HDA Intel PCH], device 0: Generic Analog [Generic Analog][/LEFT]
 [LEFT]   Subdevices: 1/1[/LEFT]
 [LEFT]   Subdevice #0: subdevice #0[/LEFT]
 [LEFT] card 0: PCH [HDA Intel PCH], device 3: Generic Digital [Generic Digital][/LEFT]
 [LEFT]   Subdevices: 1/1[/LEFT]
 [LEFT]   Subdevice #0: subdevice #0[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] locus@locus-fuss:~$ **cat /proc/asound/card0/codec* | grep Codec**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] Codec: Realtek Generic[/LEFT]
 [LEFT] Codec: Intel Generic[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] locus@locus-fuss:~$ **lspci**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 00:00.0 Host bridge: Intel Corporation 10th Gen Core Processor Host Bridge/DRAM Registers (rev 03)[/LEFT]
 [LEFT] 00:02.0 VGA compatible controller: Intel Corporation CometLake-S GT2 [UHD Graphics 630] (rev 03)[/LEFT]
 [LEFT] 00:14.0 USB controller: Intel Corporation Tiger Lake-H USB 3.2 Gen 2x1 xHCI Host Controller (rev 11)[/LEFT]
 [LEFT] 00:14.2 RAM memory: Intel Corporation Tiger Lake-H Shared SRAM (rev 11)[/LEFT]
 [LEFT] 00:16.0 Communication controller: Intel Corporation Tiger Lake-H Management Engine Interface (rev 11)[/LEFT]
 [LEFT] 00:17.0 SATA controller: Intel Corporation Device 43d2 (rev 11)[/LEFT]
 [LEFT] 00:1c.0 PCI bridge: Intel Corporation Tiger Lake-H PCI Express Root Port #5 (rev 11)[/LEFT]
 [LEFT] 00:1f.0 ISA bridge: Intel Corporation Device 4388 (rev 11)[/LEFT]
 [LEFT] 00:1f.3 Audio device: Intel Corporation Device f0c8 (rev 11)[/LEFT]
 [LEFT] 00:1f.4 SMBus: Intel Corporation Tiger Lake-H SMBus Controller (rev 11)[/LEFT]
 [LEFT] 00:1f.5 Serial bus controller: Intel Corporation Tiger Lake-H SPI Controller (rev 11)[/LEFT]
 [LEFT] 00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (14) I219-V (rev 11)[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] locus@locus-fuss:~$ **pacmd list-cards**[/LEFT]
 [LEFT] 
 [/LEFT]
 [LEFT] 1 card(s) available.[/LEFT]
 [LEFT]     index: 0[/LEFT]
 [LEFT]     name: <alsa_card.pci-0000_00_1f.3>[/LEFT]
 [LEFT]     driver: <module-alsa-card.c>[/LEFT]
 [LEFT]     owner module: 19[/LEFT]
 [LEFT]     properties:[/LEFT]
 [LEFT]         alsa.card = "0"[/LEFT]
 [LEFT]         alsa.card_name = "HDA Intel PCH"[/LEFT]
 [LEFT]         alsa.long_card_name = "HDA Intel PCH at 0x51130000 irq 128"[/LEFT]
 [LEFT]         alsa.driver_name = "snd_hda_intel"[/LEFT]
 [LEFT]         device.bus_path = "pci-0000:00:1f.3"[/LEFT]
 [LEFT]         sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"[/LEFT]
 [LEFT]         device.bus = "pci"[/LEFT]
 [LEFT]         device.vendor.id = "8086"[/LEFT]
 [LEFT]         device.vendor.name = "Intel Corporation"[/LEFT]
 [LEFT]         device.product.id = "f0c8"[/LEFT]
 [LEFT]         device.form_factor = "internal"[/LEFT]
 [LEFT]         device.string = "0"[/LEFT]
 [LEFT]         device.description = "Built-in Audio"[/LEFT]
 [LEFT]         module-udev-detect.discovered = "1"[/LEFT]
 [LEFT]         device.icon_name = "audio-card-pci"[/LEFT]
 [LEFT]     profiles:[/LEFT]
 [LEFT]         input:analog-stereo: Analog Stereo Input (priority 32833, available: unknown)[/LEFT]
 [LEFT]         output:analog-stereo: Analog Stereo Output (priority 39268, available: unknown)[/LEFT]
 [LEFT]         output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 39333, available: unknown)[/LEFT]
 [LEFT]         output:analog-surround-40: Analog Surround 4.0 Output (priority 1200, available: no)[/LEFT]
 [LEFT]         output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (priority 1265, available: unknown)[/LEFT]
 [LEFT]         output:analog-surround-51: Analog Surround 5.1 Output (priority 1300, available: no)[/LEFT]
 [LEFT]         output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 1365, available: unknown)[/LEFT]
 [LEFT]         output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 38668, available: unknown)[/LEFT]
 [LEFT]         output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 38733, available: unknown)[/LEFT]
 [LEFT]         off: Off (priority 0, available: unknown)[/LEFT]
 [LEFT]     active profile: <output:analog-stereo+input:analog-stereo>[/LEFT]
 [LEFT]     sinks:[/LEFT]
 [LEFT]         alsa_output.pci-0000_00_1f.3.analog-stereo/#1: Built-in Audio Analog Stereo[/LEFT]
 [LEFT]     sources:[/LEFT]
 [LEFT]         alsa_output.pci-0000_00_1f.3.analog-stereo.monitor/#1: Monitor of Built-in Audio Analog Stereo[/LEFT]
 [LEFT]         alsa_input.pci-0000_00_1f.3.analog-stereo/#2: Built-in Audio Analog Stereo[/LEFT]
 [LEFT]     ports:[/LEFT]
 [LEFT]         analog-input-front-mic: Front Microphone (priority 8500, latency offset 0 usec, available: yes)[/LEFT]
 [LEFT]             properties:[/LEFT]
 [LEFT]                 device.icon_name = "audio-input-microphone"[/LEFT]
 [LEFT]         analog-input-rear-mic: Rear Microphone (priority 8200, latency offset 0 usec, available: no)[/LEFT]
 [LEFT]             properties:[/LEFT]
 [LEFT]                 device.icon_name = "audio-input-microphone"[/LEFT]
 [LEFT]         analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: no)[/LEFT]
 [LEFT]             properties:[/LEFT]
 [LEFT]                 [/LEFT]
 [LEFT]         analog-output-lineout: Line Out (priority 9000, latency offset 0 usec, available: no)[/LEFT]
 [LEFT]             properties:[/LEFT]
 [LEFT]                 [/LEFT]
 [LEFT]         analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: yes)[/LEFT]
 [LEFT]             properties:[/LEFT]
 [LEFT]                 device.icon_name = "audio-headphones"[/LEFT]
 [LEFT]         hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: unknown)[/LEFT]
 [LEFT]             properties:[/LEFT]
 [LEFT]                 device.icon_name = "video-display"[/LEFT]
 [LEFT] 
 [/LEFT]

---

### Post by matthewrkarlsen on 2022-12-18
Hello surendra-mum,

This may be a naive question, but have you got [FONT=courier new]pavucontrol[/FONT] installed? If so you can check the correct output is selected under the Configuration tab.

Also, I once tried almost everything only to find out that under [FONT=courier new]alsamixer[/FONT] I had the output muted (you can toggle it via the 'm' key).

Whilst the detail in the post above suggests that these two solutions may be too elementary, I leave this post here in case it helps someone.

Regards,
Matthew

---

### Post by surendra-mum on 2022-12-20
I had installed [FONT=courier new]pavucontrol & unmuted the muted part in [/FONT][FONT=courier new]alsamixer but nothing worked. Tried all options & went for upgrading other version i.e ubuntu 22.10 but still again there is problem with no sound.  [/FONT]


**locus@locus-fuss:~$ lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.10
Release:    22.10
Codename:    kinetic
[FONT=Liberation Mono, Courier New, monospace][SIZE=3]
locus@locus-fuss:~$ **uname -a**[/SIZE][/FONT]
 
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Linux locus-fuss 5.19.0-26-generic #27-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov 23 20:44:15 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux[/SIZE][/FONT]

  
 
  
[FONT=Liberation Mono, Courier New, monospace][SIZE=3]locus@locus-fuss:~$ **cat /proc/asound/cards**[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]0 [PCH            ]: HDA-Intel - HDA Intel PCH[/SIZE][/FONT]

                        [FONT=Liberation Mono, Courier New, monospace][SIZE=3]HDA Intel PCH at 0x51130000 irq 128[/SIZE][/FONT]
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]locus@locus-fuss:~$ **lsmod | grep snd**[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_usb_audio         372736  0[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_usbmidi_lib        45056  1 snd_usb_audio[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]mc                     65536  1 snd_usb_audio[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_hda_codec_hdmi     81920  1[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_hda_codec_realtek   163840  1[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_hda_codec_generic   102400  1 snd_hda_codec_realtek[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]ledtrig_audio          16384  1 snd_hda_codec_generic[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_hda_intel          53248  0[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_intel_dspcfg       36864  1 snd_hda_intel[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_hda_codec         172032  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_hda_core          118784  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_pcm               155648  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_seq_midi           20480  0[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_seq_midi_event     16384  1 snd_seq_midi[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_rawmidi            45056  2 snd_seq_midi,snd_usbmidi_lib[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_seq                77824  2 snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd_timer              40960  2 snd_seq,snd_pcm[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]snd                   114688  13 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]soundcore              16384  1 snd[/SIZE][/FONT]

  
 
  
 
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]locus@locus-fuss:~$ **dpkg -L linux-modules-$(uname -r) | grep snd**[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/seq/snd-seq-dummy.ko[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/seq/snd-seq-midi-event.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/seq/snd-seq-midi.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/seq/snd-seq-virmidi.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/seq/snd-seq.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-compress.ko[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-ctl-led.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-hrtimer.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-hwdep.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-pcm-dmaengine.ko[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-pcm.ko[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-rawmidi.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-seq-device.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd-timer.ko[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/core/snd.ko[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/pci/snd-ens1370.ko[/SIZE][/FONT]

  
 
  
 
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]locus@locus-fuss:~$ **inxi -SA**[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]System:[/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Host: locus-fuss Kernel: 5.19.0-26-generic arch: x86_64 bits: 64[/SIZE][/FONT]
      [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Desktop: Xfce v: 4.17.0 Distro: Ubuntu 22.10 (Kinetic Kudu)[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Audio:[/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Device-1: Intel driver: snd_hda_intel[/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Sound Server-1: ALSA v: k5.19.0-26-generic running: yes[/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Sound Server-2: PipeWire v: 0.3.58 running: yes[/SIZE][/FONT]
  
 
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]locus@locus-fuss:~$ **lspci -nnk | grep -A 1 Audio**[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]00:1f.3 Audio device [0403]: Intel Corporation Device [8086:f0c8] (rev 11)[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]	DeviceName: Onboard - Sound[/SIZE][/FONT]

  
 
  
 
[FONT=Liberation Mono, Courier New, monospace][SIZE=3]locus@locus-fuss:~$ **aplay -l**[/SIZE][/FONT]
 
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]**** List of PLAYBACK Hardware Devices ****[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]card 0: PCH [HDA Intel PCH], device 0: ALC897 Analog [ALC897 Analog][/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevices: 1/1[/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevice #0: subdevice #0[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0][/SIZE][/FONT]
    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevices: 1/1[/SIZE][/FONT]
    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevice #0: subdevice #0[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1][/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevices: 1/1[/SIZE][/FONT]
    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevice #0: subdevice #0[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2][/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevices: 1/1[/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevice #0: subdevice #0[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3][/SIZE][/FONT]
    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevices: 1/1[/SIZE][/FONT]
    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevice #0: subdevice #0[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4][/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevices: 1/1[/SIZE][/FONT]

    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]Subdevice #0: subdevice #0[/SIZE][/FONT]
  
 
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]locus@locus-fuss:~$  **lshw -C multimedia**[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]WARNING: you should run this program as super-user.[/SIZE][/FONT]
    [FONT=Liberation Mono, Courier New, monospace][SIZE=3]*-multimedia              [/SIZE][/FONT] 

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]description: Audio device[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]product: Intel Corporation[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]vendor: Intel Corporation[/SIZE][/FONT]
         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]physical id: 1f.3[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]bus info: pci@0000:00:1f.3[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: card0[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/controlC0[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/hwC0D0[/SIZE][/FONT]
         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/hwC0D2[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D0c[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D0p[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D10p[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D2c[/SIZE][/FONT]
         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D3p[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D7p[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D8p[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]logical name: /dev/snd/pcmC0D9p[/SIZE][/FONT]
         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]version: 11[/SIZE][/FONT]
         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]width: 64 bits[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]clock: 33MHz[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]capabilities: bus_master cap_list[/SIZE][/FONT]

         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]configuration: driver=snd_hda_intel latency=32[/SIZE][/FONT]
         [FONT=Liberation Mono, Courier New, monospace][SIZE=3]resources: irq:128 memory:51130000-51133fff memory:51000000-510fffff[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]WARNING: output may be incomplete or inaccurate, you should run this program as super-user.[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]**locus@locus-fuss:~$ dpkg -l | grep alsa**[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]ii  alsa-base                                  1.0.25+dfsg-0ubuntu7                       all          ALSA driver configuration files[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]ii  alsa-oss                                   1.1.8-1                                    amd64        ALSA wrapper for OSS applications[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]ii  alsa-topology-conf                         1.2.5.1-2                                  all          ALSA topology configuration files[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]ii  alsa-ucm-conf                              1.2.6.3-1ubuntu2                           all          ALSA Use Case Manager configuration files[/SIZE][/FONT]

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]ii  alsa-utils                                 1.2.6-1ubuntu1                             amd64        Utilities for configuring and using ALSA[/SIZE][/FONT]
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]ii  gstreamer1.0-alsa:amd64                    1.20.3-2                                   amd64        GStreamer plugin for ALSA[/SIZE][/FONT]

  
 
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]**locus@locus-fuss:~$ grep intel /etc/modprobe.d/alsa-base.conf**[/SIZE][/FONT]
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]options snd-intel8x0m index=-2[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]**locus@locus-fuss:~$ modprobe --show-depends snd_hda_intel **[/SIZE][/FONT] 

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/soundcore.ko [/SIZE][/FONT] 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]install /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; } [/SIZE][/FONT] 

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/core/snd-timer.ko [/SIZE][/FONT] 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]install /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; } [/SIZE][/FONT] 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/core/snd-hwdep.ko [/SIZE][/FONT] 

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/hda/snd-hda-core.ko [/SIZE][/FONT] 

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/pci/hda/snd-hda-codec.ko [/SIZE][/FONT] 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/hda/snd-intel-sdw-acpi.ko [/SIZE][/FONT] 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/hda/snd-intel-dspcfg.ko [/SIZE][/FONT] 

  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]insmod /lib/modules/5.19.0-26-generic/kernel/sound/pci/hda/snd-hda-intel.ko [/SIZE][/FONT] 

  
 
  
 
  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]**locus@locus-fuss:~$ find /lib/modules/$(uname -r)/kernel/sound -name snd-hda-intel.ko**[/SIZE][/FONT]

  
 
  [FONT=Liberation Mono, Courier New, monospace][SIZE=3]/lib/modules/5.19.0-26-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/SIZE][/FONT]

---

### Post by surendra-mum on 2022-12-20
**locus@locus-fuss:~$ grep intel /etc/modprobe.d/alsa-base.conf**
options snd-intel8x0m index=-2
options snd-hda-intel model=auto


Hope 				 				 					 						 	[**[COLOR=#000000]matthewrkarlsen[/COLOR]**]("https://ubuntuforums.org/member.php?u=2175452")  you would find a solution to retrieve back sound.   

Regards,
Surendra

---

### Post by surendra-mum on 2022-12-20
**locus@locus-fuss:~$ dpkg --list | grep linux-image**
rc  linux-image-5.15.0-43-generic              5.15.0-43.46                               amd64        Signed kernel image generic
ii  linux-image-5.15.0-56-generic              5.15.0-56.62                               amd64        Signed kernel image generic
ii  linux-image-5.19.0-26-generic              5.19.0-26.27                               amd64        Signed kernel image generic
ii  linux-image-generic                        5.19.0.26.23                               amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-22.04              5.19.0.26.23                               amd64        Generic Linux kernel image

---

