---
title: "Chromium-browser fatal error"
date: 2013-03-19
forum: General Help
---

### Post by Kotrfa on 2013-03-19
Hi.
I have problem with chromium-browse v[COLOR=#303942][FONT=Ubuntu]ersion 25.0.1364.160 Ubuntu 13.04 (25.0.1364.160-0ubuntu1b1) using GNOME 3.
Time to time (I can't figure out what is cause) I get terrible error and I need to restart computer (using hardware power button). In /var/log/syslog I found that error. 



[/FONT][/COLOR]```
Mar 19 16:43:50 dan530u kernel: [   18.477095] chromium-browse: Corrupted page table at address 4e91f000
Mar 19 16:43:50 dan530u kernel: [   18.477147] *pdpt = 0000000000000000 *pde = 03b40008304285b6 
Mar 19 16:43:50 dan530u kernel: [   18.477184] Bad pagetable: 000f [#1] SMP 
Mar 19 16:43:50 dan530u kernel: [   18.477209] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek joydev(F) coretemp kvm_intel kvm aesni_intel(F) aes_i586(F) xts(F) lrw(F) gf128mul(F) ablk_helper(F) cryptd(F) samsung_laptop microcode(F) arc4(F) iwldvm snd_hda_intel snd_hda_codec mac80211 snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) uvcvideo snd_seq_midi_event(F) i915 bnep snd_rawmidi(F) videobuf2_vmalloc rfcomm iwlwifi videobuf2_memops videobuf2_core btusb psmouse(F) snd_seq(F) bluetooth videodev parport_pc(F) ppdev(F) snd_seq_device(F) snd_timer(F) serio_raw(F) video(F) lpc_ich drm_kms_helper mac_hid snd(F) cfg80211 mei soundcore(F) drm i2c_algo_bit lp(F) parport(F) nls_iso8859_1(F) hid_generic usbhid hid r8169 ahci(F) libahci(F)
Mar 19 16:43:50 dan530u kernel: [   18.477646] Pid: 2228, comm: chromium-browse Tainted: GF            3.8.0-13-generic #22-Ubuntu SAMSUNG ELECTRONICS CO., LTD. 530U3BI/530U4BI/530U4BH/530U3BI/530U4BI/530U4BH
Mar 19 16:43:50 dan530u kernel: [   18.477722] EIP: 0073:[<b3b2ef37>] EFLAGS: 00210202 CPU: 0
Mar 19 16:43:50 dan530u kernel: [   18.477752] EIP is at 0xb3b2ef37
Mar 19 16:43:50 dan530u kernel: [   18.477770] EAX: 4e91f000 EBX: b793dc08 ECX: 00000001 EDX: 00000057
Mar 19 16:43:50 dan530u kernel: [   18.477802] ESI: bf81a540 EDI: bf81a58c EBP: bf81a52c ESP: bf81a4c0
Mar 19 16:43:50 dan530u kernel: [   18.477834]  DS: 007b ES: 007b FS: 0000 GS: 0033 SS: 007b
Mar 19 16:43:50 dan530u kernel: [   18.477862] Process chromium-browse (pid: 2228, ti=ee334000 task=ee1c3340 task.ti=ee334000)
Mar 19 16:43:50 dan530u kernel: [   18.477904] 
Mar 19 16:43:50 dan530u kernel: [   18.477913] EIP: [<b3b2ef37>] 0xb3b2ef37 SS:ESP 007b:bf81a4c0
Mar 19 16:43:50 dan530u kernel: [   18.488945] ---[ end trace 7db39dc0fc051b49 ]---
```[COLOR=#303942][FONT=Ubuntu]

Does anybody have any idea? Shoud I reported it as a bug? Thanks[/FONT][/COLOR]

---

