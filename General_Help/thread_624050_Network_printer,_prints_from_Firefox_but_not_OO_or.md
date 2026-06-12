---
title: "Network printer, prints from Firefox but not OO or Evolution"
date: 2007-11-26
forum: General Help
---

### Post by bigH on 2007-11-26
I have just installed an HP Officejet Pro L7680 on my LAN.  It is connected directly to the HUB.  It was recognised and installed on my wife's M$ laptop, but my Ubuntu 7.10 printer configuration new printer option couldn't find it, so I installed it under "Other" using "socket://<<IP address>>:9100"

Test page prints fine and printing from Firefox goes without problem, but when I try to print from OpenOffice Writer or Evolution it gets sent from the local machine but nothing happens on the printer.

Is this a CUPS or a permission thing?  But then why would Firefox print OK?  I would really appreciate some help.

Thanks
[SIZE="4"]H[/SIZE]

---

### Post by bigH on 2007-11-30
OK, no takers yet but being ever hopefull here's an update:

I have played arround with different options for the printer in "Printer Set-up" and tried using the various HPLIP programs.  Result is the printer is visible on the network and works.  When I try printing from Evolution I get the following in DMESG:

> [ 6847.653206] audit(1196445674.387:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=7248 profile="/usr/sbin/cupsd"
[ 6847.798558] audit(1196445674.387:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=7251 profile="/usr/sbin/cupsd"


So it looks like a permissions issue, but where????

Help please
[SIZE="4"]H[/SIZE]

---

