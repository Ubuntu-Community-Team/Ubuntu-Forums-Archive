---
title: "Hibernate does not resume / suspend way too slow in Hardy (Thinkpad T40)"
date: 2008-05-03
forum: General Help
---

### Post by mcarro on 2008-05-03
I have upgraded from gutsy to hardy - mostly smooth.  Hibernate seems to actually hibernate, but when I restart the laptop it performs a normal boot.  I do not know whether this matter, but I resized and moved partitions shortly before upgrading - however, gutsy was working flawlessly.  Upon upgrade I manually changed /etc/initramfs-tools/conf.d/resume to point to the swap partition (I have 1Gb ram and 2Gb swap).

When hibernating, the following lines appear in /var/log/messages:

```
May  3 01:23:46 balboa gnome-power-manager: (mcarro) Hibernating computer. Reason: User clicked on tray
May  3 01:23:49 balboa kernel: [ 4321.185317] ACPI: PCI interrupt for device 0000:02:01.0 disabled
May  3 01:23:49 balboa kernel: [11523.638276] ACPI: PCI interrupt for device 0000:02:02.0 disabled
May  3 01:23:50 balboa avahi-autoipd(eth0)[4816]: if_indextoname() failed: No such device or address
May  3 01:23:50 balboa avahi-daemon[5619]: Interface eth0.IPv4 no longer relevant for mDNS.
May  3 01:23:50 balboa avahi-daemon[5619]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.3.181.
May  3 01:23:50 balboa avahi-daemon[5619]: Withdrawing address record for 169.254.3.181 on eth0.
May  3 01:23:50 balboa avahi-daemon[5619]: Interface eth1.IPv4 no longer relevant for mDNS.
May  3 01:23:50 balboa avahi-daemon[5619]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.192.
May  3 01:23:50 balboa avahi-daemon[5619]: Withdrawing address record for fe80::204:23ff:fe97:20f8 on eth1.
May  3 01:23:50 balboa avahi-daemon[5619]: Withdrawing address record for 192.168.0.192 on eth1.
May  3 01:23:53 balboa kernel: [ 4324.191219] PM: suspend-to-disk mode set to 'platform'
May  3 01:23:53 balboa kernel: [ 4324.191691] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
May  3 01:23:53 balboa kernel: [ 4324.191698] swsusp: Basic memory bitmaps created
```

and after that the computer (seems to) hibernates.  What can I look for in the messakes/syslog/kernel log files to find out what is lacking?

OTOH, suspend to ram works fine - except that resuming is *very* slow (and messages for the ntp daemon being shut off and restarted appear).  It is actually slower than booting the computer.

I'd be grateful for any help.  Also, if more information is needed, please let me know.

Thanks in advance!

---

### Post by mcarro on 2008-05-04
Solved the hibernation issue by manually running *update-initramfs -u -k all* after changing the contents of the resume file to point to the actual swap partition.

---

