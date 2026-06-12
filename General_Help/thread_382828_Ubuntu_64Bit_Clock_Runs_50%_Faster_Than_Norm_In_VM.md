---
title: "Ubuntu 64Bit Clock Runs 50% Faster Than Norm In VMware Virtual Machine"
date: 2007-03-12
forum: General Help
---

### Post by veletron on 2007-03-12
Hi

I have installed Ubuntu 6.10 x64 in a VMware virtual machine. The clock is gaining 30 seconds every minute. I have tried a selection of supposed solutions to this issue, but none of them work.

Host hardware is an Athlon X2 with 4GB mem.

This far I have tried the following kernel boot options:

noapic
nolapic
acpi=noirq
noapic
acpi=off
noapictimer
irqpoll
acpi=noirq
clock=pmtmr
notsc
no_timer_check

I have tried these both combined and together. For the record, my old Mandrake10 (32 bit) install has no clock issues running under vmware.

Anyone know how to fix this?? I need an accurate clock!!

Cheers

Nigel

---

### Post by m.musashi on 2007-03-13
I have this problem on my athlon desktop but not my core duo laptop. I don't know if that means it's related to the athlon or just coincidence. I installed vmware tools but that didn't help. Have you tried installing the tools? Other than that I'm sorry I can't help but maybe someone has a solution.

---

### Post by blake.ong on 2007-03-18
I am having the same problem in 64bit Ubuntu 6.06 LTS server edition running on opteron. My workaround is updating my time with a NTP server.

[http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/](http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/)

---

### Post by hashinclude on 2008-05-09
I was having the same issue with VMWare on Ubuntu 7.10 (on a Laptop). A dig through the VMWare forum points to this:

  [http://communities.vmware.com/message/7818](http://communities.vmware.com/message/7818)

Apparantly, VMware may not be able to understand automatic CPU Frequency scaling (or its time sync may be off).

---

