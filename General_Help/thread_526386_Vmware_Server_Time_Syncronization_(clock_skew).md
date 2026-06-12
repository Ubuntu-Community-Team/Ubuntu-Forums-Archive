---
title: "Vmware Server Time Syncronization (clock skew)"
date: 2007-08-15
forum: General Help
---

### Post by tygrel on 2007-08-15
Specs:

system :    Dell Optiplex 745 
Processor: P4 2.4 Core Duo 2
Memory:    4GB ram
OS:             Ubuntu 7.04 64-bit
Kernel:        2.6.20.16-server


In my BIOS, I have the option [Virtualization = On]

A lot of people have been complaining about Vmware time syncronization issues with running Vmware server on a linux host (in my case Ubuntu) using a linux guest having the clock run too slowly.

My problem is a bit different.

I am running Vmware Server 1.02 on Ubuntu and all of my Vmware guests are Windows 2003 server.  I have Vmware tools installed with 'Time sync with host' enabled.  The clock on these guest systems run FAST.  It seems that the clock speed is doubled.

I was under the impression this was fixed in linux kernels 2.6.18 or above, but it seems not.  

If anyone has been able to resolve this issue please let me know.  I have done some searching on VMware and forums, but it seems that the fixes include adding kernel parameters to fix SLOW clocks.

TIA,
Tygrel

---

### Post by Midahed on 2007-08-15
I had the same problem with VMware Server running on Ubuntu 7.04 Feisty 64-bit with a Windows 2000 guest.

It's all down to VMware getting confused by the power management features on your motherboard - in my case it was AMD's Cool 'n' Quiet throttling back the cpu clock.

The fix is here - it worked for me:-

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1591](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1591)

Hope this helps.

I also found a utility that would specify the range of clock speeds used by the processor, but I haven't been able to find it again....

Correction - just found it - cpufrequtils - it's in Synaptic.

Mike

---

