---
title: "XDMCP Cannot connect"
date: 2007-12-31
forum: General Help
---

### Post by JointTech on 2007-12-31
Using Gutsy on laptop and desktop.

desktop has 2 NICs
Bind9
DHCP Server.
Shorewall Firewall

eth0 ->internet via DHCP
eth11 ->LAN static IP

From laptop login screen I choose options/Remote Login via XDMCP

I get the XDMCP login chooser. 
it finds my desktop (and itself)
name/ip info is correct.

After selecting the desktop and clicking connect I get a flash to terminal style screen with something about loading boot scripts boot.rc and then it switches to a Windows with a cursor on it.  I cant move the cursor.  It then imediately drops me back to the original login window.

I heard XDMCP need reverse DNS working correctly so I fixed that.  I also verified that my firewall is not interfereing by running a tail on var/log/messages and syslog.  I then attempted to connect.  It shows no errors.

I ran Wireshark and it shows XDMCP query and then a reply of Willing.  However then there is no more talking between them.

The desktop has a Nvidia graphics card and is using restricted driver.

FWIW I cant connect to the laptop from the laptop either.  I also tried to connect to the laptop from the desktop and the same thing happens.

Any ideas?  this is driving me crazy.

---

### Post by disturbed1 on 2007-12-31
Dumb question ;) Do you have remote access enabled?

For XDMCP I use this -

Xephyr :1 -query NAS

NAS is the name of the machine I'm connecting to. It also works with IP address, but once a month depending on the number of PCs on the network NAS may get a new IP.

---

