---
title: "Syslog warning and errror: What does this mean?"
date: 2006-07-30
forum: General Help
---

### Post by cantormath on 2006-07-30
**KERNAL WARNING...**
Jul 29 06:23:45 localhost kernel: [17179569.184000] **WARNING:** NR_CPUS limit of 1 reached.  Processor ignored.

**NETWORKMANAGER ERROR**
Jul 29 19:46:54 localhost NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul 29 19:46:54 localhost NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): nm-dbus-nmi.c:522 (nm_dbus_get_networks_cb): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks

Im more concerned about the first error, mainly because the wireless is working fine, however, any help would be nice.

---

### Post by vigleik on 2006-07-30
Do you by any chance have a dual core processor, but using the regular ubuntu kernel? The regular kernel only has support for one CPU, so you need to install a new kernel, one with SMP.

Vigleik

---

### Post by cantormath on 2006-07-31
> **vigleik said:**
> Do you by any chance have a dual core processor, but using the regular ubuntu kernel? The regular kernel only has support for one CPU, so you need to install a new kernel, one with SMP.

Vigleik

I have hyperthread Pentium 4 chip.

Would that classify as dual core?  I know that I am able to turn the hyperthread off in the bios.

I have tried the smp kernal before, but that usually caused wierd stuff to happen, maybe I picked the wrong one. I did install it through synaptic.

**here is my lshw**
[http://cantormath.com/lshw.txt](http://cantormath.com/lshw.txt)
**my hwinfo**
[http://cantormath.com/hwinfo.txt](http://cantormath.com/hwinfo.txt)
**my lspci** which isn't to helpful.
[http://cantormath.com/lspci.txt](http://cantormath.com/lspci.txt)

[I]laptop:~/Desktop$ uname -srv
Linux 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006

laptop:~/Desktop$ sudo lshw |grep cpu
     *-cpu
          bus info: cpu@0
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl est tm2 cid xtpr cpufreq
        *-logicalcpu:0
        *-logicalcpu:1[/I]

So if anyone could help me with installing the smp kernel, that would be 
greatly appriciated.

---

