---
title: "Empty filesystemss after kernel upgrade"
date: 2007-02-04
forum: General Help
---

### Post by Toontje on 2007-02-04
Hi all,

I have a strange problem: after I upgrade my kernel, all date on my /dev/hdc is gone.

I have installed 6.06 LTS on my ASUS A8V-VM SE with 2 PATA disks.
Because of the VIA VT8237A controller, I don't have DMA support, so my HD's are very slow.

I found that the VIA VT82367A is supported from kernel 2.6.18 so I upgraded the kernel to 2.6.18.6.
I use the config of the original kernel (2.6.15-26) and the only thing I change is the CPU, which I change from Pentium Pro to Athlon 64.

After the first reboot I find that my HD's are fast now (with hdparm -Tt /dev/hda), but the filesystems on /dev/hdc are empty.

The filesystems on /dev/hdc are there, but I don't see any files in there.

When I change /root/grup/menu.lst to start with the old (original kernel), the files are back:confused: 

Anybody ideas??

---

