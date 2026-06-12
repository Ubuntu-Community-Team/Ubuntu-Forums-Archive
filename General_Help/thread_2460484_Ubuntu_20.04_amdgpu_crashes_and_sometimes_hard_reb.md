---
title: "Ubuntu 20.04 amdgpu crashes and sometimes hard reboot is necessary"
date: 2021-04-11
forum: General Help
---

### Post by nemethda on 2021-04-11
Hi all,

I originally had problems with my wireless ([https://ubuntuforums.org/showthread.php?t=2452107&page=3](https://ubuntuforums.org/showthread.php?t=2452107&page=3)) - actually still do - but I was advised to try to resolve the frequent crash of amdgpu that can be seen in my dmesg logs. First of all, I'm using  an Acer Nitro 5 (AN515-43) and the following is the output of inxi:

```
~$ inxi -Fzx
System:    Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.7 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Acer product: Nitro AN515-43 v: V1.08 serial: <filter> 
           Mobo: PK model: Octavia_PKS v: V1.08 serial: <filter> UEFI: Insyde v: 1.08 date: 12/24/2019 
Battery:   ID-1: BAT1 charge: 54.2 Wh condition: 54.2/57.5 Wh (94%) model: LG 0x41,0x50,0x31,0x38,0x45,0x38,0x0098 
           status: Full 
           Device-1: hidpp_battery_0 model: Logitech Wireless Mouse PID:1020 charge: 55% (should be ignored) 
           status: Discharging 
CPU:       Topology: Quad Core model: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx bits: 64 type: MT MCP arch: Zen+ rev: 1 
           L2 cache: 2048 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 36730 
           Speed: 1186 MHz min/max: 1400/2300 MHz Core speeds (MHz): 1: 1166 2: 1199 3: 1452 4: 1603 5: 1205 6: 1187 7: 1361 
           8: 1396 
Graphics:  Device-1: NVIDIA GP107M [GeForce GTX 1050 Ti Mobile] vendor: Acer Incorporated ALI driver: nvidia v: 450.102.04 
           bus ID: 01:00.0 
           Device-2: Advanced Micro Devices [AMD/ATI] Picasso vendor: Acer Incorporated ALI driver: amdgpu v: kernel 
           bus ID: 05:00.0 
           Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati,nvidia unloaded: fbdev,modesetting,nouveau,vesa 
           resolution: 1920x1080~60Hz, 1920x1080~120Hz 
           OpenGL: renderer: GeForce GTX 1050 Ti/PCIe/SSE2 v: 4.6.0 NVIDIA 450.102.04 direct render: Yes 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio vendor: Acer Incorporated ALI 
           driver: snd_hda_intel v: kernel bus ID: 05:00.1 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio vendor: Acer Incorporated ALI driver: snd_hda_intel 
           v: kernel bus ID: 05:00.6 
           Sound Server: ALSA v: k5.8.0-48-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Acer Incorporated ALI driver: r8169 
           v: kernel port: 2000 bus ID: 03:00.0 
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter vendor: Lite-On driver: ath10k_pci v: kernel 
           port: 2000 bus ID: 04:00.0 
           IF: wlp4s0 state: down mac: <filter> 
Drives:    Local Storage: total: 1.14 TiB used: 51.24 GiB (4.4%) 
           ID-1: /dev/nvme0n1 vendor: SK Hynix model: HFM256GDJTNG-8310A size: 238.47 GiB 
           ID-2: /dev/sda vendor: Seagate model: ST1000LM049-2GH172 size: 931.51 GiB temp: 40 C 
Partition: ID-1: / size: 233.24 GiB used: 51.24 GiB (22.0%) fs: ext4 dev: /dev/nvme0n1p2 
Sensors:   System Temperatures: cpu: 68.4 C mobo: N/A 
           Fan Speeds (RPM): N/A 
           GPU: device: nvidia screen: :1.0 temp: 60 C device: amdgpu temp: 68 C 
Info:      Processes: 367 Uptime: 16m Memory: 13.67 GiB used: 3.12 GiB (22.8%) Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 
           Shell: bash v: 5.0.17 inxi: 3.0.38
```

The type of error I can see in dmesg is the below:
```
~$dmesg -T
[v ápr 11 18:24:21 2021] ------------[ cut here ]------------
[v ápr 11 18:24:21 2021] WARNING: CPU: 1 PID: 796 at drivers/gpu/drm/amd/amdgpu/../display/dc/core/dc_link.c:2546 dc_link_set_backlight_level+0x92/0xf0 [amdgpu]
[v ápr 11 18:24:21 2021] Modules linked in: amd64_edac_mod(-) fjes(-) nvidia_uvm(OE) snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi nvidia_drm(POE) edac_mce_amd snd_hda_intel nvidia_modeset(POE) snd_intel_dspcfg snd_hda_codec kvm_amd snd_hda_core kvm snd_hwdep snd_pcm crct10dif_pclmul ghash_clmulni_intel uvcvideo aesni_intel ath10k_pci crypto_simd snd_seq_midi videobuf2_vmalloc nvidia(POE) cryptd videobuf2_memops ath10k_core snd_seq_midi_event videobuf2_v4l2 glue_helper btusb btrtl videobuf2_common nls_iso8859_1 btbcm amdgpu rapl ath btintel snd_rawmidi videodev joydev bluetooth mc mac80211 snd_seq snd_seq_device iommu_v2 ecdh_generic ecc gpu_sched snd_timer ttm input_leds hid_multitouch serio_raw efi_pstore drm_kms_helper snd cfg80211 acer_wmi cec wmi_bmof sparse_keymap rc_core i2c_algo_bit fb_sys_fops syscopyarea sysfillrect sysimgblt soundcore k10temp ccp libarc4 mac_hid acer_wireless sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4
[v ápr 11 18:24:21 2021]  hid_logitech_hidpp hid_logitech_dj usbhid hid_generic nvme crc32_pclmul ahci xhci_pci libahci r8169 i2c_piix4 xhci_pci_renesas nvme_core realtek i2c_hid hid video wmi
[v ápr 11 18:24:21 2021] CPU: 1 PID: 796 Comm: systemd-backlig Tainted: P           OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[v ápr 11 18:24:21 2021] Hardware name: Acer Nitro AN515-43/Octavia_PKS, BIOS V1.08 12/24/2019
[v ápr 11 18:24:21 2021] RIP: 0010:dc_link_set_backlight_level+0x92/0xf0 [amdgpu]
[v ápr 11 18:24:21 2021] Code: 30 03 00 00 31 c0 48 8d 96 c0 01 00 00 48 8b 0a 48 85 c9 74 06 4c 3b 61 08 74 22 83 c0 01 48 81 c2 c8 04 00 00 83 f8 06 75 e3 <0f> 0b 45 31 ff 5b 44 89 f8 41 5c 41 5d 41 5e 41 5f 5d c3 48 98 48
[v ápr 11 18:24:21 2021] RSP: 0018:ffffaac940a83d98 EFLAGS: 00010246
[v ápr 11 18:24:21 2021] RAX: 0000000000000006 RBX: ffff979c1a860000 RCX: 0000000000000000
[v ápr 11 18:24:21 2021] RDX: ffff979c14b61e70 RSI: ffff979c14b60000 RDI: 0000000000000004
[v ápr 11 18:24:21 2021] RBP: ffffaac940a83dc0 R08: 000000000000008b R09: 0000000000000003
[v ápr 11 18:24:21 2021] R10: 000000000000000a R11: f000000000000000 R12: ffff979c128a2400
[v ápr 11 18:24:21 2021] R13: 0000000000000000 R14: 00000000000094ad R15: 0000000000009401
[v ápr 11 18:24:21 2021] FS:  00007fd5a67fa980(0000) GS:ffff979c20a40000(0000) knlGS:0000000000000000
[v ápr 11 18:24:21 2021] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[v ápr 11 18:24:21 2021] CR2: 00007fd5a74fb2e3 CR3: 00000003d3078000 CR4: 00000000003406e0
[v ápr 11 18:24:21 2021] Call Trace:
[v ápr 11 18:24:21 2021]  amdgpu_dm_backlight_update_status+0xb9/0xd0 [amdgpu]
[v ápr 11 18:24:21 2021]  backlight_device_set_brightness+0x6b/0xd0
[v ápr 11 18:24:21 2021]  brightness_store+0x61/0x80
[v ápr 11 18:24:21 2021]  dev_attr_store+0x17/0x30
[v ápr 11 18:24:21 2021]  sysfs_kf_write+0x3e/0x50
[v ápr 11 18:24:21 2021]  kernfs_fop_write+0xda/0x1b0
[v ápr 11 18:24:21 2021]  vfs_write+0xc9/0x200
[v ápr 11 18:24:21 2021]  ksys_write+0x67/0xe0
[v ápr 11 18:24:21 2021]  __x64_sys_write+0x1a/0x20
[v ápr 11 18:24:21 2021]  do_syscall_64+0x49/0xc0
[v ápr 11 18:24:21 2021]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[v ápr 11 18:24:21 2021] RIP: 0033:0x7fd5a76a81e7
[v ápr 11 18:24:21 2021] Code: 64 89 02 48 c7 c0 ff ff ff ff eb bb 0f 1f 80 00 00 00 00 f3 0f 1e fa 64 8b 04 25 18 00 00 00 85 c0 75 10 b8 01 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 51 c3 48 83 ec 28 48 89 54 24 18 48 89 74 24
[v ápr 11 18:24:21 2021] RSP: 002b:00007ffdbd2019e8 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
[v ápr 11 18:24:21 2021] RAX: ffffffffffffffda RBX: 0000000000000004 RCX: 00007fd5a76a81e7
[v ápr 11 18:24:21 2021] RDX: 0000000000000004 RSI: 00007ffdbd201aa0 RDI: 0000000000000004
[v ápr 11 18:24:21 2021] RBP: 00007ffdbd201aa0 R08: 0000000000000004 R09: 0000000000000000
[v ápr 11 18:24:21 2021] R10: 0000000000000000 R11: 0000000000000246 R12: 0000000000000004
[v ápr 11 18:24:21 2021] R13: 00005579bfb862d0 R14: 0000000000000004 R15: 00007fd5a77838a0
[v ápr 11 18:24:21 2021] ---[ end trace 00250ade6ee3aba2 ]---
```

Most of the times these errors are in the log after I started the laptop, but not all the time. So far I wasn't able to attribute this to anything specific. I think one side effect of the above is that the screen brightness is always set to minimum, regardless that I always set it to something else after startup. Maybe this is what the below log message means too (but I'm just guessing):

```
daniel@daniel-Nitro-AN515-43:~$ journalctl -b | grep brightness
ápr 11 18:24:22 daniel-Nitro-AN515-43 kernel:  backlight_device_set_brightness+0x6b/0xd0
ápr 11 18:24:22 daniel-Nitro-AN515-43 kernel:  brightness_store+0x61/0x80
ápr 11 18:24:22 daniel-Nitro-AN515-43 systemd-backlight[796]: amdgpu_bl0: Failed to write system 'brightness' attribute: No such device or address

```

My biggest problem though is that recently I often got to a stage where my laptop becomes totally unresponsive. Usually it starts after my WiFi connection is lost, than I try to restart the network-manager which just hangs in the terminal and in the GUI as well. This always had to end with a hard reboot.

I've seen many similar posts like this [https://gitlab.freedesktop.org/drm/amd/-/issues/1251](https://gitlab.freedesktop.org/drm/amd/-/issues/1251) and [https://ubuntuforums.org/showthread.php?t=2459895&p=14028901#post14028901](https://ubuntuforums.org/showthread.php?t=2459895&p=14028901#post14028901) but all  those cases are a little bit different. Mostly, that I'm able to suspend the laptop right now (although oddly that wasn't working for me either in the past, just like in those forums).

Following suggestions in [this post]("https://bbs.archlinux.org/viewtopic.php?id=262456") (and as I was advised by chilli555 as well in my other issue) I already did the below uninstall:
```
[COLOR=#000000][FONT=&amp]sudo apt purge  xserver-xorg-video-intel[/FONT][/COLOR]
```

Secure boot is also disabled now for me as I read somewhere that could be a problem too. I can still see the crash logs in dmesg.

Finally if that helps, I can confirm that amdgpu modules are loaded (and not radeon):
```
~$ lsmod | grep radeon
~$ lsmod | grep amdgpu
amdgpu               5214208  12
iommu_v2               20480  1 amdgpu
gpu_sched              36864  1 amdgpu
ttm                   102400  1 amdgpu
drm_kms_helper        217088  2 amdgpu,nvidia_drm
i2c_algo_bit           16384  1 amdgpu
drm                   552960  17 gpu_sched,drm_kms_helper,amdgpu,nvidia_drm,ttm

```


Can anyone please take a look and advise what could I try to fix the above issue? Please let me know if there's any more info needed and sorry if included to much useless information too..

---

### Post by CelticWarrior on 2021-04-11
Start with updating the UEFI.

---

### Post by nemethda on 2021-04-11
Thanks for replying! Sorry, I've been trying to find specific instructions how to do this for my model but with no luck. I downloaded the latest BIOS, backed up [COLOR=#333333][FONT=Ubuntu]/boot/efi/EFI/. I copied .exe file to a USB but I'm not actually sure I'll be able to use it as a flash drive. 

I looked at this guide: [/FONT][/COLOR]https://help.ubuntu.com/community/BIOSUpdate, but the laptop I have is not listed in the Acer section (and the link that is has doesn't work anyway). Would you recommend point number 6 from the 'Vendor independent methods'?

In BIOS I do see an option called 'Select an UEFI file as trusted for executing' - could this option work? I would really appreciate some guidance.

Thanks very much!
Daniel

---

### Post by nemethda on 2021-04-16
Hello,

So far I haven't been able to figure out a way how to do the UEFI update. The "Flash BIOS upgrade" is not supported by my machine. I've created a bootable FreeDos USB and copied the executable file as well, but I'm unable to boot from the USB stick. My laptop's BIOS only allows UEFI mode so I cannot switch to the legacy mode. Could anyone please advise what should I do so that the USB stick is recognized as a boot option? Should I raise this as separate question?

Many thanks
Daniel

---

