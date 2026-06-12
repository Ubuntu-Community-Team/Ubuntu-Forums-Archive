---
title: "Lenovo P series (P50, P71) - Ubuntu 18.04 does not complete shutdown"
date: 2020-03-12
forum: General Help
---

### Post by wb0gaz on 2020-03-12
I've installed Ubuntu 18.04 on secondary storage devices (both NVME and SATA SSD) on both a Lenovo P50 and a Lenovo P71.

In both cases, Ubuntu does not complete shutdown (requires hard reset with power button.)

Once, about 2 years ago, I had installed Ubuntu 18.04 on the P50 and encountered this problem and the solution (so it is possible to work properly), however, I've not been able retrieve my notes from that issue. In the case of the P50, there are 3 storage devices (one with Windows 10, one with Ubuntu 18.04 from prior time that was "fixed" to shut down normally, and one with Ubuntu 18.04 just installed that fails to shut down. In the case of the P71, there are also 3 devices, however, both installs of Ubuntu 18.04 (on two of the three storage devices) fail to shut down.

The BIOS/UEFI settings are the same in all (former and current) cases for both machines. 

During shutdown, the following messages appear:

[ OK ] Reached target Final Step.
Starting Reboot...
[ 30.xxxx] systemd-shutdown[1]: Failed to wait for process: Protcol error
[ 30.xxxx] kernel BUG at /build/linux-60XibS/linux-.15.0/drivers/pci/msi.c:342!
[ 30.xxxx] invalid opcode: 0000 [#1] SMP PTI
(more lines)
[ 30.xxxx] Call Trace:
(more lines)
[ 30.xxxx] ---[ end trace xxxx ]---

(then the machine needs a hard powerdown)

Thank you for a pointer to the issue/solution/advice!

Dave

---

### Post by wb0gaz on 2020-03-12
This turns out to have been self-inflicted user error - neither machine was connected to the internet during the installs, and the problems were evidently fixed in some subsequent update, because once the new installs on both machines were updated, the shutdown/reboot problems were fixed. This is also shows a benefit of the "update during install" feature of Ubuntu installations.

Sorry for the bandwidth!

Dave

---

