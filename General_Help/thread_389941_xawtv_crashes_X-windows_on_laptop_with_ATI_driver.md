---
title: "xawtv crashes X-windows on laptop with ATI driver"
date: 2007-03-21
forum: General Help
---

### Post by scotty64 on 2007-03-21
Whenever I try to start xawtv or other TV apps on my laptop the whole X-System crashes and I get the following log:
[17180312.288000] scheduling while atomic: xawtv/0x00000001/7176
[17180312.288000]  [<c030b9bd>] schedule+0x99d/0xd20
[17180312.288000]  [<c011f423>] __wake_up_common+0x43/0x70
[17180312.288000]  [<c011f490>] __wake_up+0x40/0x60
[17180312.288000]  [<f8f1c381>] firegl_irq_cleanup+0x121/0x1d0 [fglrx]
[17180312.288000]  [<f8f1b79b>] firegl_takedown+0x8fb/0xc00 [fglrx]
[17180312.288000]  [<f8f1a5af>] firegl_release+0x12f/0x190 [fglrx]
[17180312.288000]  [<c01735d9>] __fput+0xa9/0x1a0
[17180312.288000]  [<c0171972>] filp_close+0x52/0x90
[17180312.288000]  [<c0126e61>] put_files_struct+0x91/0xe0
[17180312.288000]  [<c0127c31>] do_exit+0x111/0x420
[17180312.288000]  [<c0127fc0>] do_group_exit+0x40/0xb0
[17180312.288000]  [<c01033ff>] sysenter_past_esp+0x54/0x75
[17180313.764000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 209
[17180316.476000] [fglrx] PCIe has already been initialized. Reinitializing ...
[17180316.496000] [fglrx] total      GART = 130023424
[17180316.496000] [fglrx] free       GART = 114032640
[17180316.496000] [fglrx] max single GART = 114032640
[17180316.496000] [fglrx] total      LFB  = 134086656
[17180316.496000] [fglrx] free       LFB  = 119697408
[17180316.496000] [fglrx] max single LFB  = 119697408
[17180316.496000] [fglrx] total      Inv  = 0
[17180316.496000] [fglrx] free       Inv  = 0
[17180316.496000] [fglrx] max single Inv  = 0
[17180316.496000] [fglrx] total      TIM  = 0

I am using the proprietary fglrx driver from ATI and no other problems with it on my Radeon Xpress 200M.

---

