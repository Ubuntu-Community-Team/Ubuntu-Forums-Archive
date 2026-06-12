---
title: "VMWare 'Interface vmnet1 is not marked &quot;UP&quot;.' after resuming host from standby"
date: 2007-01-10
forum: General Help
---

### Post by desmondo on 2007-01-10
On my Linux Ubuntu Dapper Drake 6.06 host, after resuming from ACPI sleep, I am unable to boot my Windows XP guest with a NAT network connection.

Immediately upon powering on the virtual machine, I get this Warning:

[INDENT][I]Interface vmnet1 is not marked "UP". This should be done at boot time; please check your installation and try again after you have corrected this.
Virtual device Ethernet1 will start disconnected.[/I][/INDENT]

The only workaround I know of is to reboot my host (obviously annoying, as it negates the benefit of being able to standby).

Is there a way to ensure that when my Ubuntu host wakes up from ACPI sleep the VMWare virtual network interfaces are properly configured? Alternatively, is there some command I can run to re-configure the interfaces so I don't have to reboot the host?

Thanks for your help!

---

### Post by desmondo on 2007-01-13
Thanks to jimpop on the [VMWare forum]("http://www.vmware.com/community/thread.jspa?threadID=67809&tstart=0"):

> try adding vmware to STOP_SERVICES in /etc/default/acpi-support, this will shutdown and restart vmware between hibernations/suspends, as will as restarting vmware on resume. Also, you will need to restart /etc/init.d/acpi-support after making this change, or just do a clean reboot.

---

### Post by aexl on 2007-06-20
you might be interested to read here:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/18180](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/18180)

---

