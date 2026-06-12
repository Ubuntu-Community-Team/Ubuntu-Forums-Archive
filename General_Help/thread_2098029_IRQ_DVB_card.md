---
title: "IRQ DVB card"
date: 2012-12-25
forum: General Help
---

### Post by Axio on 2012-12-25
Hi,

I am on Ubuntu 12.04 with a DVB card (Nova T 500). I get some random bugs that break the dvb card. Here is my kern.log: [http://paste.ubuntu.com/1464641/](http://paste.ubuntu.com/1464641/)

```
Dec 24 20:54:16 server kernel: [20819.069431] irq 16: nobody cared (try booting with the "irqpoll" option)
Dec 24 20:54:16 server kernel: [20819.069464] Pid: 823, comm: kdvb-ad-0-fe-0 Tainted: P           O 3.2.0-35-generic #55-Ubuntu
Dec 24 20:54:16 server kernel: [20819.069473] Call Trace:
Dec 24 20:54:16 server kernel: [20819.069492]  [<c1560f2c>] ? printk+0x2d/0x2f
Dec 24 20:54:16 server kernel: [20819.069509]  [<c10b1259>] __report_bad_irq+0x29/0xd0
Dec 24 20:54:16 server kernel: [20819.069521]  [<c15630fb>] ? misrouted_irq+0x5f/0x75
Dec 24 20:54:16 server kernel: [20819.069533]  [<c10b14b4>] note_interrupt+0x104/0x150
Dec 24 20:54:16 server kernel: [20819.069546]  [<c14735d3>] ? dev_alloc_skb+0x23/0x40
Dec 24 20:54:16 server kernel: [20819.069557]  [<c10af38f>] handle_irq_event_percpu+0x9f/0x1f0
Dec 24 20:54:16 server kernel: [20819.069569]  [<c10b1d90>] ? handle_fasteoi_irq+0xd0/0xd0
Dec 24 20:54:16 server kernel: [20819.069579]  [<c10b1d90>] ? handle_fasteoi_irq+0xd0/0xd0
Dec 24 20:54:16 server kernel: [20819.069591]  [<c10af51b>] handle_irq_event+0x3b/0x60
Dec 24 20:54:16 server kernel: [20819.069601]  [<c10b1cc0>] ? unmask_irq+0x30/0x30
Dec 24 20:54:16 server kernel: [20819.069611]  [<c10b1d0e>] handle_fasteoi_irq+0x4e/0xd0
Dec 24 20:54:16 server kernel: [20819.069618]  <IRQ>  [<c157d832>] ? do_IRQ+0x42/0xc0
Dec 24 20:54:16 server kernel: [20819.069639]  [<c1124178>] ? __kmalloc_track_caller+0x1c8/0x1d0
Dec 24 20:54:16 server kernel: [20819.069651]  [<c157d770>] ? common_interrupt+0x30/0x38
Dec 24 20:54:16 server kernel: [20819.069662]  [<c14735d3>] ? dev_alloc_skb+0x23/0x40
Dec 24 20:54:16 server kernel: [20819.069717]  [<f8081bbd>] ? rtl8168_rx_fill.isra.44+0x6d/0x140 [r8168]
Dec 24 20:54:16 server kernel: [20819.069742]  [<f8081f87>] ? rtl8168_rx_interrupt.isra.46+0x2f7/0x400 [r8168]
Dec 24 20:54:16 server kernel: [20819.069754]  [<c10b5c3d>] ? rcu_irq_exit+0xd/0x10
Dec 24 20:54:16 server kernel: [20819.069777]  [<f8081a50>] ? rtl8168_rx_desc_offset0_init.isra.24+0x50/0x50 [r8168]
Dec 24 20:54:16 server kernel: [20819.069800]  [<f8082200>] ? rtl8168_poll+0x30/0x210 [r8168]
Dec 24 20:54:16 server kernel: [20819.069814]  [<c102747d>] ? __ticket_spin_lock+0xd/0x30
Dec 24 20:54:16 server kernel: [20819.069826]  [<c147febd>] ? net_rx_action+0x10d/0x220
Dec 24 20:54:16 server kernel: [20819.069836]  [<c147296e>] ? __kfree_skb+0x1e/0x30
Dec 24 20:54:16 server kernel: [20819.069848]  [<c1051c00>] ? local_bh_enable_ip+0x90/0x90
Dec 24 20:54:16 server kernel: [20819.069857]  [<c1051c81>] ? __do_softirq+0x81/0x1a0
Dec 24 20:54:16 server kernel: [20819.069867]  [<c1051c00>] ? local_bh_enable_ip+0x90/0x90
Dec 24 20:54:16 server kernel: [20819.069877]  [<c1051c00>] ? local_bh_enable_ip+0x90/0x90
Dec 24 20:54:16 server kernel: [20819.069883]  <IRQ>  [<c1051fc6>] ? irq_exit+0x76/0xa0
Dec 24 20:54:16 server kernel: [20819.069899]  [<c157d83b>] ? do_IRQ+0x4b/0xc0
Dec 24 20:54:16 server kernel: [20819.069908]  [<c10b5c3d>] ? rcu_irq_exit+0xd/0x10
Dec 24 20:54:16 server kernel: [20819.069918]  [<c1051f8c>] ? irq_exit+0x3c/0xa0
Dec 24 20:54:16 server kernel: [20819.069928]  [<c157d909>] ? smp_apic_timer_interrupt+0x59/0x88
Dec 24 20:54:16 server kernel: [20819.069939]  [<c157d770>] ? common_interrupt+0x30/0x38
Dec 24 20:54:16 server kernel: [20819.069952]  [<c103a744>] ? finish_task_switch+0x54/0xc0
Dec 24 20:54:16 server kernel: [20819.069966]  [<c1573f69>] ? __schedule+0x2e9/0x620
Dec 24 20:54:16 server kernel: [20819.069976]  [<c103aaad>] ? update_curr+0x1ed/0x360
Dec 24 20:54:16 server kernel: [20819.069988]  [<c1008bc8>] ? sched_clock+0x8/0x10
Dec 24 20:54:16 server kernel: [20819.070001]  [<c1118577>] ? dma_pool_alloc+0x107/0x130
Dec 24 20:54:16 server kernel: [20819.070012]  [<c1027518>] ? default_spin_lock_flags+0x8/0x10
Dec 24 20:54:16 server kernel: [20819.070023]  [<c157614d>] ? _raw_spin_lock_irqsave+0x2d/0x40
Dec 24 20:54:16 server kernel: [20819.070035]  [<c1574545>] ? schedule+0x35/0x50
Dec 24 20:54:16 server kernel: [20819.070046]  [<c157496f>] ? schedule_timeout+0x12f/0x2a0
Dec 24 20:54:16 server kernel: [20819.070059]  [<c10588f0>] ? usleep_range+0x40/0x40
Dec 24 20:54:16 server kernel: [20819.070071]  [<c15743c7>] ? wait_for_common+0xa7/0x110
Dec 24 20:54:16 server kernel: [20819.070082]  [<c13e03a0>] ? usb_hcd_submit_urb+0x80/0x180
Dec 24 20:54:16 server kernel: [20819.070095]  [<c10448a0>] ? try_to_wake_up+0x190/0x190
Dec 24 20:54:16 server kernel: [20819.070107]  [<c15744e2>] ? wait_for_completion_timeout+0x12/0x20
Dec 24 20:54:16 server kernel: [20819.070118]  [<c13e1f01>] ? usb_start_wait_urb+0xa1/0xc0
Dec 24 20:54:16 server kernel: [20819.070128]  [<c13e0202>] ? usb_add_hcd.part.22+0x262/0x2d0
Dec 24 20:54:16 server kernel: [20819.070139]  [<c13e2126>] ? usb_control_msg+0xc6/0x100
Dec 24 20:54:16 server kernel: [20819.070157]  [<f843d74f>] ? dib0700_ctrl_rd+0x8f/0xd0 [dvb_usb_dib0700]
Dec 24 20:54:16 server kernel: [20819.070173]  [<f843d8b3>] ? dib0700_i2c_xfer_legacy+0x123/0x170 [dvb_usb_dib0700]
Dec 24 20:54:16 server kernel: [20819.070190]  [<f843d939>] ? dib0700_i2c_xfer+0x39/0x60 [dvb_usb_dib0700]
Dec 24 20:54:16 server kernel: [20819.070205]  [<c141f59d>] ? i2c_transfer+0x8d/0xc0
Dec 24 20:54:16 server kernel: [20819.070222]  [<f84180fc>] ? dib7000p_read_word.part.6+0xdc/0x180 [dib7000p]
Dec 24 20:54:16 server kernel: [20819.070238]  [<f84181ce>] ? dib7000p_read_word+0x2e/0x80 [dib7000p]
Dec 24 20:54:16 server kernel: [20819.070249]  [<c1027518>] ? default_spin_lock_flags+0x8/0x10
Dec 24 20:54:16 server kernel: [20819.070264]  [<f841840b>] ? dib7000p_read_status+0x1b/0x50 [dib7000p]
Dec 24 20:54:16 server kernel: [20819.070291]  [<f83e0bcf>] ? dvb_frontend_swzigzag+0xcf/0x2f0 [dvb_core]
Dec 24 20:54:16 server kernel: [20819.070316]  [<f83e20df>] ? dvb_frontend_thread+0x38f/0x6d0 [dvb_core]
Dec 24 20:54:16 server kernel: [20819.070328]  [<c10448b0>] ? default_wake_function+0x10/0x20
Dec 24 20:54:16 server kernel: [20819.070340]  [<c10306d7>] ? __wake_up_common+0x47/0x70
Dec 24 20:54:16 server kernel: [20819.070352]  [<c106a200>] ? add_wait_queue+0x50/0x50
Dec 24 20:54:16 server kernel: [20819.070376]  [<f83e1d50>] ? dvb_frontend_reinitialise+0x30/0x30 [dvb_core]
Dec 24 20:54:16 server kernel: [20819.070387]  [<c10699ed>] ? kthread+0x6d/0x80
Dec 24 20:54:16 server kernel: [20819.070398]  [<c1069980>] ? flush_kthread_worker+0x80/0x80
Dec 24 20:54:16 server kernel: [20819.070409]  [<c157d77e>] ? kernel_thread_helper+0x6/0x10
Dec 24 20:54:16 server kernel: [20819.070415] handlers:
Dec 24 20:54:16 server kernel: [20819.070426] [<c13deb10>] usb_hcd_irq
Dec 24 20:54:16 server kernel: [20819.070451] [<f806d7e0>] irq_handler
Dec 24 20:54:16 server kernel: [20819.070469] [<f82e3040>] azx_interrupt
Dec 24 20:54:16 server kernel: [20819.070481] Disabling IRQ #16

```

When it happens the dvb card isn't doing anything special, no tv channel is being registered or shown. These bugs were kinda rare till I activate HD channels of my DVB card. Now it is much more frequent, I don't really know why.

I have of course tried to boot with "irqpool", but it doesn't change a thing. What should I do about it?

---

### Post by Axio on 2012-12-31
Bug opened on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1094904](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1094904)

---

