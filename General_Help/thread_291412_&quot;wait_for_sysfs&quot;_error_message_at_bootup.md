---
title: "&quot;wait_for_sysfs&quot; error message at bootup"
date: 2006-11-02
forum: General Help
---

### Post by egilfe on 2006-11-02
During boot-up I get the following error message:

"udevd-event [2970] wait_for_sysfs: waiting for '/sys/devices/platform/i8042/serio0/serio2/bus' failed"

Otherwise, everything seems normal, but the message is annoying and slows up bootup.

I have a Thinkpad T41p. 'serio2' is the name of the trackpoint device (which works fine). I'm running edgy, but the exact same message also appeared in dapper. 

I've seen that there's some info on this at
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/34286](https://launchpad.net/distros/ubuntu/+source/udev/+bug/34286)
(bug report 34286), here it's said that this "appears to be being caused by class/net/wifi0", and they propose to add "arp1" to the end of the file /etc/iftab. They say that this fixes the bug. However, my /etc/iftab was

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:10:c6:cf:32:aa arp 1
ath0 mac 00:05:4e:44:88:61 arp 1

...so the "arp 1" was already there. I even tried adding an additional "arp 1" to the end, but this produced several additional errors at bootup. So, the proposed "fix" doesn't help me.

Extensive googling doesn't help...

Any suggestions?

---

### Post by solotim on 2007-01-26
I get the exact same error. 
Help~~

---

### Post by Konami on 2007-06-09
> **solotim said:**
> I get the exact same error. 
Help~~

me too! is there a fix to this. I have Ubuntu 6.06 server. :KS

---

