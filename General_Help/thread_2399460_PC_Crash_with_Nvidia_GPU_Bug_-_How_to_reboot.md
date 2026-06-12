---
title: "PC Crash with Nvidia GPU Bug - How to reboot"
date: 2018-08-25
forum: General Help
---

### Post by bizhat on 2018-08-25
My PC some fimes crash with following error in syslog

```
Aug 25 21:42:22 localhost kernel: [ 2843.955363] NVRM: GPU at PCI:0000:03:00: GPU-e1c069dd-4adf-9be1-da0a-87c4a72ed9fa
Aug 25 21:42:22 localhost kernel: [ 2843.955370] NVRM: Xid (PCI:0000:03:00): 62, 153f(1670) 840131a5 0000fff6
Aug 25 21:42:27 localhost kernel: [ 2849.309588] NVRM: Xid (PCI:0000:03:00): 31, Ch 0000002a, engmask 00000101, intr 10000000
Aug 25 21:42:43 localhost kernel: [ 2861.310068] NVRM: Xid (PCI:0000:03:00): 8, Channel 00000028
Aug 25 21:42:43 localhost kernel: [ 2863.309996] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Aug 25 21:42:43 localhost kernel: [ 2865.309856] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Aug 25 21:43:00 localhost kernel: [ 2881.422254] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000020 intr 80864000
Aug 25 21:43:00 localhost kernel: [ 2881.422894] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000020 intr 00864000
Aug 25 21:43:00 localhost kernel: [ 2881.423418] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000020 intr1 00000001 HCE_DBG0 00000008 HCE_DBG1 00000000
Aug 25 21:43:00 localhost kernel: [ 2881.423954] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000020 intr 00800000
Aug 25 21:43:12 localhost kernel: [ 2893.438162] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000020 intr 80846000
Aug 25 21:43:12 localhost kernel: [ 2893.438644] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000020 intr1 00000001 HCE_DBG0 00000008 HCE_DBG1 00000000
Aug 25 21:43:20 localhost kernel: [ 2902.397193] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000001 intr 80844000
Aug 25 21:43:20 localhost kernel: [ 2902.397747] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000001 intr 00844000
Aug 25 21:43:20 localhost kernel: [ 2902.398192] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000001 intr1 00000001 HCE_DBG0 00000000 HCE_DBG1 00000000
Aug 25 21:43:43 localhost kernel: [ 2925.309262] NVRM: Xid (PCI:0000:03:00): 31, Ch 00000018, engmask 00000101, intr 10000000
Aug 25 21:43:43 localhost kernel: [ 2925.313813] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000028 intr 80846000
Aug 25 21:43:43 localhost kernel: [ 2925.314348] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000028 intr 00800000
Aug 25 21:43:43 localhost kernel: [ 2925.314835] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000028 intr1 00000001 HCE_DBG0 00000000 HCE_DBG1 ffffff00
Aug 25 21:43:43 localhost kernel: [ 2925.315336] NVRM: Xid (PCI:0000:03:00): 32, Channel ID 00000028 intr 00800000
Aug 25 21:43:47 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE) NVIDIA(0): The NVIDIA X driver has encountered an error; attempting to
Aug 25 21:43:47 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE) NVIDIA(0):     recover...
Aug 25 21:43:54 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE) NVIDIA(GPU-0): Failed to initialize DMA.
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE) NVIDIA(0): Failed to allocate push buffer
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE) NVIDIA(0): Error recovery failed.
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE) NVIDIA(0):  *** Aborting ***
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE)
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: Fatal server error:
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE) Failed to recover from error!
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE)
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: (EE)
Aug 25 21:43:55 localhost /usr/lib/gdm3/gdm-x-session[7246]: Please consult the The X.Org Foundation support

```

This happens like once or twice in a week. But there are months/weeks with out this issue.  I have this issue for years now. May be a GPU hardware issue, i can't get it replaced now.

When this error occour, screen freezes, that is i can't see anything on monitor.

But PC works.

I want some script/software that monitor syslog for above error message, if it found, reboot the system. For now i have to hard reboot, that cause some disk errors on next boot. 

What is the best solution for monitoring syslog for this error and reboot PC if error detected ?

---

