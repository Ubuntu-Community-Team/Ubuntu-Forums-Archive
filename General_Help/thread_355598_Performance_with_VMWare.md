---
title: "Performance with VMWare"
date: 2007-02-07
forum: General Help
---

### Post by darylw on 2007-02-07
Not sure If this is the proper place for this post but here goes...

We have recently moved most of our apps from a single (P4 3.0) CPU server with 2Gb RAM and SBS 2003 Standard Edition and 100mb NICS to a new server running Ubuntu 6.06 LTS as the host and SBS 2003 Premium as a Virtual Machine. We also have an IP COP Vm installed on this host. This host has Dual AMD Opteron 265 (Dual Core) CPU's, 4Gb RAM, 3Ware 9500 RAID Controller (Raid 1 array with hot spare), and a SuperMicro H8DAE-O Motherboard with Dual GB NIC's.  

The APPS are slightly slower than the old server but worst of all is that randomly throughout the day they simply stop responding for a few seconds then proceed again at normal speeds, sometimes faster than normal for a few seconds. :confused: 

Looking at the realtime CPU chart (Attached) it appears one processor is handling all the load. Notice the SBS Guest hitting almost 100% usage at the same time CPU3 hits almost 100% usage, and all the other CPU's running at less than 25%. Why is this happening? Should not the load be close to equally balanced between all CPU's?

Anyone have any idea's as to how to determine were the problem lies...Disk I/O, NIC'S, VMWare Layer, CPU load balancing mentioned if the paragraph above, any known issues with the hardware used Etc.?

Thanks for any insight.

---

### Post by s@bertooth on 2007-02-07
Hi! If You use VMWare Workstation, You should enable the support for 2 CPU-s for the virtual machine. It can be done by pressing ctrl-D if VMWare Workstation has focus, and there You will see Processors in the Hardware tab...try to set to 2...it should help... ):P

---

