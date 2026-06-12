---
title: "Thinkpad T440 - Battery Monitor Does not Function"
date: 2015-07-13
forum: General Help
---

### Post by UncertainT on 2015-07-13
Hello,

I have the battery monitor on the lxpanel and it is always at 100%. I have read through some old posts where similar things have happened but they did not help (re-installing power manager, etc..).

This laptop has two batteries, I don't know if this is causing issues. It worked fine with Arch linux.

From dmesg, the only thing that stands out is:
```

[    1.320639] Error parsing PCC subspaces from PCCT
[    1.320643] ACPI PCC probe failed.

```

I have also found this report bug but am not sure if it is the same deal.
[https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/1290623](https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/1290623)

The fun begins!

---

### Post by tgalati4 on 2015-07-14
Try booting with one battery and see if the behavior changes.  If so, then you know that the 2-battery configuration may be related.

Yes, there does seem to be a bug related to multiple batteries and the power manager display.  Because of the many ways that 2 batteries can be combined, I don't think the power-manager framework knows how to handle them correctly.

On my T43p, which supports multiple batteries, but I don't have one to test, I recall a setting (in BIOS or in a Windows/IBM config utility) to establish the battery policy:

1.  Use the main battery first, then use the DVD/second battery when the main battery drops to 15%.
2.  Combine batteries and draw from them equally.
3.  Use the DVD/second battery first, then switch to the main battery.
4.  Some other custom profile, back and forth between them.

As I recall, it was sophisticated, so it's not surprising that the power manager does not handle it correctly.

Check your BIOS for multiple battery settings.

---

