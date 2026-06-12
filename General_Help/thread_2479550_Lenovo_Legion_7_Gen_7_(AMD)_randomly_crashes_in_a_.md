---
title: "Lenovo Legion 7 Gen 7 (AMD) randomly crashes in a loop"
date: 2022-09-28
forum: General Help
---

### Post by Korkwin on 2022-09-28
Immediate apologies if this is the wrong section or a repost. I couldn't find anything already out there or a better section to drop this in.

Anyway, so I recently got a new laptop. The Lenovo Legion 7 Gen 7 (16ARHA7 82UH0001US) that comes with an AMD Ryzen 9 6900HX CPU and an integrated Radeon 680M as well as a dedicated RX 6850M XT graphics processors. As soon as I received the laptop, I upgraded the firmware, wiped the SSD and installed a dual boot setup with Windows 10 first and Kubuntu 22.04 second. I love the machine but that's not what this post is about.

So, while I am booted into Kubuntu 22.04, randomly this laptop will just reboot. I assume something is crashing and causing the reboot. What is very strange for me here is that the machine will work flawlessly for days, and then completely out of the blue it will just reboot while I'm using it. On top of that, when that first reboot/crash happens, it will keep doing it! If I let the machine boot up right after the reboot/crash and wait maybe 30 seconds after the display manager loads, it will reboot/crash again. And again. And again. The only way that I have been able to stop this cycle is to shut down the laptop and leave it alone for a few hours. After that, it's as if nothing ever happened, meaning I can boot up the machine with Kubuntu and use it as you would expect to. During these random episodes, the recovery mode doesn't seem to experience this. I do not experience this when booted into Windows 10. After a crash I can select Windows 10 from the grub menu and it will boot up and remain stable, but as soon as I reboot and try to get back into the lovely Kubuntu, the crash happens (well after the 30ish seconds as I previously mentioned).

I have experienced this issue both while running with the AC adapter connected and while using the laptop with the battery only. Whether my external monitors are connected or not it doesn't seem to matter. Same goes for any USB devices. Here's what else I have tried:

- Besides the stock kernel included (5.15), I have tried  kernel provided by the repo package linux-oem-22.04 and linux-oem-22.04a (5.17)
- The following Ubuntu kernels from the [kernal-ppa/mainline]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") 
     v6.0-rc3
     v5.19.5
- The XanMod 5.19 'Stable' kernel (linux-xanmod) from here: [XanMod]("https://xanmod.org/")

None of those kernels have changed the behavior at all.

I assume that this machine is simply too new for it's hardware to be in the hands of the masses/devs/testers and therefore I am running into a rather rare situation. I also assume it's probably an issue related to the GPU driver (which is why I figured a new kernel would solve it). But hey, you know what they say when you assume things.

Anyway, I imagine anyone who reads this is certainly going to want some logs, and for that I'm not really sure which logs to pull. I do see what appears to be some sort of a dump or trace that occurs whenever I run into the issue. I'm going to try and drop one of those below. Apologies for the formatting as I copied these from LNAV. I grabed the line that shows the kernel so you know that at least this one was with a stock Ubuntu kernel. These are from /var/log/syslog

```
&#9474;Sep 14 09:06:22 spacedust kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-5.15.0-47-generic root=UUID=801b16f9-7e5c-415f-ad34-21489a52deec ro quiet splash vt.handoff=7                              &#9474;
~~~~~~~~~~~~
&#9474;Sep 14 16:01:27 spacedust kernel: [24936.928793] [drm] PCIE GART of 512M enabled (table at 0x0000008000000000).                                                                                               &#9474;
&#9474;Sep 14 16:01:27 spacedust kernel: [24936.928818] [drm] PSP is resuming...                                                                                                                                     &#9508;
&#9474;Sep 14 16:01:27 spacedust kernel: [24937.021443] [drm] reserve 0xa00000 from 0x82fe000000 for PSP TMR                                                                                                         &#9508;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.109457] amdgpu 0000:03:00.0: amdgpu: RAS: optional ras ta ucode is not available                                                                                     &#9474;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.122395] amdgpu 0000:03:00.0: amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available                                                                          &#9508;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.122398] amdgpu 0000:03:00.0: amdgpu: SMU is resuming...                                                                                                              &#9508;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.122402] amdgpu 0000:03:00.0: amdgpu: smu driver if version = 0x0000000e, smu fw if version = 0x00000012, smu fw version = 0x00413500 (65.53.0)                       &#9474;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.122405] amdgpu 0000:03:00.0: amdgpu: SMU driver if version not matched                                                                                               &#9508;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.177618] amdgpu 0000:03:00.0: amdgpu: SMU is resumed successfully!                                                                                                    &#9508;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.178848] [drm] DMUB hardware initialized: version=0x0202000C                                                                                                          &#9474;
&#9474;Sep 14 16:01:28 spacedust kernel: [24937.840859] [drm:dce110_edp_wait_for_hpd_ready [amdgpu]] *ERROR* dce110_edp_wait_for_hpd_ready: wait timed out!                                                          &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.440189] [drm:dce110_edp_wait_for_hpd_ready [amdgpu]] *ERROR* dce110_edp_wait_for_hpd_ready: wait timed out!                                                          &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.442786] [drm] kiq ring mec 2 pipe 1 q 0                                                                                                                              &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447562] [drm] VCN decode and encode initialized successfully(under DPG Mode).                                                                                        &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447837] [drm] JPEG decode initialized successfully.                                                                                                                  &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447862] amdgpu 0000:03:00.0: amdgpu: ring gfx_0.0.0 uses VM inv eng 0 on hub 0                                                                                       &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447868] amdgpu 0000:03:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 1 on hub 0                                                                                      &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447871] amdgpu 0000:03:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 4 on hub 0                                                                                      &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447874] amdgpu 0000:03:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 5 on hub 0                                                                                      &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447876] amdgpu 0000:03:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 6 on hub 0                                                                                      &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447878] amdgpu 0000:03:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 7 on hub 0                                                                                      &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447880] amdgpu 0000:03:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 8 on hub 0                                                                                      &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447882] amdgpu 0000:03:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 9 on hub 0                                                                                      &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447884] amdgpu 0000:03:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 10 on hub 0                                                                                     &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447887] amdgpu 0000:03:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 11 on hub 0                                                                                      &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447890] amdgpu 0000:03:00.0: amdgpu: ring sdma0 uses VM inv eng 12 on hub 0                                                                                          &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447892] amdgpu 0000:03:00.0: amdgpu: ring sdma1 uses VM inv eng 13 on hub 0                                                                                          &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447894] amdgpu 0000:03:00.0: amdgpu: ring vcn_dec_0 uses VM inv eng 0 on hub 1                                                                                       &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447897] amdgpu 0000:03:00.0: amdgpu: ring vcn_enc_0.0 uses VM inv eng 1 on hub 1                                                                                     &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447899] amdgpu 0000:03:00.0: amdgpu: ring vcn_enc_0.1 uses VM inv eng 4 on hub 1                                                                                     &#9474;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.447901] amdgpu 0000:03:00.0: amdgpu: ring jpeg_dec uses VM inv eng 5 on hub 1                                                                                        &#9508;
&#9474;Sep 14 16:01:29 spacedust kernel: [24938.451712] amdgpu 0000:03:00.0: [drm] Cannot find any crtc or sizes                                                                                                     &#9508;
&#9474;Sep 14 16:01:33 spacedust kernel: [24942.547199] audit: type=1400 audit(1663185693.315:4432): apparmor="DENIED" operation="open" profile="snap.teams.teams" name="/sys/devices/virtual/net/lo/speed" pid=5379 &#9508;
&#9474;Sep 14 16:01:33 spacedust kernel: [24942.547206] audit: type=1400 audit(1663185693.315:4433): apparmor="DENIED" operation="open" profile="snap.teams.teams" name="/sys/devices/pci0000:00/0000:00:02.3/0000:05&#9508;
&#9474;Sep 14 16:01:33 spacedust kernel: [24942.547239] audit: type=1400 audit(1663185693.315:4434): apparmor="DENIED" operation="open" profile="snap.teams.teams" name="/sys/devices/pci0000:00/0000:00:02.2/0000:04&#9474;
&#9474;Sep 14 16:01:33 spacedust kernel: [24942.547254] audit: type=1400 audit(1663185693.315:4435): apparmor="DENIED" operation="open" profile="snap.teams.teams" name="/sys/devices/virtual/net/virbr0/speed" pid=5&#9508;
&#9474;Sep 14 16:01:33 spacedust kernel: [24942.547270] audit: type=1400 audit(1663185693.315:4436): apparmor="DENIED" operation="open" profile="snap.teams.teams" name="/sys/devices/virtual/net/vnet0/speed" pid=53&#9508;
&#9474;Sep 14 16:01:33 spacedust kernel: [24942.547276] audit: type=1400 audit(1663185693.315:4437): apparmor="DENIED" operation="open" profile="snap.teams.teams" name="/sys/devices/virtual/net/ppp0/speed" pid=537&#9508;
```


Here's another bunch of lines from /var/log/syslog but this time it is with the XanMod kernel running. Not posting to troubleshoot that kernel, just including it here because it does appear to have some more information.

```
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127058] ------------[ cut here ]------------                                                                                                                         &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127060] WARNING: CPU: 0 PID: 49499 at do_dentry_open+0x31d/0x380                                                                                                     &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127065] Modules linked in: hid_sensor_custom uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common videodev hid_sensor_hub hid_lenovo hidp r815&#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127100]  snd_rawmidi ecdh_generic mt76 serio_raw snd_hda_core ecc wmi_bmof hid_multitouch rapl mc cdc_acm k10temp joydev input_leds snd_hwdep snd_seq mac80211 snd_pc&#9508;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127152] CPU: 0 PID: 49499 Comm: TaskerWorker134 Not tainted 5.19.11-xanmod1 #0~20220924.git1592972                                                                   &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127154] Hardware name: LENOVO 82UH/LNVNB161216, BIOS K9CN34WW 07/22/2022                                                                                             &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127156] RIP: 0010:do_dentry_open+0x31d/0x380                                                                                                                         &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127158] Code: 28 c0 6e 62 a5 5b 5d 41 5c 41 5d 41 5e 41 5f c3 cc cc cc cc 48 8b 53 28 4c 8b 6a 70 4d 85 ed 0f 84 3c fe ff ff e9 21 fe ff ff <0f> 0b 41 bc ea ff ff ff&#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127159] RSP: 0018:ffffaf6bce7cbcb0 EFLAGS: 00010206                                                                                                                  &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127161] RAX: ffffffffa5651520 RBX: ffff8ffbd1613500 RCX: 00000000000f187d                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127162] RDX: 0000000000000020 RSI: d1e2f2955b99ed3a RDI: ffff8ffa951a8e80                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127162] RBP: ffff8ff7184db980 R08: ffff8ffa951a8e88 R09: 0000000000000001                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127163] R10: 0000000000000001 R11: 0000000000000040 R12: 0000000000001388                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127164] R13: ffffffffa4a05fb0 R14: ffff8ffbd1613510 R15: 0000000000000000                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127165] FS:  00007f085d921640(0000) GS:ffff8ffd41e00000(0000) knlGS:0000000000000000                                                                                 &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127167] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033                                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127168] CR2: 00007f086dbe0010 CR3: 000000013d05a000 CR4: 0000000000750ef0                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127169] PKRU: 55555554                                                                                                                                               &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127170] Call Trace:                                                                                                                                                  &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127171]  <TASK>                                                                                                                                                      &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127174]  path_openat+0xb23/0x1210                                                                                                                                    &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127178]  ? _copy_to_user+0x21/0x30                                                                                                                                   &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127181]  ? cp_new_stat+0x14b/0x180                                                                                                                                   &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127183]  do_filp_open+0xad/0x150                                                                                                                                     &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127185]  ? __check_object_size+0x1f0/0x250                                                                                                                           &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127188]  do_sys_openat2+0x95/0x160                                                                                                                                   &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127190]  __x64_sys_openat+0x4e/0x90                                                                                                                                  &#9508;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127192]  do_syscall_64+0x5c/0x90                                                                                                                                     &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127196]  ? exit_to_user_mode_prepare+0x2b/0x130                                                                                                                      &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127199]  entry_SYSCALL_64_after_hwframe+0x63/0xcd                                                                                                                    &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127202] RIP: 0033:0x7f08c0d148f3                                                                                                                                     &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127204] Code: 89 7c 24 18 44 89 54 24 0c e8 99 c1 f7 ff 44 8b 54 24 0c 8b 54 24 1c 41 89 c0 48 8b 74 24 10 8b 7c 24 18 b8 01 01 00 00 0f 05 <48> 3d 00 f0 ff ff 77 35&#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127205] RSP: 002b:00007f085d914520 EFLAGS: 00000293 ORIG_RAX: 0000000000000101                                                                                       &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127206] RAX: ffffffffffffffda RBX: 00007f07f002fcb2 RCX: 00007f08c0d148f3                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127207] RDX: 0000000000000000 RSI: 00007f07f002fcb3 RDI: 000000000000001c                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127207] RBP: 000000000000001c R08: 0000000000000000 R09: 0000000000000000                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127208] R10: 0000000000000000 R11: 0000000000000293 R12: 00007f07f00124dc                                                                                            &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127209] R13: 0000000000000000 R14: 00007f07f002fc90 R15: 0000000000000002                                                                                            &#9508;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127211]  </TASK>                                                                                                                                                     &#9474;
&#9474;Sep 28 16:02:50 spacedust kernel: [24219.127211] ---[ end trace 0000000000000000 ]---                                                                                                                         &#9474;
&#9474;Sep 28 16:02:51 spacedust kernel: [24219.405552] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:51 spacedust kernel: [24219.405558] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:51 spacedust kernel: [24219.864300] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:51 spacedust kernel: [24219.864305] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:51 spacedust kernel: [24220.093679] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:51 spacedust kernel: [24220.093684] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:52 spacedust kernel: [24220.514198] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:52 spacedust kernel: [24220.514204] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9508;
&#9474;Sep 28 16:02:52 spacedust kernel: [24220.972958] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:52 spacedust kernel: [24220.972965] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:52 spacedust kernel: [24221.202339] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:52 spacedust kernel: [24221.202342] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:53 spacedust kernel: [24221.431718] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:53 spacedust kernel: [24221.431723] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:53 spacedust kernel: [24221.890480] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:53 spacedust kernel: [24221.890484] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:53 spacedust kernel: [24222.119857] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9508;
&#9474;Sep 28 16:02:53 spacedust kernel: [24222.119860] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:53 spacedust kernel: [24222.349240] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?                                           &#9474;
&#9474;Sep 28 16:02:53 spacedust kernel: [24222.349246] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:54 spacedust kernel: [24222.807999] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:54 spacedust kernel: [24223.037380] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9508;
&#9474;Sep 28 16:02:54 spacedust kernel: [24223.266761] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:55 spacedust kernel: [24223.725515] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!                                                                                             &#9474;
&#9474;Sep 28 16:02:55 spacedust kernel: [24223.954898] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
```

UPDATE: It happened again today. It was crash free for about 6 days. This time I'm running the Ubuntu provided mainline kernel 6.0 (Linux spacedust 6.0.0-060000-generic #202210022231 SMP PREEMPT_DYNAMIC Sun Oct 2 22:35:09 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux)

/var/log/syslog around the time of the crash:
```
Oct  5 16:00:50 spacedust kernel: [177104.219113] kauditd_printk_skb: 10 callbacks suppressed
Oct  5 16:00:50 spacedust kernel: [177104.219117] audit: type=1400 audit(1665000050.688:6352): apparmor="DENIED" operation="open" profile="snap.firefox.firefox" name="/etc/fstab" pid=257418 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  5 16:00:50 spacedust dbus-daemon[1503]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.3823' (uid=1000 pid=257418 comm="/snap/firefox/1918/usr/lib/firefox/firefox ")
Oct  5 16:00:50 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser: OpenFile called with parameters:
Oct  5 16:00:50 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     handle:  "/org/freedesktop/portal/desktop/request/1_330/gtk447758218"
Oct  5 16:00:50 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     parent_window:  "x11:4000427"
Oct  5 16:00:50 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     title:  "File Upload"
Oct  5 16:00:50 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     options:  QMap(("current_filter", QVariant(QDBusArgument, ))("directory", QVariant(bool, false))("filters", QVariant(QDBusArgument, ))("modal", QVariant(bool, true))("multiple", QVariant(bool, false)))
Oct  5 16:00:50 spacedust systemd[1]: Starting Hostname Service...
Oct  5 16:00:50 spacedust dbus-daemon[1503]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct  5 16:00:50 spacedust systemd[1]: Started Hostname Service.
Oct  5 16:00:51 spacedust xdg-desktop-portal-kde[295670]: Qt: Session management error: networkIdsList argument is NULL
Oct  5 16:00:54 spacedust kernel: [177108.009852] audit: type=1400 audit(1665000054.480:6353): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/kubuntu-default-settings/kf5-settings/kdeglobals" pid=295458 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=
1000 ouid=0
Oct  5 16:00:54 spacedust kernel: [177108.009912] audit: type=1400 audit(1665000054.480:6354): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/corey/.config/kdedefaults/kdeglobals" pid=295458 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Oct  5 16:01:20 spacedust systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Oct  5 16:01:21 spacedust kernel: [177134.561948] [UFW BLOCK] IN=wlp4s0 OUT= MAC=3c:55:76:e9:7e:f3:ac:ae:19:07:ca:d4:08:00 SRC=192.168.77.35 DST=192.168.77.135 LEN=308 TOS=0x00 PREC=0x00 TTL=64 ID=987 DF PROTO=UDP SPT=1900 DPT=41395 LEN=288 
Oct  5 16:01:21 spacedust kernel: [177135.050339] [UFW BLOCK] IN=wlp4s0 OUT= MAC=3c:55:76:e9:7e:f3:ac:ae:19:07:ca:d4:08:00 SRC=192.168.77.35 DST=192.168.77.135 LEN=308 TOS=0x00 PREC=0x00 TTL=64 ID=990 DF PROTO=UDP SPT=1900 DPT=41395 LEN=288 
Oct  5 16:01:22 spacedust kernel: [177135.691954] [UFW BLOCK] IN=wlp4s0 OUT= MAC=3c:55:76:e9:7e:f3:ac:ae:19:07:ca:d4:08:00 SRC=192.168.77.35 DST=192.168.77.135 LEN=308 TOS=0x00 PREC=0x00 TTL=64 ID=1014 DF PROTO=UDP SPT=1900 DPT=41395 LEN=288 
Oct  5 16:01:23 spacedust kernel: [177137.357664] [UFW BLOCK] IN=wlp4s0 OUT= MAC=3c:55:76:e9:7e:f3:ac:ae:19:07:ca:d4:08:00 SRC=192.168.77.35 DST=192.168.77.135 LEN=308 TOS=0x00 PREC=0x00 TTL=64 ID=1115 DF PROTO=UDP SPT=1900 DPT=41395 LEN=288 
Oct  5 16:02:29 spacedust dbus-daemon[1503]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.3823' (uid=1000 pid=257418 comm="/snap/firefox/1918/usr/lib/firefox/firefox ")
Oct  5 16:02:29 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser: OpenFile called with parameters:
Oct  5 16:02:29 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     handle:  "/org/freedesktop/portal/desktop/request/1_330/gtk1034096283"
Oct  5 16:02:29 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     parent_window:  "x11:4000427"
Oct  5 16:02:29 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     title:  "File Upload"
Oct  5 16:02:29 spacedust xdg-desktop-portal-kde[4505]: xdp-kde-file-chooser:     options:  QMap(("current_filter", QVariant(QDBusArgument, ))("directory", QVariant(bool, false))("filters", QVariant(QDBusArgument, ))("modal", QVariant(bool, true))("multiple", QVariant(bool, false)))
Oct  5 16:02:29 spacedust systemd[1]: Starting Hostname Service...
Oct  5 16:02:30 spacedust dbus-daemon[1503]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct  5 16:02:30 spacedust systemd[1]: Started Hostname Service.
Oct  5 16:02:31 spacedust kernel: [177205.305017] audit: type=1400 audit(1665000151.776:6355): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/kubuntu-default-settings/kf5-settings/kdeglobals" pid=295458 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=
1000 ouid=0
Oct  5 16:02:31 spacedust kernel: [177205.305243] audit: type=1400 audit(1665000151.776:6356): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/corey/.config/kdedefaults/kdeglobals" pid=295458 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Oct  5 16:02:43 spacedust kernel: [177216.828109] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:43 spacedust kernel: [177216.828120] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:43 spacedust kernel: [177217.057467] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:43 spacedust kernel: [177217.057473] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:43 spacedust kernel: [177217.286842] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:43 spacedust kernel: [177217.286847] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:43 spacedust kernel: [177217.286889] Bluetooth: hci0: ACL packet for unknown connection handle 3837
Oct  5 16:02:44 spacedust kernel: [177217.554444] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:44 spacedust kernel: [177217.554449] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:44 spacedust kernel: [177217.783820] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:44 spacedust kernel: [177217.783825] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:44 spacedust kernel: [177218.013209] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:44 spacedust kernel: [177218.013216] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:44 spacedust kernel: [177218.242585] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:44 spacedust kernel: [177218.242591] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:44 spacedust kernel: [177218.249378] logitech-hidpp-device 0003:046D:406F.002A: hidpp20_batterylevel_get_battery_info: received protocol error 0x09
Oct  5 16:02:44 spacedust kernel: [177218.471963] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:44 spacedust kernel: [177218.471967] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:45 spacedust kernel: [177218.701357] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:45 spacedust kernel: [177218.701362] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:45 spacedust kernel: [177218.930726] amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:18 param:0x00000005 message:TransferTableSmu2Dram?
Oct  5 16:02:45 spacedust kernel: [177218.930733] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:45 spacedust kernel: [177219.160098] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:45 spacedust kernel: [177219.389473] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:46 spacedust kernel: [177219.618850] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:46 spacedust kernel: [177219.848227] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:46 spacedust kernel: [177220.077613] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:47 spacedust kernel: [177220.306987] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:47 spacedust kernel: [177220.536368] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:47 spacedust kernel: [177220.765745] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:47 spacedust kernel: [177220.995131] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
Oct  5 16:02:47 spacedust kernel: [177221.224505] amdgpu 0000:03:00.0: amdgpu: Failed to export SMU metrics table!
```

If there are better logs to show, or if I can somehow make them more verbose, do let me know. I would be happy to provide them, but it may take a few days as this issue is as far as I can tell totally random. If you made it this far, thank you. I'm willing to do whatever it takes to get this laptop to purr like a walrus.

---

### Post by Scott Deagan on 2023-08-20
Did you ever resolved this issue?

---

### Post by MAFoElffen on 2023-08-21
@Scott Deagan --
This is an old (dead) thread... If I had seen it, I would have advised him to update his amdgpu firmware. That was where his problem was/is. That is what the errors were saying.

If you are having a similar problem, instead of posting to a 10 month old thread that was unanswered, please start your own thread, geared towards yourself and your current problem, and I will help you.

---

### Post by Scott Deagan on 2023-08-21
Okay, will do...

---

