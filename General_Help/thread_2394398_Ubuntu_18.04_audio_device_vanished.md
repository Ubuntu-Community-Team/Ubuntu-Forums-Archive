---
title: "Ubuntu 18.04 audio device vanished"
date: 2018-06-16
forum: General Help
---

### Post by ansgar.snow on 2018-06-16
[COLOR=#111111][FONT=Ubuntu]I dont even know when and how, but my laptop audio device seems to be gone, I see only hdaudio output from hdmi port, but nothing else so my builtin speakers are quiet.Its weird and I could use some help on it.Cheers.[/FONT][/COLOR]

```
$lspci
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: NVIDIA Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: NVIDIA Corporation MCP79 [GeForce 8200M G] (rev b1)
06:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)

   $lsmod
    Module                  Size  Used by
    bnep                   20480  2
    msr                    16384  0
    nfnetlink_queue        24576  0
    nfnetlink_log          20480  0
    nfnetlink              16384  2 nfnetlink_log,nfnetlink_queue
    bluetooth             548864  7 bnep
    ecdh_generic           24576  1 bluetooth
    binfmt_misc            20480  1
    nvidia_uvm             36864  0
    uvcvideo               86016  0
    videobuf2_vmalloc      16384  1 uvcvideo
    videobuf2_memops       16384  1 videobuf2_vmalloc
    videobuf2_v4l2         24576  1 uvcvideo
    videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
    videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
    media                  40960  2 uvcvideo,videodev
    wmi_bmof               16384  0
    arc4                   16384  4
    nvidia              10559488  57 nvidia_uvm
    rt2800usb              32768  0
    rt2x00usb              20480  1 rt2800usb
    rt2800lib             114688  1 rt2800usb
    rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb
    ath9k                 151552  0
    ath9k_common           36864  1 ath9k
    ath9k_hw              471040  2 ath9k,ath9k_common
    ath                    28672  3 ath9k_hw,ath9k,ath9k_common
    mac80211              778240  4 rt2800lib,rt2x00lib,rt2x00usb,ath9k
    snd_hda_codec_hdmi     49152  1
    cfg80211              622592  5 rt2x00lib,mac80211,ath9k,ath,ath9k_common
    snd_hda_intel          40960  3
    snd_hda_codec         126976  2 snd_hda_intel,snd_hda_codec_hdmi
    coretemp               16384  0
    snd_hda_core           81920  3 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi
    snd_hwdep              20480  1 snd_hda_codec
    snd_pcm                98304  5 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
    joydev                 24576  0
    input_leds             16384  0
    serio_raw              16384  0
    shpchp                 36864  0
    snd_seq_midi           16384  0
    snd_seq_midi_event     16384  1 snd_seq_midi
    snd_rawmidi            32768  1 snd_seq_midi
    snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
    snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
    snd_timer              32768  2 snd_seq,snd_pcm
    snd                    81920  14 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_seq_device,snd_pcm
    drm                   401408  3 nvidia
    asus_laptop            32768  0
    sparse_keymap          16384  1 asus_laptop
    input_polldev          16384  1 asus_laptop
    wmi                    24576  1 wmi_bmof
    soundcore              16384  1 snd
    mac_hid                16384  0
    sch_fq_codel           20480  6
    parport_pc             36864  0
    ppdev                  20480  0
    lp                     20480  0
    parport                49152  3 lp,parport_pc,ppdev
    ip_tables              28672  0
    x_tables               40960  1 ip_tables
    autofs4                40960  2
    uas                    24576  0
    usb_storage            69632  5 uas
    pata_acpi              16384  0
    psmouse               147456  0
    ahci                   36864  0
    forcedeth              69632  0
    libahci                32768  1 ahci
    i2c_nforce2            16384  0
    video                  40960  1 asus_laptop



      $dmesg -l warn 
    [    0.045030] mtrr: your CPUs had inconsistent variable MTRR settings
    [    0.156842] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
    [    0.236535] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
    [    1.363690] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 21
    [    1.364314] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 20
    [    1.364876] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 23
    [    1.365429] ACPI: PCI Interrupt Link [LRP6] enabled at IRQ 22
    [    1.372116] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
    [    1.777531] ACPI Warning: SystemIO range 0x0000000000004E00-0x0000000000004E3F conflicts with OpRegion 0x0000000000004E00-0x0000000000004E3F (\_SB.PCI0.SM00) (20170831/utaddress-247)
    [    1.783969] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
    [    2.321660] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
    [   26.161005] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
    [   27.271051] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 19
    [   27.495020] nvidia: loading out-of-tree module taints kernel.
    [   27.495033] nvidia: module license 'NVIDIA' taints kernel.
    [   27.495034] Disabling lock debugging due to kernel taint
    [   27.539061] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 22
    [   27.541937] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 21
    [   27.547556] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.106  Tue Jan  9 15:10:23 PST 2018
    [   28.706235] uvcvideo 1-7:1.0: Entity type for entity Extension 4 was not initialized!
    [   28.706240] uvcvideo 1-7:1.0: Entity type for entity Processing 3 was not initialized!
    [   28.706242] uvcvideo 1-7:1.0: Entity type for entity Camera 1 was not initialized!
    [   29.566848] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]
    [   29.567093] caller os_map_kernel_space+0x86/0xb0 [nvidia] mapping multiple BARs
    [   29.974350] NVRM: Your system is not currently configured to drive a VGA console
    [   29.974353] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
    [   29.974354] NVRM: requires the use of a text-mode VGA console. Use of other console
    [   29.974355] NVRM: drivers including, but not limited to, vesafb, may result in
    [   29.974356] NVRM: corruption and stability problems, and is not supported.
    [   45.290634] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]
    [   45.290992] caller os_map_kernel_space+0x86/0xb0 [nvidia] mapping multiple BARs</code></pre></div><br>

```
alsa-info:[https://pastebin.com/nrq616Dz](https://pastebin.com/nrq616Dz)

---

