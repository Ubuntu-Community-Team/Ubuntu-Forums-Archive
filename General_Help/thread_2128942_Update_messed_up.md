---
title: "Update messed up"
date: 2013-03-24
forum: General Help
---

### Post by wetzeldc on 2013-03-24
After installing the last update (which ran an unusually long time) on 3/17/13 my desktop system fails after startup.  Everything is OK for about 10-20 seconds, then the screen blinks and the launcher and tool bar disappear.  If left alone the screen will blink black 2-3 times for a minute or two before everything is frozen.  If started in Recovery Mode it runs OK.  Any ideas where the problem is and how to fix it?

---

### Post by Bashing-om on 2013-03-24
wetzeldc;

Are you running a proprietary graphics driver? Maybe that got broke in a update process ?

Can you successfully boot from the grub menu an older kernel ?

Further advise is pending ->[INDENT=4]try'n to help

[/INDENT]

---

### Post by wetzeldc on 2013-03-24
On first try it did boot OK and continued running by booting with previous version. There was one System program problem error message but it has continued running OK.  So I guess I will continue using the older boot version.  Will this mess up further updates?

---

### Post by Bashing-om on 2013-03-24
wetzeldc;

To run the older kernel will not adversely affect updates. At this point all that is known is "something" in the new kernel is not compatible.
Maybe a graphics driver ? If you want to pursue the issue, additional info is required. The more likely thing is graphics.
Let's do this:To see your graphics card and info:
With the older kernel booted post the output of terminal codes:
```
sudo lshw -C display
lspci -nnk | grep -iA3 vga
```
Reboot into the new kernel and run those commands again, post these outputs. Looking to see if the same driver is loaded.[INDENT=3]
one step at a time

[/INDENT]

---

### Post by wetzeldc on 2013-03-26
[SIZE=4][SIZE=2]Perhaps of interest is that the error message refers to:
apport-gpu-error-intel.py[/SIZE][U]

Old Version 3.2.0-38[/U][/SIZE]

 

 david@No2:~$ sudo lshw -C display  
 [sudo] password for david:  
   *-display                
        description: VGA compatible controller  
        product: 2nd Generation Core Processor Family Integrated Graphics Controller  
        vendor: Intel Corporation  
        physical id: 2  
        bus info: pci@0000:00:02.0  
        version: 09  
        width: 64 bits  
        clock: 33MHz  
        capabilities: msi pm vga_controller bus_master cap_list rom  
        configuration: driver=i915 latency=0  
        resources: irq:55 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)  
 david@No2:~$ lspci -nnk | grep -iA3 vga 
 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)  
 	Subsystem: ASUSTeK Computer Inc. Device [1043:844d]  
 	Kernel driver in use: i915  
 	Kernel modules: i915  
 david@No2:~$  
 

 

 [SIZE=4]_New Version 3.2.0-39_[/SIZE]

 The following was obtained while running in Recovery Mode.

 
david@No2:~$ sudo lshw -C display 

 [sudo] password for david:  
   *-display UNCLAIMED      
        description: VGA compatible controller 
        product: 2nd Generation Core Processor Family Integrated Graphics Controller 
        vendor: Intel Corporation 
        physical id: 2 
        bus info: pci@0000:00:02.0 
        version: 09 
        width: 64 bits 
        clock: 33MHz 
        capabilities: msi pm vga_controller bus_master cap_list 
        configuration: latency=0 
        resources: memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64) 
 david@No2:~$ lspci -nnk | grep -iA3 vga 
 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09) 
 	Subsystem: ASUSTeK Computer Inc. Device [1043:844d] 
 	Kernel modules: i915 
 00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04) 
 david@No2:~$

---

### Post by Bashing-om on 2013-03-26
wetzeldc;

"[SIZE=4][SIZE=2]apport-gpu-error-intel.py" is a known bug // If you update to the most recent kernel, should be resolved.
Your output [/SIZE][/SIZE][SIZE=4][SIZE=2][SIZE=4]_Old Version 3.2.0-38_[/SIZE][/SIZE][/SIZE][SIZE=4][SIZE=2] looks good, Perhaps the only problem is the known bug.
```
uname -r
``` to see the kernel version presently loaded (12.04 mine ->3.2.0-39-generic// 3.5 series can be done)
I do not recall the date of the last update [SIZE=2]a[/SIZE]vail[SIZE=2]a[/SIZE]ble-ity, if the last update causing your problem was prior to this (.39); Try updating again. 

[SIZE=2]Recovery mode[SIZE=2] - Graphics driver, no driver will be loaded in this instance[SIZE=2]. Display will be hand[SIZE=2]le[SIZE=2]d by the [SIZE=2]in-kernel driver "vesa"[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE].
[INDENT=3]
just try'n to help

[/INDENT]

---

