---
title: "i915 Issues With Ubuntu 16.04"
date: 2016-09-04
forum: General Help
---

### Post by gajuith on 2016-09-04
Hi, 

Is there anyone that is familiar with the i915 video driver issues with 16.04? I've attempted the fix at [https://aboutsimon.com/blog/2016/07/20/Ubuntu-16.04-external-monitor-flickering-and-turning-off-on-intel-i915.html](https://aboutsimon.com/blog/2016/07/20/Ubuntu-16.04-external-monitor-flickering-and-turning-off-on-intel-i915.html) which did not correct the issue.

I have attempted to install kernel 4.6, but it only resulted in a blank screen immediately after the login screen was displayed upon boot-up.

The output of lshw -c video is as follows:

  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64)

Current kernel information is as follows:

simpsonc@simpsonc-nbk:~$ uname -r
4.4.0-36-generic

simpsonc@simpsonc-nbk:~$ uname -v
#55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016



When an external monitor goes blank, the following errors are sometimes written to syslog:

Sep  4 16:49:00 simpsonc-nbk kernel: [ 9709.832348] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
Sep  4 17:13:48 simpsonc-nbk kernel: [11197.640834] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe C FIFO underrun

It may also be worth noting that this seems to coincide with keystrokes, but this may be merely a coincidence. Any assistance or advise would be greatly appreciated as this has become quite annoying. Please let me know if any further information would be helpful.

---

### Post by gajuith on 2016-09-07
I have been able to successfully boot into kernel 4.6.4, and it appears to have corrected the issue.

---

### Post by mörgæs on 2016-09-08
Good, then please mark the thread 'solved'.

---

