---
title: "Soft Lockup?  Keskasay?"
date: 2007-01-12
forum: General Help
---

### Post by allwin on 2007-01-12
Every once in a while when I boot, my syslog shows a soft lockup on CPU#0.  What is this, and should I be afraid of it?  1999 era Dell 550Mhz P-III 256mb desktop resurrected from the closet just for Ubuntu-ing.  I also suspect hda is about to flake out on me as it is an old one in dog years at least...however, I have been playing with hdparm to see if I can squeeze any additional speed out of it.  I have "hdparm -c1 -m16 -X66 -d1 -u1" which seems to be optimum.  Stranger still, the system then comes up OK, though it hangs about 15 uncomfortable seconds or so during the boot...no ill effects apparent.  WT-que pasa-qu'est que c'est is going on here?  Thanks.

Jan 12 23:11:46 allwin kernel: [17179634.744000] Floppy drive(s): fd0 is 1.44M
Jan 12 23:11:46 allwin kernel: [17179634.768000] FDC 0 is a post-1991 82077
Jan 12 23:11:46 allwin kernel: [17179644.548000] BUG: soft lockup detected on CPU#0!
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c01491cf> softlockup_tick+0x9f/0xf0  <c012bee1> update_process_times+0x31/0x80
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c01070ac> timer_interrupt+0x7c/0xb0  <c0149323> handle_IRQ_event+0x33/0x60
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c01493ed> __do_IRQ+0x9d/0x110  <c0105c89> do_IRQ+0x19/0x30
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c010408a> common_interrupt+0x1a/0x20  <c0253273> ide_inb+0x3/0x10
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c025442c> ide_config_drive_speed+0x13c/0x310  <d08204f7> piix_tune_chipset+0x1c7/0x370 [piix]
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c0254e4c> ide_set_xfer_rate+0x1c/0x20  <c0257cc2> ide_cmd_ioctl+0x1f2/0x240
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0107b4d> enable_8259A_irq+0xd/0x50
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c0149415> __do_IRQ+0xc5/0x110  <c0105c8e> do_IRQ+0x1e/0x30
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c010408a> common_interrupt+0x1a/0x20  <c014007b> disk_store+0x10b/0x12e
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c0259e5c> __ide_dma_host_on+0x5c/0x80  <c0254512> ide_config_drive_speed+0x222/0x310
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c02511d0> generic_ide_ioctl+0x2a0/0x4a7  <c0178953> do_lookup+0x53/0x160
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <d092a170> ext3_permission+0x0/0x10 [ext3]  <c0183107> dput+0xb7/0x140
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c017ac7a> __link_path_walk+0xb6a/0xf20  <d0849dcc> idedisk_ioctl+0x2c/0x40 [ide_disk]
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c01d6d8d> blkdev_driver_ioctl+0x6d/0x80  <c01d708f> blkdev_ioctl+0x2ef/0x7d0
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c01512e2> get_page_from_freelist+0x3a2/0x410  <c01d7570> exact_match+0x0/0x10
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c014ba30> find_get_page+0x20/0x50  <c014ebf3> filemap_nopage+0x2f3/0x3a0
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c0158f41> __handle_mm_fault+0x211/0x900  <c02d8dce> schedule+0x41e/0xcc0
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c01724b8> block_ioctl+0x18/0x20  <c01724a0> block_ioctl+0x0/0x20
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c017d5eb> do_ioctl+0x2b/0x90  <c017d6ac> vfs_ioctl+0x5c/0x2b0
Jan 12 23:11:46 allwin kernel: [17179644.548000]  <c017d972> sys_ioctl+0x72/0x90  <c0102fbb> sysenter_past_esp+0x54/0x79
Jan 12 23:11:46 allwin kernel: [17179644.780000] hda: dma_intr: status=0xd0 { Busy }
Jan 12 23:11:46 allwin kernel: [17179644.780000] ide: failed opcode was: unknown
Jan 12 23:11:46 allwin kernel: [17179644.780000] hda: DMA disabled
Jan 12 23:11:46 allwin kernel: [17179644.780000] hda: set_drive_speed_status: status=0xd0 { Busy }
Jan 12 23:11:46 allwin kernel: [17179644.780000] ide: failed opcode was: unknown
Jan 12 23:11:46 allwin kernel: [17179644.796000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
Jan 12 23:11:46 allwin kernel: [17179644.828000] ide0: reset: success
Jan 12 23:11:46 allwin kernel: [17179644.940000] hdd: No disk in drive
Jan 12 23:11:46 allwin kernel: [17179645.968000] hdd: No disk in drive
Jan 12 23:11:46 allwin kernel: [17179654.948000] hda: irq timeout: status=0xd0 { Busy }
Jan 12 23:11:46 allwin kernel: [17179654.948000] ide: failed opcode was: unknown
Jan 12 23:11:46 allwin kernel: [17179654.996000] ide0: reset: success
Jan 12 23:11:46 allwin kernel: [17179655.372000] ts: Compaq touchscreen protocol output
Jan 12 23:11:46 allwin kernel: [17179655.892000] hda: CHECK for good STATUS
Jan 12 23:11:46 allwin kernel: [17179656.132000] hda: CHECK for good STATUS
Jan 12 23:11:46 allwin kernel: [17179656.132000] hda: CHECK for good STATUS
Jan 12 23:11:46 allwin kernel: [17179656.824000] PCI: Enabling device 0000:00:0f.0 (0104 -> 0107)

---

### Post by allwin on 2007-01-13
Bumperino.

---

### Post by allwin on 2007-01-14
Bumpsky!

Doesn't anybody out there on this forum know what a soft lockup is who could at least explain to me what I'm up against?

---

### Post by glabouni on 2007-01-29
obviously, you didn't try to type "soft lockup" in google.
seems this is a known bug with newer kernels.

check this post, maybe it can help.
[http://www.stuvel.eu/archive/37/bug-soft-lockup-detected-on-cpu0](http://www.stuvel.eu/archive/37/bug-soft-lockup-detected-on-cpu0)

---

### Post by allwin on 2007-01-29
> **glabouni said:**
> obviously, you didn't try to type "soft lockup" in google.
seems this is a known bug with newer kernels.

check this post, maybe it can help.
[http://www.stuvel.eu/archive/37/bug-soft-lockup-detected-on-cpu0](http://www.stuvel.eu/archive/37/bug-soft-lockup-detected-on-cpu0)

[http://www.google.com/search?hl=en&q=soft+lockup]("http://www.google.com/search?hl=en&q=soft+lockup")

May I ask with all due respect how you decided out of 989,000 hits for "Soft Lockup" that this one was the one that applies to my situation?

Of course I googled for it before I decided to post my question.

What I was hoping was that someone who knew what a Soft Lockup was would explain it to me and suggest reasons why it appeared, not just to challenge my google-fu.  If I was truly able to sift through almost a million articles, I would not have asked.

Thanks anyhow for replying.  It must be dreadful to be a Linux expert and have to deal with noobs all the time and share your secrets on matters such as these.:D

---

### Post by llamakc on 2007-01-29
For starters you could tell us what kernels give you this error, which kernels you have tried, and which kernels didn't give you this error (if any). Also, if you don't tell us you googled, how are we to know you did so?

---

### Post by allwin on 2007-01-29
> **llamakc said:**
> For starters you could tell us what kernels give you this error, which kernels you have tried, and which kernels didn't give you this error (if any). Also, if you don't tell us you googled, how are we to know you did so?

Kernel 2.6.17-10generic.  As I stated before, this is an intermittent error;  I have not seen it since I replaced the HD in that system with a larger one.  My main questions are, if the system comes up OK, what is the significance of a "soft lockup" if I should get one again.  Is it the kind of bug I should report immediately (eg open a bug report) or are there any things I can check which might lead to this in the future?  It's an 8 year old Dell system, otherwise seemingly in perfect shape.

What is a soft lockup anyhow, just to expand my knowledge of Linux?  That is, what is the definition of the term?  Thanks!

---

### Post by llamakc on 2007-01-29
I don't know. Have you messaged the kernel list? Perhaps you should try other kernels to see if the same condition occurs. Also, telling us what your hardware specs are would help. What net connections do you have? Wired? Wireless? Many of the Google hits point to wireless issues on newer kernels.

Are you passing any extra parameters at boot? That is one more thing in your OP that could help you arrive at a quicker resolution.

---

### Post by allwin on 2007-01-29
> **llamakc said:**
> I don't know. Have you messaged the kernel list? Perhaps you should try other kernels to see if the same condition occurs. Also, telling us what your hardware specs are would help. What net connections do you have? Wired? Wireless? Many of the Google hits point to wireless issues on newer kernels.

Are you passing any extra parameters at boot? That is one more thing in your OP that could help you arrive at a quicker resolution.

Offhand, I'm not sure what you mean by "messaged the kernel list".  It's as I stated, a Dell 550mhz Pentium desktop, no wireless, no USB devices attached at boot time, vintage 1999, ps2 mouse + keyboard, happens to be on a KVM switch, two nic cards, one connected to my router which then goes to the cable modem, one unused.

My concern is that in playing with hdparm, I accidentally specified some option which might have overworked the disk drive in some way or caused its operation to be unreliable because I specified some feature which is not supported, another reason for asking.

---

### Post by llamakc on 2007-01-29
Have you tried commenting out any options in /etc/hdparm.conf and rebooting to see if the error persists?

---

