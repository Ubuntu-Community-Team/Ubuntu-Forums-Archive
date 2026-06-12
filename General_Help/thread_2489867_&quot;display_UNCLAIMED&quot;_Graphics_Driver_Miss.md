---
title: "&quot;display UNCLAIMED&quot; Graphics Driver Missing?"
date: 2023-08-12
forum: General Help
---

### Post by treadmill855 on 2023-08-12
So I was watching an episode of Avatar on my desktop using Kodi and the video output suddenly stopped and my monitor said "no input". The computer has been running fine for about a year up until this point. After the video cut out, I could SSH into the machine though, and I rebooted it to see what would happen. After reboot, the display was just blank, although the monitor wasn't displaying "no input" anymore. I also could see the splash screen for the motherboard so I know the cables etc. are working properly. And, even with the blank output, I can still SSH into the machine and everything besides the display seems to be working properly.

I found another forum thread that adding the following parameters to grub might help: 

```
GRUB_CMDLINE_LINUX="quiet splash nomodeset"
```

After updating grub and rebooting, the machine does output the normal desktop, however it seems like the correct AMD display driver is not loading. Video playback is possible but it is stuttering and slow like a generic video driver is loaded, not the correct AMD one. I will also note I am using an Intel processor which has integrated video, however output is through a discrete AMD card. I only mention that because I have had problems getting the computer to output video using the AMD card in the past as it seemed to "default" to the Intel graphics for some reason. But I don't think that is the issue here. 

I have tried a few other things as well, being sure to change my grub configuration back to default each time, and every time I change it back it just goes back to displaying a blank output. Reinstalling *linux-firmware* has no effect. Same with reinstalling *xserver-xorg-video-amdgpu*. I also tried to add *amdgpu* to */etc/modules-load.d/modules.conf*. Trying to load the amdgpu driver manually outputs this error message:

```
$ sudo modprobe amdgpu
modprobe: ERROR: could not insert 'amdgpu': Invalid argument
```

The information about the video driver still says that it is "Unclaimed": 

```
$ sudo lshw -C display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:df900000-df9fffff memory:c0000-dffff
  *-graphics
       product: EFI VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=2560,1440
```

And here is the information about my computer: 

```
$ lspci -k | grep -iEA5 'vga|3d'
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 743f (rev c1)
        Subsystem: Gigabyte Technology Co., Ltd Device 2402
        Kernel modules: amdgpu
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Navi 21 HDMI Audio [Radeon RX 6800/6800 XT / 6900 XT]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Navi 21 HDMI Audio [Radeon RX 6800/6800 XT / 6900 XT]
        Kernel driver in use: snd_hda_intel
```

```
$ sudo dmesg | grep -i 'amdgpu\|radeon'
$ sudo lsmod | grep -i 'amd\|radeon'
```

(both commands output nothing)

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy
```

```
$ echo $XDG_SESSION_TYPE
x11
```

```
$ uname -r
6.2.0-26-generic
```

---

### Post by MAFoElffen on 2023-08-12
Please refer to this post of mine that goes over the steps of using the opensource amdgpu driver: [https://ubuntuforums.org/showthread.php?t=2489555&p=14152990#post14152990](https://ubuntuforums.org/showthread.php?t=2489555&p=14152990#post14152990)

Note that the "video=..." part of that is optional, but that setting the KMS in the kernel does help. The other three boot parameters preceding that sets up the kernel, to use the amdgpu kernel module.

In that post, if the lsmod command comes back with nothing, then it means that it is not loaded. And it should be.

If you try to load it and it fails, please, instead of just looking in dmesg, also look in syslog and journalctl for the earch term of 'amdgpu' for clues in why your your system does nto want to load it.

Please stay in the loop with responses, and I will follow this thread to try to help you with this. If you have any question, please feel free to ask.

---

### Post by treadmill855 on 2023-08-12
If I go to the Grub2 boot menu and edit, and follow the instructions below, I still get just a gray/blank output, the same as I was when the problem started. 

```
Press the <E> key. <Arrow-Down to the line that starts with the  word "linux". <Arrow-Right> until you get to the words "quiet  splash" Delete the word "quiet" and replace with "---" (3 dashes).  <Arrow-Right until after "splash"...

Add a <Space> after the word "splash, then type in the text  "radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1  video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank " (without the  quotes). Then press <Cntrl><X>. See if it boots and test.
```

The output of *$ lsmod | grep amdgpu *shows the following though: 
```
amdgpu              14491648  0
iommu_v2               24576  1 amdgpu
drm_buddy              20480  1 amdgpu
gpu_sched              61440  1 amdgpu
drm_ttm_helper         16384  1 amdgpu
ttm                   110592  2 amdgpu,drm_ttm_helper
drm_display_helper    212992  1 amdgpu
drm_kms_helper        249856  2 drm_display_helper,amdgpu
drm                   696320  7 gpu_sched,drm_kms_helper,drm_display_helper,drm_buddy,amdgpu,drm_ttm_helper,ttm
i2c_algo_bit           16384  2 igb,amdgpu
video                  73728  1 amdgpu
```

Does this mean the module is loaded? 

I also checked syslog, and while looking for mentions of amdgpu outputs a text file that is quite long, I think some relevant parts may be here: 

```
Aug 12 17:27:59 server kernel: [    5.074794] [drm] amdgpu: 4080M of VRAM memory ready
Aug 12 17:27:59 server kernel: [    5.074796] [drm] amdgpu: 15995M of GTT memory ready.
Aug 12 17:27:59 server kernel: [    5.086668] amdgpu 0000:03:00.0: amdgpu: PSP runtime database doesn't exist
Aug 12 17:27:59 server kernel: [    5.086672] amdgpu 0000:03:00.0: amdgpu: PSP runtime database doesn't exist
Aug 12 17:27:59 server kernel: [    6.421827] amdgpu 0000:03:00.0: amdgpu: STB initialized to 2048 entries
Aug 12 17:27:59 server kernel: [    6.427760] amdgpu 0000:03:00.0: amdgpu: Will use PSP to load VCN firmware
Aug 12 17:27:59 server kernel: [    6.585352] amdgpu 0000:03:00.0: amdgpu: RAS: optional ras ta ucode is not available
Aug 12 17:27:59 server kernel: [    6.600841] amdgpu 0000:03:00.0: amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available
Aug 12 17:27:59 server kernel: [    6.600865] amdgpu 0000:03:00.0: amdgpu: smu driver if version = 0x0000000d, smu fw if version = 0x0000000f, smu fw program = 0, version = 0x00491a00 (73.26.0)
Aug 12 17:27:59 server kernel: [    6.600869] amdgpu 0000:03:00.0: amdgpu: SMU driver if version not matched
Aug 12 17:27:59 server kernel: [    6.600895] amdgpu 0000:03:00.0: amdgpu: use vbios provided pptable
Aug 12 17:28:02 server kernel: [    9.700686] amdgpu 0000:03:00.0: amdgpu: SMU: I'm not done with your previous command: SMN_C2PMSG_66:0x00000006 SMN_C2PMSG_82:0x00000000
Aug 12 17:28:02 server kernel: [    9.700694] amdgpu 0000:03:00.0: amdgpu: Failed to enable requested dpm features!
Aug 12 17:28:02 server kernel: [    9.700697] amdgpu 0000:03:00.0: amdgpu: Failed to setup smc hw!
Aug 12 17:28:02 server kernel: [    9.700700] [drm:amdgpu_device_ip_init [amdgpu]] *ERROR* hw_init of IP block <smu> failed -62
Aug 12 17:28:02 server kernel: [    9.700960] amdgpu 0000:03:00.0: amdgpu: amdgpu_device_ip_init failed
Aug 12 17:28:02 server kernel: [    9.700963] amdgpu 0000:03:00.0: amdgpu: Fatal error during GPU init
Aug 12 17:28:02 server kernel: [    9.700975] amdgpu 0000:03:00.0: amdgpu: amdgpu: finishing device.
Aug 12 17:28:02 server kernel: [    9.701119] WARNING: CPU: 7 PID: 384 at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.701314] Modules linked in: nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep intel_rapl_msr intel_rapl_common amdgpu(+) intel_tcc_cooling snd_soc_avs snd_hda_codec_realtek snd_soc_hda_codec snd_hda_codec_generic snd_hda_ext_core ledtrig_audio snd_soc_core snd_hda_codec_hdmi snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec snd_hda_core x86_pkg_temp_thermal snd_hwdep intel_powerclamp snd_pcm coretemp iommu_v2 kvm_intel drm_buddy snd_seq_midi iwlmvm snd_seq_midi_event gpu_sched binfmt_misc drm_ttm_helper snd_rawmidi kvm ttm mac80211 btusb irqbypass drm_display_helper crct10dif_pclmul nls_iso8859_1 btrtl polyval_clmulni snd_seq libarc4 polyval_generic cec ghash_clmulni_intel btbcm btintel sha512_ssse3 rc_core snd_seq_device aesni_intel btmtk iwlwifi snd_timer crypto_simd drm_kms_helper cryptd bluetooth syscopyarea rapl snd sysfillrect ecdh_generic intel_cstate cfg80211 intel_wmi_thunderbolt ee1004 mxm_wmi
Aug 12 17:28:02 server kernel: [    9.701387] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.701586]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.701742]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.701894]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.702046]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.702197]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.702375]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.702560]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 12 17:28:02 server kernel: [    9.702826] WARNING: CPU: 7 PID: 384 at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0 [amdgpu]
```

I don't see anything in journalctl though: 

```
$ journalctl -k -t amdgpu
-- No entries --
```

---

### Post by MAFoElffen on 2023-08-12
Your problem on your machine. seems to start from this:
```

Aug 12 17:27:59 server kernel: [    6.600865] amdgpu 0000:03:00.0: amdgpu: smu driver if version = 0x0000000d, smu fw if version = 0x0000000f, smu fw program = 0, version = 0x00491a00 (73.26.0)

```
Which the firmware should come from package 'linux-firmware'... which for 22.04, should include these files
```

/lib/firmware/amdgpu/aldebaran_mec.bin
/lib/firmware/amdgpu/aldebaran_mec2.bin
/lib/firmware/amdgpu/aldebaran_rlc.bin
/lib/firmware/amdgpu/aldebaran_sdma.bin
/lib/firmware/amdgpu/aldebaran_smc.bin
/lib/firmware/amdgpu/aldebaran_sos.bin
/lib/firmware/amdgpu/aldebaran_ta.bin
/lib/firmware/amdgpu/aldebaran_vcn.bin
/lib/firmware/amdgpu/arcturus_asd.bin
/lib/firmware/amdgpu/arcturus_gpu_info.bin
/lib/firmware/amdgpu/arcturus_mec.bin
/lib/firmware/amdgpu/arcturus_mec2.bin
/lib/firmware/amdgpu/arcturus_rlc.bin
/lib/firmware/amdgpu/arcturus_sdma.bin
/lib/firmware/amdgpu/arcturus_smc.bin
/lib/firmware/amdgpu/arcturus_sos.bin
/lib/firmware/amdgpu/arcturus_ta.bin
/lib/firmware/amdgpu/arcturus_vcn.bin
/lib/firmware/amdgpu/banks_k_2_smc.bin
/lib/firmware/amdgpu/beige_goby_ce.bin
/lib/firmware/amdgpu/beige_goby_dmcub.bin
/lib/firmware/amdgpu/beige_goby_me.bin
/lib/firmware/amdgpu/beige_goby_mec.bin
/lib/firmware/amdgpu/beige_goby_mec2.bin
/lib/firmware/amdgpu/beige_goby_pfp.bin
/lib/firmware/amdgpu/beige_goby_rlc.bin
/lib/firmware/amdgpu/beige_goby_sdma.bin
/lib/firmware/amdgpu/beige_goby_smc.bin
/lib/firmware/amdgpu/beige_goby_sos.bin
/lib/firmware/amdgpu/beige_goby_ta.bin
/lib/firmware/amdgpu/beige_goby_vcn.bin
/lib/firmware/amdgpu/bonaire_ce.bin
/lib/firmware/amdgpu/bonaire_k_smc.bin
/lib/firmware/amdgpu/bonaire_mc.bin
/lib/firmware/amdgpu/bonaire_me.bin
/lib/firmware/amdgpu/bonaire_mec.bin
/lib/firmware/amdgpu/bonaire_pfp.bin
/lib/firmware/amdgpu/bonaire_rlc.bin
/lib/firmware/amdgpu/bonaire_sdma.bin
/lib/firmware/amdgpu/bonaire_sdma1.bin
/lib/firmware/amdgpu/bonaire_smc.bin
/lib/firmware/amdgpu/bonaire_uvd.bin
/lib/firmware/amdgpu/bonaire_vce.bin
/lib/firmware/amdgpu/carrizo_ce.bin
/lib/firmware/amdgpu/carrizo_me.bin
/lib/firmware/amdgpu/carrizo_mec.bin
/lib/firmware/amdgpu/carrizo_mec2.bin
/lib/firmware/amdgpu/carrizo_pfp.bin
/lib/firmware/amdgpu/carrizo_rlc.bin
/lib/firmware/amdgpu/carrizo_sdma.bin
/lib/firmware/amdgpu/carrizo_sdma1.bin
/lib/firmware/amdgpu/carrizo_uvd.bin
/lib/firmware/amdgpu/carrizo_vce.bin
/lib/firmware/amdgpu/cyan_skillfish2_ce.bin
/lib/firmware/amdgpu/cyan_skillfish2_me.bin
/lib/firmware/amdgpu/cyan_skillfish2_mec.bin
/lib/firmware/amdgpu/cyan_skillfish2_mec2.bin
/lib/firmware/amdgpu/cyan_skillfish2_pfp.bin
/lib/firmware/amdgpu/cyan_skillfish2_rlc.bin
/lib/firmware/amdgpu/cyan_skillfish2_sdma.bin
/lib/firmware/amdgpu/cyan_skillfish2_sdma1.bin
/lib/firmware/amdgpu/dcn_3_1_6_dmcub.bin
/lib/firmware/amdgpu/dimgrey_cavefish_ce.bin
/lib/firmware/amdgpu/dimgrey_cavefish_dmcub.bin
/lib/firmware/amdgpu/dimgrey_cavefish_me.bin
/lib/firmware/amdgpu/dimgrey_cavefish_mec.bin
/lib/firmware/amdgpu/dimgrey_cavefish_mec2.bin
/lib/firmware/amdgpu/dimgrey_cavefish_pfp.bin
/lib/firmware/amdgpu/dimgrey_cavefish_rlc.bin
/lib/firmware/amdgpu/dimgrey_cavefish_sdma.bin
/lib/firmware/amdgpu/dimgrey_cavefish_smc.bin
/lib/firmware/amdgpu/dimgrey_cavefish_sos.bin
/lib/firmware/amdgpu/dimgrey_cavefish_ta.bin
/lib/firmware/amdgpu/dimgrey_cavefish_vcn.bin
/lib/firmware/amdgpu/fiji_ce.bin
/lib/firmware/amdgpu/fiji_mc.bin
/lib/firmware/amdgpu/fiji_me.bin
/lib/firmware/amdgpu/fiji_mec.bin
/lib/firmware/amdgpu/fiji_mec2.bin
/lib/firmware/amdgpu/fiji_pfp.bin
/lib/firmware/amdgpu/fiji_rlc.bin
/lib/firmware/amdgpu/fiji_sdma.bin
/lib/firmware/amdgpu/fiji_sdma1.bin
/lib/firmware/amdgpu/fiji_smc.bin
/lib/firmware/amdgpu/fiji_uvd.bin
/lib/firmware/amdgpu/fiji_vce.bin
/lib/firmware/amdgpu/gc_10_3_7_ce.bin
/lib/firmware/amdgpu/gc_10_3_7_me.bin
/lib/firmware/amdgpu/gc_10_3_7_mec.bin
/lib/firmware/amdgpu/gc_10_3_7_mec2.bin
/lib/firmware/amdgpu/gc_10_3_7_pfp.bin
/lib/firmware/amdgpu/gc_10_3_7_rlc.bin
/lib/firmware/amdgpu/green_sardine_asd.bin
/lib/firmware/amdgpu/green_sardine_ce.bin
/lib/firmware/amdgpu/green_sardine_dmcub.bin
/lib/firmware/amdgpu/green_sardine_me.bin
/lib/firmware/amdgpu/green_sardine_mec.bin
/lib/firmware/amdgpu/green_sardine_mec2.bin
/lib/firmware/amdgpu/green_sardine_pfp.bin
/lib/firmware/amdgpu/green_sardine_rlc.bin
/lib/firmware/amdgpu/green_sardine_sdma.bin
/lib/firmware/amdgpu/green_sardine_ta.bin
/lib/firmware/amdgpu/green_sardine_vcn.bin
/lib/firmware/amdgpu/hainan_ce.bin
/lib/firmware/amdgpu/hainan_k_smc.bin
/lib/firmware/amdgpu/hainan_mc.bin
/lib/firmware/amdgpu/hainan_me.bin
/lib/firmware/amdgpu/hainan_pfp.bin
/lib/firmware/amdgpu/hainan_rlc.bin
/lib/firmware/amdgpu/hainan_smc.bin
/lib/firmware/amdgpu/hawaii_ce.bin
/lib/firmware/amdgpu/hawaii_k_smc.bin
/lib/firmware/amdgpu/hawaii_mc.bin
/lib/firmware/amdgpu/hawaii_me.bin
/lib/firmware/amdgpu/hawaii_mec.bin
/lib/firmware/amdgpu/hawaii_pfp.bin
/lib/firmware/amdgpu/hawaii_rlc.bin
/lib/firmware/amdgpu/hawaii_sdma.bin
/lib/firmware/amdgpu/hawaii_sdma1.bin
/lib/firmware/amdgpu/hawaii_smc.bin
/lib/firmware/amdgpu/hawaii_uvd.bin
/lib/firmware/amdgpu/hawaii_vce.bin
/lib/firmware/amdgpu/kabini_ce.bin
/lib/firmware/amdgpu/kabini_me.bin
/lib/firmware/amdgpu/kabini_mec.bin
/lib/firmware/amdgpu/kabini_pfp.bin
/lib/firmware/amdgpu/kabini_rlc.bin
/lib/firmware/amdgpu/kabini_sdma.bin
/lib/firmware/amdgpu/kabini_sdma1.bin
/lib/firmware/amdgpu/kabini_uvd.bin
/lib/firmware/amdgpu/kabini_vce.bin
/lib/firmware/amdgpu/kaveri_ce.bin
/lib/firmware/amdgpu/kaveri_me.bin
/lib/firmware/amdgpu/kaveri_mec.bin
/lib/firmware/amdgpu/kaveri_mec2.bin
/lib/firmware/amdgpu/kaveri_pfp.bin
/lib/firmware/amdgpu/kaveri_rlc.bin
/lib/firmware/amdgpu/kaveri_sdma.bin
/lib/firmware/amdgpu/kaveri_sdma1.bin
/lib/firmware/amdgpu/kaveri_uvd.bin
/lib/firmware/amdgpu/kaveri_vce.bin
/lib/firmware/amdgpu/mullins_ce.bin
/lib/firmware/amdgpu/mullins_me.bin
/lib/firmware/amdgpu/mullins_mec.bin
/lib/firmware/amdgpu/mullins_pfp.bin
/lib/firmware/amdgpu/mullins_rlc.bin
/lib/firmware/amdgpu/mullins_sdma.bin
/lib/firmware/amdgpu/mullins_sdma1.bin
/lib/firmware/amdgpu/mullins_uvd.bin
/lib/firmware/amdgpu/mullins_vce.bin
/lib/firmware/amdgpu/navi10_asd.bin
/lib/firmware/amdgpu/navi10_ce.bin
/lib/firmware/amdgpu/navi10_gpu_info.bin
/lib/firmware/amdgpu/navi10_me.bin
/lib/firmware/amdgpu/navi10_mec.bin
/lib/firmware/amdgpu/navi10_mec2.bin
/lib/firmware/amdgpu/navi10_pfp.bin
/lib/firmware/amdgpu/navi10_rlc.bin
/lib/firmware/amdgpu/navi10_sdma.bin
/lib/firmware/amdgpu/navi10_sdma1.bin
/lib/firmware/amdgpu/navi10_smc.bin
/lib/firmware/amdgpu/navi10_sos.bin
/lib/firmware/amdgpu/navi10_ta.bin
/lib/firmware/amdgpu/navi10_vcn.bin
/lib/firmware/amdgpu/navi12_asd.bin
/lib/firmware/amdgpu/navi12_ce.bin
/lib/firmware/amdgpu/navi12_dmcu.bin
/lib/firmware/amdgpu/navi12_gpu_info.bin
/lib/firmware/amdgpu/navi12_me.bin
/lib/firmware/amdgpu/navi12_mec.bin
/lib/firmware/amdgpu/navi12_mec2.bin
/lib/firmware/amdgpu/navi12_pfp.bin
/lib/firmware/amdgpu/navi12_rlc.bin
/lib/firmware/amdgpu/navi12_sdma.bin
/lib/firmware/amdgpu/navi12_sdma1.bin
/lib/firmware/amdgpu/navi12_smc.bin
/lib/firmware/amdgpu/navi12_sos.bin
/lib/firmware/amdgpu/navi12_ta.bin
/lib/firmware/amdgpu/navi12_vcn.bin
/lib/firmware/amdgpu/navi14_asd.bin
/lib/firmware/amdgpu/navi14_ce.bin
/lib/firmware/amdgpu/navi14_ce_wks.bin
/lib/firmware/amdgpu/navi14_gpu_info.bin
/lib/firmware/amdgpu/navi14_me.bin
/lib/firmware/amdgpu/navi14_me_wks.bin
/lib/firmware/amdgpu/navi14_mec.bin
/lib/firmware/amdgpu/navi14_mec2.bin
/lib/firmware/amdgpu/navi14_mec2_wks.bin
/lib/firmware/amdgpu/navi14_mec_wks.bin
/lib/firmware/amdgpu/navi14_pfp.bin
/lib/firmware/amdgpu/navi14_pfp_wks.bin
/lib/firmware/amdgpu/navi14_rlc.bin
/lib/firmware/amdgpu/navi14_sdma.bin
/lib/firmware/amdgpu/navi14_sdma1.bin
/lib/firmware/amdgpu/navi14_smc.bin
/lib/firmware/amdgpu/navi14_sos.bin
/lib/firmware/amdgpu/navi14_ta.bin
/lib/firmware/amdgpu/navi14_vcn.bin
/lib/firmware/amdgpu/navy_flounder_ce.bin
/lib/firmware/amdgpu/navy_flounder_dmcub.bin
/lib/firmware/amdgpu/navy_flounder_me.bin
/lib/firmware/amdgpu/navy_flounder_mec.bin
/lib/firmware/amdgpu/navy_flounder_mec2.bin
/lib/firmware/amdgpu/navy_flounder_pfp.bin
/lib/firmware/amdgpu/navy_flounder_rlc.bin
/lib/firmware/amdgpu/navy_flounder_sdma.bin
/lib/firmware/amdgpu/navy_flounder_smc.bin
/lib/firmware/amdgpu/navy_flounder_sos.bin
/lib/firmware/amdgpu/navy_flounder_ta.bin
/lib/firmware/amdgpu/navy_flounder_vcn.bin
/lib/firmware/amdgpu/oland_ce.bin
/lib/firmware/amdgpu/oland_k_smc.bin
/lib/firmware/amdgpu/oland_mc.bin
/lib/firmware/amdgpu/oland_me.bin
/lib/firmware/amdgpu/oland_pfp.bin
/lib/firmware/amdgpu/oland_rlc.bin
/lib/firmware/amdgpu/oland_smc.bin
/lib/firmware/amdgpu/oland_uvd.bin
/lib/firmware/amdgpu/picasso_asd.bin
/lib/firmware/amdgpu/picasso_ce.bin
/lib/firmware/amdgpu/picasso_gpu_info.bin
/lib/firmware/amdgpu/picasso_me.bin
/lib/firmware/amdgpu/picasso_mec.bin
/lib/firmware/amdgpu/picasso_mec2.bin
/lib/firmware/amdgpu/picasso_pfp.bin
/lib/firmware/amdgpu/picasso_rlc.bin
/lib/firmware/amdgpu/picasso_rlc_am4.bin
/lib/firmware/amdgpu/picasso_sdma.bin
/lib/firmware/amdgpu/picasso_ta.bin
/lib/firmware/amdgpu/picasso_vcn.bin
/lib/firmware/amdgpu/pitcairn_ce.bin
/lib/firmware/amdgpu/pitcairn_k_smc.bin
/lib/firmware/amdgpu/pitcairn_mc.bin
/lib/firmware/amdgpu/pitcairn_me.bin
/lib/firmware/amdgpu/pitcairn_pfp.bin
/lib/firmware/amdgpu/pitcairn_rlc.bin
/lib/firmware/amdgpu/pitcairn_smc.bin
/lib/firmware/amdgpu/pitcairn_uvd.bin
/lib/firmware/amdgpu/polaris10_ce.bin
/lib/firmware/amdgpu/polaris10_ce_2.bin
/lib/firmware/amdgpu/polaris10_k2_smc.bin
/lib/firmware/amdgpu/polaris10_k_mc.bin
/lib/firmware/amdgpu/polaris10_k_smc.bin
/lib/firmware/amdgpu/polaris10_mc.bin
/lib/firmware/amdgpu/polaris10_me.bin
/lib/firmware/amdgpu/polaris10_me_2.bin
/lib/firmware/amdgpu/polaris10_mec.bin
/lib/firmware/amdgpu/polaris10_mec2.bin
/lib/firmware/amdgpu/polaris10_mec2_2.bin
/lib/firmware/amdgpu/polaris10_mec_2.bin
/lib/firmware/amdgpu/polaris10_pfp.bin
/lib/firmware/amdgpu/polaris10_pfp_2.bin
/lib/firmware/amdgpu/polaris10_rlc.bin
/lib/firmware/amdgpu/polaris10_sdma.bin
/lib/firmware/amdgpu/polaris10_sdma1.bin
/lib/firmware/amdgpu/polaris10_smc.bin
/lib/firmware/amdgpu/polaris10_smc_sk.bin
/lib/firmware/amdgpu/polaris10_uvd.bin
/lib/firmware/amdgpu/polaris10_vce.bin
/lib/firmware/amdgpu/polaris11_ce.bin
/lib/firmware/amdgpu/polaris11_ce_2.bin
/lib/firmware/amdgpu/polaris11_k2_smc.bin
/lib/firmware/amdgpu/polaris11_k_mc.bin
/lib/firmware/amdgpu/polaris11_k_smc.bin
/lib/firmware/amdgpu/polaris11_mc.bin
/lib/firmware/amdgpu/polaris11_me.bin
/lib/firmware/amdgpu/polaris11_me_2.bin
/lib/firmware/amdgpu/polaris11_mec.bin
/lib/firmware/amdgpu/polaris11_mec2.bin
/lib/firmware/amdgpu/polaris11_mec2_2.bin
/lib/firmware/amdgpu/polaris11_mec_2.bin
/lib/firmware/amdgpu/polaris11_pfp.bin
/lib/firmware/amdgpu/polaris11_pfp_2.bin
/lib/firmware/amdgpu/polaris11_rlc.bin
/lib/firmware/amdgpu/polaris11_sdma.bin
/lib/firmware/amdgpu/polaris11_sdma1.bin
/lib/firmware/amdgpu/polaris11_smc.bin
/lib/firmware/amdgpu/polaris11_smc_sk.bin
/lib/firmware/amdgpu/polaris11_uvd.bin
/lib/firmware/amdgpu/polaris11_vce.bin
/lib/firmware/amdgpu/polaris12_32_mc.bin
/lib/firmware/amdgpu/polaris12_ce.bin
/lib/firmware/amdgpu/polaris12_ce_2.bin
/lib/firmware/amdgpu/polaris12_k_mc.bin
/lib/firmware/amdgpu/polaris12_k_smc.bin
/lib/firmware/amdgpu/polaris12_mc.bin
/lib/firmware/amdgpu/polaris12_me.bin
/lib/firmware/amdgpu/polaris12_me_2.bin
/lib/firmware/amdgpu/polaris12_mec.bin
/lib/firmware/amdgpu/polaris12_mec2.bin
/lib/firmware/amdgpu/polaris12_mec2_2.bin
/lib/firmware/amdgpu/polaris12_mec_2.bin
/lib/firmware/amdgpu/polaris12_pfp.bin
/lib/firmware/amdgpu/polaris12_pfp_2.bin
/lib/firmware/amdgpu/polaris12_rlc.bin
/lib/firmware/amdgpu/polaris12_sdma.bin
/lib/firmware/amdgpu/polaris12_sdma1.bin
/lib/firmware/amdgpu/polaris12_smc.bin
/lib/firmware/amdgpu/polaris12_uvd.bin
/lib/firmware/amdgpu/polaris12_vce.bin
/lib/firmware/amdgpu/psp_13_0_8_asd.bin
/lib/firmware/amdgpu/psp_13_0_8_ta.bin
/lib/firmware/amdgpu/psp_13_0_8_toc.bin
/lib/firmware/amdgpu/raven2_asd.bin
/lib/firmware/amdgpu/raven2_ce.bin
/lib/firmware/amdgpu/raven2_gpu_info.bin
/lib/firmware/amdgpu/raven2_me.bin
/lib/firmware/amdgpu/raven2_mec.bin
/lib/firmware/amdgpu/raven2_mec2.bin
/lib/firmware/amdgpu/raven2_pfp.bin
/lib/firmware/amdgpu/raven2_rlc.bin
/lib/firmware/amdgpu/raven2_sdma.bin
/lib/firmware/amdgpu/raven2_ta.bin
/lib/firmware/amdgpu/raven2_vcn.bin
/lib/firmware/amdgpu/raven_asd.bin
/lib/firmware/amdgpu/raven_ce.bin
/lib/firmware/amdgpu/raven_dmcu.bin
/lib/firmware/amdgpu/raven_gpu_info.bin
/lib/firmware/amdgpu/raven_kicker_rlc.bin
/lib/firmware/amdgpu/raven_me.bin
/lib/firmware/amdgpu/raven_mec.bin
/lib/firmware/amdgpu/raven_mec2.bin
/lib/firmware/amdgpu/raven_pfp.bin
/lib/firmware/amdgpu/raven_rlc.bin
/lib/firmware/amdgpu/raven_sdma.bin
/lib/firmware/amdgpu/raven_ta.bin
/lib/firmware/amdgpu/raven_vcn.bin
/lib/firmware/amdgpu/renoir_asd.bin
/lib/firmware/amdgpu/renoir_ce.bin
/lib/firmware/amdgpu/renoir_dmcub.bin
/lib/firmware/amdgpu/renoir_gpu_info.bin
/lib/firmware/amdgpu/renoir_me.bin
/lib/firmware/amdgpu/renoir_mec.bin
/lib/firmware/amdgpu/renoir_mec2.bin
/lib/firmware/amdgpu/renoir_pfp.bin
/lib/firmware/amdgpu/renoir_rlc.bin
/lib/firmware/amdgpu/renoir_sdma.bin
/lib/firmware/amdgpu/renoir_ta.bin
/lib/firmware/amdgpu/renoir_vcn.bin
/lib/firmware/amdgpu/sdma_5_2_7.bin
/lib/firmware/amdgpu/si58_mc.bin
/lib/firmware/amdgpu/sienna_cichlid_ce.bin
/lib/firmware/amdgpu/sienna_cichlid_dmcub.bin
/lib/firmware/amdgpu/sienna_cichlid_me.bin
/lib/firmware/amdgpu/sienna_cichlid_mec.bin
/lib/firmware/amdgpu/sienna_cichlid_mec2.bin
/lib/firmware/amdgpu/sienna_cichlid_pfp.bin
/lib/firmware/amdgpu/sienna_cichlid_rlc.bin
/lib/firmware/amdgpu/sienna_cichlid_sdma.bin
/lib/firmware/amdgpu/sienna_cichlid_smc.bin
/lib/firmware/amdgpu/sienna_cichlid_sos.bin
/lib/firmware/amdgpu/sienna_cichlid_ta.bin
/lib/firmware/amdgpu/sienna_cichlid_vcn.bin
/lib/firmware/amdgpu/stoney_ce.bin
/lib/firmware/amdgpu/stoney_me.bin
/lib/firmware/amdgpu/stoney_mec.bin
/lib/firmware/amdgpu/stoney_pfp.bin
/lib/firmware/amdgpu/stoney_rlc.bin
/lib/firmware/amdgpu/stoney_sdma.bin
/lib/firmware/amdgpu/stoney_uvd.bin
/lib/firmware/amdgpu/stoney_vce.bin
/lib/firmware/amdgpu/tahiti_ce.bin
/lib/firmware/amdgpu/tahiti_k_smc.bin
/lib/firmware/amdgpu/tahiti_mc.bin
/lib/firmware/amdgpu/tahiti_me.bin
/lib/firmware/amdgpu/tahiti_pfp.bin
/lib/firmware/amdgpu/tahiti_rlc.bin
/lib/firmware/amdgpu/tahiti_smc.bin
/lib/firmware/amdgpu/tahiti_uvd.bin
/lib/firmware/amdgpu/tonga_ce.bin
/lib/firmware/amdgpu/tonga_k_smc.bin
/lib/firmware/amdgpu/tonga_mc.bin
/lib/firmware/amdgpu/tonga_me.bin
/lib/firmware/amdgpu/tonga_mec.bin
/lib/firmware/amdgpu/tonga_mec2.bin
/lib/firmware/amdgpu/tonga_pfp.bin
/lib/firmware/amdgpu/tonga_rlc.bin
/lib/firmware/amdgpu/tonga_sdma.bin
/lib/firmware/amdgpu/tonga_sdma1.bin
/lib/firmware/amdgpu/tonga_smc.bin
/lib/firmware/amdgpu/tonga_uvd.bin
/lib/firmware/amdgpu/tonga_vce.bin
/lib/firmware/amdgpu/topaz_ce.bin
/lib/firmware/amdgpu/topaz_k_smc.bin
/lib/firmware/amdgpu/topaz_mc.bin
/lib/firmware/amdgpu/topaz_me.bin
/lib/firmware/amdgpu/topaz_mec.bin
/lib/firmware/amdgpu/topaz_mec2.bin
/lib/firmware/amdgpu/topaz_pfp.bin
/lib/firmware/amdgpu/topaz_rlc.bin
/lib/firmware/amdgpu/topaz_sdma.bin
/lib/firmware/amdgpu/topaz_sdma1.bin
/lib/firmware/amdgpu/topaz_smc.bin
/lib/firmware/amdgpu/vangogh_asd.bin
/lib/firmware/amdgpu/vangogh_ce.bin
/lib/firmware/amdgpu/vangogh_dmcub.bin
/lib/firmware/amdgpu/vangogh_me.bin
/lib/firmware/amdgpu/vangogh_mec.bin
/lib/firmware/amdgpu/vangogh_mec2.bin
/lib/firmware/amdgpu/vangogh_pfp.bin
/lib/firmware/amdgpu/vangogh_rlc.bin
/lib/firmware/amdgpu/vangogh_sdma.bin
/lib/firmware/amdgpu/vangogh_toc.bin
/lib/firmware/amdgpu/vangogh_vcn.bin
/lib/firmware/amdgpu/vega10_acg_smc.bin
/lib/firmware/amdgpu/vega10_asd.bin
/lib/firmware/amdgpu/vega10_ce.bin
/lib/firmware/amdgpu/vega10_gpu_info.bin
/lib/firmware/amdgpu/vega10_me.bin
/lib/firmware/amdgpu/vega10_mec.bin
/lib/firmware/amdgpu/vega10_mec2.bin
/lib/firmware/amdgpu/vega10_pfp.bin
/lib/firmware/amdgpu/vega10_rlc.bin
/lib/firmware/amdgpu/vega10_sdma.bin
/lib/firmware/amdgpu/vega10_sdma1.bin
/lib/firmware/amdgpu/vega10_smc.bin
/lib/firmware/amdgpu/vega10_sos.bin
/lib/firmware/amdgpu/vega10_uvd.bin
/lib/firmware/amdgpu/vega10_vce.bin
/lib/firmware/amdgpu/vega12_asd.bin
/lib/firmware/amdgpu/vega12_ce.bin
/lib/firmware/amdgpu/vega12_gpu_info.bin
/lib/firmware/amdgpu/vega12_me.bin
/lib/firmware/amdgpu/vega12_mec.bin
/lib/firmware/amdgpu/vega12_mec2.bin
/lib/firmware/amdgpu/vega12_pfp.bin
/lib/firmware/amdgpu/vega12_rlc.bin
/lib/firmware/amdgpu/vega12_sdma.bin
/lib/firmware/amdgpu/vega12_sdma1.bin
/lib/firmware/amdgpu/vega12_smc.bin
/lib/firmware/amdgpu/vega12_sos.bin
/lib/firmware/amdgpu/vega12_uvd.bin
/lib/firmware/amdgpu/vega12_vce.bin
/lib/firmware/amdgpu/vega20_asd.bin
/lib/firmware/amdgpu/vega20_ce.bin
/lib/firmware/amdgpu/vega20_me.bin
/lib/firmware/amdgpu/vega20_mec.bin
/lib/firmware/amdgpu/vega20_mec2.bin
/lib/firmware/amdgpu/vega20_pfp.bin
/lib/firmware/amdgpu/vega20_rlc.bin
/lib/firmware/amdgpu/vega20_sdma.bin
/lib/firmware/amdgpu/vega20_sdma1.bin
/lib/firmware/amdgpu/vega20_smc.bin
/lib/firmware/amdgpu/vega20_sos.bin
/lib/firmware/amdgpu/vega20_ta.bin
/lib/firmware/amdgpu/vega20_uvd.bin
/lib/firmware/amdgpu/vega20_vce.bin
/lib/firmware/amdgpu/vegam_ce.bin
/lib/firmware/amdgpu/vegam_me.bin
/lib/firmware/amdgpu/vegam_mec.bin
/lib/firmware/amdgpu/vegam_mec2.bin
/lib/firmware/amdgpu/vegam_pfp.bin
/lib/firmware/amdgpu/vegam_rlc.bin
/lib/firmware/amdgpu/vegam_sdma.bin
/lib/firmware/amdgpu/vegam_sdma1.bin
/lib/firmware/amdgpu/vegam_smc.bin
/lib/firmware/amdgpu/vegam_uvd.bin
/lib/firmware/amdgpu/vegam_vce.bin
/lib/firmware/amdgpu/verde_ce.bin
/lib/firmware/amdgpu/verde_k_smc.bin
/lib/firmware/amdgpu/verde_mc.bin
/lib/firmware/amdgpu/verde_me.bin
/lib/firmware/amdgpu/verde_pfp.bin
/lib/firmware/amdgpu/verde_rlc.bin
/lib/firmware/amdgpu/verde_smc.bin
/lib/firmware/amdgpu/verde_uvd.bin
/lib/firmware/amdgpu/yellow_carp_asd.bin
/lib/firmware/amdgpu/yellow_carp_ce.bin
/lib/firmware/amdgpu/yellow_carp_dmcub.bin
/lib/firmware/amdgpu/yellow_carp_me.bin
/lib/firmware/amdgpu/yellow_carp_mec.bin
/lib/firmware/amdgpu/yellow_carp_mec2.bin
/lib/firmware/amdgpu/yellow_carp_pfp.bin
/lib/firmware/amdgpu/yellow_carp_rlc.bin
/lib/firmware/amdgpu/yellow_carp_sdma.bin
/lib/firmware/amdgpu/yellow_carp_ta.bin
/lib/firmware/amdgpu/yellow_carp_toc.bin
/lib/firmware/amdgpu/yellow_carp_vcn.bin

```
Could you please confirm by doing this?
```

ls /lib/firmware/amdgpu/*smu*.bin

```

---

### Post by treadmill855 on 2023-08-12
Only two show up: 

```
$ ls /lib/firmware/amdgpu/*smu*.bin
/lib/firmware/amdgpu/smu_13_0_0.bin  /lib/firmware/amdgpu/smu_13_0_7.bin
```

---

### Post by MAFoElffen on 2023-08-13
> **treadmill855 said:**
> Only two show up: 

```
$ ls /lib/firmware/amdgpu/*smu*.bin
/lib/firmware/amdgpu/smu_13_0_0.bin  /lib/firmware/amdgpu/smu_13_0_7.bin
```
Same two files and versions as mine.
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls /lib/firmware/amdgpu/*smu*.bin
/lib/firmware/amdgpu/smu_13_0_0.bin  /lib/firmware/amdgpu/smu_13_0_7.bin

```
Now I'm just guessing and reaching for things.

Maybe if one of those files is corrupted(?) In that case, reinstalling linux-firmware would correct that. No-harm done if not.
```

sudo apt install --reinstall linux-firmware

```

---

### Post by treadmill855 on 2023-08-13
[$ sudo apt install --reinstall linux-firmware
[sudo] password for :
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 5 not upgraded.
Need to get 0 B/254 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 293951 files and directories currently installed.)
Preparing to unpack .../linux-firmware_20220329.git681281e4-0ubuntu3.17_all.deb ...
Unpacking linux-firmware (20220329.git681281e4-0ubuntu3.17) over (20220329.git681281e4-0ubuntu3.17) ...
Setting up linux-firmware (20220329.git681281e4-0ubuntu3.17) ...
update-initramfs: Generating /boot/initrd.img-6.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-5.19.0-50-generic
update-initramfs: Generating /boot/initrd.img-5.15.0-78-generic[/CODE]

This is also my Grub configuration file in case any of that is wrong: 

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#this was the original setting before there were problems:
GRUB_CMDLINE_LINUX=""
#this gets it to at least boot to a usable desktop:
#GRUB_CMDLINE_LINUX="quiet splash nomodeset"
```

```
$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Found linux image: /boot/vmlinuz-5.19.0-50-generic
Found initrd image: /boot/initrd.img-5.19.0-50-generic
Found linux image: /boot/vmlinuz-5.15.0-78-generic
Found initrd image: /boot/initrd.img-5.15.0-78-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
```

Still boots to a gray/blank screen after that. 

Also gave this another shot for good measure: 

```
$ sudo apt install --reinstall xserver-xorg-video-amdgpu
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 5 not upgraded.
Need to get 71.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 xserver-xorg-video-amdgpu amd64 22.0.0-1ubuntu0.1 [71.9 kB]
Fetched 71.9 kB in 0s (432 kB/s)
(Reading database ... 293951 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-video-amdgpu_22.0.0-1ubuntu0.1_amd64.deb ...
Unpacking xserver-xorg-video-amdgpu (22.0.0-1ubuntu0.1) over (22.0.0-1ubuntu0.1) ...
Setting up xserver-xorg-video-amdgpu (22.0.0-1ubuntu0.1) ...
Processing triggers for man-db (2.10.2-1) ...
```

I am also getting a "BIOS error (bug) could not resolve symbol ..." when I boot but I am reasonably sure that was happening beforehand. 

```
Aug 13 10:07:15 server kernel: [    1.222707] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.PRT4._GTF.DSSP], AE_NOT_FOUND (20221020/psargs-330)
Aug 13 10:07:15 server kernel: [    1.222978] ACPI Error: Aborting method \_SB.PCI0.SAT0.PRT4._GTF due to previous error (AE_NOT_FOUND) (20221020/psparse-529)
Aug 13 10:07:15 server kernel: [    1.224311] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.PRT4._GTF.DSSP], AE_NOT_FOUND (20221020/psargs-330)
Aug 13 10:07:15 server kernel: [    1.224579] ACPI Error: Aborting method \_SB.PCI0.SAT0.PRT4._GTF due to previous error (AE_NOT_FOUND) (20221020/psparse-529)
Aug 13 10:07:15 server kernel: [    1.263886] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.PRT2._GTF.DSSP], AE_NOT_FOUND (20221020/psargs-330)
Aug 13 10:07:15 server kernel: [    1.264153] ACPI Error: Aborting method \_SB.PCI0.SAT0.PRT2._GTF due to previous error (AE_NOT_FOUND) (20221020/psparse-529)
Aug 13 10:07:15 server kernel: [    1.352540] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.PRT2._GTF.DSSP], AE_NOT_FOUND (20221020/psargs-330)
Aug 13 10:07:15 server kernel: [    1.352807] ACPI Error: Aborting method \_SB.PCI0.SAT0.PRT2._GTF due to previous error (AE_NOT_FOUND) (20221020/psparse-529)
Aug 13 10:07:15 server kernel: [    3.322820] ACPI: bus type drm_connector registered
```

---

### Post by MAFoElffen on 2023-08-13
You are still using this as a kernel boot command line in file /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
Please change it to 
```

GRUB_CMDLINE_LINUX_DEFAULT="--- quite splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1 "

```
Save, exit, and do update-grub again.
```

sudo update-grub
sudo update-initramfs -c -k all

```
Boot and retest.

---

### Post by treadmill855 on 2023-08-13
So I think the problem is a little improved but not fully fixed. A grub configuration like this still gets me to a gray/blank video output: 

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1"
#this was the original setting before there were problems:
GRUB_CMDLINE_LINUX=""
#this gets it to at least boot to a usable desktop:
#GRUB_CMDLINE_LINUX="quiet splash nomodeset"
```

But swapping in the *GRUB_CMDLINE_LINUX *statements gets me into a desktop environment where it seems like I can at least play HD video on Kodi. Before the playback would have been all stuttery and janky. However trying to launch a video game is giving me a graphics driver error message saying the graphics driver is not loaded. 

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1"
#this was the original setting before there were problems:
#GRUB_CMDLINE_LINUX=""
#this gets it to at least boot to a usable desktop:
GRUB_CMDLINE_LINUX="quiet splash nomodeset"
```

Output of* $ sudo lshw -C display*
```
[sudo] password for :
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:df900000-df9fffff memory:c0000-dffff
  *-graphics
       product: EFI VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=2560,1440
```

---

### Post by MAFoElffen on 2023-08-14
So the amdgpu driver is loaded as a module now in the syslog? And what does xorg.0.log say about what is loading and trying to claim that display?

---

### Post by treadmill855 on 2023-08-14
I am not really sure how to interpret it. It seems that "device  UNCLAIMED" error is still there which makes it seem like the driver is  still not loaded but the syslog is cryptic to me:

```
$ cat /var/log/syslog | grep amdgpu
Aug 13 21:27:42 server kernel: [    0.000000] Command line:  BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic  root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro --- quiet splash  radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1 vt.handoff=7
Aug 13 21:27:42 server kernel: [    0.044987] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic  root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro --- quiet splash  radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1 vt.handoff=7
Aug 13 21:27:44 server kernel: [    5.149397] [drm] amdgpu kernel modesetting enabled.
Aug 13 21:27:44 server kernel: [    5.149476] amdgpu: CRAT table not found
Aug 13 21:27:44 server kernel: [    5.149480] amdgpu: Virtual CRAT table created for CPU
Aug 13 21:27:44 server kernel: [    5.149493] amdgpu: Topology: Add CPU node
Aug 13 21:27:44 server kernel: [    5.151324] amdgpu 0000:03:00.0: No more image in the PCI ROM
Aug 13 21:27:44 server kernel: [    5.151336] amdgpu 0000:03:00.0: amdgpu: Fetched VBIOS from ROM BAR
Aug 13 21:27:44 server kernel: [    5.151338] amdgpu: ATOM BIOS: 113-D63201-R65XTE
Aug 13 21:27:44 server kernel: [    5.151725] amdgpu 0000:03:00.0: vgaarb: deactivate vga console
Aug 13 21:27:44 server kernel: [    5.151728] amdgpu 0000:03:00.0:  amdgpu: Trusted Memory Zone (TMZ) feature disabled as experimental  (default)
Aug 13 21:27:44 server kernel: [    5.151770] amdgpu 0000:03:00.0:  amdgpu: VRAM: 4080M 0x0000008000000000 - 0x00000080FEFFFFFF (4080M used)
Aug 13 21:27:44 server kernel: [    5.151773] amdgpu 0000:03:00.0: amdgpu: GART: 512M 0x0000000000000000 - 0x000000001FFFFFFF
Aug 13 21:27:44 server kernel: [    5.151776] amdgpu 0000:03:00.0:  amdgpu: AGP: 267894784M 0x0000008400000000 - 0x0000FFFFFFFFFFFF
Aug 13 21:27:44 server kernel: [    5.151842] [drm] amdgpu: 4080M of VRAM memory ready
Aug 13 21:27:44 server kernel: [    5.151844] [drm] amdgpu: 15995M of GTT memory ready.
Aug 13 21:27:44 server kernel: [    5.163971] amdgpu 0000:03:00.0: amdgpu: PSP runtime database doesn't exist
Aug 13 21:27:44 server kernel: [    5.163975] amdgpu 0000:03:00.0: amdgpu: PSP runtime database doesn't exist
Aug 13 21:27:45 server kernel: [    6.560528] amdgpu 0000:03:00.0: amdgpu: STB initialized to 2048 entries
Aug 13 21:27:45 server kernel: [    6.565363] amdgpu 0000:03:00.0: amdgpu: Will use PSP to load VCN firmware
Aug 13 21:27:45 server kernel: [    6.721654] amdgpu 0000:03:00.0: amdgpu: RAS: optional ras ta ucode is not available
Aug 13 21:27:45 server kernel: [    6.736491] amdgpu 0000:03:00.0:  amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available
Aug 13 21:27:45 server kernel: [    6.736510] amdgpu 0000:03:00.0:  amdgpu: smu driver if version = 0x0000000d, smu fw if version =  0x0000000f, smu fw program = 0, version = 0x00491a00 (73.26.0)
Aug 13 21:27:45 server kernel: [    6.736513] amdgpu 0000:03:00.0: amdgpu: SMU driver if version not matched
Aug 13 21:27:45 server kernel: [    6.736539] amdgpu 0000:03:00.0: amdgpu: use vbios provided pptable
Aug 13 21:27:48 server kernel: [    9.822014] amdgpu 0000:03:00.0:  amdgpu: SMU: I'm not done with your previous command:  SMN_C2PMSG_66:0x00000006 SMN_C2PMSG_82:0x00000000
Aug 13 21:27:48 server kernel: [    9.822022] amdgpu 0000:03:00.0: amdgpu: Failed to enable requested dpm features!
Aug 13 21:27:48 server kernel: [    9.822025] amdgpu 0000:03:00.0: amdgpu: Failed to setup smc hw!
Aug 13 21:27:48 server kernel: [    9.822028] [drm:amdgpu_device_ip_init  [amdgpu]] *ERROR* hw_init of IP block <smu> failed -62
Aug 13 21:27:48 server kernel: [    9.822291] amdgpu 0000:03:00.0: amdgpu: amdgpu_device_ip_init failed
Aug 13 21:27:48 server kernel: [    9.822294] amdgpu 0000:03:00.0: amdgpu: Fatal error during GPU init
Aug 13 21:27:48 server kernel: [    9.822306] amdgpu 0000:03:00.0: amdgpu: amdgpu: finishing device.
Aug 13 21:27:48 server kernel: [    9.822431] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.822695] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.822780] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.823052]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.823282]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.823507]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.823730]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.823952]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.824204]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.824427]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.824721] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.824976] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.825041] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.825244]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.825402]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.825557]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.825709]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.825864]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.826042]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.826195]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.826405] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.826597] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.826657] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.826852]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.827009]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.827162]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.827315]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.827468]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.827645]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.827798]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.828005] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.828188] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.828246] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.828441]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.828598]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.828751]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.828904]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.829056]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.829233]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.829385]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.829590] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.829772] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.829830] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.830024]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.830181]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.830334]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.830493]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.830645]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.830822]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.830974]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.831180] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.831363] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.831421] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.831616]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.831773]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.831926]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.832079]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.832231]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.832408]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.832560]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.832766] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.832948] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.833006] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.833200]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.833357]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.833510]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.833662]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.833815]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.833991]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.834143]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.834348] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.834534] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.834595] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.834790]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.834947]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.835099]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.835251]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.835402]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.835578]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.835729]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.835934] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.836115] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.836173] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.836368]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.836524]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.836676]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.836828]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.836979]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.837155]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.837306]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.837510] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.837691] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.837749] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.837942]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.838098]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.838250]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.838402]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.838556]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.838733]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.838885]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.839090] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.839272] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.839330] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.839524]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.839680]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.839832]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.839984]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.840136]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.840311]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.840463]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.840667] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:48 server kernel: [    9.840848] Modules linked in:  nf_tables libcrc32c nfnetlink cmac algif_hash algif_skcipher af_alg bnep  snd_hda_codec_realtek snd_soc_avs snd_hda_codec_generic  snd_soc_hda_codec ledtrig_audio snd_hda_ext_core snd_soc_core  intel_rapl_msr intel_rapl_common snd_compress snd_hda_codec_hdmi  intel_tcc_cooling x86_pkg_temp_thermal ac97_bus intel_powerclamp  snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp snd_intel_dspcfg  snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2 snd_hda_core iwlmvm  drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm irqbypass binfmt_misc  drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb polyval_clmulni  snd_seq_midi drm_display_helper snd_seq_midi_event btrtl polyval_generic  ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3 iwlwifi  aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper  intel_wmi_thunderbolt intel_cstate input_leds ee1004 mxm_wmi snd  cfg80211 syscopyarea sysfillrect
Aug 13 21:27:48 server kernel: [    9.840906] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.841099]  amdgpu_fence_driver_hw_fini+0x55/0x100 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.841256]  amdgpu_device_fini_hw+0xbc/0x240 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.841408]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.841560]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.841711]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.841887]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:48 server kernel: [    9.842038]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.980085] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:50 server kernel: [   10.980370] Modules linked in:  xt_MASQUERADE xt_mark nft_compat nft_chain_nat nf_nat nf_conntrack  nf_defrag_ipv6 nf_defrag_ipv4 nf_tables libcrc32c nfnetlink cmac  algif_hash algif_skcipher af_alg bnep snd_hda_codec_realtek snd_soc_avs  snd_hda_codec_generic snd_soc_hda_codec ledtrig_audio snd_hda_ext_core  snd_soc_core intel_rapl_msr intel_rapl_common snd_compress  snd_hda_codec_hdmi intel_tcc_cooling x86_pkg_temp_thermal ac97_bus  intel_powerclamp snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp  snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2  snd_hda_core iwlmvm drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm  irqbypass binfmt_misc drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb  polyval_clmulni snd_seq_midi drm_display_helper snd_seq_midi_event btrtl  polyval_generic ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3  iwlwifi aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper
Aug 13 21:27:50 server kernel: [   10.980447] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.980647]  gmc_v10_0_hw_fini+0x4f/0xa0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.980827]  amdgpu_device_ip_fini_early.isra.0+0x16c/0x2a0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.980979]  amdgpu_device_fini_hw+0x148/0x240 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.981131]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.981282]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.981434]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.981613]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.981764]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.981981] WARNING: CPU: 5 PID: 385  at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0  [amdgpu]
Aug 13 21:27:50 server kernel: [   10.982163] Modules linked in:  xt_MASQUERADE xt_mark nft_compat nft_chain_nat nf_nat nf_conntrack  nf_defrag_ipv6 nf_defrag_ipv4 nf_tables libcrc32c nfnetlink cmac  algif_hash algif_skcipher af_alg bnep snd_hda_codec_realtek snd_soc_avs  snd_hda_codec_generic snd_soc_hda_codec ledtrig_audio snd_hda_ext_core  snd_soc_core intel_rapl_msr intel_rapl_common snd_compress  snd_hda_codec_hdmi intel_tcc_cooling x86_pkg_temp_thermal ac97_bus  intel_powerclamp snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp  snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2  snd_hda_core iwlmvm drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm  irqbypass binfmt_misc drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb  polyval_clmulni snd_seq_midi drm_display_helper snd_seq_midi_event btrtl  polyval_generic ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3  iwlwifi aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper
Aug 13 21:27:50 server kernel: [   10.982226] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.982421]  gmc_v10_0_hw_fini+0x61/0xa0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.982607]  amdgpu_device_ip_fini_early.isra.0+0x16c/0x2a0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.982845]  amdgpu_device_fini_hw+0x148/0x240 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.982997]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.983149]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.983301]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.983477]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.983629]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.983966] amdgpu: probe of 0000:03:00.0 failed with error -62
Aug 13 21:27:50 server kernel: [   10.997305] Modules linked in:  xt_MASQUERADE xt_mark nft_compat nft_chain_nat nf_nat nf_conntrack  nf_defrag_ipv6 nf_defrag_ipv4 nf_tables libcrc32c nfnetlink cmac  algif_hash algif_skcipher af_alg bnep snd_hda_codec_realtek snd_soc_avs  snd_hda_codec_generic snd_soc_hda_codec ledtrig_audio snd_hda_ext_core  snd_soc_core intel_rapl_msr intel_rapl_common snd_compress  snd_hda_codec_hdmi intel_tcc_cooling x86_pkg_temp_thermal ac97_bus  intel_powerclamp snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp  snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2  snd_hda_core iwlmvm drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm  irqbypass binfmt_misc drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb  polyval_clmulni snd_seq_midi drm_display_helper snd_seq_midi_event btrtl  polyval_generic ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3  iwlwifi aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper
Aug 13 21:27:50 server kernel: [   10.997390]  amdgpu_vram_mgr_fini+0x13f/0x1d0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.997597]  amdgpu_ttm_fini+0x148/0x1c0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.997754]  amdgpu_bo_fini+0x27/0xa0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.997910]  gmc_v10_0_sw_fini+0x2b/0x40 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.998090]  amdgpu_device_ip_fini.isra.0+0xf9/0x320 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.998241]  ? amdgpu_fence_driver_sw_fini+0xbf/0x120 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.998396]  amdgpu_device_fini_sw+0x2d/0x220 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.998562]  amdgpu_driver_release_kms+0x16/0x40 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.998804]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.998958]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.999176] Modules linked in:  xt_MASQUERADE xt_mark nft_compat nft_chain_nat nf_nat nf_conntrack  nf_defrag_ipv6 nf_defrag_ipv4 nf_tables libcrc32c nfnetlink cmac  algif_hash algif_skcipher af_alg bnep snd_hda_codec_realtek snd_soc_avs  snd_hda_codec_generic snd_soc_hda_codec ledtrig_audio snd_hda_ext_core  snd_soc_core intel_rapl_msr intel_rapl_common snd_compress  snd_hda_codec_hdmi intel_tcc_cooling x86_pkg_temp_thermal ac97_bus  intel_powerclamp snd_pcm_dmaengine amdgpu(+) snd_hda_intel coretemp  snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec kvm_intel iommu_v2  snd_hda_core iwlmvm drm_buddy snd_hwdep kvm gpu_sched mac80211 snd_pcm  irqbypass binfmt_misc drm_ttm_helper ttm libarc4 crct10dif_pclmul btusb  polyval_clmulni snd_seq_midi drm_display_helper snd_seq_midi_event btrtl  polyval_generic ghash_clmulni_intel btbcm snd_rawmidi cec sha512_ssse3  iwlwifi aesni_intel snd_seq btintel crypto_simd rc_core cryptd btmtk  snd_seq_device nls_iso8859_1 snd_timer rapl bluetooth drm_kms_helper
Aug 13 21:27:50 server kernel: [   10.999255]  amdgpu_vram_mgr_fini+0x13f/0x1d0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.999423]  amdgpu_ttm_fini+0x148/0x1c0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.999579]  amdgpu_bo_fini+0x27/0xa0 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.999735]  gmc_v10_0_sw_fini+0x2b/0x40 [amdgpu]
Aug 13 21:27:50 server kernel: [   10.999916]  amdgpu_device_ip_fini.isra.0+0xf9/0x320 [amdgpu]
Aug 13 21:27:50 server kernel: [   11.000066]  ? amdgpu_fence_driver_sw_fini+0xbf/0x120 [amdgpu]
Aug 13 21:27:50 server kernel: [   11.000222]  amdgpu_device_fini_sw+0x2d/0x220 [amdgpu]
Aug 13 21:27:50 server kernel: [   11.000375]  amdgpu_driver_release_kms+0x16/0x40 [amdgpu]
Aug 13 21:27:50 server kernel: [   11.000581]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 13 21:27:50 server kernel: [   11.000734]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 13 21:27:50 server kernel: [   11.000944] [drm] amdgpu: ttm finalized
Aug 13 21:27:55 server /usr/libexec/gdm-x-session[1785]: Kernel command  line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic  root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro --- quiet splash  radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1 vt.handoff=7
Aug 13 21:30:22 server kernel: [    0.000000] Command line:  BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic  root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset  --- quiet splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1  vt.handoff=7
Aug 13 21:30:22 server kernel: [    0.045141] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic  root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset  --- quiet splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1  vt.handoff=7
Aug 13 21:30:34 server /usr/libexec/gdm-x-session[1545]: Kernel command  line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic  root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset  --- quiet splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1  vt.handoff=7
```

---

### Post by MAFoElffen on 2023-08-14
See, the smu module failing is causing this:
```

Aug 12 17:28:02 server kernel: [    9.700694] amdgpu 0000:03:00.0: amdgpu: Failed to enable requested dpm features!

```
I just read an upstream bug at freedesktop, where they are having a problem with that from kernels 5.14 through 6.4... and having problems with a 6700XT card and similar... where they said that if they switch off PP_PCIE_DPM_MASK, Which toggles "Dynamic adjustment of PCIE clocks and lanes", that they disabled DPM and it started working again... Let's test that.

Remove the kernel parameters I recommended previously, and replace them with 
```

amdgpu.ppfeaturemask=0xffffb

```

---

### Post by treadmill855 on 2023-08-14
Still gray/blank with this configuration:

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1"
GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash amdgpu.ppfeaturemask=0xffffb"
#this was the original setting before there were problems:
GRUB_CMDLINE_LINUX=""
#this gets it to at least boot to a usable desktop:
#GRUB_CMDLINE_LINUX="quiet splash nomodeset"
```

---

### Post by MAFoElffen on 2023-08-14
What happens if you install the third party driver from here? [https://www.amd.com/en/support/graphics/amd-radeon-6000-series/amd-radeon-6800-series/amd-radeon-rx-6800-xt](https://www.amd.com/en/support/graphics/amd-radeon-6000-series/amd-radeon-6800-series/amd-radeon-rx-6800-xt)

Alternately, I found this PPA, that has very good instructions for it's use, which updates the amdgpu firmware: [https://launchpad.net/~darxus/+archive/ubuntu/linux-firmware-amdgpu-daily](https://launchpad.net/~darxus/+archive/ubuntu/linux-firmware-amdgpu-daily) This may be a good alternative fix for running the opensource module and ensuring it runs the latest firmware patches.

---

### Post by treadmill855 on 2023-08-14
I attempted to install the module from that PPA and I think it did install, however I don't think it solved all of the problem. I do get this error message on the last step but I think it's because the PPA might be from 20.04 and I am running 22.04:

```
$ sudo apt update && apt dist-upgrade
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease
Get:4 https://pkgs.tailscale.com/stable/ubuntu impish InRelease
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease
Ign:6 https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu jammy InRelease
Err:7 https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

But, after following all the steps on that page for installing the PPA, I can boot into the system using my "default" grub configuration:

```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1"
#GRUB_CMDLINE_LINUX_DEFAULT="--- quiet splash amdgpu.ppfeaturemask=0xffffb"
#this was the original setting before there were problems:
GRUB_CMDLINE_LINUX=""
#this gets it to at least boot to a usable desktop:
#GRUB_CMDLINE_LINUX="quiet splash nomodeset"
```

However I still can't launch a game without the driver error showing up, and $ sudo lshw -C display still gives me a "display UNCLAIMED" error. So the module is still not loading for whatever reason.

Here's the latest from syslog:

```
$ cat /var/log/syslog | grep amdgpu
14:15:24 server kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset --- quiet splash amdgpu.ppfeaturemask=0xffffb vt.handoff=7
Aug 14 14:15:24 server kernel: [    0.045239] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset --- quiet splash amdgpu.ppfeaturemask=0xffffb vt.handoff=7
Aug 14 14:15:37 server /usr/libexec/gdm-x-session[1539]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset --- quiet splash amdgpu.ppfeaturemask=0xffffb vt.handoff=7
Aug 14 14:30:38 server kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset --- quiet splash amdgpu.ppfeaturemask=0xffffb vt.handoff=7
Aug 14 14:30:38 server kernel: [    0.045006] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset --- quiet splash amdgpu.ppfeaturemask=0xffffb vt.handoff=7
Aug 14 14:30:49 server /usr/libexec/gdm-x-session[1532]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=82c990ef-74ca-4c06-bd20-96856edb0faf ro quiet splash nomodeset --- quiet splash amdgpu.ppfeaturemask=0xffffb vt.handoff=7
Aug 14 14:30:53 server packagekitd[1949]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:30:53 server gnome-software[2068]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 14 14:30:55 server packagekitd[1949]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:30:55 server snap-store[2161]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 14 14:30:56 server packagekitd[1949]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:30:56 server snap-store[2161]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 14 14:30:59 server packagekitd[1949]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:30:59 server snap-store[2161]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 14 14:32:24 server kernel: [    4.907059] [drm] amdgpu kernel modesetting enabled.
Aug 14 14:32:24 server kernel: [    4.907233] amdgpu: CRAT table not found
Aug 14 14:32:24 server kernel: [    4.907235] amdgpu: Virtual CRAT table created for CPU
Aug 14 14:32:24 server kernel: [    4.907247] amdgpu: Topology: Add CPU node
Aug 14 14:32:24 server kernel: [    4.908928] amdgpu 0000:03:00.0: No more image in the PCI ROM
Aug 14 14:32:24 server kernel: [    4.908938] amdgpu 0000:03:00.0: amdgpu: Fetched VBIOS from ROM BAR
Aug 14 14:32:24 server kernel: [    4.908940] amdgpu: ATOM BIOS: 113-D63201-R65XTE
Aug 14 14:32:24 server kernel: [    4.909115] amdgpu 0000:03:00.0: vgaarb: deactivate vga console
Aug 14 14:32:24 server kernel: [    4.909118] amdgpu 0000:03:00.0: amdgpu: Trusted Memory Zone (TMZ) feature disabled as experimental (default)
Aug 14 14:32:24 server kernel: [    4.909152] amdgpu 0000:03:00.0: amdgpu: VRAM: 4080M 0x0000008000000000 - 0x00000080FEFFFFFF (4080M used)
Aug 14 14:32:24 server kernel: [    4.909154] amdgpu 0000:03:00.0: amdgpu: GART: 512M 0x0000000000000000 - 0x000000001FFFFFFF
Aug 14 14:32:24 server kernel: [    4.909156] amdgpu 0000:03:00.0: amdgpu: AGP: 267894784M 0x0000008400000000 - 0x0000FFFFFFFFFFFF
Aug 14 14:32:24 server kernel: [    4.909200] [drm] amdgpu: 4080M of VRAM memory ready
Aug 14 14:32:24 server kernel: [    4.909203] [drm] amdgpu: 15995M of GTT memory ready.
Aug 14 14:32:24 server kernel: [    4.909373] amdgpu 0000:03:00.0: Direct firmware load for amdgpu/beige_goby_sos.bin failed with error -2
Aug 14 14:32:24 server kernel: [    4.909376] amdgpu 0000:03:00.0: amdgpu: failed to init sos firmware
Aug 14 14:32:24 server kernel: [    4.909379] [drm:psp_sw_init [amdgpu]] *ERROR* Failed to load psp firmware!
Aug 14 14:32:24 server kernel: [    4.909651] [drm:amdgpu_device_ip_init [amdgpu]] *ERROR* sw_init of IP block <psp> failed -2
Aug 14 14:32:24 server kernel: [    4.909802] amdgpu 0000:03:00.0: amdgpu: amdgpu_device_ip_init failed
Aug 14 14:32:24 server kernel: [    4.909805] amdgpu 0000:03:00.0: amdgpu: Fatal error during GPU init
Aug 14 14:32:24 server kernel: [    4.909808] amdgpu 0000:03:00.0: amdgpu: amdgpu: finishing device.
Aug 14 14:32:24 server kernel: [    4.909907] WARNING: CPU: 9 PID: 375 at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.910107] Modules linked in: snd_soc_avs intel_rapl_msr intel_rapl_common snd_hda_codec_realtek snd_soc_hda_codec intel_tcc_cooling x86_pkg_temp_thermal snd_hda_codec_generic snd_hda_ext_core ledtrig_audio amdgpu(+) intel_powerclamp snd_soc_core snd_hda_codec_hdmi snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_intel_dspcfg binfmt_misc snd_intel_sdw_acpi coretemp snd_hda_codec snd_hda_core snd_hwdep kvm_intel snd_pcm nls_iso8859_1 kvm iommu_v2 drm_buddy snd_seq_midi gpu_sched snd_seq_midi_event drm_ttm_helper irqbypass ttm iwlwifi crct10dif_pclmul snd_rawmidi polyval_clmulni polyval_generic ghash_clmulni_intel btusb drm_display_helper sha512_ssse3 btrtl snd_seq aesni_intel cec btbcm crypto_simd btintel snd_seq_device rc_core cryptd btmtk rapl intel_cstate snd_timer bluetooth mxm_wmi drm_kms_helper intel_wmi_thunderbolt input_leds cfg80211 ee1004 syscopyarea snd sysfillrect ecdh_generic sysimgblt soundcore ecc mac_hid acpi_pad sch_fq_codel nfsd msr auth_rpcgss parport_pc
Aug 14 14:32:24 server kernel: [    4.910181] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.910381]  gmc_v10_0_hw_fini+0x4f/0xa0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.910568]  amdgpu_device_ip_fini_early.isra.0+0x16c/0x2a0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.910715]  amdgpu_device_fini_hw+0x148/0x240 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.910861]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.911023]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.911169]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.911342]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.911505]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.911713] WARNING: CPU: 9 PID: 375 at drivers/gpu/drm/amd/amdgpu/amdgpu_irq.c:600 amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.911885] Modules linked in: snd_soc_avs intel_rapl_msr intel_rapl_common snd_hda_codec_realtek snd_soc_hda_codec intel_tcc_cooling x86_pkg_temp_thermal snd_hda_codec_generic snd_hda_ext_core ledtrig_audio amdgpu(+) intel_powerclamp snd_soc_core snd_hda_codec_hdmi snd_compress ac97_bus snd_pcm_dmaengine snd_hda_intel snd_intel_dspcfg binfmt_misc snd_intel_sdw_acpi coretemp snd_hda_codec snd_hda_core snd_hwdep kvm_intel snd_pcm nls_iso8859_1 kvm iommu_v2 drm_buddy snd_seq_midi gpu_sched snd_seq_midi_event drm_ttm_helper irqbypass ttm iwlwifi crct10dif_pclmul snd_rawmidi polyval_clmulni polyval_generic ghash_clmulni_intel btusb drm_display_helper sha512_ssse3 btrtl snd_seq aesni_intel cec btbcm crypto_simd btintel snd_seq_device rc_core cryptd btmtk rapl intel_cstate snd_timer bluetooth mxm_wmi drm_kms_helper intel_wmi_thunderbolt input_leds cfg80211 ee1004 syscopyarea snd sysfillrect ecdh_generic sysimgblt soundcore ecc mac_hid acpi_pad sch_fq_codel nfsd msr auth_rpcgss parport_pc
Aug 14 14:32:24 server kernel: [    4.911941] RIP: 0010:amdgpu_irq_put+0xa4/0xc0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.912125]  gmc_v10_0_hw_fini+0x61/0xa0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.912294]  amdgpu_device_ip_fini_early.isra.0+0x16c/0x2a0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.912440]  amdgpu_device_fini_hw+0x148/0x240 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.912585]  amdgpu_driver_unload_kms+0x4d/0x70 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.912730]  amdgpu_driver_load_kms+0xf9/0x1c0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.912876]  amdgpu_pci_probe+0x169/0x470 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.913045]  ? __pfx_init_module+0x10/0x10 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.913191]  amdgpu_init+0x69/0xff0 [amdgpu]
Aug 14 14:32:24 server kernel: [    4.913550] amdgpu: probe of 0000:03:00.0 failed with error -2
Aug 14 14:32:24 server kernel: [    4.913617] [drm] amdgpu: ttm finalized
Aug 14 14:32:38 server packagekitd[1950]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:32:38 server gnome-software[2071]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 14 14:32:39 server packagekitd[1950]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:32:39 server snap-store[2193]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 14 14:32:41 server packagekitd[1950]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:32:41 server snap-store[2193]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
Aug 14 14:32:44 server packagekitd[1950]: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease
Aug 14 14:32:44 server snap-store[2193]: not handling error failed for action refresh: E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  #012E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  #012E: Failed to fetch https://ppa.launchpadcontent.net/darxus/linux-firmware-amdgpu-daily/ubuntu/dists/jammy/InRelease  #012E: Failed to fetch https://pkgs.tailscale.com/stable/ubuntu/dists/impish/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by treadmill855 on 2023-08-14
I'm also skeptical of installing the third party driver because in my experiences with it, it leads to generally more headaches. But if that's the next step here then I'll give it a shot.

---

### Post by MAFoElffen on 2023-08-14
It is saying that there is no package in that PPA built for 22.04 (jammy)... You can remove / purge that PPA.

One more thing to try then (before going third party). Download this and extract the amdgpu directory from it, to /lib/firmware/amdgpu/
```

wget -N -t 5 -T 10 https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20230804.tar.gz

```
I have done this with the i915 directory to my new workstation, which is i9-13900K. (New hardware and needed latest firmware).

After that, play with trying the boot parameters I suggested or none, to see if something works.

They are also listed here (but individually): [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu)

---

### Post by treadmill855 on 2023-08-15
So I put all of the files from the archive into the folder: 

```
@server:/lib/firmware/amdgpu$ ls
aldebaran_mec2.bin          gc_11_0_4_mes_2.bin      picasso_sdma.bin          sienna_cichlid_sdma.bin
aldebaran_mec.bin           gc_11_0_4_mes.bin        picasso_ta.bin            sienna_cichlid_smc.bin
aldebaran_rlc.bin           gc_11_0_4_pfp.bin        picasso_vcn.bin           sienna_cichlid_sos.bin
aldebaran_sdma.bin          gc_11_0_4_rlc.bin        pitcairn_ce.bin           sienna_cichlid_ta.bin
aldebaran_sjt_mec2.bin      green_sardine_asd.bin    pitcairn_k_smc.bin        sienna_cichlid_vcn.bin
aldebaran_sjt_mec.bin       green_sardine_ce.bin     pitcairn_mc.bin           smu_13_0_0.bin
aldebaran_smc.bin           green_sardine_dmcub.bin  pitcairn_me.bin           smu_13_0_10.bin
aldebaran_sos.bin           green_sardine_me.bin     pitcairn_pfp.bin          smu_13_0_7.bin
aldebaran_ta.bin            green_sardine_mec2.bin   pitcairn_rlc.bin          stoney_ce.bin
aldebaran_vcn.bin           green_sardine_mec.bin    pitcairn_smc.bin          stoney_me.bin
arcturus_asd.bin            green_sardine_pfp.bin    pitcairn_uvd.bin          stoney_mec.bin
arcturus_gpu_info.bin       green_sardine_rlc.bin    polaris10_ce_2.bin        stoney_pfp.bin
arcturus_mec2.bin           green_sardine_sdma.bin   polaris10_ce.bin          stoney_rlc.bin
arcturus_mec.bin            green_sardine_ta.bin     polaris10_k2_smc.bin      stoney_sdma.bin
arcturus_rlc.bin            green_sardine_vcn.bin    polaris10_k_mc.bin        stoney_uvd.bin
arcturus_sdma.bin           hainan_ce.bin            polaris10_k_smc.bin       stoney_vce.bin
arcturus_smc.bin            hainan_k_smc.bin         polaris10_mc.bin          tahiti_ce.bin
arcturus_sos.bin            hainan_mc.bin            polaris10_me_2.bin        tahiti_k_smc.bin
arcturus_ta.bin             hainan_me.bin            polaris10_me.bin          tahiti_mc.bin
arcturus_vcn.bin            hainan_pfp.bin           polaris10_mec2_2.bin      tahiti_me.bin
banks_k_2_smc.bin           hainan_rlc.bin           polaris10_mec_2.bin       tahiti_pfp.bin
beige_goby_ce.bin           hainan_smc.bin           polaris10_mec2.bin        tahiti_rlc.bin
beige_goby_dmcub.bin        hawaii_ce.bin            polaris10_mec.bin         tahiti_smc.bin
beige_goby_me.bin           hawaii_k_smc.bin         polaris10_pfp_2.bin       tahiti_uvd.bin
beige_goby_mec2.bin         hawaii_mc.bin            polaris10_pfp.bin         tonga_ce.bin
beige_goby_mec.bin          hawaii_me.bin            polaris10_rlc.bin         tonga_k_smc.bin
beige_goby_pfp.bin          hawaii_mec.bin           polaris10_sdma1.bin       tonga_mc.bin
beige_goby_rlc.bin          hawaii_pfp.bin           polaris10_sdma.bin        tonga_me.bin
beige_goby_sdma.bin         hawaii_rlc.bin           polaris10_smc.bin         tonga_mec2.bin
beige_goby_smc.bin          hawaii_sdma1.bin         polaris10_smc_sk.bin      tonga_mec.bin
beige_goby_sos.bin          hawaii_sdma.bin          polaris10_uvd.bin         tonga_pfp.bin
beige_goby_ta.bin           hawaii_smc.bin           polaris10_vce.bin         tonga_rlc.bin
beige_goby_vcn.bin          hawaii_uvd.bin           polaris11_ce_2.bin        tonga_sdma1.bin
bonaire_ce.bin              hawaii_vce.bin           polaris11_ce.bin          tonga_sdma.bin
bonaire_k_smc.bin           kabini_ce.bin            polaris11_k2_smc.bin      tonga_smc.bin
bonaire_mc.bin              kabini_me.bin            polaris11_k_mc.bin        tonga_uvd.bin
bonaire_me.bin              kabini_mec.bin           polaris11_k_smc.bin       tonga_vce.bin
bonaire_mec.bin             kabini_pfp.bin           polaris11_mc.bin          topaz_ce.bin
bonaire_pfp.bin             kabini_rlc.bin           polaris11_me_2.bin        topaz_k_smc.bin
bonaire_rlc.bin             kabini_sdma1.bin         polaris11_me.bin          topaz_mc.bin
bonaire_sdma1.bin           kabini_sdma.bin          polaris11_mec2_2.bin      topaz_me.bin
bonaire_sdma.bin            kabini_uvd.bin           polaris11_mec_2.bin       topaz_mec2.bin
bonaire_smc.bin             kabini_vce.bin           polaris11_mec2.bin        topaz_mec.bin
bonaire_uvd.bin             kaveri_ce.bin            polaris11_mec.bin         topaz_pfp.bin
bonaire_vce.bin             kaveri_me.bin            polaris11_pfp_2.bin       topaz_rlc.bin
carrizo_ce.bin              kaveri_mec2.bin          polaris11_pfp.bin         topaz_sdma1.bin
carrizo_me.bin              kaveri_mec.bin           polaris11_rlc.bin         topaz_sdma.bin
carrizo_mec2.bin            kaveri_pfp.bin           polaris11_sdma1.bin       topaz_smc.bin
carrizo_mec.bin             kaveri_rlc.bin           polaris11_sdma.bin        vangogh_asd.bin
carrizo_pfp.bin             kaveri_sdma1.bin         polaris11_smc.bin         vangogh_ce.bin
carrizo_rlc.bin             kaveri_sdma.bin          polaris11_smc_sk.bin      vangogh_dmcub.bin
carrizo_sdma1.bin           kaveri_uvd.bin           polaris11_uvd.bin         vangogh_me.bin
carrizo_sdma.bin            kaveri_vce.bin           polaris11_vce.bin         vangogh_mec2.bin
carrizo_uvd.bin             mullins_ce.bin           polaris12_32_mc.bin       vangogh_mec.bin
carrizo_vce.bin             mullins_me.bin           polaris12_ce_2.bin        vangogh_pfp.bin
cyan_skillfish2_ce.bin      mullins_mec.bin          polaris12_ce.bin          vangogh_rlc.bin
cyan_skillfish2_me.bin      mullins_pfp.bin          polaris12_k_mc.bin        vangogh_sdma.bin
cyan_skillfish2_mec2.bin    mullins_rlc.bin          polaris12_k_smc.bin       vangogh_toc.bin
cyan_skillfish2_mec.bin     mullins_sdma1.bin        polaris12_mc.bin          vangogh_vcn.bin
cyan_skillfish2_pfp.bin     mullins_sdma.bin         polaris12_me_2.bin        vcn_3_1_2.bin
cyan_skillfish2_rlc.bin     mullins_uvd.bin          polaris12_me.bin          vcn_4_0_0.bin
cyan_skillfish2_sdma1.bin   mullins_vce.bin          polaris12_mec2_2.bin      vcn_4_0_2.bin
cyan_skillfish2_sdma.bin    navi10_asd.bin           polaris12_mec_2.bin       vcn_4_0_4.bin
dcn_3_1_4_dmcub.bin         navi10_ce.bin            polaris12_mec2.bin        vega10_acg_smc.bin
dcn_3_1_5_dmcub.bin         navi10_gpu_info.bin      polaris12_mec.bin         vega10_asd.bin
dcn_3_1_6_dmcub.bin         navi10_me.bin            polaris12_pfp_2.bin       vega10_ce.bin
dcn_3_2_0_dmcub.bin         navi10_mec2.bin          polaris12_pfp.bin         vega10_gpu_info.bin
dcn_3_2_1_dmcub.bin         navi10_mec.bin           polaris12_rlc.bin         vega10_me.bin
dimgrey_cavefish_ce.bin     navi10_pfp.bin           polaris12_sdma1.bin       vega10_mec2.bin
dimgrey_cavefish_dmcub.bin  navi10_rlc.bin           polaris12_sdma.bin        vega10_mec.bin
dimgrey_cavefish_me.bin     navi10_sdma1.bin         polaris12_smc.bin         vega10_pfp.bin
dimgrey_cavefish_mec2.bin   navi10_sdma.bin          polaris12_uvd.bin         vega10_rlc.bin
dimgrey_cavefish_mec.bin    navi10_smc.bin           polaris12_vce.bin         vega10_sdma1.bin
dimgrey_cavefish_pfp.bin    navi10_sos.bin           psp_13_0_0_sos.bin        vega10_sdma.bin
dimgrey_cavefish_rlc.bin    navi10_ta.bin            psp_13_0_0_ta.bin         vega10_smc.bin
dimgrey_cavefish_sdma.bin   navi10_vcn.bin           psp_13_0_10_sos.bin       vega10_sos.bin
dimgrey_cavefish_smc.bin    navi12_asd.bin           psp_13_0_10_ta.bin        vega10_uvd.bin
dimgrey_cavefish_sos.bin    navi12_ce.bin            psp_13_0_11_ta.bin        vega10_vce.bin
dimgrey_cavefish_ta.bin     navi12_dmcu.bin          psp_13_0_11_toc.bin       vega12_asd.bin
dimgrey_cavefish_vcn.bin    navi12_gpu_info.bin      psp_13_0_4_ta.bin         vega12_ce.bin
fiji_ce.bin                 navi12_me.bin            psp_13_0_4_toc.bin        vega12_gpu_info.bin
fiji_mc.bin                 navi12_mec2.bin          psp_13_0_5_asd.bin        vega12_me.bin
fiji_me.bin                 navi12_mec.bin           psp_13_0_5_ta.bin         vega12_mec2.bin
fiji_mec2.bin               navi12_pfp.bin           psp_13_0_5_toc.bin        vega12_mec.bin
fiji_mec.bin                navi12_rlc.bin           psp_13_0_7_sos.bin        vega12_pfp.bin
fiji_pfp.bin                navi12_sdma1.bin         psp_13_0_7_ta.bin         vega12_rlc.bin
fiji_rlc.bin                navi12_sdma.bin          psp_13_0_8_asd.bin        vega12_sdma1.bin
fiji_sdma1.bin              navi12_smc.bin           psp_13_0_8_ta.bin         vega12_sdma.bin
fiji_sdma.bin               navi12_sos.bin           psp_13_0_8_toc.bin        vega12_smc.bin
fiji_smc.bin                navi12_ta.bin            raven2_asd.bin            vega12_sos.bin
fiji_uvd.bin                navi12_vcn.bin           raven2_ce.bin             vega12_uvd.bin
fiji_vce.bin                navi14_asd.bin           raven2_gpu_info.bin       vega12_vce.bin
gc_10_3_6_ce.bin            navi14_ce.bin            raven2_me.bin             vega20_asd.bin
gc_10_3_6_me.bin            navi14_ce_wks.bin        raven2_mec2.bin           vega20_ce.bin
gc_10_3_6_mec2.bin          navi14_gpu_info.bin      raven2_mec.bin            vega20_me.bin
gc_10_3_6_mec.bin           navi14_me.bin            raven2_pfp.bin            vega20_mec2.bin
gc_10_3_6_pfp.bin           navi14_mec2.bin          raven2_rlc.bin            vega20_mec.bin
gc_10_3_6_rlc.bin           navi14_mec2_wks.bin      raven2_sdma.bin           vega20_pfp.bin
gc_10_3_7_ce.bin            navi14_mec.bin           raven2_ta.bin             vega20_rlc.bin
gc_10_3_7_me.bin            navi14_mec_wks.bin       raven2_vcn.bin            vega20_sdma1.bin
gc_10_3_7_mec2.bin          navi14_me_wks.bin        raven_asd.bin             vega20_sdma.bin
gc_10_3_7_mec.bin           navi14_pfp.bin           raven_ce.bin              vega20_smc.bin
gc_10_3_7_pfp.bin           navi14_pfp_wks.bin       raven_dmcu.bin            vega20_sos.bin
gc_10_3_7_rlc.bin           navi14_rlc.bin           raven_gpu_info.bin        vega20_ta.bin
gc_11_0_0_imu.bin           navi14_sdma1.bin         raven_kicker_rlc.bin      vega20_uvd.bin
gc_11_0_0_me.bin            navi14_sdma.bin          raven_me.bin              vega20_vce.bin
gc_11_0_0_mec.bin           navi14_smc.bin           raven_mec2.bin            vegam_ce.bin
gc_11_0_0_mes1.bin          navi14_sos.bin           raven_mec.bin             vegam_me.bin
gc_11_0_0_mes_2.bin         navi14_ta.bin            raven_pfp.bin             vegam_mec2.bin
gc_11_0_0_mes.bin           navi14_vcn.bin           raven_rlc.bin             vegam_mec.bin
gc_11_0_0_pfp.bin           navy_flounder_ce.bin     raven_sdma.bin            vegam_pfp.bin
gc_11_0_0_rlc.bin           navy_flounder_dmcub.bin  raven_ta.bin              vegam_rlc.bin
gc_11_0_1_imu.bin           navy_flounder_me.bin     raven_vcn.bin             vegam_sdma1.bin
gc_11_0_1_me.bin            navy_flounder_mec2.bin   renoir_asd.bin            vegam_sdma.bin
gc_11_0_1_mec.bin           navy_flounder_mec.bin    renoir_ce.bin             vegam_smc.bin
gc_11_0_1_mes1.bin          navy_flounder_pfp.bin    renoir_dmcub.bin          vegam_uvd.bin
gc_11_0_1_mes_2.bin         navy_flounder_rlc.bin    renoir_gpu_info.bin       vegam_vce.bin
gc_11_0_1_mes.bin           navy_flounder_sdma.bin   renoir_me.bin             verde_ce.bin
gc_11_0_1_pfp.bin           navy_flounder_smc.bin    renoir_mec2.bin           verde_k_smc.bin
gc_11_0_1_rlc.bin           navy_flounder_sos.bin    renoir_mec.bin            verde_mc.bin
gc_11_0_2_imu.bin           navy_flounder_ta.bin     renoir_pfp.bin            verde_me.bin
gc_11_0_2_me.bin            navy_flounder_vcn.bin    renoir_rlc.bin            verde_pfp.bin
gc_11_0_2_mec.bin           oland_ce.bin             renoir_sdma.bin           verde_rlc.bin
gc_11_0_2_mes1.bin          oland_k_smc.bin          renoir_ta.bin             verde_smc.bin
gc_11_0_2_mes_2.bin         oland_mc.bin             renoir_vcn.bin            verde_uvd.bin
gc_11_0_2_mes.bin           oland_me.bin             sdma_5_2_6.bin            yellow_carp_asd.bin
gc_11_0_2_pfp.bin           oland_pfp.bin            sdma_5_2_7.bin            yellow_carp_ce.bin
gc_11_0_2_rlc.bin           oland_rlc.bin            sdma_6_0_0.bin            yellow_carp_dmcub.bin
gc_11_0_3_imu.bin           oland_smc.bin            sdma_6_0_1.bin            yellow_carp_me.bin
gc_11_0_3_me.bin            oland_uvd.bin            sdma_6_0_2.bin            yellow_carp_mec2.bin
gc_11_0_3_mec.bin           picasso_asd.bin          sdma_6_0_3.bin            yellow_carp_mec.bin
gc_11_0_3_mes1.bin          picasso_ce.bin           si58_mc.bin               yellow_carp_pfp.bin
gc_11_0_3_mes_2.bin         picasso_gpu_info.bin     sienna_cichlid_ce.bin     yellow_carp_rlc.bin
gc_11_0_3_pfp.bin           picasso_me.bin           sienna_cichlid_dmcub.bin  yellow_carp_sdma.bin
gc_11_0_3_rlc.bin           picasso_mec2.bin         sienna_cichlid_me.bin     yellow_carp_ta.bin
gc_11_0_4_imu.bin           picasso_mec.bin          sienna_cichlid_mec2.bin   yellow_carp_toc.bin
gc_11_0_4_me.bin            picasso_pfp.bin          sienna_cichlid_mec.bin    yellow_carp_vcn.bin
gc_11_0_4_mec.bin           picasso_rlc_am4.bin      sienna_cichlid_pfp.bin
gc_11_0_4_mes1.bin          picasso_rlc.bin          sienna_cichlid_rlc.bin
```

That folder didn't already exist, though. I don't need to do anything to point out that this is here now? I did use all of the grub configurations I've saved up too, and ran update-grub after each one (and update-initramfs) and the video output is still blank.

---

### Post by MAFoElffen on 2023-08-15
Here is the list of file (on mine) that go in that specific directory...
```

mafoelffen@Mikes-ThinkPad-T520:~$ tree /lib/firmware/amdgpu
/lib/firmware/amdgpu
&#9500;&#9472;&#9472; aldebaran_mec2.bin
&#9500;&#9472;&#9472; aldebaran_mec.bin
&#9500;&#9472;&#9472; aldebaran_rlc.bin
&#9500;&#9472;&#9472; aldebaran_sdma.bin
&#9500;&#9472;&#9472; aldebaran_smc.bin
&#9500;&#9472;&#9472; aldebaran_sos.bin
&#9500;&#9472;&#9472; aldebaran_ta.bin
&#9500;&#9472;&#9472; aldebaran_vcn.bin
&#9500;&#9472;&#9472; arcturus_asd.bin
&#9500;&#9472;&#9472; arcturus_gpu_info.bin
&#9500;&#9472;&#9472; arcturus_mec2.bin
&#9500;&#9472;&#9472; arcturus_mec.bin
&#9500;&#9472;&#9472; arcturus_rlc.bin
&#9500;&#9472;&#9472; arcturus_sdma.bin
&#9500;&#9472;&#9472; arcturus_smc.bin
&#9500;&#9472;&#9472; arcturus_sos.bin
&#9500;&#9472;&#9472; arcturus_ta.bin
&#9500;&#9472;&#9472; arcturus_vcn.bin
&#9500;&#9472;&#9472; banks_k_2_smc.bin
&#9500;&#9472;&#9472; beige_goby_ce.bin
&#9500;&#9472;&#9472; beige_goby_dmcub.bin
&#9500;&#9472;&#9472; beige_goby_me.bin
&#9500;&#9472;&#9472; beige_goby_mec2.bin
&#9500;&#9472;&#9472; beige_goby_mec.bin
&#9500;&#9472;&#9472; beige_goby_pfp.bin
&#9500;&#9472;&#9472; beige_goby_rlc.bin
&#9500;&#9472;&#9472; beige_goby_sdma.bin
&#9500;&#9472;&#9472; beige_goby_smc.bin
&#9500;&#9472;&#9472; beige_goby_sos.bin
&#9500;&#9472;&#9472; beige_goby_ta.bin
&#9500;&#9472;&#9472; beige_goby_vcn.bin
&#9500;&#9472;&#9472; bonaire_ce.bin
&#9500;&#9472;&#9472; bonaire_k_smc.bin
&#9500;&#9472;&#9472; bonaire_mc.bin
&#9500;&#9472;&#9472; bonaire_me.bin
&#9500;&#9472;&#9472; bonaire_mec.bin
&#9500;&#9472;&#9472; bonaire_pfp.bin
&#9500;&#9472;&#9472; bonaire_rlc.bin
&#9500;&#9472;&#9472; bonaire_sdma1.bin
&#9500;&#9472;&#9472; bonaire_sdma.bin
&#9500;&#9472;&#9472; bonaire_smc.bin
&#9500;&#9472;&#9472; bonaire_uvd.bin
&#9500;&#9472;&#9472; bonaire_vce.bin
&#9500;&#9472;&#9472; carrizo_ce.bin
&#9500;&#9472;&#9472; carrizo_me.bin
&#9500;&#9472;&#9472; carrizo_mec2.bin
&#9500;&#9472;&#9472; carrizo_mec.bin
&#9500;&#9472;&#9472; carrizo_pfp.bin
&#9500;&#9472;&#9472; carrizo_rlc.bin
&#9500;&#9472;&#9472; carrizo_sdma1.bin
&#9500;&#9472;&#9472; carrizo_sdma.bin
&#9500;&#9472;&#9472; carrizo_uvd.bin
&#9500;&#9472;&#9472; carrizo_vce.bin
&#9500;&#9472;&#9472; cyan_skillfish2_ce.bin
&#9500;&#9472;&#9472; cyan_skillfish2_me.bin
&#9500;&#9472;&#9472; cyan_skillfish2_mec2.bin
&#9500;&#9472;&#9472; cyan_skillfish2_mec.bin
&#9500;&#9472;&#9472; cyan_skillfish2_pfp.bin
&#9500;&#9472;&#9472; cyan_skillfish2_rlc.bin
&#9500;&#9472;&#9472; cyan_skillfish2_sdma1.bin
&#9500;&#9472;&#9472; cyan_skillfish2_sdma.bin
&#9500;&#9472;&#9472; dcn_3_1_4_dmcub.bin
&#9500;&#9472;&#9472; dcn_3_1_5_dmcub.bin
&#9500;&#9472;&#9472; dcn_3_1_6_dmcub.bin
&#9500;&#9472;&#9472; dcn_3_2_0_dmcub.bin
&#9500;&#9472;&#9472; dcn_3_2_1_dmcub.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_ce.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_dmcub.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_me.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_mec2.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_mec.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_pfp.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_rlc.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_sdma.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_smc.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_sos.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_ta.bin
&#9500;&#9472;&#9472; dimgrey_cavefish_vcn.bin
&#9500;&#9472;&#9472; fiji_ce.bin
&#9500;&#9472;&#9472; fiji_mc.bin
&#9500;&#9472;&#9472; fiji_me.bin
&#9500;&#9472;&#9472; fiji_mec2.bin
&#9500;&#9472;&#9472; fiji_mec.bin
&#9500;&#9472;&#9472; fiji_pfp.bin
&#9500;&#9472;&#9472; fiji_rlc.bin
&#9500;&#9472;&#9472; fiji_sdma1.bin
&#9500;&#9472;&#9472; fiji_sdma.bin
&#9500;&#9472;&#9472; fiji_smc.bin
&#9500;&#9472;&#9472; fiji_uvd.bin
&#9500;&#9472;&#9472; fiji_vce.bin
&#9500;&#9472;&#9472; gc_10_3_6_ce.bin
&#9500;&#9472;&#9472; gc_10_3_6_me.bin
&#9500;&#9472;&#9472; gc_10_3_6_mec2.bin
&#9500;&#9472;&#9472; gc_10_3_6_mec.bin
&#9500;&#9472;&#9472; gc_10_3_6_pfp.bin
&#9500;&#9472;&#9472; gc_10_3_6_rlc.bin
&#9500;&#9472;&#9472; gc_10_3_7_ce.bin
&#9500;&#9472;&#9472; gc_10_3_7_me.bin
&#9500;&#9472;&#9472; gc_10_3_7_mec2.bin
&#9500;&#9472;&#9472; gc_10_3_7_mec.bin
&#9500;&#9472;&#9472; gc_10_3_7_pfp.bin
&#9500;&#9472;&#9472; gc_10_3_7_rlc.bin
&#9500;&#9472;&#9472; gc_11_0_0_imu.bin
&#9500;&#9472;&#9472; gc_11_0_0_me.bin
&#9500;&#9472;&#9472; gc_11_0_0_mec.bin
&#9500;&#9472;&#9472; gc_11_0_0_mes1.bin
&#9500;&#9472;&#9472; gc_11_0_0_mes_2.bin
&#9500;&#9472;&#9472; gc_11_0_0_mes.bin
&#9500;&#9472;&#9472; gc_11_0_0_pfp.bin
&#9500;&#9472;&#9472; gc_11_0_0_rlc.bin
&#9500;&#9472;&#9472; gc_11_0_1_imu.bin
&#9500;&#9472;&#9472; gc_11_0_1_me.bin
&#9500;&#9472;&#9472; gc_11_0_1_mec.bin
&#9500;&#9472;&#9472; gc_11_0_1_mes1.bin
&#9500;&#9472;&#9472; gc_11_0_1_mes_2.bin
&#9500;&#9472;&#9472; gc_11_0_1_mes.bin
&#9500;&#9472;&#9472; gc_11_0_1_pfp.bin
&#9500;&#9472;&#9472; gc_11_0_1_rlc.bin
&#9500;&#9472;&#9472; gc_11_0_2_imu.bin
&#9500;&#9472;&#9472; gc_11_0_2_me.bin
&#9500;&#9472;&#9472; gc_11_0_2_mec.bin
&#9500;&#9472;&#9472; gc_11_0_2_mes1.bin
&#9500;&#9472;&#9472; gc_11_0_2_mes_2.bin
&#9500;&#9472;&#9472; gc_11_0_2_mes.bin
&#9500;&#9472;&#9472; gc_11_0_2_pfp.bin
&#9500;&#9472;&#9472; gc_11_0_2_rlc.bin
&#9500;&#9472;&#9472; gc_11_0_4_imu.bin
&#9500;&#9472;&#9472; gc_11_0_4_me.bin
&#9500;&#9472;&#9472; gc_11_0_4_mec.bin
&#9500;&#9472;&#9472; gc_11_0_4_mes1.bin
&#9500;&#9472;&#9472; gc_11_0_4_mes_2.bin
&#9500;&#9472;&#9472; gc_11_0_4_mes.bin
&#9500;&#9472;&#9472; gc_11_0_4_pfp.bin
&#9500;&#9472;&#9472; gc_11_0_4_rlc.bin
&#9500;&#9472;&#9472; green_sardine_asd.bin
&#9500;&#9472;&#9472; green_sardine_ce.bin
&#9500;&#9472;&#9472; green_sardine_dmcub.bin
&#9500;&#9472;&#9472; green_sardine_me.bin
&#9500;&#9472;&#9472; green_sardine_mec2.bin
&#9500;&#9472;&#9472; green_sardine_mec.bin
&#9500;&#9472;&#9472; green_sardine_pfp.bin
&#9500;&#9472;&#9472; green_sardine_rlc.bin
&#9500;&#9472;&#9472; green_sardine_sdma.bin
&#9500;&#9472;&#9472; green_sardine_ta.bin
&#9500;&#9472;&#9472; green_sardine_vcn.bin
&#9500;&#9472;&#9472; hainan_ce.bin
&#9500;&#9472;&#9472; hainan_k_smc.bin
&#9500;&#9472;&#9472; hainan_mc.bin
&#9500;&#9472;&#9472; hainan_me.bin
&#9500;&#9472;&#9472; hainan_pfp.bin
&#9500;&#9472;&#9472; hainan_rlc.bin
&#9500;&#9472;&#9472; hainan_smc.bin
&#9500;&#9472;&#9472; hawaii_ce.bin
&#9500;&#9472;&#9472; hawaii_k_smc.bin
&#9500;&#9472;&#9472; hawaii_mc.bin
&#9500;&#9472;&#9472; hawaii_me.bin
&#9500;&#9472;&#9472; hawaii_mec.bin
&#9500;&#9472;&#9472; hawaii_pfp.bin
&#9500;&#9472;&#9472; hawaii_rlc.bin
&#9500;&#9472;&#9472; hawaii_sdma1.bin
&#9500;&#9472;&#9472; hawaii_sdma.bin
&#9500;&#9472;&#9472; hawaii_smc.bin
&#9500;&#9472;&#9472; hawaii_uvd.bin
&#9500;&#9472;&#9472; hawaii_vce.bin
&#9500;&#9472;&#9472; kabini_ce.bin
&#9500;&#9472;&#9472; kabini_me.bin
&#9500;&#9472;&#9472; kabini_mec.bin
&#9500;&#9472;&#9472; kabini_pfp.bin
&#9500;&#9472;&#9472; kabini_rlc.bin
&#9500;&#9472;&#9472; kabini_sdma1.bin
&#9500;&#9472;&#9472; kabini_sdma.bin
&#9500;&#9472;&#9472; kabini_uvd.bin
&#9500;&#9472;&#9472; kabini_vce.bin
&#9500;&#9472;&#9472; kaveri_ce.bin
&#9500;&#9472;&#9472; kaveri_me.bin
&#9500;&#9472;&#9472; kaveri_mec2.bin
&#9500;&#9472;&#9472; kaveri_mec.bin
&#9500;&#9472;&#9472; kaveri_pfp.bin
&#9500;&#9472;&#9472; kaveri_rlc.bin
&#9500;&#9472;&#9472; kaveri_sdma1.bin
&#9500;&#9472;&#9472; kaveri_sdma.bin
&#9500;&#9472;&#9472; kaveri_uvd.bin
&#9500;&#9472;&#9472; kaveri_vce.bin
&#9500;&#9472;&#9472; mullins_ce.bin
&#9500;&#9472;&#9472; mullins_me.bin
&#9500;&#9472;&#9472; mullins_mec.bin
&#9500;&#9472;&#9472; mullins_pfp.bin
&#9500;&#9472;&#9472; mullins_rlc.bin
&#9500;&#9472;&#9472; mullins_sdma1.bin
&#9500;&#9472;&#9472; mullins_sdma.bin
&#9500;&#9472;&#9472; mullins_uvd.bin
&#9500;&#9472;&#9472; mullins_vce.bin
&#9500;&#9472;&#9472; navi10_asd.bin
&#9500;&#9472;&#9472; navi10_ce.bin
&#9500;&#9472;&#9472; navi10_gpu_info.bin
&#9500;&#9472;&#9472; navi10_me.bin
&#9500;&#9472;&#9472; navi10_mec2.bin
&#9500;&#9472;&#9472; navi10_mec.bin
&#9500;&#9472;&#9472; navi10_pfp.bin
&#9500;&#9472;&#9472; navi10_rlc.bin
&#9500;&#9472;&#9472; navi10_sdma1.bin
&#9500;&#9472;&#9472; navi10_sdma.bin
&#9500;&#9472;&#9472; navi10_smc.bin
&#9500;&#9472;&#9472; navi10_sos.bin
&#9500;&#9472;&#9472; navi10_ta.bin
&#9500;&#9472;&#9472; navi10_vcn.bin
&#9500;&#9472;&#9472; navi12_asd.bin
&#9500;&#9472;&#9472; navi12_ce.bin
&#9500;&#9472;&#9472; navi12_dmcu.bin
&#9500;&#9472;&#9472; navi12_gpu_info.bin
&#9500;&#9472;&#9472; navi12_me.bin
&#9500;&#9472;&#9472; navi12_mec2.bin
&#9500;&#9472;&#9472; navi12_mec.bin
&#9500;&#9472;&#9472; navi12_pfp.bin
&#9500;&#9472;&#9472; navi12_rlc.bin
&#9500;&#9472;&#9472; navi12_sdma1.bin
&#9500;&#9472;&#9472; navi12_sdma.bin
&#9500;&#9472;&#9472; navi12_smc.bin
&#9500;&#9472;&#9472; navi12_sos.bin
&#9500;&#9472;&#9472; navi12_ta.bin
&#9500;&#9472;&#9472; navi12_vcn.bin
&#9500;&#9472;&#9472; navi14_asd.bin
&#9500;&#9472;&#9472; navi14_ce.bin
&#9500;&#9472;&#9472; navi14_ce_wks.bin
&#9500;&#9472;&#9472; navi14_gpu_info.bin
&#9500;&#9472;&#9472; navi14_me.bin
&#9500;&#9472;&#9472; navi14_mec2.bin
&#9500;&#9472;&#9472; navi14_mec2_wks.bin
&#9500;&#9472;&#9472; navi14_mec.bin
&#9500;&#9472;&#9472; navi14_mec_wks.bin
&#9500;&#9472;&#9472; navi14_me_wks.bin
&#9500;&#9472;&#9472; navi14_pfp.bin
&#9500;&#9472;&#9472; navi14_pfp_wks.bin
&#9500;&#9472;&#9472; navi14_rlc.bin
&#9500;&#9472;&#9472; navi14_sdma1.bin
&#9500;&#9472;&#9472; navi14_sdma.bin
&#9500;&#9472;&#9472; navi14_smc.bin
&#9500;&#9472;&#9472; navi14_sos.bin
&#9500;&#9472;&#9472; navi14_ta.bin
&#9500;&#9472;&#9472; navi14_vcn.bin
&#9500;&#9472;&#9472; navy_flounder_ce.bin
&#9500;&#9472;&#9472; navy_flounder_dmcub.bin
&#9500;&#9472;&#9472; navy_flounder_me.bin
&#9500;&#9472;&#9472; navy_flounder_mec2.bin
&#9500;&#9472;&#9472; navy_flounder_mec.bin
&#9500;&#9472;&#9472; navy_flounder_pfp.bin
&#9500;&#9472;&#9472; navy_flounder_rlc.bin
&#9500;&#9472;&#9472; navy_flounder_sdma.bin
&#9500;&#9472;&#9472; navy_flounder_smc.bin
&#9500;&#9472;&#9472; navy_flounder_sos.bin
&#9500;&#9472;&#9472; navy_flounder_ta.bin
&#9500;&#9472;&#9472; navy_flounder_vcn.bin
&#9500;&#9472;&#9472; oland_ce.bin
&#9500;&#9472;&#9472; oland_k_smc.bin
&#9500;&#9472;&#9472; oland_mc.bin
&#9500;&#9472;&#9472; oland_me.bin
&#9500;&#9472;&#9472; oland_pfp.bin
&#9500;&#9472;&#9472; oland_rlc.bin
&#9500;&#9472;&#9472; oland_smc.bin
&#9500;&#9472;&#9472; oland_uvd.bin
&#9500;&#9472;&#9472; picasso_asd.bin
&#9500;&#9472;&#9472; picasso_ce.bin
&#9500;&#9472;&#9472; picasso_gpu_info.bin
&#9500;&#9472;&#9472; picasso_me.bin
&#9500;&#9472;&#9472; picasso_mec2.bin
&#9500;&#9472;&#9472; picasso_mec.bin
&#9500;&#9472;&#9472; picasso_pfp.bin
&#9500;&#9472;&#9472; picasso_rlc_am4.bin
&#9500;&#9472;&#9472; picasso_rlc.bin
&#9500;&#9472;&#9472; picasso_sdma.bin
&#9500;&#9472;&#9472; picasso_ta.bin
&#9500;&#9472;&#9472; picasso_vcn.bin
&#9500;&#9472;&#9472; pitcairn_ce.bin
&#9500;&#9472;&#9472; pitcairn_k_smc.bin
&#9500;&#9472;&#9472; pitcairn_mc.bin
&#9500;&#9472;&#9472; pitcairn_me.bin
&#9500;&#9472;&#9472; pitcairn_pfp.bin
&#9500;&#9472;&#9472; pitcairn_rlc.bin
&#9500;&#9472;&#9472; pitcairn_smc.bin
&#9500;&#9472;&#9472; pitcairn_uvd.bin
&#9500;&#9472;&#9472; polaris10_ce_2.bin
&#9500;&#9472;&#9472; polaris10_ce.bin
&#9500;&#9472;&#9472; polaris10_k2_smc.bin
&#9500;&#9472;&#9472; polaris10_k_mc.bin
&#9500;&#9472;&#9472; polaris10_k_smc.bin
&#9500;&#9472;&#9472; polaris10_mc.bin
&#9500;&#9472;&#9472; polaris10_me_2.bin
&#9500;&#9472;&#9472; polaris10_me.bin
&#9500;&#9472;&#9472; polaris10_mec2_2.bin
&#9500;&#9472;&#9472; polaris10_mec_2.bin
&#9500;&#9472;&#9472; polaris10_mec2.bin
&#9500;&#9472;&#9472; polaris10_mec.bin
&#9500;&#9472;&#9472; polaris10_pfp_2.bin
&#9500;&#9472;&#9472; polaris10_pfp.bin
&#9500;&#9472;&#9472; polaris10_rlc.bin
&#9500;&#9472;&#9472; polaris10_sdma1.bin
&#9500;&#9472;&#9472; polaris10_sdma.bin
&#9500;&#9472;&#9472; polaris10_smc.bin
&#9500;&#9472;&#9472; polaris10_smc_sk.bin
&#9500;&#9472;&#9472; polaris10_uvd.bin
&#9500;&#9472;&#9472; polaris10_vce.bin
&#9500;&#9472;&#9472; polaris11_ce_2.bin
&#9500;&#9472;&#9472; polaris11_ce.bin
&#9500;&#9472;&#9472; polaris11_k2_smc.bin
&#9500;&#9472;&#9472; polaris11_k_mc.bin
&#9500;&#9472;&#9472; polaris11_k_smc.bin
&#9500;&#9472;&#9472; polaris11_mc.bin
&#9500;&#9472;&#9472; polaris11_me_2.bin
&#9500;&#9472;&#9472; polaris11_me.bin
&#9500;&#9472;&#9472; polaris11_mec2_2.bin
&#9500;&#9472;&#9472; polaris11_mec_2.bin
&#9500;&#9472;&#9472; polaris11_mec2.bin
&#9500;&#9472;&#9472; polaris11_mec.bin
&#9500;&#9472;&#9472; polaris11_pfp_2.bin
&#9500;&#9472;&#9472; polaris11_pfp.bin
&#9500;&#9472;&#9472; polaris11_rlc.bin
&#9500;&#9472;&#9472; polaris11_sdma1.bin
&#9500;&#9472;&#9472; polaris11_sdma.bin
&#9500;&#9472;&#9472; polaris11_smc.bin
&#9500;&#9472;&#9472; polaris11_smc_sk.bin
&#9500;&#9472;&#9472; polaris11_uvd.bin
&#9500;&#9472;&#9472; polaris11_vce.bin
&#9500;&#9472;&#9472; polaris12_32_mc.bin
&#9500;&#9472;&#9472; polaris12_ce_2.bin
&#9500;&#9472;&#9472; polaris12_ce.bin
&#9500;&#9472;&#9472; polaris12_k_mc.bin
&#9500;&#9472;&#9472; polaris12_k_smc.bin
&#9500;&#9472;&#9472; polaris12_mc.bin
&#9500;&#9472;&#9472; polaris12_me_2.bin
&#9500;&#9472;&#9472; polaris12_me.bin
&#9500;&#9472;&#9472; polaris12_mec2_2.bin
&#9500;&#9472;&#9472; polaris12_mec_2.bin
&#9500;&#9472;&#9472; polaris12_mec2.bin
&#9500;&#9472;&#9472; polaris12_mec.bin
&#9500;&#9472;&#9472; polaris12_pfp_2.bin
&#9500;&#9472;&#9472; polaris12_pfp.bin
&#9500;&#9472;&#9472; polaris12_rlc.bin
&#9500;&#9472;&#9472; polaris12_sdma1.bin
&#9500;&#9472;&#9472; polaris12_sdma.bin
&#9500;&#9472;&#9472; polaris12_smc.bin
&#9500;&#9472;&#9472; polaris12_uvd.bin
&#9500;&#9472;&#9472; polaris12_vce.bin
&#9500;&#9472;&#9472; psp_13_0_0_sos.bin
&#9500;&#9472;&#9472; psp_13_0_0_ta.bin
&#9500;&#9472;&#9472; psp_13_0_11_ta.bin
&#9500;&#9472;&#9472; psp_13_0_11_toc.bin
&#9500;&#9472;&#9472; psp_13_0_4_ta.bin
&#9500;&#9472;&#9472; psp_13_0_4_toc.bin
&#9500;&#9472;&#9472; psp_13_0_5_asd.bin
&#9500;&#9472;&#9472; psp_13_0_5_ta.bin
&#9500;&#9472;&#9472; psp_13_0_5_toc.bin
&#9500;&#9472;&#9472; psp_13_0_7_sos.bin
&#9500;&#9472;&#9472; psp_13_0_7_ta.bin
&#9500;&#9472;&#9472; psp_13_0_8_asd.bin
&#9500;&#9472;&#9472; psp_13_0_8_ta.bin
&#9500;&#9472;&#9472; psp_13_0_8_toc.bin
&#9500;&#9472;&#9472; raven2_asd.bin
&#9500;&#9472;&#9472; raven2_ce.bin
&#9500;&#9472;&#9472; raven2_gpu_info.bin
&#9500;&#9472;&#9472; raven2_me.bin
&#9500;&#9472;&#9472; raven2_mec2.bin
&#9500;&#9472;&#9472; raven2_mec.bin
&#9500;&#9472;&#9472; raven2_pfp.bin
&#9500;&#9472;&#9472; raven2_rlc.bin
&#9500;&#9472;&#9472; raven2_sdma.bin
&#9500;&#9472;&#9472; raven2_ta.bin
&#9500;&#9472;&#9472; raven2_vcn.bin
&#9500;&#9472;&#9472; raven_asd.bin
&#9500;&#9472;&#9472; raven_ce.bin
&#9500;&#9472;&#9472; raven_dmcu.bin
&#9500;&#9472;&#9472; raven_gpu_info.bin
&#9500;&#9472;&#9472; raven_kicker_rlc.bin
&#9500;&#9472;&#9472; raven_me.bin
&#9500;&#9472;&#9472; raven_mec2.bin
&#9500;&#9472;&#9472; raven_mec.bin
&#9500;&#9472;&#9472; raven_pfp.bin
&#9500;&#9472;&#9472; raven_rlc.bin
&#9500;&#9472;&#9472; raven_sdma.bin
&#9500;&#9472;&#9472; raven_ta.bin
&#9500;&#9472;&#9472; raven_vcn.bin
&#9500;&#9472;&#9472; renoir_asd.bin
&#9500;&#9472;&#9472; renoir_ce.bin
&#9500;&#9472;&#9472; renoir_dmcub.bin
&#9500;&#9472;&#9472; renoir_gpu_info.bin
&#9500;&#9472;&#9472; renoir_me.bin
&#9500;&#9472;&#9472; renoir_mec2.bin
&#9500;&#9472;&#9472; renoir_mec.bin
&#9500;&#9472;&#9472; renoir_pfp.bin
&#9500;&#9472;&#9472; renoir_rlc.bin
&#9500;&#9472;&#9472; renoir_sdma.bin
&#9500;&#9472;&#9472; renoir_ta.bin
&#9500;&#9472;&#9472; renoir_vcn.bin
&#9500;&#9472;&#9472; sdma_5_2_6.bin
&#9500;&#9472;&#9472; sdma_5_2_7.bin
&#9500;&#9472;&#9472; sdma_6_0_0.bin
&#9500;&#9472;&#9472; sdma_6_0_1.bin
&#9500;&#9472;&#9472; sdma_6_0_2.bin
&#9500;&#9472;&#9472; si58_mc.bin
&#9500;&#9472;&#9472; sienna_cichlid_ce.bin
&#9500;&#9472;&#9472; sienna_cichlid_dmcub.bin
&#9500;&#9472;&#9472; sienna_cichlid_me.bin
&#9500;&#9472;&#9472; sienna_cichlid_mec2.bin
&#9500;&#9472;&#9472; sienna_cichlid_mec.bin
&#9500;&#9472;&#9472; sienna_cichlid_pfp.bin
&#9500;&#9472;&#9472; sienna_cichlid_rlc.bin
&#9500;&#9472;&#9472; sienna_cichlid_sdma.bin
&#9500;&#9472;&#9472; sienna_cichlid_smc.bin
&#9500;&#9472;&#9472; sienna_cichlid_sos.bin
&#9500;&#9472;&#9472; sienna_cichlid_ta.bin
&#9500;&#9472;&#9472; sienna_cichlid_vcn.bin
&#9500;&#9472;&#9472; smu_13_0_0.bin
&#9500;&#9472;&#9472; smu_13_0_7.bin
&#9500;&#9472;&#9472; stoney_ce.bin
&#9500;&#9472;&#9472; stoney_me.bin
&#9500;&#9472;&#9472; stoney_mec.bin
&#9500;&#9472;&#9472; stoney_pfp.bin
&#9500;&#9472;&#9472; stoney_rlc.bin
&#9500;&#9472;&#9472; stoney_sdma.bin
&#9500;&#9472;&#9472; stoney_uvd.bin
&#9500;&#9472;&#9472; stoney_vce.bin
&#9500;&#9472;&#9472; tahiti_ce.bin
&#9500;&#9472;&#9472; tahiti_k_smc.bin
&#9500;&#9472;&#9472; tahiti_mc.bin
&#9500;&#9472;&#9472; tahiti_me.bin
&#9500;&#9472;&#9472; tahiti_pfp.bin
&#9500;&#9472;&#9472; tahiti_rlc.bin
&#9500;&#9472;&#9472; tahiti_smc.bin
&#9500;&#9472;&#9472; tahiti_uvd.bin
&#9500;&#9472;&#9472; tonga_ce.bin
&#9500;&#9472;&#9472; tonga_k_smc.bin
&#9500;&#9472;&#9472; tonga_mc.bin
&#9500;&#9472;&#9472; tonga_me.bin
&#9500;&#9472;&#9472; tonga_mec2.bin
&#9500;&#9472;&#9472; tonga_mec.bin
&#9500;&#9472;&#9472; tonga_pfp.bin
&#9500;&#9472;&#9472; tonga_rlc.bin
&#9500;&#9472;&#9472; tonga_sdma1.bin
&#9500;&#9472;&#9472; tonga_sdma.bin
&#9500;&#9472;&#9472; tonga_smc.bin
&#9500;&#9472;&#9472; tonga_uvd.bin
&#9500;&#9472;&#9472; tonga_vce.bin
&#9500;&#9472;&#9472; topaz_ce.bin
&#9500;&#9472;&#9472; topaz_k_smc.bin
&#9500;&#9472;&#9472; topaz_mc.bin
&#9500;&#9472;&#9472; topaz_me.bin
&#9500;&#9472;&#9472; topaz_mec2.bin
&#9500;&#9472;&#9472; topaz_mec.bin
&#9500;&#9472;&#9472; topaz_pfp.bin
&#9500;&#9472;&#9472; topaz_rlc.bin
&#9500;&#9472;&#9472; topaz_sdma1.bin
&#9500;&#9472;&#9472; topaz_sdma.bin
&#9500;&#9472;&#9472; topaz_smc.bin
&#9500;&#9472;&#9472; vangogh_asd.bin
&#9500;&#9472;&#9472; vangogh_ce.bin
&#9500;&#9472;&#9472; vangogh_dmcub.bin
&#9500;&#9472;&#9472; vangogh_me.bin
&#9500;&#9472;&#9472; vangogh_mec2.bin
&#9500;&#9472;&#9472; vangogh_mec.bin
&#9500;&#9472;&#9472; vangogh_pfp.bin
&#9500;&#9472;&#9472; vangogh_rlc.bin
&#9500;&#9472;&#9472; vangogh_sdma.bin
&#9500;&#9472;&#9472; vangogh_toc.bin
&#9500;&#9472;&#9472; vangogh_vcn.bin
&#9500;&#9472;&#9472; vcn_3_1_2.bin
&#9500;&#9472;&#9472; vcn_4_0_0.bin
&#9500;&#9472;&#9472; vcn_4_0_2.bin
&#9500;&#9472;&#9472; vcn_4_0_4.bin
&#9500;&#9472;&#9472; vega10_acg_smc.bin
&#9500;&#9472;&#9472; vega10_asd.bin
&#9500;&#9472;&#9472; vega10_ce.bin
&#9500;&#9472;&#9472; vega10_gpu_info.bin
&#9500;&#9472;&#9472; vega10_me.bin
&#9500;&#9472;&#9472; vega10_mec2.bin
&#9500;&#9472;&#9472; vega10_mec.bin
&#9500;&#9472;&#9472; vega10_pfp.bin
&#9500;&#9472;&#9472; vega10_rlc.bin
&#9500;&#9472;&#9472; vega10_sdma1.bin
&#9500;&#9472;&#9472; vega10_sdma.bin
&#9500;&#9472;&#9472; vega10_smc.bin
&#9500;&#9472;&#9472; vega10_sos.bin
&#9500;&#9472;&#9472; vega10_uvd.bin
&#9500;&#9472;&#9472; vega10_vce.bin
&#9500;&#9472;&#9472; vega12_asd.bin
&#9500;&#9472;&#9472; vega12_ce.bin
&#9500;&#9472;&#9472; vega12_gpu_info.bin
&#9500;&#9472;&#9472; vega12_me.bin
&#9500;&#9472;&#9472; vega12_mec2.bin
&#9500;&#9472;&#9472; vega12_mec.bin
&#9500;&#9472;&#9472; vega12_pfp.bin
&#9500;&#9472;&#9472; vega12_rlc.bin
&#9500;&#9472;&#9472; vega12_sdma1.bin
&#9500;&#9472;&#9472; vega12_sdma.bin
&#9500;&#9472;&#9472; vega12_smc.bin
&#9500;&#9472;&#9472; vega12_sos.bin
&#9500;&#9472;&#9472; vega12_uvd.bin
&#9500;&#9472;&#9472; vega12_vce.bin
&#9500;&#9472;&#9472; vega20_asd.bin
&#9500;&#9472;&#9472; vega20_ce.bin
&#9500;&#9472;&#9472; vega20_me.bin
&#9500;&#9472;&#9472; vega20_mec2.bin
&#9500;&#9472;&#9472; vega20_mec.bin
&#9500;&#9472;&#9472; vega20_pfp.bin
&#9500;&#9472;&#9472; vega20_rlc.bin
&#9500;&#9472;&#9472; vega20_sdma1.bin
&#9500;&#9472;&#9472; vega20_sdma.bin
&#9500;&#9472;&#9472; vega20_smc.bin
&#9500;&#9472;&#9472; vega20_sos.bin
&#9500;&#9472;&#9472; vega20_ta.bin
&#9500;&#9472;&#9472; vega20_uvd.bin
&#9500;&#9472;&#9472; vega20_vce.bin
&#9500;&#9472;&#9472; vegam_ce.bin
&#9500;&#9472;&#9472; vegam_me.bin
&#9500;&#9472;&#9472; vegam_mec2.bin
&#9500;&#9472;&#9472; vegam_mec.bin
&#9500;&#9472;&#9472; vegam_pfp.bin
&#9500;&#9472;&#9472; vegam_rlc.bin
&#9500;&#9472;&#9472; vegam_sdma1.bin
&#9500;&#9472;&#9472; vegam_sdma.bin
&#9500;&#9472;&#9472; vegam_smc.bin
&#9500;&#9472;&#9472; vegam_uvd.bin
&#9500;&#9472;&#9472; vegam_vce.bin
&#9500;&#9472;&#9472; verde_ce.bin
&#9500;&#9472;&#9472; verde_k_smc.bin
&#9500;&#9472;&#9472; verde_mc.bin
&#9500;&#9472;&#9472; verde_me.bin
&#9500;&#9472;&#9472; verde_pfp.bin
&#9500;&#9472;&#9472; verde_rlc.bin
&#9500;&#9472;&#9472; verde_smc.bin
&#9500;&#9472;&#9472; verde_uvd.bin
&#9500;&#9472;&#9472; yellow_carp_asd.bin
&#9500;&#9472;&#9472; yellow_carp_ce.bin
&#9500;&#9472;&#9472; yellow_carp_dmcub.bin
&#9500;&#9472;&#9472; yellow_carp_me.bin
&#9500;&#9472;&#9472; yellow_carp_mec2.bin
&#9500;&#9472;&#9472; yellow_carp_mec.bin
&#9500;&#9472;&#9472; yellow_carp_pfp.bin
&#9500;&#9472;&#9472; yellow_carp_rlc.bin
&#9500;&#9472;&#9472; yellow_carp_sdma.bin
&#9500;&#9472;&#9472; yellow_carp_ta.bin
&#9500;&#9472;&#9472; yellow_carp_toc.bin
&#9492;&#9472;&#9472; yellow_carp_vcn.bin

0 directories, 541 files

```
It also exists as /usr/lib/firmware/amdgpu

The reason they match... Is that "/lib" is actually as symlink to "/usr/lib/"... 

IN YOUR LAST POST--> You just said that /usr/lib/firmware/amdgpu did not exist??? But in Post #5
> **treadmill855 said:**
> Only two show up:

```
$ [COLOR=#ff0000]ls /lib/firmware/amdgpu/*smu*.bin[/COLOR]
/lib/firmware/amdgpu/smu_13_0_0.bin  /lib/firmware/amdgpu/smu_13_0_7.bin
```
That query confirmed that that folder did exist, and with the filter, that at the least, the smu firmware that it is having troubles with was in that folder.

You do not need a pointer to the /lib/firmware, the Linux kernel is hardcoded to look in that folder for any firmware... If there was a problem with that pointer, then you would have many errors, and not just with "amdgpu". LOL AND-- You posted errors from dmesg. There would have been many "missing firmware" messages in syslog.

---

### Post by treadmill855 on 2023-08-15
Yes so when I went through the process of installing the PPA from earlier, it had me perform the following steps to backup and then remove the contents of that folder. 

```
apt update && apt dist-upgrade
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git ~/linux-firmware.tmp/linux-firmware
cd /lib
mv firmware firmware.bak
...
rm -r firmware/amdgpu/
cp -a ~/linux-firmware.tmp/linux-firmware/amdgpu/ firmware/
mv firmware firmware.goal
```

So I believe part of that process may have removed or changed what the computer might have been looking at, as far as what's in the "amdgpu" folder goes. I am not a Linux expert by any means, but if something has to get done like doing *update-grub* has to get done when you change the grub config files, then it wasn't done.

---

### Post by MAFoElffen on 2023-08-15
> **treadmill855 said:**
> Yes so when I went through the process of installing the PPA from earlier, it had me perform the following steps to backup and then remove the contents of that folder. 

```
apt update && apt dist-upgrade
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git ~/linux-firmware.tmp/linux-firmware
cd /lib
mv firmware firmware.bak
...
rm -r firmware/amdgpu/
cp -a ~/linux-firmware.tmp/linux-firmware/amdgpu/ firmware/
mv firmware firmware.goal
```

So I believe part of that process may have removed or changed what the computer might have been looking at, as far as what's in the "amdgpu" folder goes. I am not a Linux expert by any means, but if something has to get done like doing *update-grub* has to get done when you change the grub config files, then it wasn't done.
Let me fill in the blanks with that, using full path names, for a translation:
```

apt update && apt dist-upgrade  [COLOR=#0000ff]## Line #1[/COLOR]
mkdir $HOME/linux-firmware.tmp
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git $HOME/linux-firmware.tmp/linux-firmware
[COLOR=#ff0000]cd /lib[/COLOR]
sudo mv /lib/firmware /lib/firmware.bak
[COLOR=#008000]sudo apt install --reinstall linux-firmware[/COLOR] # get rid of cruft
[COLOR=#008000]sudo rm -r /lib/firmware/amdgpu/*[/COLOR]  ## This would prune off everything under /lib/firmware/amdgpu/
[COLOR=#008000]sudo cp -a $HOME/linux-firmware.tmp/linux-firmware/amdgpu/* /lib/firmware/amdgpu/[/COLOR] ## This would add everything back into that directory [COLOR=#0000ff]### Line #8[/COLOR] 
sudo mv /lib/firmware /lib/firmware.goal
sudo add-apt-repository ppa:darxus/linux-firmware-amdgpu-daily
sudo apt update && apt dist-upgrade
## There should be a command here, added below
[COLOR=#ff0000]sudo apt install --reinstall linux-firmware [/COLOR]## Only package in that PPA
# this should not output anything, unless upstream has updated in the last day:
diff -r /lib/firmware.goal /lib/firmware ## This would compare the two directories and point out any differences
  
```
I edited "his" commands for what I would do for that instead...

But since that PPA only has packages built for 20.04 and yours is 22.04, it never added linux-firmware back in, so that full /lib/firmware folder tree was still gone.

EDIT:
Look at my code notes in [COLOR=#0000ff]Blue[/COLOR] above... If you did [COLOR=#0000ff]Lines #1[/COLOR] through [COLOR=#0000ff]Line #8[/COLOR] and stop there... That is the instructions for people to manually update the linux-firmware to the latest from kernel.org(???) IDK why he did that twice... to use his own package from his repo, which should have been a duplicate of that process, but packaged. That would be so people did not have to do the manual process, and to try to save them work. (not double it.) I would have thought he would have known that. That is obvious to me.

---

### Post by treadmill855 on 2023-08-16
OK, so I think I am following along correctly and I thought I saw where I may have made a mistake. So I went through, created a second backup of everything in the firmware folder, and then followed *only* steps 1-8. I believe this should have gotten me the most up-to-date open source drivers into the amdgpu folder where the computer would be looking for them. But even after playing with all the grub settings I still have a blank output. 

Time for third party driver?

---

### Post by MAFoElffen on 2023-08-17
Yes. Time for the third party driver. We have tried everything else.

Crossing fingers.

---

### Post by treadmill855 on 2023-09-09
Hello to anyone coming here from the Google. As an update, I decided not to install the proprietary driver. In my experience this would just lead to more problems down the line. 

What I did do was get a spare NVME drive, take out the one with my Ubuntu installation on it, and install a fresh copy of Debian 12. When the computer started it had the exact same problem: gray/blank screen, display active but blank, and possible to SSH to the machine. None of the grub configurations worked there either. The Intel integrated video works perfectly though. 

My conclusion is that this is some sort of bug in the kernel or in the amdgpu driver for these specific cards. For reference the specific one I am using is the Gigabyte Radeon RX 6500 XT Eagle 4GB 64-bit GDDR6. I have a nearly identical machine (9th gen Intel i7 instead of 8th gen i7, but both have the same motherboard, bios, ram, now running latest Debian 12 Bookworm) and that one is using a Gigabyte Radeon Rx 5700 XT 8GB 256-Bit GDDR6 card with no issues running the amdgpu driver.

---

### Post by MAFoElffen on 2023-09-09
Thank you for returning and updating us on this. I was wondering how you were doing with this. Will have to add this card model to my notes, that it is "very challenged" and does not want to work with the opensource driver.

Feel free to PM me if a future kernel changes how the acts, and starts working again. I do care about that people enjoy Linux (whatever Distro they are using), and that they can do what they want to.

---

### Post by uusers on 2024-08-01
Hi, same problem, absolutely nothing helps.

[COLOR=#000000][FONT=Menlo]5.15.0-117-generic #127-Ubuntu SMP Fri Jul 5 20:13:28 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Ubuntu 22.04.4 LTS[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]**modprobe radeon**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**modprobe: ERROR: could not insert 'radeon': Invalid argument**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**modprobe amdgpu**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**modprobe: ERROR: could not insert 'amdgpu': Invalid argument**[/FONT][/COLOR]

And nothing from this forum thread.

[COLOR=#000000][FONT=Menlo]lshw -c video[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  *-display UNCLAIMED       [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       product: Kabini [Radeon HD 8210][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       vendor: Advanced Micro Devices, Inc. [AMD/ATI][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       physical id: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       bus info: pci@0000:00:01.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       version: 00[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       capabilities: pm pciexpress msi vga_controller bus_master cap_list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       configuration: latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       resources: memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:fea00000-fea3ffff memory:c0000-dffff[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  *-graphics[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       product: EFI VGA[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       physical id: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       logical name: /dev/fb0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       capabilities: fb[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]       configuration: depth=32 resolution=1280,1024

_Something to do with kernel, because I have lost driver functionality after upgraded from 20 to 22 LTS._ [/FONT][/COLOR]

---

