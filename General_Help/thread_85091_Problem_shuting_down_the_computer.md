---
title: "Problem shuting down the computer"
date: 2005-11-01
forum: General Help
---

### Post by Cuppa-Chino on 2005-11-01
hi my computer crasheds when I shut it down via the gnome shutdown button, the following is the error message I get:
```

[4304068.889000]
7c018c 00000000
[4304068.889000] Call Trace:
[4304068.889000][<c02527aa>] fib_lookup+0xa0/0xdf
[4304068.889000][<c022887b>] ip route output slow+0x27c/0xb6a [4304068.889000][<c011ba4a>] _mod timer+0x58/0x69
[4304068.889000][<c0229284>] ip route output_flow+0xibi0x67
[4304068.889000][<c0241216>] tcp_u4_rebuild header+0x101/0xib0
[4304068.889000][<c01124e3>] try _to_wake up+0x3f/0x73
[4304068.889000][<c023bda9>] tcp_retransmit skb+0x16f/0x2ba
[4304068.889000][<c023da39>] tcp write timer+0x0/0xa5
[4304068.889000][<c023d907>] tcp_retransmit timer+0x217/0x349
[4304068.889000][<c023dab1>] tcp write timer+0x?8/0xa5 
[4304068.889000][<c011c049>] run timer_softirq+08x126/0x14c 
[4304068.889000][<c0119060>] _do_softirq+0x34/0x7d 
[4304068.889000][<c01190cb>] do_softirq+0x22/0x26 
[4304068.889000][<c0104caa>] d0_IRQ+0x1e/0x24
[4304068.889000][<c01038b6>] common_interrupt+0x1a/0x20 [4304068.889000][<f8941a38>] acpi_processor_idle+0x0/0x29b [processor] 
[4304068.889000][<f8941b37>] acpi_processor_idle+0xff/0x29b [processor]
[4304068.889000][<c01010ai>] cpu_idle•0x2d/0x42
[4304068.889000][<c0324665>] start-kernel+0x176/0x178
[4304068.889000] Code:    Bad EIP value.
[4304068.889000] <0>Kernel panic - not syncing: Fatal exception in interrupt 
[4304069.264000]

``` 
I am not sure but from the output I would guess power management of the processor could be the problem, is this the correct assumption?

Also can I turn off time sync with ntp.ubuntu at start up? I never works and only holds up booting the computer.

Thanks :eek:

---

### Post by felix_stegerman on 2005-11-01
I can't help you w/ the crash, but you can disable or uninstall ntpdate
to get rid of the time sync.

e.g. rename /etc/rc*.d/S*ntpdate to disabled_Sxxntpdate
(just prepend disabled_ to the name) to disable.


Felix

---

### Post by Cuppa-Chino on 2005-11-06
thanks felix

anybody help me with the shutdown issue?

---

