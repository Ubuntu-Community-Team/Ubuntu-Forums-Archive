---
title: "Thinkpad X1 Yoga Gen 4 no longer resumes from suspend"
date: 2020-03-25
forum: General Help
---

### Post by al3x-waib3l on 2020-03-25
I've had this laptop for a few months now, and have had no problems until now using Ubuntu 19.10. I started noticing today that suddenly the laptop won't resume from a suspend. The power button remains illuminated, but no key presses or power button presses will bring back the display and I am forced to reboot. This applies both when I close my laptop lid and when I use ```
systemctl suspend
```. 

From ```
journalctl | grep suspend
``` I have a ton of errors like so:

```
md-suspend.service)/device/speed} for writing: No such file or directory
Dec 05 14:16:39 alex-ThinkPad-X1-Yoga-4th systemd-udevd[18665]: anon_vma_chain(2367:systemd-suspend.service): Failed to open ATTR{/sys/kernel/slab/:A-0000064/cgroup/anon_vma_chain(2367:systemd-suspend.service)/device/inertia} for writing: No such file or directory
Dec 05 14:16:39 alex-ThinkPad-X1-Yoga-4th systemd-udevd[18665]: anon_vma_chain(2367:systemd-suspend.service): Failed to open ATTR{/sys/kernel/slab/:A-0000064/cgroup/anon_vma_chain(2367:systemd-suspend.service)/device/press_to_select} for writing: No such file or directory
Dec 05 14:16:39 alex-ThinkPad-X1-Yoga-4th systemd-udevd[18642]: cred_jar(2367:systemd-suspend.service): Failed to open ATTR{/sys/cred_jar(2367:systemd-suspend.service)/device/sensitivity} for writing: No such file or directory
Dec 05 14:16:39 alex-ThinkPad-X1-Yoga-4th systemd-udevd[18642]: cred_jar(2367:systemd-suspend.service): Failed to open ATTR{/sys/cred_jar(2367:systemd-suspend.service)/device/speed} for writing: No such file or directory
Dec 05 14:16:39 alex-ThinkPad-X1-Yoga-4th systemd-udevd[18642]: cred_jar(2367:systemd-suspend.service): Failed to open ATTR{/sys/cred_jar(2367:systemd-suspend.service)/device/inertia} for writing: No such file or directory
Dec 05 14:16:39 alex-ThinkPad-X1-Yoga-4th systemd-udevd[18642]: cred_jar(2367:systemd-suspend.service): Failed to open ATTR{/sys/cred_jar(2367:systemd-suspend.service)/device/press_to_select} for writing: No such file or directory
Dec 05 14:49:29 alex-ThinkPad-X1-Yoga-4th systemd-udevd[8257]: radix_tree_node(1819:systemd-suspend.service): Failed to open ATTR{/sys/radix_tree_node(1819:systemd-suspend.service)/device/sensitivity} for writing: No such file or directory
```

Any ideas what the issue might be or how to better troubleshoot these kinds of errors?

---

