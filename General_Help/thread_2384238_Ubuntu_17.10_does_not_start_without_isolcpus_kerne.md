---
title: "Ubuntu 17.10 does not start without isolcpus kernel parameter"
date: 2018-02-04
forum: General Help
---

### Post by amk1543 on 2018-02-04
Hi, I am running Ubuntu 17.10 x64 (kernel 4.13.0-32), my CPU is Intel i7-6700K.

I have gotten myself into the following situation. While tuning performance of a virtual machine with VGA passthrough, I tried booting the system with the following kernel parameters
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on isolcpus=4,5,6,7 nohz_full=4,5,6,7 rcu_nocbs=4,5,6,7"
```
This worked fine.

However now the system will not start correctly unless the "isolcpus" parameter is given! It does not seem to matter what the parameters value is (as long as it is a non-empty subset of {0..7}).

What happens is that the system freezes on startup after displaying the log message
```
[OK] Started User Manager for UID 129.
```

I am attaching the startup logs as reported by journalctl for
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on"
``` (freezes)
vs
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on isolcpus=7"
``` (works fine)

Per an ad-hoc comparison, the first "significant" difference I see is that the lines
```
Feb 04 16:19:12 amakhlin-pc kernel: efifb: probing for efifb
Feb 04 16:19:12 amakhlin-pc kernel: efifb: framebuffer at 0xb0000000, using 3072k, total 3072k
Feb 04 16:19:12 amakhlin-pc kernel: efifb: mode is 1024x768x32, linelength=4096, pages=1
Feb 04 16:19:12 amakhlin-pc kernel: efifb: scrolling: redraw
Feb 04 16:19:12 amakhlin-pc kernel: efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0

```
are present only without "isolcpus" (i.e. when the system freezes).

Does anybody have an idea what might be going on here?

---

