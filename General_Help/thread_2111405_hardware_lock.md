---
title: "hardware lock"
date: 2013-02-01
forum: General Help
---

### Post by sandsjh on 2013-02-01
Hi all:

My system has completely locked a few times now. It was horrific with 12.10x64, but only a couple times with 12.04x64. Please assist.

Linux uslitdm0 3.2.0-36-generic #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```
Jan 28 19:21:21 uslrkpr0 screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/user is already mounted
Jan 28 19:21:31 uslrkpr0 kernel: [192402.226972] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824574] irq 16: nobody cared (try booting with the "irqpoll" option)
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824577] Pid: 0, comm: swapper/0 Tainted: P           O 3.2.0-36-generic #57-Ubuntu
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824579] Call Trace:
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824580]  <IRQ>  [<ffffffff810dc40d>] __report_bad_irq+0x3d/0xe0
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824588]  [<ffffffff810dc695>] note_interrupt+0x135/0x190
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824591]  [<ffffffff810d9f0a>] handle_irq_event_percpu+0xaa/0x210
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824593]  [<ffffffff810da0c1>] handle_irq_event+0x51/0x80
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824595]  [<ffffffff810dd0ea>] handle_fasteoi_irq+0x6a/0x110
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824599]  [<ffffffff81016282>] handle_irq+0x22/0x40
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824603]  [<ffffffff8166851a>] do_IRQ+0x5a/0xe0
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824606]  [<ffffffff8165d8ae>] common_interrupt+0x6e/0x6e
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824607]  <EOI>  [<ffffffff8108f189>] ? enqueue_hrtimer+0x39/0xc0
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824614]  [<ffffffff8136d89d>] ? intel_idle+0xed/0x150
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824616]  [<ffffffff8136d87f>] ? intel_idle+0xcf/0x150
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824619]  [<ffffffff815086e1>] cpuidle_idle_call+0xc1/0x280
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824622]  [<ffffffff8101322a>] cpu_idle+0xca/0x120
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824626]  [<ffffffff816239fe>] rest_init+0x72/0x74
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824630]  [<ffffffff81cfcc03>] start_kernel+0x3b0/0x3bd
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824633]  [<ffffffff81cfc388>] x86_64_start_reservations+0x132/0x136
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824635]  [<ffffffff81cfc140>] ? early_idt_handlers+0x140/0x140
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824638]  [<ffffffff81cfc459>] x86_64_start_kernel+0xcd/0xdc
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824639] handlers:
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824642] [<ffffffff81493b90>] usb_hcd_irq
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824721] [<ffffffffa06f9f40>] nv_kern_isr
Jan 28 19:21:33 uslrkpr0 kernel: [192403.824723] Disabling IRQ #16
Jan 28 19:24:03 uslrkpr0 kernel: Kernel logging (proc) stopped.
Jan 28 19:24:03 uslrkpr0 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1043" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

---

### Post by tgalati4 on 2013-02-01
Looks like a graphics card or power supply problem or both.

---

### Post by sandsjh on 2013-02-01
Thank you, tgalati4. Now I see the "NVRM: GPU at 0000:01:00.0 has fallen off the bus."

---

### Post by tgalati4 on 2013-02-01
What kind of machine is this?  Laptop or desktop?  Try cleaning the machine out and reseating cards and cables.  Check that the fans are running OK.  Check the temperature of the GPU.  When they get hot, they tend to shut down--and not gracefully.

---

### Post by sandsjh on 2013-02-03
System:    Host: me Kernel: 3.2.0-36-generic x86_64 (64 bit) Desktop: N/A 
Machine:   System: HP product: ProLiant ML110 G6 serial: 
           Mobo: Wistron model: ProLiant ML110 G6 serial: Bios: HP version: O27 date: 09/06/2010
CPU:       Quad core Intel Xeon CPU X3440 (-HT-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) 
           Clock Speeds: 1: 1197.00 MHz 2: 1197.00 MHz 3: 1197.00 MHz 4: 1197.00 MHz 5: 1197.00 MHz 6: 1197.00 MHz 7: 1197.00 MHz 8: 1197.00 MHz
Graphics:  Card: NVIDIA G92 [GeForce 8800 GTS 512] 
           X.org: 1.11.3 drivers: nvidia (unloaded: nouveau,vesa,fbdev) tty size: 159x45 Advanced Data: N/A for root 
Audio:     Card-1: C-Media USB Headphone Set driver: USB-Audio Sound: ALSA ver: 1.0.24
           Card-2: C-Media Audio Adapter driver: USB Audio
Network:   Card: Broadcom NetXtreme BCM5723 Gigabit Ethernet PCIe driver: tg3 
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: f4:ce:46:0f:07:54
Drives:    HDD Total Size: 366.0GB (72.6% used) 1: /dev/sda OCZ 115.0GB 
           2: /dev/sdb Logical_Disk_0 251.0GB

---

