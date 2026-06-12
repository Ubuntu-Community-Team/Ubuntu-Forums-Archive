---
title: "Suspend-to-RAM timer setting (without X)"
date: 2008-03-19
forum: General Help
---

### Post by hemish on 2008-03-19
How do I setup sleep (suspend-to-RAM) and hibernate (suspend-to-disk) from the command line?

I have a laptop with Ubuntu server Gutsy (only use it as low power home server), so I don't have X, but still want the machine to enter ACPI state S3 (suspend-to-ram) after some idle time. I just don't know where to set the idle time?

I can manually suspend-to-ram with 

```
echo -n mem > /sys/power/state
```

seen at [http://www.linux.com/feature/54610](http://www.linux.com/feature/54610).

But how do I set it to do so automatically?

---

### Post by hemish on 2008-03-20
Found [sleepd]("http://packages.ubuntu.com/source/gutsy/sleepd") which could be a step in the right direction.

I already run laptop-mode-tools. Can that do the trick for me already if setup correct, or do I still need sleepd?

---

### Post by hemish on 2008-03-20
Getting closer.

With sleepd and these settings in /etc/default/sleepd, I get the machine to suspend-to-ram after 60 minutes.

```
PARAMS="-u 3600 -U 3600 -a -s suspend.sh"
```

with suspend.sh being a simple bash line with

```
echo -n mem > /sys/power/state
```

But as the keyboard and mouse are never used on the machine itself, since I ssh to it, it sleeps when I don't want it to. So I have to let it monitor some other kinds of interrupts too. I have tried to identify my NIC with lspci 

```

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
	Subsystem: IBM Unknown device 0577
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Capabilities: [d0] Express Endpoint IRQ 0

```

and have now extended the options to

```
PARAMS="-u 3600 -U 3600 -a -i 16 -s suspend.sh"
```

But unfortunately the machine never felt asleep when being left alone over night - without any clients connected.

Is it possible than something else in Ubuntu server is keeping the NIC active? And what could be mose obvious candidates?

---

### Post by hemish on 2008-03-22
Found additional good information and script (autosleep.sh) at [http://ubuntuforums.org/showthread.php?t=406650]("http://ubuntuforums.org/showthread.php?t=406650").

---

