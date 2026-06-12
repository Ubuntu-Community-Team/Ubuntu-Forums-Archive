---
title: "I can't boot Ubuntu 22.04's live environment at all on my HP laptop."
date: 2022-07-24
forum: General Help
---

### Post by wowitskaylie on 2022-07-24
I've tried a lot of things, like multiple writing tools including raw dd, multiple isos like daily builds vs stable builds, multiple flash drives, I've tried all I could. Most other 22.04 distros fail to boot, except PopOS and the beta of Linux Mint 21. Neither use systemd-oomd so that might be it. What happens is "a start job is running for wait for udev to complete device initialization" shows on the screen for 15 minutes, and after that Network Name Resolution, Network Time Synchronization, and Userspace Out-Of-Memory (DOM) Killer get stuck in a loop forever. I've left it for literal weeks before and nothing's happened. What do I do????

---

### Post by oldfred on 2022-07-24
What model HP?
What video card/chip?

Have you updated UEFI and SSD firmware if you have SSD?

Most systems need UEFI settings.

 HP Spectre x360 15t  Optane issue
[https://ubuntuforums.org/showthread.php?t=2474790](https://ubuntuforums.org/showthread.php?t=2474790)
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)
HP Pavilion 15-eh1001ur laptop - Used Etcher in UEFI/gpt mode
[https://ubuntuforums.org/showthread.php?t=2466815](https://ubuntuforums.org/showthread.php?t=2466815)

HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10) & 
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)

---

### Post by wowitskaylie on 2022-07-25
Solved. For some reason, using a USB-C to USB-A adapter on the USB-C port makes it boot consistently. Not exactly sure why

---

### Post by wowitskaylie on 2022-07-26
Nevermind. Not even that works! I can install Ubuntu but if I try to boot my new install, it just loops trying to run User Login Management, Network Manager, Power Profiles Daemon, and Snap Daemon forever

---

### Post by wowitskaylie on 2022-07-26
I have an HP ENVY x360.

---

### Post by oldfred on 2022-07-26
Some other HP 360 systems. But there seem to be many versions.
But these may have some hints of a solution.
Did any of the HP links above help. HP's often have similar issues across models.

HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume) & 
[https://askubuntu.com/questions/1345338/common-failed-to-install-grub](https://askubuntu.com/questions/1345338/common-failed-to-install-grub)
HP X360 Update UEFI F20, probably newer now
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)

---

### Post by wowitskaylie on 2022-07-26
Thanks for the links, but none of these seem relevant to my issue. I was able to boot to the login screen once, but logging in didn't work. After rebooting its stuck on services just like last time.

---

### Post by ActionParsnip on 2022-07-26
Is this a dual boot system or single boot Ubuntu?
Do you have the latest BIOS?

---

### Post by wowitskaylie on 2022-07-26
Single-boot. Windows is no longer installed on this computer. I have not updated the BIOS/UEFI, but it was refurbished so its possible that it was updated by someone else in the past

---

### Post by ActionParsnip on 2022-07-26
Worth a check. You can see the BIOS version with
```

sudo dmidecode -t 1

```
Then check manufacturer's website

---

### Post by wowitskaylie on 2022-07-26
I'm unable to update the BIOS. The BIOS update is distributed as a .exe file, and the BIOS has no self-flash function that I can find

---

### Post by wowitskaylie on 2022-07-26
Turns out I need to use another Windows PC to write the tool to the flash drive

---

### Post by wowitskaylie on 2022-07-26
I don't have a Windows machine to do this with so I can't update it

---

### Post by wowitskaylie on 2022-07-26
I got it to boot again! I'm going to keep the laptop on until I can get any instructions on what commands to try in a TTY
edit: I cant even log into a tty. if i type my username it just sits there forever and never prompts me for a password

---

### Post by wowitskaylie on 2022-07-27
Reinstalled and masked systemd-oomd externally using chroot and now it works fine-ish. ive been able to boot and log in a few times but it also stalls on boot often (oddly not showing the splash screen)

---

### Post by stephenlofgren on 2022-10-10
> **ActionParsnip said:**
> Is this a dual boot system or single boot Ubuntu?
Do you have the latest BIOS?

I have a Dual boot HP Envy with the latest updates to the firmware and I get this error about 50% of the time.  It just cycles through messages
A start job is running for Network Time Synchronization
A start job is running for Network Name Resolution
A start job is running for Userspace Out-of-Memory (dom) Killer

I did find that I had a much better success rate when plugged in via usb-c.  Also interestingly it still fails just as much when powered using the supplied power adapter.

---

### Post by stephenlofgren on 2022-10-15
Because I can get it to boot when it is plugged in via USB-C I was able to compare successful and failed boot logs.  The first difference is 
__common_interrupt: 0.110 No irq handler for vector
not sure if that helps identify the root cause.

---

### Post by stephenlofgren on 2022-10-15
I reviewed the boot logs between the successful boot and the failure, this seems to be the first significant difference, this only happens when the usb-c power isn't connected.  Any help would be appreciated

```
Oct 15 06:52:26 HP-ENVY-x360 kernel: BUG: kernel NULL pointer dereference, address: 0000000000000058
Oct 15 06:52:26 HP-ENVY-x360 kernel: #PF: supervisor read access in kernel mode
Oct 15 06:52:26 HP-ENVY-x360 kernel: #PF: error_code(0x0000) - not-present page
Oct 15 06:52:26 HP-ENVY-x360 kernel: PGD 0 P4D 0 
Oct 15 06:52:26 HP-ENVY-x360 kernel: Oops: 0000 [#1] SMP NOPTI
Oct 15 06:52:26 HP-ENVY-x360 kernel: CPU: 1 PID: 128 Comm: kworker/1:1 Not tainted 5.15.0-48-generic #54-Ubuntu
Oct 15 06:52:26 HP-ENVY-x360 kernel: Hardware name: HP HP ENVY x360 Convertible 15m-ds0xxx/85DD, BIOS F.24 04/19/2022
Oct 15 06:52:26 HP-ENVY-x360 kernel: Workqueue: events_long ucsi_init_work [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel: RIP: 0010:typec_register_altmode+0x30/0x3b0 [typec]
Oct 15 06:52:26 HP-ENVY-x360 kernel: Code: 48 89 e5 41 57 41 56 41 55 49 89 f5 41 54 49 89 fc 48 8d bf 00 03 00 00 53 48 83 ec 30 65 48 8b 04 25 28 00 00 00 48 89 45 d0 <48> 8b 87 58 fd ff ff 48 3d 80 f7 32 c0 74 1a 49 8d 94 24 f0 02 00
Oct 15 06:52:26 HP-ENVY-x360 kernel: RSP: 0018:ffffa772005e3ca0 EFLAGS: 00010286
Oct 15 06:52:26 HP-ENVY-x360 kernel: RAX: 8483d548d779f800 RBX: ffff94554774d800 RCX: 0000000000000001
Oct 15 06:52:26 HP-ENVY-x360 kernel: RDX: 0000000000000000 RSI: ffffa772005e3d78 RDI: 0000000000000300
Oct 15 06:52:26 HP-ENVY-x360 kernel: RBP: ffffa772005e3cf8 R08: 0000000000000000 R09: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: kvm: Nested Virtualization enabled
Oct 15 06:52:26 HP-ENVY-x360 kernel: R13: ffffa772005e3d78 R14: ffffa772005e3d78 R15: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: kvm: Nested Paging enabled
Oct 15 06:52:26 HP-ENVY-x360 kernel: FS:  0000000000000000(0000) GS:ffff945bc0a40000(0000) knlGS:0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 15 06:52:26 HP-ENVY-x360 kernel: CR2: 0000000000000058 CR3: 0000000106b7a000 CR4: 00000000003506e0
Oct 15 06:52:26 HP-ENVY-x360 kernel: Call Trace:
Oct 15 06:52:26 HP-ENVY-x360 kernel:  <TASK>
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? wait_for_completion_timeout+0x1d/0x30
Oct 15 06:52:26 HP-ENVY-x360 kernel:  typec_partner_register_altmode+0xe/0x20 [typec]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_altmode.constprop.0+0x1f0/0x280 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_altmodes+0x156/0x210 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_check_altmodes+0x1c/0x50 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_port+0x4d4/0x510 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_init+0xce/0x1b0 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_init_work+0x16/0x30 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  process_one_work+0x22b/0x3d0
Oct 15 06:52:26 HP-ENVY-x360 kernel:  worker_thread+0x53/0x420
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? process_one_work+0x3d0/0x3d0
Oct 15 06:52:26 HP-ENVY-x360 kernel:  kthread+0x12a/0x150
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? set_kthread_struct+0x50/0x50
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ret_from_fork+0x22/0x30
Oct 15 06:52:26 HP-ENVY-x360 kernel:  </TASK>
Oct 15 06:52:26 HP-ENVY-x360 kernel: Modules linked in: snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec snd_hda_core snd_hwdep snd_pci_acp6x kvm_amd(+) snd_pcm nls_iso8859_1 fjes(-) kvm snd_seq_midi snd_seq_midi_event iommu_v2 rtw88_8822be crct10dif_pclmul ghash_clmulni_intel rtw88_8822b gpu_sched snd_rawmidi
Oct 15 06:52:26 HP-ENVY-x360 kernel: SEV supported: 16 ASIDs
Oct 15 06:52:26 HP-ENVY-x360 kernel:  rtw88_pci drm_ttm_helper aesni_intel btusb rtw88_core ttm input_leds crypto_simd btrtl btbcm cryptd btintel
Oct 15 06:52:26 HP-ENVY-x360 kernel: SEV-ES supported: 4294967295 ASIDs
Oct 15 06:52:26 HP-ENVY-x360 kernel:  hp_wmi sparse_keymap mac80211 snd_seq rapl serio_raw drm_kms_helper wmi_bmof platform_profile bluetooth snd_seq_device cec
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input16
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: Virtual VMLOAD VMSAVE supported
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 UNKNOWN as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input17
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 UNKNOWN as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input18
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 Stylus as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input19
Oct 15 06:52:26 HP-ENVY-x360 kernel: hid-multitouch 0018:04F3:2402.0004: input,hidraw0: I2C HID v1.00 Device [ELAN2514:00 04F3:2402] on i2c-ELAN2514:00
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ecdh_generic rc_core k10temp hid_multitouch(+) ecc snd_timer cfg80211 ccp i2c_algo_bit
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: Virtual GIF supported
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince//sanitized_helper" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer//sanitized_helper" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[552]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=552 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 kernel:  snd snd_pci_acp5x fb_sys_fops snd_rn_pci_acp3x syscopyarea
Oct 15 06:52:26 HP-ENVY-x360 kernel: i2c_hid_acpi i2c-ELAN2514:00: i2c_hid_get_input: IRQ triggered but there's no data
Oct 15 06:52:26 HP-ENVY-x360 kernel:  sysfillrect soundcore sysimgblt snd_pci_acp3x libarc4 ucsi_acpi typec_ucsi typec mac_hid hp_accel hid_sensor_magn_3d lis3lv02d amd_pmc wireless_hotkey hid_sensor_gyro_3d acpi_tad hid_sensor_accel_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf hid_sensor_iio_common industrialio sch_fq_codel ipmi_devintf ipmi_msghandler msr parport_pc ppdev lp parport ramoops reed_solomon pstore_blk pstore_zone drm efi_pstore ip_tables x_tables autofs4 rtsx_pci_sdmmc hid_sensor_hub nvme hid_generic xhci_pci crc32_pclmul i2c_piix4 amd_sfh nvme_core xhci_pci_renesas rtsx_pci wmi i2c_hid_acpi i2c_hid video hid
Oct 15 06:52:26 HP-ENVY-x360 kernel: CR2: 0000000000000058
Oct 15 06:52:26 HP-ENVY-x360 kernel: ---[ end trace b091059ee4714cbd ]---
```

---

### Post by ajgreeny on 2022-10-15
Thread merged with [https://ubuntuforums.org/showthread.php?t=2477432](https://ubuntuforums.org/showthread.php?t=2477432) about the same problem.

**Please don't confuse everybody, including yourself, by creating duplicate, or almost duplicate threads** as it will not help you solve the problem.

---

### Post by stephenlofgren on 2022-10-28
I reviewed the boot logs between the successful boot (with USB-C power) and the failure, this seems to be the first significant difference, this only happens when the usb-c power isn't connected. Any help would be appreciated

```
Oct 15 06:52:26 HP-ENVY-x360 kernel: BUG: kernel NULL pointer dereference, address: 0000000000000058
Oct 15 06:52:26 HP-ENVY-x360 kernel: #PF: supervisor read access in kernel mode
Oct 15 06:52:26 HP-ENVY-x360 kernel: #PF: error_code(0x0000) - not-present page
Oct 15 06:52:26 HP-ENVY-x360 kernel: PGD 0 P4D 0
Oct 15 06:52:26 HP-ENVY-x360 kernel: Oops: 0000 [#1] SMP NOPTI
Oct 15 06:52:26 HP-ENVY-x360 kernel: CPU: 1 PID: 128 Comm: kworker/1:1 Not tainted 5.15.0-48-generic #54-Ubuntu
Oct 15 06:52:26 HP-ENVY-x360 kernel: Hardware name: HP HP ENVY x360 Convertible 15m-ds0xxx/85DD, BIOS F.24 04/19/2022
Oct 15 06:52:26 HP-ENVY-x360 kernel: Workqueue: events_long ucsi_init_work [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel: RIP: 0010:typec_register_altmode+0x30/0x3b0 [typec]
Oct 15 06:52:26 HP-ENVY-x360 kernel: Code: 48 89 e5 41 57 41 56 41 55 49 89 f5 41 54 49 89 fc 48 8d bf 00 03 00 00 53 48 83 ec 30 65 48 8b 04 25 28 00 00 00 48 89 45 d0 <48> 8b 87 58 fd ff ff 48 3d 80 f7 32 c0 74 1a 49 8d 94 24 f0 02 00
Oct 15 06:52:26 HP-ENVY-x360 kernel: RSP: 0018:ffffa772005e3ca0 EFLAGS: 00010286
Oct 15 06:52:26 HP-ENVY-x360 kernel: RAX: 8483d548d779f800 RBX: ffff94554774d800 RCX: 0000000000000001
Oct 15 06:52:26 HP-ENVY-x360 kernel: RDX: 0000000000000000 RSI: ffffa772005e3d78 RDI: 0000000000000300
Oct 15 06:52:26 HP-ENVY-x360 kernel: RBP: ffffa772005e3cf8 R08: 0000000000000000 R09: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: kvm: Nested Virtualization enabled
Oct 15 06:52:26 HP-ENVY-x360 kernel: R13: ffffa772005e3d78 R14: ffffa772005e3d78 R15: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: kvm: Nested Paging enabled
Oct 15 06:52:26 HP-ENVY-x360 kernel: FS:  0000000000000000(0000) GS:ffff945bc0a40000(0000) knlGS:0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 15 06:52:26 HP-ENVY-x360 kernel: CR2: 0000000000000058 CR3: 0000000106b7a000 CR4: 00000000003506e0
Oct 15 06:52:26 HP-ENVY-x360 kernel: Call Trace:
Oct 15 06:52:26 HP-ENVY-x360 kernel:  <TASK>
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? wait_for_completion_timeout+0x1d/0x30
Oct 15 06:52:26 HP-ENVY-x360 kernel:  typec_partner_register_altmode+0xe/0x20 [typec]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_altmode.constprop.0+0x1f0/0x280 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_altmodes+0x156/0x210 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_check_altmodes+0x1c/0x50 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_port+0x4d4/0x510 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_init+0xce/0x1b0 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_init_work+0x16/0x30 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  process_one_work+0x22b/0x3d0
Oct 15 06:52:26 HP-ENVY-x360 kernel:  worker_thread+0x53/0x420
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? process_one_work+0x3d0/0x3d0
Oct 15 06:52:26 HP-ENVY-x360 kernel:  kthread+0x12a/0x150
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? set_kthread_struct+0x50/0x50
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ret_from_fork+0x22/0x30
Oct 15 06:52:26 HP-ENVY-x360 kernel:  </TASK>
Oct 15 06:52:26 HP-ENVY-x360 kernel: Modules linked in: snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec snd_hda_core snd_hwdep snd_pci_acp6x kvm_amd(+) snd_pcm nls_iso8859_1 fjes(-) kvm snd_seq_midi snd_seq_midi_event iommu_v2 rtw88_8822be crct10dif_pclmul ghash_clmulni_intel rtw88_8822b gpu_sched snd_rawmidi
Oct 15 06:52:26 HP-ENVY-x360 kernel: SEV supported: 16 ASIDs
Oct 15 06:52:26 HP-ENVY-x360 kernel:  rtw88_pci drm_ttm_helper aesni_intel btusb rtw88_core ttm input_leds crypto_simd btrtl btbcm cryptd btintel
Oct 15 06:52:26 HP-ENVY-x360 kernel: SEV-ES supported: 4294967295 ASIDs
Oct 15 06:52:26 HP-ENVY-x360 kernel:  hp_wmi sparse_keymap mac80211 snd_seq rapl serio_raw drm_kms_helper wmi_bmof platform_profile bluetooth snd_seq_device cec
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input16
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: Virtual VMLOAD VMSAVE supported
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 UNKNOWN as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input17
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 UNKNOWN as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input18
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 Stylus as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input19
Oct 15 06:52:26 HP-ENVY-x360 kernel: hid-multitouch 0018:04F3:2402.0004: input,hidraw0: I2C HID v1.00 Device [ELAN2514:00 04F3:2402] on i2c-ELAN2514:00
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ecdh_generic rc_core k10temp hid_multitouch(+) ecc snd_timer cfg80211 ccp i2c_algo_bit
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: Virtual GIF supported
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince//sanitized_helper" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer//sanitized_helper" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[552]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=552 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 kernel:  snd snd_pci_acp5x fb_sys_fops snd_rn_pci_acp3x syscopyarea
Oct 15 06:52:26 HP-ENVY-x360 kernel: i2c_hid_acpi i2c-ELAN2514:00: i2c_hid_get_input: IRQ triggered but there's no data
Oct 15 06:52:26 HP-ENVY-x360 kernel:  sysfillrect soundcore sysimgblt snd_pci_acp3x libarc4 ucsi_acpi typec_ucsi typec mac_hid hp_accel hid_sensor_magn_3d lis3lv02d amd_pmc wireless_hotkey hid_sensor_gyro_3d acpi_tad hid_sensor_accel_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf hid_sensor_iio_common industrialio sch_fq_codel ipmi_devintf ipmi_msghandler msr parport_pc ppdev lp parport ramoops reed_solomon pstore_blk pstore_zone drm efi_pstore ip_tables x_tables autofs4 rtsx_pci_sdmmc hid_sensor_hub nvme hid_generic xhci_pci crc32_pclmul i2c_piix4 amd_sfh nvme_core xhci_pci_renesas rtsx_pci wmi i2c_hid_acpi i2c_hid video hid
Oct 15 06:52:26 HP-ENVY-x360 kernel: CR2: 0000000000000058
Oct 15 06:52:26 HP-ENVY-x360 kernel: ---[ end trace b091059ee4714cbd ]---
```

---

### Post by oldfred on 2022-10-29
Is this the latest UEFI from HP for your system?
> BIOS F.24 04/19/2022

Older thread said UEFI update resolved some issues.
HP X360 Update UEFI F20, probably newer now
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)

 HP Spectre x360 15t  Optane issue
[https://ubuntuforums.org/showthread.php?t=2474790](https://ubuntuforums.org/showthread.php?t=2474790)

Older x360 threads may cover similar issue?
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086) & 
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

### Post by stephenlofgren on 2022-10-29
I reviewed the boot logs between the successful boot (with USB-C power) and the failure, this seems to be the first significant difference, this only happens when the usb-c power isn't connected. Any help would be appreciated

```
Oct 15 06:52:26 HP-ENVY-x360 kernel: BUG: kernel NULL pointer dereference, address: 0000000000000058
Oct 15 06:52:26 HP-ENVY-x360 kernel: #PF: supervisor read access in kernel mode
Oct 15 06:52:26 HP-ENVY-x360 kernel: #PF: error_code(0x0000) - not-present page
Oct 15 06:52:26 HP-ENVY-x360 kernel: PGD 0 P4D 0
Oct 15 06:52:26 HP-ENVY-x360 kernel: Oops: 0000 [#1] SMP NOPTI
Oct 15 06:52:26 HP-ENVY-x360 kernel: CPU: 1 PID: 128 Comm: kworker/1:1 Not tainted 5.15.0-48-generic #54-Ubuntu
Oct 15 06:52:26 HP-ENVY-x360 kernel: Hardware name: HP HP ENVY x360 Convertible 15m-ds0xxx/85DD, BIOS F.24 04/19/2022
Oct 15 06:52:26 HP-ENVY-x360 kernel: Workqueue: events_long ucsi_init_work [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel: RIP: 0010:typec_register_altmode+0x30/0x3b0 [typec]
Oct 15 06:52:26 HP-ENVY-x360 kernel: Code: 48 89 e5 41 57 41 56 41 55 49 89 f5 41 54 49 89 fc 48 8d bf 00 03 00 00 53 48 83 ec 30 65 48 8b 04 25 28 00 00 00 48 89 45 d0 <48> 8b 87 58 fd ff ff 48 3d 80 f7 32 c0 74 1a 49 8d 94 24 f0 02 00
Oct 15 06:52:26 HP-ENVY-x360 kernel: RSP: 0018:ffffa772005e3ca0 EFLAGS: 00010286
Oct 15 06:52:26 HP-ENVY-x360 kernel: RAX: 8483d548d779f800 RBX: ffff94554774d800 RCX: 0000000000000001
Oct 15 06:52:26 HP-ENVY-x360 kernel: RDX: 0000000000000000 RSI: ffffa772005e3d78 RDI: 0000000000000300
Oct 15 06:52:26 HP-ENVY-x360 kernel: RBP: ffffa772005e3cf8 R08: 0000000000000000 R09: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: kvm: Nested Virtualization enabled
Oct 15 06:52:26 HP-ENVY-x360 kernel: R13: ffffa772005e3d78 R14: ffffa772005e3d78 R15: 0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: kvm: Nested Paging enabled
Oct 15 06:52:26 HP-ENVY-x360 kernel: FS:  0000000000000000(0000) GS:ffff945bc0a40000(0000) knlGS:0000000000000000
Oct 15 06:52:26 HP-ENVY-x360 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 15 06:52:26 HP-ENVY-x360 kernel: CR2: 0000000000000058 CR3: 0000000106b7a000 CR4: 00000000003506e0
Oct 15 06:52:26 HP-ENVY-x360 kernel: Call Trace:
Oct 15 06:52:26 HP-ENVY-x360 kernel:  <TASK>
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? wait_for_completion_timeout+0x1d/0x30
Oct 15 06:52:26 HP-ENVY-x360 kernel:  typec_partner_register_altmode+0xe/0x20 [typec]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_altmode.constprop.0+0x1f0/0x280 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_altmodes+0x156/0x210 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_check_altmodes+0x1c/0x50 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_register_port+0x4d4/0x510 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_init+0xce/0x1b0 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ucsi_init_work+0x16/0x30 [typec_ucsi]
Oct 15 06:52:26 HP-ENVY-x360 kernel:  process_one_work+0x22b/0x3d0
Oct 15 06:52:26 HP-ENVY-x360 kernel:  worker_thread+0x53/0x420
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? process_one_work+0x3d0/0x3d0
Oct 15 06:52:26 HP-ENVY-x360 kernel:  kthread+0x12a/0x150
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ? set_kthread_struct+0x50/0x50
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ret_from_fork+0x22/0x30
Oct 15 06:52:26 HP-ENVY-x360 kernel:  </TASK>
Oct 15 06:52:26 HP-ENVY-x360 kernel: Modules linked in: snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec snd_hda_core snd_hwdep snd_pci_acp6x kvm_amd(+) snd_pcm nls_iso8859_1 fjes(-) kvm snd_seq_midi snd_seq_midi_event iommu_v2 rtw88_8822be crct10dif_pclmul ghash_clmulni_intel rtw88_8822b gpu_sched snd_rawmidi
Oct 15 06:52:26 HP-ENVY-x360 kernel: SEV supported: 16 ASIDs
Oct 15 06:52:26 HP-ENVY-x360 kernel:  rtw88_pci drm_ttm_helper aesni_intel btusb rtw88_core ttm input_leds crypto_simd btrtl btbcm cryptd btintel
Oct 15 06:52:26 HP-ENVY-x360 kernel: SEV-ES supported: 4294967295 ASIDs
Oct 15 06:52:26 HP-ENVY-x360 kernel:  hp_wmi sparse_keymap mac80211 snd_seq rapl serio_raw drm_kms_helper wmi_bmof platform_profile bluetooth snd_seq_device cec
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input16
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: Virtual VMLOAD VMSAVE supported
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 UNKNOWN as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input17
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 UNKNOWN as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input18
Oct 15 06:52:26 HP-ENVY-x360 kernel: input: ELAN2514:00 04F3:2402 Stylus as /devices/platform/AMDI0010:00/i2c-0/i2c-ELAN2514:00/0018:04F3:2402.0004/input/input19
Oct 15 06:52:26 HP-ENVY-x360 kernel: hid-multitouch 0018:04F3:2402.0004: input,hidraw0: I2C HID v1.00 Device [ELAN2514:00 04F3:2402] on i2c-ELAN2514:00
Oct 15 06:52:26 HP-ENVY-x360 kernel:  ecdh_generic rc_core k10temp hid_multitouch(+) ecc snd_timer cfg80211 ccp i2c_algo_bit
Oct 15 06:52:26 HP-ENVY-x360 kernel: SVM: Virtual GIF supported
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince//sanitized_helper" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer//sanitized_helper" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[544]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=544 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 audit[552]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=552 comm="apparmor_parser"
Oct 15 06:52:26 HP-ENVY-x360 kernel:  snd snd_pci_acp5x fb_sys_fops snd_rn_pci_acp3x syscopyarea
Oct 15 06:52:26 HP-ENVY-x360 kernel: i2c_hid_acpi i2c-ELAN2514:00: i2c_hid_get_input: IRQ triggered but there's no data
Oct 15 06:52:26 HP-ENVY-x360 kernel:  sysfillrect soundcore sysimgblt snd_pci_acp3x libarc4 ucsi_acpi typec_ucsi typec mac_hid hp_accel hid_sensor_magn_3d lis3lv02d amd_pmc wireless_hotkey hid_sensor_gyro_3d acpi_tad hid_sensor_accel_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf hid_sensor_iio_common industrialio sch_fq_codel ipmi_devintf ipmi_msghandler msr parport_pc ppdev lp parport ramoops reed_solomon pstore_blk pstore_zone drm efi_pstore ip_tables x_tables autofs4 rtsx_pci_sdmmc hid_sensor_hub nvme hid_generic xhci_pci crc32_pclmul i2c_piix4 amd_sfh nvme_core xhci_pci_renesas rtsx_pci wmi i2c_hid_acpi i2c_hid video hid
Oct 15 06:52:26 HP-ENVY-x360 kernel: CR2: 0000000000000058
Oct 15 06:52:26 HP-ENVY-x360 kernel: ---[ end trace b091059ee4714cbd ]---
```

---

### Post by C.S.Cameron on 2022-10-30
Have you tried letting UEFI boot the device?
- Create a 5GB FAT32 partition on the disk.
- Extract the Ubuntu ISO files to the FAT32 partition.
- When booting press F9 to start Live USB or Installation. 

The above works for me but 22.04.1 is crap on my HP EliteBook 8560w.

---

### Post by tto90 on 2022-11-29
I have exactly the same problem with my HP envy x360 13. Updating BIOS didn't help. The only solution is to plug some device into USB-C port. Works with either phone or Ethernet adapter. Otherwise, I wait for infinity but booting process stalls at "a start job is running for wait for ...."

---

