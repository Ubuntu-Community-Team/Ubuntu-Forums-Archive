---
title: "Startup freezes"
date: 2014-07-13
forum: General Help
---

### Post by peterqb on 2014-07-13
Running 14.4 in Virtual Box 4.3.12 on OS X Mavericks (10.9.4).

Ubuntu doesn't start. I get the following in the startup box:

ith apic=debug and send a report. Then try booting with the inoapie option.
[ 0.412000]
[ 0.412000] CPU: 0 PID: 1 Comm: swapper/0 Not tainted 3.13.0-24-generic 1147-U
kuntu
[ 0.412000] Hardware name: innotek GmbH UirtualBox/UirtualBox, BIOS UirtualBo
k 12/01/2006
[0.412000]0000000000000008 ffff88007c7ebdf8 ffffffff81715ac4 ffffffff81a47
f8
[0.412000]ffff88007c7ebe70 ffffffff8170ecc5 0100000000000008 ffff88007c7eb
80
[0.412000]ffff88007c7ebe20 ffffffff8170f7e6 0000000000000046 0000000000000
d6
[0.412000]Call Trace:
[0.412000]Iafffffff81715ac4>1 dump_stack4-0x45/0x56
[0.412000]Iafffffff8170ecc5>1 panic-F0xc8/0x1d7
[0.412000]Iafffffff8170f7e6>1 7 printk4-0x67/0x69
[0.412000]Iafffffff81d49c4d>1 setup_IO_APIC-1.0x5f7/0x7b6
[0.412000]Iafffffff81d46377>1 native_smp_prepare_cpus4-0x36f/Ox3c7
[0.412000]Iafffffff81d35039>1 kernel_init_freeable-FOxbe/0x200
I0.4120001Iafffffff81703fa0>1 7 rest_init4.0x80/0x80
I0.4120001I<ffffffff81703fae>1 kernel_init+Oxe/0x130
[0.412000]Iafffffff817263fc>1 ret_from_fork-F0x7c/OxbO
[0.412000]Iafffffff81703faO>1 7 rest_init4.0x80/0x80
[32.768061]random: nonblocking pool is initialized


I think the start of the process is missing from this log, but if anyone can suggest something, I'd be grateful.

The installation is for just trying out Ubuntu, with little else on the virtual machine, so a reinstallation would not be disastrous.

TIA
--
pqb

---

