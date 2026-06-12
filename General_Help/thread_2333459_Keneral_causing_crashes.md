---
title: "Keneral causing crashes"
date: 2016-08-10
forum: General Help
---

### Post by rezam on 2016-08-10
Hello,

I have just installed a fresh version of ubuntu 14.04 on my computer. Unfortunately, firefox keeps crashing on startup/randomly. I cannot relate it to any specific behavior. Sometimes it works and sometimes it is just crashing. Please see below for the error report, I have no idea how to fix this.

Thanks! 

```

ProblemType: KernelOops
Annotation: Your system might become unstable now and might need to be restarted.
Date: Wed Aug 10 16:19:14 2016
Failure: oops
OopsText:
 general protection fault: 0000 [#1] SMP 
 Modules linked in: pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) rfcomm bnep bluetooth nls_iso8859_1 arc4 ath9k ath9k_common ath9k_hw amdkfd ath mac80211 kvm_amd kvm amd_iommu_v2 radeon input_leds snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec hp_wmi sparse_keymap ttm snd_hda_core snd_hwdep cfg80211 irqbypass crct10dif_pclmul crc32_pclmul aesni_intel snd_pcm drm_kms_helper aes_x86_64 lrw snd_seq_midi drm snd_seq_midi_event gf128mul snd_rawmidi glue_helper snd_seq snd_seq_device ablk_helper snd_timer cryptd snd serio_raw shpchp soundcore fam15h_power edac_mce_amd k10temp edac_core wmi i2c_algo_bit fb_sys_fops syscopyarea sysfillrect sysimgblt i2c_piix4 parport_pc video ppdev mac_hid lp parport hid_generic usbhid hid uas usb_storage ahci libahci r8169 mii fjes
 CPU: 0 PID: 2678 Comm: JS Helper Tainted: G    B      OE   4.4.0-34-generic #53~14.04.1-Ubuntu
 Hardware name: HP 550-167ng/2B35, BIOS A0.04 08/05/2015
 task: ffff880321430000 ti: ffff880306894000 task.ti: ffff880306894000
 RIP: 0010:[<ffffffff811aff33>]  [<ffffffff811aff33>] unmap_page_range+0x493/0x7b0
 RSP: 0018:ffff880306897ae0  EFLAGS: 00010207
 RAX: 1feed2477fee6800 RBX: ffff880306885990 RCX: 00000000ffff9626
 RDX: 0000000000000000 RSI: ffffea0000000000 RDI: 3c7fbba11dffb9a0
 RBP: ffff880306897ba8 R08: 0000000306b19067 R09: 0000000000000000
 R10: 0000000000000000 R11: 0000000000000c47 R12: 00007fbde7332000
 R13: ff77423bff73403c R14: ffff880306897c30 R15: 00007fbde7333000
 FS:  00007fbe0bdec700(0000) GS:ffff88033ec00000(0000) knlGS:0000000000000000
 CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
 CR2: 00007fbe0e057cd6 CR3: 0000000001c0c000 CR4: 00000000000406f0
 Stack:
  00007fbde76fffff 00007fbde7700000 00007fbde76fffff ffff88030cb8d7f8
  ffff88030cb8e7b8 00007fbde7700000 00007fbde76fffff 00000000000000ff
  ffff880321430000 00007fbde7700000 ffffea000c1a2170 ffff880306b199c8
 Call Trace:
  [<ffffffff811b02d1>] unmap_single_vma+0x81/0xf0
  [<ffffffff811b0bd7>] unmap_vmas+0x47/0x90
  [<ffffffff811b9b78>] exit_mmap+0x98/0x150
  [<ffffffff8107aaf7>] mmput+0x57/0x110
  [<ffffffff81080129>] do_exit+0x259/0xaf0
  [<ffffffff810f83b3>] ? __unqueue_futex+0x33/0x70
  [<ffffffff810f9001>] ? futex_wait+0x121/0x270
  [<ffffffff81080a3f>] do_group_exit+0x3f/0xa0
  [<ffffffff8108c16c>] get_signal+0x1cc/0x610
  [<ffffffff8102d478>] do_signal+0x28/0x6c0
  [<ffffffff811b30c0>] ? handle_mm_fault+0x250/0x540
  [<ffffffff8107873c>] exit_to_usermode_loop+0x59/0xa2
  [<ffffffff81003a6e>] syscall_return_slowpath+0x4e/0x60
  [<ffffffff817f74d8>] int_ret_from_sys_call+0x25/0x8f
 Code: ff 83 e8 1e 83 f8 01 0f 87 47 ff ff ff 48 b8 ff ff ff ff ff ff ff 01 48 be 00 00 00 00 00 ea ff ff 48 21 f8 48 c1 e0 06 48 01 f0 <48> 8b 10 83 e2 01 0f 84 f2 02 00 00 f6 40 08 01 0f 84 f0 01 00 
 RIP  [<ffffffff811aff33>] unmap_page_range+0x493/0x7b0
  RSP <ffff880306897ae0>
 ---[ end trace 1a85c8d85d5f2ed7 ]---
 
Package: linux-image-4.4.0-34-generic 4.4.0-34.53~14.04.1
SourcePackage: linux
Tags: kernel-oops
Uname: Linux 4.4.0-34-generic x86_64

```

---

### Post by &amp;KyT$0P# on 2016-08-10
That is a kernel problem, not a Firefox problem.  And given my past experience, I'd say it is highly unlikely that Firefox is the culprit.
Do you have VirtualBox installed or is this inside a VirtualBox VM?  What VirtualBox version?

EDIT Are you sure you're using 14.04?  If so, and if you don't need the HWE kernel for some specific hardware, try starting over but with 14.04.1 this time.

---

### Post by rezam on 2016-08-10
Well, I tried the two available kernels (after installation), I have issues on both 4.4.0-34 and 0-31.

I also have suddenly other issues I didnt have before, for instance software center sometimes crashes without any reason. Also I see a lot of gtk issues...and apt_check issues. So apparently it is not only related to firefox. 

The error reports I am receiving are extremly long. I have ubuntu also on my laptop, where it is working as it used to. I have absolutely now idea why I have suddenly so many issues... :-( I am open to try 14.04.01 or whatever solution might make sense...:(

---

### Post by &amp;KyT$0P# on 2016-08-10
Can't be really sure what will or won't have a chance to help without knowing the answers to these questions -
> **halogen2 said:**
> Do you have VirtualBox installed or is this inside a VirtualBox VM?  What VirtualBox version?

---

### Post by rezam on 2016-08-10
Surry for not being clear enough, I dont have a Virtualbox installed and it is also not inside a VM. It is installed on hard drive.

---

### Post by &amp;KyT$0P# on 2016-08-10
Ah, I take it [that mess]("https://ubuntuforums.org/showthread.php?t=2329454") got backported...
Yeah, try starting over with 14.04.1.  **Make sure to backup all important data first,** because it's best to format any involved partitions either before the install (or just select for the installer to do it).

---

### Post by rezam on 2016-08-10
alright, I just re-installed with 14.04.1 and updated everything:

- 3.13.0-93-generic
- Ubuntu 14.04.5 LTS

No Kernel crashes report until now (working on it for 2 minutes now, great, isnt it?).

I was even able to use fglrx, which was stated under my previous install (14.04.5 wth Kernel > 4), but not installed (which makes sense). I ve also tried 16.04 ... this was full of crash reports as well. I am really a huge ubuntu fan, I am quite surprised about all the issues I just faced. Hopefully, it no works as it used to..

---

