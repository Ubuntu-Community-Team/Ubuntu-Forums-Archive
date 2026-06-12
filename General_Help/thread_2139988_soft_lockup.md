---
title: "soft lockup"
date: 2013-04-28
forum: General Help
---

### Post by rtalcott on 2013-04-28
about 70% of the time starting with 13.04 I have one machine reporting:

soft lockup  cpu#0  stuck for 22s  [migration/0:8]

No problem with Debian, Fedora, BSd etc...

any ideas on how to fix this?

---

### Post by mooreted on 2013-04-28
I just got this too: CPU#0 Stuck [USB Modeset 982] (or something like that). There are no errors in the logs and after a power cycle it comes up and runs fine.

I'll watch this thread and keep Googling. If I find something I'll post it here. So far I get the impression it's a kernel bug.

---

### Post by rtalcott on 2013-04-28
Thank You!  I have been googling too...this is very annoying....I have the problem on 60-70% of my boots.
rt

---

### Post by Elfy on 2013-04-28
I've had this once or twice myself, never did get to the bottom of it.

I've seen some bugs very similar to this on previous versions. Not found anything for 13.04.

Moved the thread as well - U+1 is for dev versions.

---

### Post by mooreted on 2013-04-28
I have top of the line hardware and it ran fine until I upgraded to 13.04. I just read syslog, kernel.log, dmesg and no errors.

They are going to want to know what we're running. Mine is:

Ubuntu 13.04 x64
Nvidia 460GTX - Driver: 313.30
8GB RAM

Output of lsusb:

lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 004: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 001 Device 005: ID 05ac:911f Apple, Inc. 
Bus 001 Device 006: ID 05ac:921e Apple, Inc. Cinema Display 24"

---

### Post by mooreted on 2013-04-28
I found this in launchpad that refers to a bug in the 3.5 kernel. Maybe it's a regression:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011914](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011914)

---

### Post by pqwoerituytrueiwoq on 2013-04-28
i have the same issue the solution is to use the mainline kernel
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

the hard part is booting the system so you can install it
edit: i had to do this

[LIST=1]
[*]boot recovery move 
[*]enable networking 
[*]install openssh-server 
[*]run ifconfig to get my ip address 
[*]ssh into it from my laptop so i could install it 
[/LIST]

---

### Post by mooreted on 2013-04-28
As OP stated, it doesn't happen every time. This is the first time for me, so we should be able to test mainline and see if that fixes it.

Thanks for the help.

---

### Post by mooreted on 2013-04-28
Ok, now running: 3.8.9-030809-generic

We'll see how it goes.

---

### Post by imbjr on 2013-04-28
I've just seen this happen on an unmount:

Apr 28 22:43:56 pc udisksd[2068]: Cleaning up mount point /media/imbjr/QUANTAL_64 (device 8:9 is not mounted)
Apr 28 22:44:22 pc kernel: [24935.572422] BUG: soft lockup - CPU#1 stuck for 23s! [umount:31063]
Apr 28 22:44:22 pc kernel: [24935.572425] Modules linked in: nfsv4(F) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm bluetooth parport_pc(F) ppdev(F) vesafb(F) nfsd(F) auth_rpcgss(F) nfs_acl(F) nfs(F) lockd(F) sunrpc(F) fscache(F) tda8290 tda10048 cx23885 joydev(F) btcx_risc altera_ci wacom videobuf_dvb tda18271 altera_stapl tveeprom cx2341x fglrx(POF) coretemp kvm_intel videobuf_dma_sg dvb_core kvm snd_hda_codec_hdmi rc_core snd_hda_codec_realtek v4l2_common snd_hda_intel videobuf_core snd_hda_codec videodev snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) ghash_clmulni_intel(F) snd_rawmidi(F) aesni_intel(F) snd_seq(F) aes_x86_64(F) xts(F) lrw(F) gf128mul(F) snd_seq_device(F) ablk_helper(F) snd_timer(F) psmouse(F) snd(F) soundcore(F) cryptd(F) mei amd_iommu_v2 lpc_ich dcdbas serio_raw(F) microcode(F) mac_hid lp(F) parport(F) usb_storage(F) hid_generic usbhid hid tg3 ptp pps_core ahci(F) libahci(F)
Apr 28 22:44:22 pc kernel: [24935.572487] CPU 1 
Apr 28 22:44:22 pc kernel: [24935.572491] Pid: 31063, comm: umount Tainted: PF          O 3.8.0-19-generic #29-Ubuntu Dell Inc. XPS 8300  /0Y2MRG
Apr 28 22:44:22 pc kernel: [24935.572493] RIP: 0010:[<ffffffff81044af8>]  [<ffffffff81044af8>] __ticket_spin_unlock+0x8/0x10
Apr 28 22:44:22 pc kernel: [24935.572501] RSP: 0000:ffff8801f026fe08  EFLAGS: 00000282
Apr 28 22:44:22 pc kernel: [24935.572503] RAX: 00000000c729c729 RBX: 0000000000000005 RCX: 000000000000c729
Apr 28 22:44:22 pc kernel: [24935.572505] RDX: 000000000000c729 RSI: ffff8801ca6fb6a8 RDI: ffff8801ca6fba38
Apr 28 22:44:22 pc kernel: [24935.572507] RBP: ffff8801f026fe08 R08: 0000000000000002 R09: 0000000000000002
Apr 28 22:44:22 pc kernel: [24935.572509] R10: 0000000000000005 R11: 0000000000000000 R12: ffff8801f026fd70
Apr 28 22:44:22 pc kernel: [24935.572510] R13: ffff8801f026fdf8 R14: ffffffff811396e6 R15: 0000000000000000
Apr 28 22:44:22 pc kernel: [24935.572513] FS:  00007ff82122d840(0000) GS:ffff88022f480000(0000) knlGS:0000000000000000
Apr 28 22:44:22 pc kernel: [24935.572515] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Apr 28 22:44:22 pc kernel: [24935.572516] CR2: 00007fde5650d000 CR3: 000000010fd37000 CR4: 00000000000407e0
Apr 28 22:44:22 pc kernel: [24935.572518] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Apr 28 22:44:22 pc kernel: [24935.572520] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Apr 28 22:44:22 pc kernel: [24935.572522] Process umount (pid: 31063, threadinfo ffff8801f026e000, task ffff8801d6f78000)
Apr 28 22:44:22 pc kernel: [24935.572523] Stack:
Apr 28 22:44:22 pc kernel: [24935.572525]  ffff8801f026fe50 ffffffff811d56f3 0000000000000000 ffff88021fb53ca0
Apr 28 22:44:22 pc kernel: [24935.572529]  ffff88021fb53c00 ffff88021fb53ca0 ffffffff8182a420 ffff8801cf93b400
Apr 28 22:44:22 pc kernel: [24935.572532]  ffff8801cf93b420 ffff8801f026fe78 ffffffff81195fab ffff880226428d00
Apr 28 22:44:22 pc kernel: [24935.572535] Call Trace:
Apr 28 22:44:22 pc kernel: [24935.572542]  [<ffffffff811d56f3>] fsnotify_unmount_inodes+0x133/0x1b0
Apr 28 22:44:22 pc kernel: [24935.572546]  [<ffffffff81195fab>] generic_shutdown_super+0x4b/0xf0
Apr 28 22:44:22 pc kernel: [24935.572550]  [<ffffffff81196080>] kill_block_super+0x30/0x80
Apr 28 22:44:22 pc kernel: [24935.572553]  [<ffffffff81196467>] deactivate_locked_super+0x57/0x80
Apr 28 22:44:22 pc kernel: [24935.572556]  [<ffffffff81197026>] deactivate_super+0x46/0x60

---

### Post by rtalcott on 2013-04-28
I have the problem with 13.04 with 3.8 and 3.9...

---

### Post by michael179 on 2013-04-29
Having EXACT same issue, except I am running it in a Parallels VM. 
I ran it as "Other Linux" and "Ubuntu Linux", both with no success.

---

### Post by mooreted on 2013-04-29
So far, with the mainline kernel, I haven't had any issues. My machine booted right up this morning.

---

### Post by pqwoerituytrueiwoq on 2013-04-29
Give 3.8.10 a try it just got added to the mainline; edit 3.9.0 is out also

this happens to me on the 3.8.0-19-generic kernel even in recovery mode on 1st boot after install (nvidia gpu: GTX 550 TI)

---

### Post by rtalcott on 2013-05-03
Everything after 3.2 is giving me problems including the newest kernels from mainline.

---

### Post by Uxorious on 2013-07-09
Same problem here (running in ESXi 5.1 Update 1).

---

### Post by davea42 on 2013-11-22
I too see this, but ONLY if running a GPU app (boinc seti@home).
Not when running otherwise (11 cores 100% busy).

---

### Post by davea42 on 2013-11-22
Should have added: 13.04 Ubuntu. x86_64

---

