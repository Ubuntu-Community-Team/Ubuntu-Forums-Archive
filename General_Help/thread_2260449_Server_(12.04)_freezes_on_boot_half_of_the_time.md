---
title: "Server (12.04) freezes on boot half of the time"
date: 2015-01-12
forum: General Help
---

### Post by benoit-schmid on 2015-01-12
Hello,

My machine hangs on boot half of the time.
I have suspected the hard drive. But replacing my ocz drive by a samsung one has not change this behaviour.

It hangs on adding swap. But if I remove the swap, it does not solve my issue.
It hangs on next boot sequence.

After reading a few posts, I have tried the following grub options:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="no splash acpi_osi=Linux acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="splash acpi=off"
GRUB_CMDLINE_LINUX="splash radeon.audio=1"

But it does not solve my problem.

Could you tell me how I could diagnose the source of my problem?

This is my hardware:
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Q67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]

These are my kernel modules:
Module                  Size  Used by
snd_hda_codec_hdmi     47006  1 
bnep                   19884  2 
rfcomm                 74748  0 
bluetooth             411194  10 bnep,rfcomm
parport_pc             32866  1 
ppdev                  17711  0 
ipt_REJECT             12576  1 
xt_LOG                 17829  5 
xt_limit               12711  7 
xt_tcpudp              12924  17 
xt_addrtype            12713  4 
nf_conntrack_ipv4      15063  7 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_state               12578  7 
ip6table_filter        12815  1 
ip6_tables             27502  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12825  0 
nf_nat                 26091  1 nf_nat_ftp
nf_conntrack_ftp       18715  1 nf_nat_ftp
nf_conntrack           97581  7 nf_conntrack_ipv4,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ftp
snd_hda_codec_realtek    66377  1 
iptable_filter         12810  1 
ip_tables              27716  1 iptable_filter
radeon               1570009  3 
snd_hda_intel          57222  5 
x_tables               34194  10 ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_hda_codec         199156  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
dcdbas                 15017  0 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30465  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ttm                    90134  1 radeon
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              30038  2 snd_pcm,snd_seq
drm_kms_helper         53540  1 radeon
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   308868  5 radeon,ttm,drm_kms_helper
psmouse               113295  0 
snd                    73890  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13564  1 radeon
serio_raw              13462  0 
video                  19914  0 
mei_me                 18674  0 
mac_hid                13253  0 
mei                    87127  1 mei_me
lpc_ich                21163  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                42481  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53021  0 
e1000e                257783  0 
hid                   106605  2 hid_generic,usbhid
ptp                    18980  1 e1000e
pps_core               19381  1 ptp

Regards,

---

