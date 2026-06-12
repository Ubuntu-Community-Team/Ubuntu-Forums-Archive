---
title: "PC will not suspend, fans still run, PC still running normally, Ubuntu 20.04"
date: 2020-05-03
forum: General Help
---

### Post by ceojosh24 on 2020-05-03
New to Ubuntu 20.04 after 9 years of working with a Mac. Almost got it to where I want, but when I click Suspend in the Power options above, and it used to work just fine, but now it no longer suspends to where the computer actually goes into sleep mode. Fans are still running normally. I can just click and turn the login screen back on like nothing happened. I tried looking for a solution and tried looking in BIOS for Power Management, but there were no suspend options like some forums said. I tried unplugging all my USB devices after suspending too, since I read that USB devices might keep it from going to sleep, but none of it worked. Even tried turning off my mouse right after I clicked Suspend. Nothing. Can anyone help? Here's the dmesg before and after I clicked Suspend.

```
[  961.378183] PM: suspend entry (deep)
[  961.382447] Filesystems sync: 0.004 seconds
[  961.585235] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 0
[  961.666450] Freezing user space processes ... (elapsed 0.003 seconds) done.
[  961.670150] OOM killer disabled.
[  961.670151] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  961.671718] printk: Suspending console(s) (use no_console_suspend to debug)
[  961.673707] PM: pci_pm_suspend(): wil6210_pm_suspend+0x0/0x20 [wil6210] returns 1
[  961.673707] e1000e: EEE TX LPI TIMER: 00000011
[  961.673713] PM: dpm_run_callback(): pci_pm_suspend+0x0/0x150 returns 1
[  961.673716] PM: Device 0000:02:00.0 failed to suspend async: error 1
**[  961.857438] PM: Some devices failed to suspend, or early wake event detected**
[  961.857919] usb usb3: root hub lost power or was reset
[  961.857924] usb usb4: root hub lost power or was reset
[  961.857940] usb usb5: root hub lost power or was reset
[  961.857944] usb usb7: root hub lost power or was reset
[  961.857945] usb usb6: root hub lost power or was reset
[  961.857947] usb usb8: root hub lost power or was reset
[  962.126411] nvme nvme0: Shutdown timeout set to 8 seconds
[  962.149654] nvme nvme0: 20/0/0 default/read/poll queues
[  962.596711] ata2: SATA link down (SStatus 4 SControl 300)
[  962.596737] ata6: SATA link down (SStatus 4 SControl 300)
[  962.596811] ata3: SATA link down (SStatus 4 SControl 300)
[  962.596848] ata4: SATA link down (SStatus 4 SControl 300)
[  962.596898] ata5: SATA link down (SStatus 4 SControl 300)
[  962.596935] ata7: SATA link down (SStatus 4 SControl 300)
[  962.596974] ata1: SATA link down (SStatus 4 SControl 300)
[  964.070765] fbcon: Taking over console
[  964.070822] OOM killer enabled.
[  964.070823] Restarting tasks ... 
[  964.075423] Console: switching to colour frame buffer device 240x67
[  964.077883] done.
[  964.081417] rfkill: input handler enabled
[  964.083719] PM: suspend exit
[  964.083843] PM: suspend entry (s2idle)
[  964.101290] Filesystems sync: 0.017 seconds
[  964.135552] Freezing user space processes ... (elapsed 0.141 seconds) done.
[  964.276726] OOM killer disabled.
[  964.276727] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  964.278419] printk: Suspending console(s) (use no_console_suspend to debug)
[  964.281302] e1000e: EEE TX LPI TIMER: 00000011
[  964.479494] ACPI: EC: interrupt blocked
[ 1129.748281] ACPI: EC: interrupt unblocked
[ 1130.028256] nvme nvme0: Shutdown timeout set to 8 seconds
[ 1130.048310] nvme nvme0: 20/0/0 default/read/poll queues
[ 1130.099585] usb 1-9: reset full-speed USB device number 3 using xhci_hcd
[ 1130.317540] OOM killer enabled.
[ 1130.317541] Restarting tasks ... done.
[ 1130.324230] PM: suspend exit
[ 1130.464666] rfkill: input handler disabled
[ 1130.479313] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 0
[ 1130.541483] ata6: SATA link down (SStatus 4 SControl 300)
[ 1130.541765] ata1: SATA link down (SStatus 4 SControl 300)
[ 1130.541798] ata7: SATA link down (SStatus 4 SControl 300)
[ 1130.541831] ata2: SATA link down (SStatus 4 SControl 300)
[ 1130.541854] ata5: SATA link down (SStatus 4 SControl 300)
[ 1130.541886] ata3: SATA link down (SStatus 4 SControl 300)
[ 1130.542049] ata4: SATA link down (SStatus 4 SControl 300)
[ 1130.546625] e1000e: eno1 NIC Link is Down
[ 1133.771938] igb 0000:05:00.0 enp5s0: igb: enp5s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[ 1133.879639] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready
```

---

### Post by wildmanne39 on 2020-05-03
Hello and welcome to the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 


 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by rldever on 2020-05-05
On 19.10, this also  just started happening for me after performing an update with "Software Updater". Previously suspend was working flawlessly. 

**In an effort at resolution I've tried the following without success:**
```

sudo apt-get update
sudo apt-get upgrade
sudo upduntu-drivers autoinstall
sudo reboot
sudo apt autoremove

```

**system log showing failed suspend errors:**
> 
May 05 08:38:34 xxxxx kernel: Freezing user space processes ... (elapsed 0.003 seconds) done.
May 05 08:38:34 xxxxx kernel: OOM killer disabled.
May 05 08:38:34 xxxxx kernel: Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
May 05 08:38:34 xxxxx kernel: printk: Suspending console(s) (use no_console_suspend to debug)
May 05 08:38:34 xxxxx kernel: PM: pci_pm_suspend(): wil6210_pm_suspend+0x0/0x20 [wil6210] returns 1
May 05 08:38:34 xxxxx kernel: PM: dpm_run_callback(): pci_pm_suspend+0x0/0x150 returns 1
May 05 08:38:34 xxxxx kernel: e1000e: EEE TX LPI TIMER: 00000011
May 05 08:38:34 xxxxx kernel: PM: Device 0000:02:00.0 failed to suspend async: error 1
May 05 08:38:34 xxxxx kernel: sd 0:0:0:0: [sda] Synchronizing SCSI cache
May 05 08:38:34 xxxxx kernel: sd 0:0:0:0: [sda] Stopping disk
May 05 08:38:34 xxxxx kernel: sd 1:0:0:0: [sdb] Synchronizing SCSI cache
May 05 08:38:34 xxxxx kernel: sd 1:0:0:0: [sdb] Stopping disk
May 05 08:38:34 xxxxx kernel: PM: Some devices failed to suspend, or early wake event detected


---

### Post by ceojosh24 on 2020-05-06
Still searching for a solution, but here is my suspend-log that I found in case anyone can give more details. 

```
Initial commandline parameters: 
Wed 06 May 2020 10:44:53 AM EDT: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux pc 5.4.0-29-generic #33-Ubuntu SMP Wed Apr 29 14:32:27 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
btrfs                1249280  0
xor                    24576  1 btrfs
zstd_compress         167936  1 btrfs
raid6_pq              114688  1 btrfs
ufs                    81920  0
qnx4                   16384  0
hfsplus               110592  0
hfs                    61440  0
minix                  36864  0
ntfs                  106496  0
msdos                  20480  0
jfs                   188416  0
xfs                  1277952  0
rfcomm                 81920  4
xt_CHECKSUM            16384  1
xt_MASQUERADE          20480  3
ip6table_mangle        16384  1
ip6table_nat           16384  1
iptable_mangle         16384  1
iptable_nat            16384  1
nf_nat                 40960  3 ip6table_nat,iptable_nat,xt_MASQUERADE
nf_tables             135168  0
nfnetlink              16384  1 nf_tables
bridge                176128  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
cmac                   16384  4
algif_hash             16384  2
algif_skcipher         16384  2
af_alg                 24576  10 algif_hash,algif_skcipher
bnep                   24576  2
nls_iso8859_1          16384  1
intel_rapl_msr         20480  0
snd_hda_codec_hdmi     61440  1
intel_rapl_common      24576  1 intel_rapl_msr
nvidia_uvm            970752  0
nvidia_drm             49152  9
isst_if_common         16384  0
nvidia_modeset       1114112  17 nvidia_drm
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
nvidia              20430848  856 nvidia_uvm,nvidia_modeset
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          53248  7
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_seq_midi           20480  0
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
nfit                   65536  0
snd_rawmidi            36864  1 snd_seq_midi
snd_hwdep              20480  1 snd_hda_codec
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
kvm_intel             286720  0
ath10k_pci             49152  0
drm_kms_helper        184320  1 nvidia_drm
kvm                   663552  1 kvm_intel
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
ath10k_core           475136  1 ath10k_pci
ipmi_devintf           20480  0
btusb                  57344  0
ipmi_msghandler       106496  2 ipmi_devintf,nvidia
eeepc_wmi              16384  0
btrtl                  24576  1 btusb
asus_wmi               32768  1 eeepc_wmi
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
btbcm                  16384  1 btusb
fb_sys_fops            16384  1 drm_kms_helper
ath                    36864  1 ath10k_core
btintel                24576  1 btusb
intel_cstate           20480  0
syscopyarea            16384  1 drm_kms_helper
sparse_keymap          16384  1 asus_wmi
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
sysfillrect            16384  1 drm_kms_helper
intel_rapl_perf        20480  0
wmi_bmof               16384  0
video                  49152  1 asus_wmi
mac80211              843776  1 ath10k_core
intel_wmi_thunderbolt    20480  0
joydev                 24576  0
input_leds             16384  0
wil6210               397312  0
sysimgblt              16384  1 drm_kms_helper
bluetooth             581632  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_timer              36864  2 snd_seq,snd_pcm
snd                    90112  25 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mxm_wmi                16384  0
libarc4                16384  1 mac80211
cfg80211              704512  4 wil6210,ath,mac80211,ath10k_core
ecdh_generic           16384  1 bluetooth
ecc                    28672  1 ecdh_generic
soundcore              16384  1 snd
mei_me                 40960  0
mei                   106496  1 mei_me
ioatdma                53248  0
mac_hid                16384  0
acpi_tad               16384  0
nf_log_ipv6            16384  5
ip6t_REJECT            16384  1
nf_reject_ipv6         20480  1 ip6t_REJECT
xt_hl                  16384  22
ip6t_rt                20480  3
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
ipt_REJECT             16384  3
nf_reject_ipv4         16384  1 ipt_REJECT
xt_LOG                 20480  10
xt_limit               16384  13
xt_addrtype            16384  4
xt_tcpudp              20480  27
xt_conntrack           16384  17
sch_fq_codel           20480  5
nf_conntrack          139264  3 xt_conntrack,nf_nat,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
libcrc32c              16384  4 nf_conntrack,nf_nat,btrfs,xfs
ip6table_filter        16384  1
parport_pc             40960  0
ip6_tables             32768  55 ip6table_filter,ip6table_nat,ip6table_mangle
ppdev                  24576  0
iptable_filter         16384  1
bpfilter               32768  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
drm                   491520  12 drm_kms_helper,nvidia_drm
ip_tables              32768  11 iptable_filter,iptable_nat,iptable_mangle
x_tables               40960  17 ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,xt_addrtype,xt_CHECKSUM,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6table_mangle,xt_MASQUERADE,ip6t_REJECT,iptable_mangle
autofs4                45056  2
hid_maltron            16384  0
dm_crypt               40960  1
hid_logitech_hidpp     40960  0
hid_logitech_dj        24576  0
hid_generic            16384  0
usbhid                 57344  1 hid_logitech_dj
hid                   131072  6 usbhid,hid_generic,hid_maltron,hid_logitech_dj,hid_logitech_hidpp
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           372736  8
crypto_simd            16384  1 aesni_intel
cryptd                 24576  5 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
nvme                   49152  3
igb                   221184  0
e1000e                258048  0
i2c_i801               32768  0
dca                    16384  2 igb,ioatdma
i2c_algo_bit           16384  1 igb
nvme_core             102400  5 nvme
ahci                   40960  0
libahci                32768  1 ahci
wmi                    32768  4 intel_wmi_thunderbolt,asus_wmi,wmi_bmof,mxm_wmi
              total        used        free      shared  buff/cache   available
Mem:       32555376     3658052    25474992      217808     3422332    28215828
Swap:        999420           0      999420
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/40inputattach suspend suspend:
/usr/lib/pm-utils/sleep.d/40inputattach suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Wed 06 May 2020 10:44:56 AM EDT: performing suspend
/usr/sbin/pm-suspend: 321: echo: echo: I/O error
Wed 06 May 2020 10:44:58 AM EDT: Awake.
Wed 06 May 2020 10:44:58 AM EDT: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/40inputattach resume suspend:
/usr/lib/pm-utils/sleep.d/40inputattach resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Wed 06 May 2020 10:44:59 AM EDT: Finished.
```

---

### Post by ActionParsnip on 2020-05-06
What is the output of:

```

sudo dmidecode -t 1; lsb_release -a; uname -a

```

Thanks

---

### Post by ceojosh24 on 2020-05-06
Here's the dmidecode. One of my friends who runs Linux told me to run an lspci command, and said that it could be the firmware in my Wifi card. Not sure if this code shows that but I'm going to try renaming the firmware.


# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: System manufacturer
    Product Name: System Product Name
    Version: System Version
    Serial Number: System Serial Number
    Wake-up Type: Power Switch
    SKU Number: ASUS_MB_KBLX
    Family: To be filled by O.E.M.


No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
Linux pc 5.4.0-29-generic #33-Ubuntu SMP Wed Apr 29 14:32:27 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ceojosh24 on 2020-05-06
Okay so this is how it was solved. My friend told me to run an lspci code in the terminal code, so I typed in lspci and hit enter. He told me that a wifi card I wasn't using was disabling the suspend. He could tell this because the dmesg command from the first post showed this:

[  961.673716] PM: Device 0000:**02:00.0 **failed to suspend async: error

and the lspci command rendered this: 

00:00.0 Host bridge: Intel Corporation Sky Lake-E DMI3 Registers (rev 04)
00:04.0 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:04.1 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:04.2 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:04.3 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:04.4 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:04.5 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:04.6 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:04.7 System peripheral: Intel Corporation Sky Lake-E CBDMA Registers (rev 04)
00:05.0 System peripheral: Intel Corporation Sky Lake-E MM/Vt-d Configuration Registers (rev 04)
00:05.2 System peripheral: Intel Corporation Sky Lake-E RAS (rev 04)
00:05.4 PIC: Intel Corporation Sky Lake-E IOAPIC (rev 04)
00:08.0 System peripheral: Intel Corporation Sky Lake-E Ubox Registers (rev 04)
00:08.1 Performance counters: Intel Corporation Sky Lake-E Ubox Registers (rev 04)
00:08.2 System peripheral: Intel Corporation Sky Lake-E Ubox Registers (rev 04)
00:14.0 USB controller: Intel Corporation 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller
00:14.2 Signal processing controller: Intel Corporation 200 Series PCH Thermal Subsystem
00:16.0 Communication controller: Intel Corporation 200 Series PCH CSME HECI #1
00:17.0 SATA controller: Intel Corporation 200 Series PCH SATA controller [AHCI mode]
00:1b.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #17 (rev f0)
00:1b.3 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #20 (rev f0)
00:1b.4 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #21 (rev f0)
00:1c.0 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #1 (rev f0)
00:1c.1 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #2 (rev f0)
00:1c.2 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #3 (rev f0)
00:1c.4 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #5 (rev f0)
00:1c.6 PCI bridge: Intel Corporation 200 Series PCH PCI Express Root Port #7 (rev f0)
00:1f.0 ISA bridge: Intel Corporation X299 Chipset LPC/eSPI Controller
00:1f.2 Memory controller: Intel Corporation 200 Series/Z370 Chipset Family Power Management Controller
00:1f.3 Audio device: Intel Corporation 200 Series PCH HD Audio
00:1f.4 SMBus: Intel Corporation 200 Series/Z370 Chipset Family SMBus Controller
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V
**02:00.0 Network controller: Wilocity Ltd. Wil6200 802.11ad Wireless Network Adapter (rev 02)**
03:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
04:00.0 USB controller: ASMedia Technology Inc. ASM2142 USB 3.1 Host Controller

They both had the same PCI address of 02:00.0 to connect the error he was trying to find. So I had to do two things. 1. Rename the firmware file so that the wifi card did not use it, and then go into BIOS and turn off the wifi card. The firmware step probably wasn't necessary, but I'm including it just in case.

In order to find which firmware it was using, I turned on that wifi in the top menu, and then ran a dmesg command to see what firmware the wifi tried to use. It used the wil6210 firmware according to the dmesg command. Then I ran this command:

find /lib/firmware -iname "wil6210"

and found the wil6210.fw file. Then I renamed it using the sudo mv command, where you type in "sudo mv" then drag the file into the terminal, then copy paste that folder address again but end the file with renaming it to something else like .fw to .bk. Look up the sudo mv command if you need more details on renaming.

Then rebooted and went into the BIOS setting. Then went to Advanced - Onboard Devices Configuration - then Disabled Wi-fi 802.11ad controller.

Rebooted again. Tried suspending. Boom. Fans and lights turned off. Normal suspension. Was able to wake up fine too.

---

### Post by ceojosh24 on 2020-05-06
So you need to run an lspci command, and then see which line shows 02:00.0 at the left that lines up with your dmesg showing the error. That will show you which device is giving you the error. Then you need to go into BIOS and disable that device in Advanced - Onboard Devices Configuration. Or if it's a USB device, you need to unplug it. This should solve your problem as it did for me.  

> **rldever said:**
> On 19.10, this also  just started happening for me after performing an update with "Software Updater". Previously suspend was working flawlessly. 

**In an effort at resolution I've tried the following without success:**
```

sudo apt-get update
sudo apt-get upgrade
sudo upduntu-drivers autoinstall
sudo reboot
sudo apt autoremove

```

**system log showing failed suspend errors:**

---

