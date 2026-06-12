---
title: "Unable to generate crash dump file"
date: 2012-12-05
forum: General Help
---

### Post by legolin on 2012-12-05
Dear all:
   Can someone help me how to generate crash dump file at Ubuntu 12.04 with kernel version (3.2.0-23-generic #36-Ubuntu SMP).

I have install linux-crashdump tools the got 1 response when I use command : cat /sys/kernel/kexec_crash_loaded

And the result of 'cat /proc/cmdline' is
BOOT_IMAGE=/vmlinuz-3.2.0-23-generic root=UUID=875d0cc9-2ba7-4eff-8cb0-08b56797162d ro crashkernel=384M-2G:64M,2G-:128M

Originally, the kdump services cannot be start due to miss vmcoreinfo. I am trying to using makedumpfile (1.3.4) to generate 1 vmcoreinfo. But fail eventually and I got (cmd: makedumpfile -g vmcoreinfo-3.2.23 -x vmlinux):  
generate_vmcoreinfo: Can't find the memory type.
makedumpfile Failed.

I did some google search and someone says that vmcoreinfo has already incorporate into kernel after 2.6.32(?) and will placed at /sys/kernel/vmcoreinfo.

So I modify the /etc/init.d/kdump so that it won't check vmcoreinfo under /boot/ directory but check /sys/kernel/vmcoreinfo.

And the kdump is running, but still fail to generate crash dump.

Can someone help on this?

---

### Post by rnerwein on 2012-12-05
> **legolin said:**
> Dear all:
   Can someone help me how to generate crash dump file at Ubuntu 12.04 with kernel version (3.2.0-23-generic #36-Ubuntu SMP).

I have install linux-crashdump tools the got 1 response when I use command : cat /sys/kernel/kexec_crash_loaded

And the result of 'cat /proc/cmdline' is
BOOT_IMAGE=/vmlinuz-3.2.0-23-generic root=UUID=875d0cc9-2ba7-4eff-8cb0-08b56797162d ro crashkernel=384M-2G:64M,2G-:128M

Originally, the kdump services cannot be start due to miss vmcoreinfo. I am trying to using makedumpfile (1.3.4) to generate 1 vmcoreinfo. But fail eventually and I got (cmd: makedumpfile -g vmcoreinfo-3.2.23 -x vmlinux):  
generate_vmcoreinfo: Can't find the memory type.
makedumpfile Failed.

I did some google search and someone says that vmcoreinfo has already incorporate into kernel after 2.6.32(?) and will placed at /sys/kernel/vmcoreinfo.

So I modify the /etc/init.d/kdump so that it won't check vmcoreinfo under /boot/ directory but check /sys/kernel/vmcoreinfo.

And the kdump is running, but still fail to generate crash dump.

Can someone help on this?

have a look at: man proc ( search for /proc/sys/kernel/panic_on_oops) may be this helps you.

---

### Post by legolin on 2012-12-05
hi, rnerwein
    Thank you for provide information. After this, I can generate .crash file: /var/crash/_usr_cloudos_dms_bin_tool_volume-tool_test.py.0.crash.

I try to using apport-retrace to open this file, but fail with response "ERROR: report file does not contain one of the required fields: CoreDump Package ExecutablePath"

I think the  /sys/kernel/vmcoreinfo should not be the one to lunch kdump service...../_\

Can you help on this more?! 

Thanks a lot

---

### Post by legolin on 2012-12-05
Meanwhile, when I echo c > /proc/sysrq-trigger, the system won't reboot. XD

---

